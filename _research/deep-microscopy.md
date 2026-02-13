---
title: "Deep learning for microscope image enhancement"
excerpt: "Exploring computational methods to achieve super-resolution and extreme low-light optical imaging"
collection: research
---

Optical microscopes have a fundamental limit of about 200 nm resolution; however, many important biological structures and phenomena are only visible at the nanoscale.  This NIH-funded project explores computational methods to achieve super-resolution optical imaging, through methods such as structured illumination and single molecule localization.  We are applying the tools of deep learning to develop the next generation of these methods to increase their speed and flexibility.   A second aim of the project is to use deep learning to build computational super-resolution techniques than can cope with extreme low-light imaging conditions, so that we can image live cells over long periods without harming the sample. 

Sponsor: National Institute Of General Medical Sciences of the National Institutes of Health via University of Colorado Colorado Springs

### Fluorescence Microscopy Datasets for Training Deep Neural Networks

Two factors that limit the usefulness and performance of fluorescence microscopy are photobleaching of fluorescent probes during imaging and, when imaging live cells, phototoxicity caused by light exposure. Recently developed methods in machine learning are able to greatly improve the signal-to-noise ratio of acquired images. This allows researchers to record images with much shorter exposure times, which in turn minimizes photobleaching and phototoxicity by reducing the dose of light reaching the sample.  We provide high-quality datasets that can be used to train and evaluate deep learning methods for microscope image restoration.

:closed_book: [Gigascience Paper (2021)](https://academic.oup.com/gigascience/article/10/5/giab032/6269106) :microscope: [Dataset](https://doi.org/10.5524/100888)

### Self Supervised Poisson-Gaussian Denoising

We extend the blindspot model for self-supervised denoising to handle Poisson-Gaussian noise and introduce an improved training scheme that avoids hyperparameters and adapts the denoiser to the test data. Self-supervised models for denoising learn to denoise from only noisy data and do not require corresponding clean images, which are difficult or impossible to acquire in some application areas of interest such as low-light microscopy. We introduce a new training strategy to handle Poisson-Gaussian noise which is the standard noise model for microscope images. Our new strategy eliminates hyperparameters from the loss function, which is important in a self-supervised regime where no ground truth data is available to guide hyperparameter tuning. We show how our denoiser can be adapted to the test data to improve performance. Our evaluations on microscope image denoising benchmarks validate our approach.

:closed_book: [WACV Paper (2021)](https://openaccess.thecvf.com/content/WACV2021/papers/Khademi_Self-Supervised_Poisson-Gaussian_Denoising_WACV_2021_paper.pdf) and 
[Supplemental Material](https://openaccess.thecvf.com/content/WACV2021/supplemental/Khademi_Self-Supervised_Poisson-Gaussian_Denoising_WACV_2021_supplemental.pdf)
:blue_book: [ArXiv version](https://arxiv.org/abs/2002.09558)
:computer: [Code](https://jonathanventura.github.io/self-supervised-poisson-gaussian/)
