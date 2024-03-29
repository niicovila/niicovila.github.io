---
layout: page
title: Entropy Regularized Reinforcement Learning Algorithms
description: Study of Entropy Regularization through Linear Programming formulations and its feasibility in large scale settings
img: assets/img/envs.jpg
importance: 1
category: Research
---

As part of my undergraduate thesis, I am conducting research on several state of the art regularized reinforcement lerning algorithms, as well as tangent variations of such algorithms. I am actively working on QREPS, which is an RL developed through the Linear Programming framework. I have also developed modifications on algorithms such as PPO and X-QL.

### X-QL modifications
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/exact_xsac.png" title="Modifications on X-QL for SAC improvements on CheetahRun" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/exact_xtd3.png" title="Modifications on X-QL for TD3 improvements on CheetahRun" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Modifications I made on both SAC and TD3 versions of X-QL improve the final reward obtained.
</div>

### PPO modifications
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/xppo.png" title="Modifications on PPO in CartPole and LunarLander" class="img-fluid rounded z-depth-1" %}
    </div>

</div>
<div class="caption">
    Used X-QL loss function to optimize the value function in PPO algorithm. It needs to be further studied.
</div>

### Q-REPS
My research is mainly focused on enhancing the performance of QREPS -which showed promising results in small scale environments- in larger scale environments with the use of DNNs, and reach comparable results to those achieving state of the art results, such as SAC, TD3 or PPO.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/minmaxqreps.png" title="MinMax QREPS Alg." class="img-fluid rounded z-depth-1" %}
    </div>

</div>
<div class="caption">
    QREPS practical implementation
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/qreps_cartpole.png" title="QREPS Results CartPole" class="img-fluid rounded z-depth-1" %}
    </div>

</div>
<div class="caption">
    QREPS performance on CartPole-v1
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid loading="eager" path="assets/video/qreps_carpole_video.mp4" title="Web-App Visualization" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    Learning CartPole with QREPS
</div>


