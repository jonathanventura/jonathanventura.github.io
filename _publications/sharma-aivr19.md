---
title: "Unsupervised Learning of Depth and Ego-Motion from Cylindrical Panoramic Video"
authors: "Alisha Sharma and Jonathan Ventura"
collection: publications
permalink: /publication/sharma-aivr19
excerpt: 'We introduce a convolutional neural network model for unsupervised learning of depth and ego-motion from cylindrical panoramic video.'
date: 2019-12-11
venue: 'IEEE Conference on Artificial Intelligence and Virtual Reality'
paperurl: '/files/sharma-aivr19.pdf'
---
We introduce a convolutional neural network model for unsupervised learning of depth and ego-motion from cylindrical panoramic video. Panoramic depth estimation is an important technology for applications such as virtual reality, 3d modeling, and autonomous robotic navigation. In contrast to previous approaches for applying convolutional neural networks to panoramic imagery, we use the cylindrical panoramic projection which allows for the use of the traditional CNN layers such as convolutional filters and max pooling without modification. Our evaluation of synthetic and real data shows that unsupervised learning of depth and ego-motion on cylindrical panoramic images can produce high-quality depth maps and that an increased field-of-view improves ego-motion estimation accuracy. We also introduce Headcam, a novel dataset of panoramic video collected from a helmet-mounted camera while biking in an urban setting.

The code for this project is [available on Github](https://github.com/jonathanventura/cylindricalsfmlearner) and our Headcam dataset is [hosted on Zenodo](https://zenodo.org/record/3520963).
