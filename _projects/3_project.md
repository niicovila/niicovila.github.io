---
layout: page
title: VQ-VAE paper extension improving reconstruction error.
description: Developed a modification on the VQ-VAE model (image generation) that improves by a factor of 2 the reconstruction error on the ImageNet dataset.
img: assets/img/imagenet.png
importance: 2
category: Research
---

### VQ-VAE

The Vector-Quantised Variational AutoEncoder is a very popular model used for image generation. It is the basic idea behind popular image generation products such as Stable Diffusion or Dall-e.   ([Aaron van den Oord, Oriol Vinyals, and Koray Kavukcuoglu. 2017](https://arxiv.org/abs/1711.00937)).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/vqvae.png" title="VQ-VAE model" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Original VQ-VAE
</div>

## Modifiactions of the original model

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/main_contrib.png" title="VQ-VAE model" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This is the main contribution, which changes the loss function used during the optimization process of reconstructing input images. All the details and motivation behind this is in this [!paper](https://github.com/niicovila/VQ-VAE-Extension/blob/main/paper.pdf)
</div>

This modification of the algorithm proved to improve the reconstruction error of the original model, leading to very good reconstructions from the original images, being in some cases almost identical.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Reconstructions.png" title="Reconstructed Images" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/errors.png" title="Training and Test Reconstruction errors." class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    On the left, a sample of the original and recomstructed images. On the right, the test and training reconstruction errors.
</div>


## Limitations

While using a discrete latent space makes it very easy to generate new images, by sampling from the discrete latent space, when I use projected latents instead of discrete, the projected space is continuous, which would make it harder to sample or generate new images. To tackle this, one might consider some sort of prior distribution on the latent space, such as a gaussian, and use it to generate new images.



### References

Aaron van den Oord, Oriol Vinyals, and Koray Kavukcuoglu. 2017. Neural discrete representation learning. In Proceedings of the 31st International Conference on Neural Information Processing Systems (NIPS'17). Curran Associates Inc., Red Hook, NY, USA, 6309–6318.

