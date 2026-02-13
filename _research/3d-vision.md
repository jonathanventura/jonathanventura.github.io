---
title: "3D computer vision for virtual reality and robotics"
excerpt: "New methods for 3D modeling and ego-motion estimation from images and video"
collection: research
---

3D computer vision involves teaching the computer to understand the three-dimensional world around it.  Because images are only two-dimensional projections of the three-dimensional world, the computer must use intelligent strategies to infer the missing third dimension in an image.  Similarly, video captured from a moving camera gives clues about the trajectory of the camera, but some form of intelligence is needed to infer the motion from the video alone.

These types of 3D computer vision problems have great relevance to many interesting applications such as robotics, augmented reality, and virtual reality.

Sponsor: National Science Foundation

Recent projects:

## 3D reconstruction

### Uncalibrated Structure From Motion on a Sphere

Spherical motion is a special case of camera motion where the camera moves on the imaginary surface of a sphere with the optical axis normal to the surface. Common sources of spherical motion are a person capturing a stereo panorama with a phone held in an outstretched hand, or a hemi- spherical camera rig used for multi-view scene capture. However, traditional structure-from-motion pipelines tend to fail on spherical camera motion sequences, especially when the camera is facing outward. Building upon prior work addressing the calibrated case, we explore uncalibrated reconstruction from spherical motion, assuming a fixed but unknown focal length parameter. We show that, although two-view spherical motion is always a critical case, self-calibration is possible from three or more views. Through analysis of the relationship between focal length and spherical relative pose, we devise a global structure- from-motion approach for uncalibrated reconstruction. We demonstrate the effectiveness of our approach on real-world captures in various settings, even when the camera motion deviates from perfect spherical motion.

:closed_book: [Paper (ICCV 2025)](https://openaccess.thecvf.com/content/ICCV2025/papers/Ventura_Uncalibrated_Structure_from_Motion_on_a_Sphere_ICCV_2025_paper.pdf) and [Supplemental Material](https://openaccess.thecvf.com/content/ICCV2025/supplemental/Ventura_Uncalibrated_Structure_from_ICCV_2025_supplemental.zip)
:signal_strength: [Poster](https://iccv.thecvf.com/media/PosterPDFs/ICCV%202025/741.png?t=1760388423.711583)
:camera: [Project page](https://jonathanventura.github.io/spherical-sfm/pages/iccv2025/)
:computer: [Code](https://jonathanventura.github.io/spherical-sfm/)
:floppy_disk: [Dataset](https://osf.io/tjc3x/)

### CasualStereo: Casual Capture of Stereo Panoramas with Spherical Structure-from-Motion

Hand-held capture of stereo panoramas involves spinning the camera in a roughly circular path to acquire a dense set of views of the scene. However, most existing structure-from-motion pipelines fail when trying to reconstruct such trajectories, due to the small baseline between frames. In this work, we evaluate the use of spherical structure-from-motion for reconstructing handheld stereo panorama captures. The spherical motion constraint introduces a strong regularization on the structure-from-motion process which mitigates the small-baseline problem, making it well-suited to the use case of stereo panorama capture with a handheld camera. We demonstrate the effectiveness of spherical structure-from-motion for casual capture of high-resolution stereo panoramas and validate our results with a user study.

:closed_book: [Paper (IEEE VR 2020)](https://ieeexplore.ieee.org/document/9089526)
:computer: [Code](https://jonathanventura.github.io/spherical-sfm/)

### Unsupervised Learning of Depth and Ego-Motion from Cylindrical Panoramic Video

We introduce a convolutional neural network model for unsupervised learning of depth and ego-motion from cylindrical panoramic video. Panoramic depth estimation is an important technology for applications such as virtual reality, 3d modeling, and autonomous robotic navigation. In contrast to previous approaches for applying convolutional neural networks to panoramic imagery, we use the cylindrical panoramic projection which allows for the use of the traditional CNN layers such as convolutional filters and max pooling without modification. Our evaluation of synthetic and real data shows that unsupervised learning of depth and ego-motion on cylindrical panoramic images can produce high-quality depth maps and that an increased field-of-view improves ego-motion estimation accuracy. We also introduce Headcam, a novel dataset of panoramic video collected from a helmet-mounted camera while biking in an urban setting.

:closed_book: [Paper (IEEE AIVR 2019)](https://ieeexplore.ieee.org/abstract/document/8942315)
:camera: [Project page](https://jonathanventura.github.io/publication/sharma-aivr19)

### Structure from Motion on a Sphere

We describe a special case of structure from motion where the camera rotates on a sphere. The camera’s optical axis lies perpendicular to the sphere’s surface. In this case, the camera’s pose is minimally represented by three rotation parameters. From analysis of the epipolar geometry we derive a novel and efficient solution for the essential matrix relating two images, requiring only three point correspondences in the minimal case. We apply this solver in a structure-from-motion pipeline that aggregates pairwise relations by rotation averaging followed by bundle adjustment with an inverse depth parameterization. Our methods enable scene modeling with an outward-facing camera and object scanning with an inward-facing camera.

:closed_book: [Paper (ECCV 2016)](https://link.springer.com/chapter/10.1007/978-3-319-46487-9_4)
:blue_book: [ArXiv version](https://arxiv.org/abs/1604.00409)
:computer: [Code](https://jonathanventura.github.io/spherical-sfm/)

## Camera localization and tracking

[Absolute Pose From One or Two Scaled and Oriented Features (CVPR 2024)](https://github.com/danini/absolute-pose-from-oriented-and-scaled-features)

[P1AC: Revisiting Absolute Pose from a Single Affine Correspondence (ICCV 2023)](https://github.com/jonathanventura/P1AC)

## View synthesis

[3D Pano Inpainting: Building a VR Environment from a Single Input Panorama (VR 2023 Poster)](https://jonathanventura.github.io/3d-pano-inpainting/)

[PanoSynthVR: View Synthesis from a Single Input Panorama with Multi-Cylinder Images (ISMAR 2022)](https://jonathanventura.github.io/PanoSynthVR/)

[View Synthesis In Casually Captured Scenes Using a Cylindrical Neural Radiance Field With Exposure Compensation (SIGGRAPH 2021 Posters)](https://wkhademi.github.io/CylindricalNeRF/)

