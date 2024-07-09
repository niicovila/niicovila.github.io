---
layout: page
title: Entropy Regularized Reinforcement Learning Algorithms
description: Study of Entropy Regularization through Linear Programming formulations and its feasibility in large scale settings
img: assets/img/envs.jpg
importance: 1
category: Research
---

As part of my undergraduate thesis, I am conducting research on several state of the art regularized reinforcement lerning algorithms, as well as tangent variations of such algorithms. This thesis is mainly about an alternative approach to traditional Deep RL, rooted on the Linear Program reformulation for Markov Decision Processes (MDPs). I implemented Q-REPS from the “Logistic q-learning” paper using neural networks and demonstrated that one can also use this framework to create new Deep RL algorithms that compete with well-known Deep RL algorithms like DQN, SAC or PPO, without needing tricks like gradient clipping, target networks or double q networks. I also propose a novel algorithm “Primal-dual approximate policy iteration” rooted in this linear program reformulation and prove that it can be a strong alternative in large scale settings too.

### Q-REPS
#### Algorithms
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/minmax_qreps.png" title="MinMax QREPS Alg." class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    MinMax-QREPS practical implementation
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/elbe_qreps.png" title="ELBE QREPS Alg." class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    ELBE QREPS practical implementation
</div>

#### Reward Curves
<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/comparison.png" title="QREPS Results" class="img-fluid rounded z-depth-1" %}
    </div>

</div>
<div class="caption">
    QREPS performance on benchmark environments
</div>

#### Q-REPS Gameplay videos
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid loading="eager" path="assets/video/cartpole.mp4" title="Cartpole in Q-REPS" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    Learning CartPole with QREPS
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid loading="eager" path="assets/video/lunarlander.mp4" title="LunarLander in QREPS" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    Learning LunarLander-v2 with QREPS
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid loading="eager" path="assets/video/acrobot.mp4" title="Acrobot in QREPS" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    Learning Acrobot-v1 with QREPS
</div>

#### Q-REPS Extensions to continuous environments
With little modification on the original algorithm one could make this algorithm work for continuous actions as well. This is an example on the Halfcheetah environent.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/qreps_continuous.png" title="Continuous QREPS Alg." class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    QREPS practical implementation on HalfCheetah
</div>

### Primal-dual Approximate Policy Iteration
#### Algorithms
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/pd-api.png" title="PD-API Alg." class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Primal-Dual API practical implementation
</div>

#### Tabular Results
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/pdapi_5x5.png" title="PD-API Alg. on 5X5 grid" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Primal-Dual API performance on 5x5 grid
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/pdapi_8x8.png" title="PD-API Alg. on 8X8 grid" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Primal-Dual API performance on 8x8 grid
</div>

### Thesis pdf
<object data="/assets/pdf/Entropy-reg-DeepRL-with-LP-final.pdf" width="600" height="800" type='application/pdf'></object>

### Thesis presentation
<object data="/assets/pdf/slide.pdf" width="800" height="500" type='application/pdf'></object>

### Other work outside of the main thesis
#### X-QL modifications
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

#### PPO modifications using Gumbel loss to learn the value function
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/xppo.png" title="Modifications on PPO in CartPole and LunarLander" class="img-fluid rounded z-depth-1" %}
    </div>

</div>
<div class="caption">
    Used X-QL loss function to optimize the value function in PPO algorithm. It needs to be further studied.
</div>




