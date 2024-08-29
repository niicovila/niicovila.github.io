---
layout: page
title: Computer Vision for mass prediction of kelp
description: Development of a computer vision pipeline that accelerates subsidy delivery by deriving total kelp mass from an image. 
img: assets/img/kelp.png
importance: 8
category: Machine Learning
---

This project is a solution for a non-profit specializing in regenerative farming techniques for aquaculture. They
expand the kelp farming industry by providing farmers with foundational training, innovative
tools, and financial support. Combining these last two efforts, they approached the DSI
to develop a computer vision pipeline that would accelerate subsidy delivery by deriving total
kelp mass from an image of the crop. A sufficiently accurate model could automate
their subsidy verification and delivery process, reducing operational overhead and
improving outcomes for participating farmers.

We began with a control image set. Kelp was hung against a white background
demarcated with measuring lines. An example can be seen in figure one, below. The approach
involved two steps. Firstly, models were developed to extract feature vectors from the images.
These numerical representations of the image are computer readable definitions of important
characteristics that vision models use to understand what an image contains. The team
employed three different models during the extraction process: rule-based methods,
transformers, and convolutional neural networks (CNNs). The rule-based method involved the
selection of specific features, followed by the setting of thresholds on pixel values of the kelp
image to predict the location of the kelp in the image. The transformer approach leveraged the
models’ context-based analysis to derive kelp mass based on the intersection of concomitant
characteristics of Kelp - such as color and shape. Finally, the CNN approach made use of a
pre-trained segmentation model to learn high-level features and parameters to identify the
presence of kelp. These extracted features were then fed through a trained neural network
attached to the segmentation model to obtain the final weight prediction.

The results are promising. Feeding the team’s CNN feature-vector into the neural network
provided the best results, showing a 23% error rate and an average loss of 0.33kg. This means
that for a given photo of kelp, on average the model predicts the weight within 0.33kg of the
actual weight. The team believes this to be a strong starting point for the project, especially
given that most of the dataset consists of smaller bunches of kelp, which the model performed
even more accurately on. 

### Q-REPS
#### Algorithms
<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/kelp_segmented.png" title="Segmentation of kelp model." class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            CNN Model segmentating Kelp
        </div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/cv_prediction_errors.png" title="Prediction errors for the CNN model" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            CNN Prediction Errors
        </div>
    </div>
</div>

#### Tabular Results
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/cv_test_learning_curves.png" title="curves" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Learning curves on test data
</div>


### One-pager write-up
<object data="/assets/pdf/cv_project.pdf" width="600" height="800" type='application/pdf'></object>



### Data Science proposal
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid loading="eager" path="assets/video/cv_project.mp4" title="Presentation on ML models" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    Presentation of our ML solution
</div>



