---
layout: page
title: Entropy Regularized Reinforcement Learning algorithms
description: Study of Entropy Regularization through Linear Programming formulations and its feasibility in large scale settings
img: assets/img/cartpole.png
importance: 1
category: Research
---

As part of my undergraduate thesis, I am conducting research on several state of the art regularized reinforcement lerning algorithms, as well as tangent variations of such algorithms. I am actively working on QREPS, which is an RL developed through the Linear Programming framework. I have also developed modifications on algorithms such as PPO and X-QL.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/minigrid_plots2.png" title="Throughput Comparison between Z Learning for a LMDP and Q Learning for an embedded MDP" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/value_function3.png" title="Optimal value function of a 4x4 Grid" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    On the left, a throughput benchmarking of Z Learning and Q Learning using the proper embedding from LMDP to MDP for precise comparison. On the right, the value function of the MDP for a small grid environment of 5 x 5 cells.
</div>

My research is mainly focused on enhancing the performance of QREPS -which showed promising results in small scale environments- in larger scale environments with the use of DNNs, and reach comparable results to those achieving state of the art results, such as SAC, TD3 or PPO.
