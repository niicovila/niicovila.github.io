---
layout: page
title: Legal Research Assistant using LLMs
description: Development of a Research Assistant in the realm of Law to draft case briefs
img: assets/img/legal_ra.png
importance: 6
category: Research
---

As part of my internship in a research group at the University of Chicago that leveraged Machine Learning and AI, my team developed an AI system capable of dissecting large PDF files of legal opinions and drafting appellate legal briefs. 
We worked closely with a team of attorneys that helped us define methodologies and implement different strategies.

### Motivation
Legal research, whether for litigation or regulatory compliance, is typically considered a high-skill task that requires trained and experienced lawyers. However, there is a formulaic component to it. This is apparent from an examination of teaching methods for legal writing and research and from the organization and style of legal memos, briefs, and opinions. It is true that there is an art to an elite legal brief, but that art is manifest in a small subset of documents written by a smaller number of advocates. For the vast majority of practical legal research, formulaic methods matter more than deviations from them.
Given that legal research is largely formulaic, one might ask whether it can be performed effectively using artificial intelligence tools, such as large language models. Here, we try to use such tools to complete two basic tasks: briefing a case and writing the sort of legal memos assigned to first-year (IL) law students at the University of Chicago.
These are non-trivial tasks. One can certainly paste a legal assignment into a large language model (LLM) such as ChatGPT. But the answer will have a few shortcomings. First, the LLM may not have “knowledge” of the cases required to answer the legal question. This is only partly solved by giving it access to the internet, as Microsoft has done with Bing. Second, even with access to cases, LLM’s have difficulty keeping text in memory. Currently GPT 4 can only hold X tokens (equivalent to Y words) in memory; but the typical legal case is Z words. Third, an LLM needs a lot of context and instruction to know how to structure an answer. It needs an outline; else it may miss important issues in its answer. Fourth, LLM are notorious for making things up [1]. This can trigger legal sanctions. Finally, it is unclear whether and how a transformer, whose job is to predict the next word in a sentence, is capable for making the sort of logical, legally-cognizable arguments required for legal research.
We address each of these issues in building software that can use LLMs to brief a case and to complete two assignments given to first-year law students in the legal writing and research class at the University of Chicago Law School.

### Methodology

1. First, we synthesize cases that the user uploads or that our search process retrieves. This synthesis has two goals: condense cases so an LLM can hold them in memory and index cases so we can search them for details as we write a memo. Think of this step as one would a lawyer taking notes on cases. We analogize our synthesis to a pyramid or an (upside-down) tree because our formal summarization process has multiple steps or layers that each prioritize a smaller and smaller subset of the key information in a case. Second, we build a temporary database of the sythesized cases, or a forest of case trees if you will.

2. Obtain from each case the specific and generic attributes that are relevant to the user’s legal question and to use these generate weights for each case that help us prioritize which cases are the most important for our answer.
   
3. Importantly, we convert each element of the outline into a question. E.g., what are the material facts of the controversey, what is the legal question presented, or what is the relevant legal test? We use these questions as prompts to an LLM to draft each section of a memo or brief. For each prompt, we provide the LLM’s memory our weighting and synthesis of the most relevant cases. After the initial draft of each section of the outline, we do post- processing to improve writing style and ask if there are places where more citations or a quote are appropriate.

4. To ensure that the LLM is not “hallucinating” we test each factual and concrete legal claim (e.g., a citation, statement of a test, or quote) with multiple, independent calls to a LLMs asking about that specific fact. Only when there is a high rate of agreement that the statements are true do we keep it in the draft

#### **Basic UI**
We've developed a very simple UI to make this process easy for any user. Intuitively, a user uploads a legal opinion -in future versions we would already have a database of cases or could take multiple input files-. Since we are still improving our information retrieval method, we are letting the user experience with different specificity levels from where to index the tree. Finally, the system will output a case brief in pdf format.
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/legal_ra.png" title="LegalRA" class="img-fluid rounded z-depth-1" %}
    </div>

</div>
<div class="caption">
    UI of the Legal Research Assistant
</div>

#### **Case synthesis process**
In this section we explain how we synthesize cases to satisfy the limited memory of existing LLMs and how to index cases for quicker search for, e.g, quotes. We then explain how we create a temporary database of cases relevant to the user’s legal question.

##### **Building a tree**: 
We first explain how we synthesize a given case. We start with words from that case organized into useful sets such as paragraphs and sections. From these subsetted batch of wordswe construct pyramids (or upside- down “trees”) that help us both synthesize and search cases more efficiently than unorganized words or raw sets.
There are two problems with giving an LLM one or more raw opinions, i.e., all the words in an opinion in order, and asking it to answer questions based on them. First, LLM’s often cannot hold in memory a whole opinion, let alone multiple opinions. So we need to reduce the dimensionality of opinions. We need to compress an opinion without losing key information. Second, opinions have a lot of redundancy and storing a whole opinion wastes memory. Our synthesis will overcome both problems.
However, it is also important to have the raw opinion on hand. First, we may need to quote from it. Second, we may need it to validate claims about it made by an LLM, i.e., to weed out hallucinations about the case. Our synthesis can be used as an index to quickly search cases for quotes or validate claims. The lowest level of a case pyramid is actually the words of an opinion in order. We need this level for quotes. The next level is sets of words that comprise either citable segments or sentences not in citable segments. The citable segments will give us sequences of words that stand for legal propositions or claims and associated citations. These can be transplanted (without plagiarizing) into memos as needed. The third level is paragraphs, which are comprised of sequences of citable segments and remaining sentences. So far, no synthesis has been done. The fourth level synthesizes 2 adjacent paragraphs in the same section into a few sentences. This is the first time an LLM is used for synthesis. We focus on adjacent paragraphs because they are likely redundant or logically connected. We do this only within sections because sections typically cover different topics. The next few layers repeat this process over multiple summaries until we have section-level summaries. We do not simply go from paragraphs to a section-level summary because there may be different topics covered within a section. For example, a section may deal with one legal claim. That section may have separate paragraphs on facts, procedural posture and standard of review, on a legal test, and then on application of (parts of) that test. A memo may want to pick up each of those parts separately, not just as a whole. Once we have section-level summaries, we repeat synthesizing until we have a few-sentence summary of the entire case.

##### **Indexing the tree**: 
The pyramid or tree that we construct has natural connections: each summary block rests on two source blocks. The information in the summary block serves as index for each source block. This index is a bit different than a book index. In a book, there is just 1 index. But in our pyramid, a summary block high in a pyramid is an index that is less informative than a summary block lower in the pyramid.
To figure out which index to use, we need either an index of indexes or a quick search. Since the indices are recursive, an index of indices would be redundant. Instead, we use search.

Specifically, for any inquiry, we allocate a search time budget T to allocate across cases. We first search at the highest level of a pyramid for a hit. If we receive it, judge the quality of the hit and we move down to the source blocks for that summary. We identify the source block that is responsible for the hit and then repeat the process. During this process we keep track of time. Each time we take a step, we subtract the time taken by the step from our time budget. We keep moving down the pyramid following hits until additional moves do not yield substantial improvement in the quality of the hit or we run out of time on our time budget.

If we do not receive a quality hit on the top level and we have time remaining, we search in the next lower later of the pyramid for a hit. If we find a hit, then we proceed as in the last paragraph. If we do not and have time remaining, then we search the next lower later of a pyramid.
These steps make sense for one case. But what if we have multiple cases. We use two rules. First, we try to spread time across similar quality cases. I.e., if we have 2 equal quality hits and time for 2 searches, we go 1 layer down in each cases rather than 2 layers down in any one case. This is motivated by the intuituion that there is diminishing returns to search and that we have an option to search further when we do post-processing on a memo.
Second, if we have N identical value cases to search but time to search only M < N cases, we randomly choose which cases to search. (If the cases are of different quality, i.e., onse set where we are pursuing hits and another set where we have found no hits yet, we first exhaust options in the high quality cases before we turn to low quality cases.)

**Memory Issues**: One might ask if a pyramid creates too much redundancy and actually overloads memory. We already have the base layer, though that is stored in ROM. More importantly, each layer includes information that is in the layer beneath it. However, the top layers also lose information. And lower layers are taking up more memory.
We view the pyramid as giving us options given the memory limitations of the LLM. The more cases that are required for a memo, the smaller the amount of information we can keep in memory in each case. The pyramid gives us the option to choose the optimum generality and amount of information for each case.
Suppose memory from an LLM call is capped at M in some memory-space units. Moreover, suppose there are N equally weighted cases to be analyzed in an LLM call to answer a legal query. Then we want M/N amount of information (in memory-space units) on each case. If a pyramid on a case scales information (in memory units) at the rate of $2^k$, where k represents layers, then we want to store information at pyramid level k where $2^k$ = M/N on each case. Of course, we may not want to weight each case equally, a topic we address later. But even in this case, we can choose the level of information we want to each case and extract just that amount based on each case’s pyramid.

#### **Retrieving the relevant 'Attributes' from a legal question**
Case briefs have a very well defined outline that can be summarized as: 1) Case citation & Date, 2) Facts, 3) Procedural Posture, 4) Issue, 5) Rule, 6) Holding, 7) Analysis, 8) Concurrences or dissents.

Under this structure, we consider the Analysis to be the most demanding segment, as it endeavors to elucidate the rationale guiding the judges' decisions in resolving the case. Since the process of obtaining all the attributes is not trivial, here we will just focus on how to obtain the Analysis:

1. **Identification of the legal tests**: We use a prompt to provide GPT with the case's context, facts, relevant law, and the issue at hand. Based on this information, we identify the specific legal tests that the case revolves around. For each factor within the test, we generate a list of subfactors. For example, if a test is related to the Equal Pay Act, a factor could be "Are the jobs equal?" and the corresponding subfactors might include "Were the jobs performed under similar conditions?" or "Did the jobs require equal skill, effort, and responsibility?"

2. **Hypothetical answer generation**: Once we have the outline of the test (including factors and subfactors), we create hypothetical answers for each subfactor. These hypothetical answers serve as "ideal" or "invented" answers and are used to facilitate the similarity search algorithm, drawing inspiration from HyDE (Gao et al.). By generating these hypothetical answers, we can help the algorithm identify the relevant information within the case text that likely contains the actual answer to each subfactor. It is important to note that these hypothetical answers are used solely for the purpose of similarity search and are never included in the analysis generation.

3. **Analysis generation for each subfactor**: We generate a hypothetical answer for each subfactor and then search for passages within the case that are similar to the hypothetical answer. These passages are likely to contain the actual answer to the subfactor. Once we have identified the relevant paragraphs, we use them as context to prompt GPT and analyze the corresponding subfactor. Only the actual information from the case is used in this analysis generation process.

4. **Compilation of the analysis**: We compile the analysis for each subfactor of each factor in the test. By combining the responses for each subfactor, we can determine the result of the factors. Similarly, by analyzing the results of the factors, we can generate the final result of the test. However, it is important to note that the analysis generated through this process is comprehensive rather than concise, which is not suitable for a case brief.

5. **Summary generation for each factor**: We create a summary for each factor in the test, focusing specifically on the "how" and "why" of the analysis. Instead of repeating the analysis using different wording, we extract only the relevant information from the judges' decisions.

6. **Compilation and summarization of the full analysis**: Once we have the summaries for each factor, we combine them and summarize the entire analysis. The goal is to ensure that the final output is cohesive and contains all the relevant information without repetition. Since each factor is generated independently, there may be repeated information across factors, which we eliminate in this step.

7. **Rewriting the summarized analysis as a case brief**: After obtaining the summarized analysis, we prompt GPT once again to rewrite it in the appropriate style and format of a case brief.

### Examples
#### **Legal Opinion 1**:
<object data="/assets/pdf/corning_glass.pdf" width="600" height="700" type='application/pdf'></object>

#### **Analysis Tests (uncompiled)**:
<object data="/assets/pdf/tests_example.pdf" width="600" height="700" type='application/pdf'></object>

#### **Legal Opinion 2**:
<object data="/assets/pdf/case_2.pdf" width="600" height="700" type='application/pdf'></object>

#### **Case Brief Output**:
<object data="/assets/pdf/case_brief.pdf" width="600" height="700" type='application/pdf'></object>
