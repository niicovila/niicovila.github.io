---
layout: page
title: VQ-VAE paper extension improving reconstruction error.
description: Developed a modification on the VQ-VAE model (image generation) that improves by a factor of 2 the reconstruction error on the ImageNet dataset.
img: assets/img/imagenet.png
importance: 3
category: Research
---

### VQ-VAE

The Vector-Quantised Variational AutoEncoder ([Aaron van den Oord, Oriol Vinyals, and Koray Kavukcuoglu. 2017](https://arxiv.org/abs/1711.00937)) is a very popular model used for image generation. It is the basic idea behind popular image generation products such as Stable Diffusion or Dall·e.   



<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/vqvae.png" title="VQ-VAE model" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Original VQ-VAE
</div>

## Motivation
VQ-VAEs have grown in popularity in the last few years given the splendid results they have proven in different
generative AI processes. They are mainly based in an encoder-decoder architecture where the latent variables are
discretized. Using a discrete space is a more compact way of coding latent variables and it seems reasonable to do so
because in real life objects have underlying discrete representations. Nevertheless, discretizing the underlying latent
space using a finite codebook as done in VQ-VAE has some limitations when generating new images given that they
can only properly represent the underlying structure of the image but misses most of the details. Moreover, sampling
from such latent space, will result in a finite set of generated images. To try tackling all these issues, I wondered if
there was a possible encoding of the latent space such that it maintains VQ VAEs’ discrete latent properties while
combining them with the continuous latents given by the encoder architecture.This, may convert the latent space
into a more varied and true to reality one. Nevertheless, I haven’t found any research trying to use both discrete and
continuous latent variables to try to make the generating process better. In this report I study how such a
combination could be done and if that’s the case, if it results in a better model.

## Modifiactions of the original model

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/main_contrib.png" title="VQ-VAE model" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This is the main contribution, which changes the loss function used during the optimization process of reconstructing input images. All the details and motivation behind this is in this <a href="https://github.com/niicovila/VQ-VAE-Extension/blob/main/paper.pdf">paper</a>.
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

## Results
Overrall, the proposed method achieves the best reconstruction errors, as we can see in the following image.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/losses.png" title="VQ-VAE losses" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Loss comparison between original method and the proposed method.
</div>

## Limitations

While using a discrete latent space makes it very easy to generate new images, by sampling from the discrete latent space, when I use projected latents instead of discrete, the projected space is continuous, which would make it harder to sample or generate new images. To tackle this, one might consider some sort of prior distribution on the latent space, such as a gaussian, and use it to generate new images.



### References

Aaron van den Oord, Oriol Vinyals, and Koray Kavukcuoglu. 2017. Neural discrete representation learning. In Proceedings of the 31st International Conference on Neural Information Processing Systems (NIPS'17). Curran Associates Inc., Red Hook, NY, USA, 6309–6318.

