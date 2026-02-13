---
title: "3D computer vision for virtual reality and robotics"
excerpt: "New methods for 3D modeling and ego-motion estimation from images and video"
collection: research
---

Sponsors: National Science Foundation

## 3D reconstruction

### Uncalibrated Structure From Motion on a Sphere

Spherical motion is a special case of camera motion where the camera moves on the imaginary surface of a sphere with the optical axis normal to the surface. Common sources of spherical motion are a person capturing a stereo panorama with a phone held in an outstretched hand, or a hemi- spherical camera rig used for multi-view scene capture. However, traditional structure-from-motion pipelines tend to fail on spherical camera motion sequences, especially when the camera is facing outward. Building upon prior work addressing the calibrated case, we explore uncalibrated reconstruction from spherical motion, assuming a fixed but unknown focal length parameter. We show that, although two-view spherical motion is always a critical case, self-calibration is possible from three or more views. Through analysis of the relationship between focal length and spherical relative pose, we devise a global structure- from-motion approach for uncalibrated reconstruction. We demonstrate the effectiveness of our approach on real-world captures in various settings, even when the camera motion deviates from perfect spherical motion.

📕[Paper (ICCV 2025)](https://openaccess.thecvf.com/content/ICCV2025/papers/Ventura_Uncalibrated_Structure_from_Motion_on_a_Sphere_ICCV_2025_paper.pdf) and [Supplemental Material](https://openaccess.thecvf.com/content/ICCV2025/supplemental/Ventura_Uncalibrated_Structure_from_ICCV_2025_supplemental.zip)
📶 [Poster](https://iccv.thecvf.com/media/PosterPDFs/ICCV%202025/741.png?t=1760388423.711583)
📷 [Project page](https://jonathanventura.github.io/spherical-sfm/pages/iccv2025/)
💻 [Code](https://jonathanventura.github.io/spherical-sfm/)
💾 [Dataset](https://osf.io/tjc3x/)

### CasualStereo: Casual Capture of Stereo Panoramas with Spherical Structure-from-Motion

Hand-held capture of stereo panoramas involves spinning the camera in a roughly circular path to acquire a dense set of views of the scene. However, most existing structure-from-motion pipelines fail when trying to reconstruct such trajectories, due to the small baseline between frames. In this work, we evaluate the use of spherical structure-from-motion for reconstructing handheld stereo panorama captures. The spherical motion constraint introduces a strong regularization on the structure-from-motion process which mitigates the small-baseline problem, making it well-suited to the use case of stereo panorama capture with a handheld camera. We demonstrate the effectiveness of spherical structure-from-motion for casual capture of high-resolution stereo panoramas and validate our results with a user study.

📕 [Paper (IEEE VR 2020)](https://ieeexplore.ieee.org/document/9089526)
💻 [Code](https://jonathanventura.github.io/spherical-sfm/)

### Unsupervised Learning of Depth and Ego-Motion from Cylindrical Panoramic Video

We introduce a convolutional neural network model for unsupervised learning of depth and ego-motion from cylindrical panoramic video. Panoramic depth estimation is an important technology for applications such as virtual reality, 3d modeling, and autonomous robotic navigation. In contrast to previous approaches for applying convolutional neural networks to panoramic imagery, we use the cylindrical panoramic projection which allows for the use of the traditional CNN layers such as convolutional filters and max pooling without modification. Our evaluation of synthetic and real data shows that unsupervised learning of depth and ego-motion on cylindrical panoramic images can produce high-quality depth maps and that an increased field-of-view improves ego-motion estimation accuracy. We also introduce Headcam, a novel dataset of panoramic video collected from a helmet-mounted camera while biking in an urban setting.

📕 [Paper (IEEE AIVR 2019)](https://ieeexplore.ieee.org/abstract/document/8942315)
📷 [Project page](https://jonathanventura.github.io/publication/sharma-aivr19)

### Structure from Motion on a Sphere

We describe a special case of structure from motion where the camera rotates on a sphere. The camera’s optical axis lies perpendicular to the sphere’s surface. In this case, the camera’s pose is minimally represented by three rotation parameters. From analysis of the epipolar geometry we derive a novel and efficient solution for the essential matrix relating two images, requiring only three point correspondences in the minimal case. We apply this solver in a structure-from-motion pipeline that aggregates pairwise relations by rotation averaging followed by bundle adjustment with an inverse depth parameterization. Our methods enable scene modeling with an outward-facing camera and object scanning with an inward-facing camera.

📕 [Paper (ECCV 2016)](https://link.springer.com/chapter/10.1007/978-3-319-46487-9_4)
📘 [ArXiv version](https://arxiv.org/abs/1604.00409)
💻 [Code](https://jonathanventura.github.io/spherical-sfm/)

## Camera localization and tracking

### Absolute Pose From One or Two Scaled and Oriented Features

Keypoints used for image matching often include an estimate of the feature scale and orientation. While recent work has demonstrated the advantages of using feature scales and orientations for relative pose estimation, relatively little work has considered their use for absolute pose estimation. We introduce minimal solutions for absolute pose from two oriented feature correspondences in the general case, or one scaled and oriented correspondence given a known vertical direction. Nowadays, assuming a known direction is not particularly restrictive as modern consumer devices, such as smartphones or drones, are equipped with Inertial Measurement Units (IMU) that provide the gravity direction by default. Compared to traditional absolute pose methods requiring three point correspondences, our solvers need a smaller minimal sample, reducing the cost and complexity of robust estimation. Evaluations on large-scale and public real datasets demonstrate the advantage of our methods for fast and accurate localization in challenging conditions.

📕 [Paper (CVPR 2024)](https://openaccess.thecvf.com/content/CVPR2024/papers/Ventura_Absolute_Pose_from_One_or_Two_Scaled_and_Oriented_Features_CVPR_2024_paper.pdf) and [Supplemental Material](https://openaccess.thecvf.com/content/CVPR2024/supplemental/Ventura_Absolute_Pose_from_CVPR_2024_supplemental.pdf)
💻 [Code](https://github.com/danini/absolute-pose-from-oriented-and-scaled-features)

### P1AC: Revisiting Absolute Pose from a Single Affine Correspondence

Affine correspondences have traditionally been used to improve feature matching over wide baselines. While recent work has successfully used affine correspondences to solve various relative camera pose estimation problems, less attention has been given to their use in absolute pose estimation. We introduce the first general solution to the problem of estimating the pose of a calibrated camera given a single observation of an oriented point and an affine correspondence. The advantage of our approach (P1AC) is that it requires only a single correspondence, in comparison to the traditional point-based approach (P3P), significantly reducing the combinatorics in robust estimation. P1AC provides a general solution that removes restrictive assumptions made in prior work and is applicable to large-scale image-based localization. We propose a minimal solution to the P1AC problem and evaluate our novel solver on synthetic data, showing its numerical stability and performance under various types of noise. On standard image-based localization benchmarks we show that P1AC achieves more accurate results than the widely used P3P algorithm.

📕 [Paper (ICCV 2023)](https://openaccess.thecvf.com/content/ICCV2023/papers/Ventura_P1AC_Revisiting_Absolute_Pose_From_a_Single_Affine_Correspondence_ICCV_2023_paper.pdf) and [Supplemental Material](https://openaccess.thecvf.com/content/ICCV2023/supplemental/Ventura_P1AC_Revisiting_Absolute_ICCV_2023_supplemental.pdf)
📘 [ArXiv version](http://arxiv.org/abs/2011.08790)
💻 [Code](https://github.com/jonathanventura/P1AC)

## View synthesis

### 3D Pano Inpainting: Building a VR Environment from a Single Input Panorama

Creating 360-degree 3D content is challenging because it requires either a multi-camera rig or a collection of many images taken from different perspectives. Our approach aims to generate a 360-degree VR scene from a single panoramic image using a learning-based inpainting method adapted for panoramic content. We introduce a pipeline capable of transforming an equirectangular panoramic RGB image into a complete 360-degree 3D virtual reality scene represented as a textured mesh, which is easily rendered on a VR headset using standard graphics rendering pipelines. We qualitatively evaluate our results on a synthetic dataset consisting of 360 panoramas in indoor scenes.

📶 [Poster abstract (IEEE VR 2024)](https://jonathanventura.github.io/3d-pano-inpainting/)
📷 [Project page](https://jonathanventura.github.io/3d-pano-inpainting/)
💻 [Code](https://github.com/jonathanventura/3d-pano-inpainting)

### PanoSynthVR: View Synthesis from a Single Input Panorama with Multi-Cylinder Images

We investigate how real-time, 360◦view synthesis can be achieved on current virtual reality hardware from a single panoramic image input. We introduce a light-weight method to automatically convert a single panoramic input into a multi-cylinder image representation that supports real-time, free-viewpoint view synthesis rendering for virtual reality. We apply an existing convolutional neural network trained on pinhole images to a cylindrical panorama with wrap
padding to ensure agreement between the left and right edges. The network outputs a stack of semi-transparent panoramas at varying depths which can be easily rendered and composited with over blending. Quantitative experiments and a user study show that the method produces convincing parallax and fewer artifacts than a textured mesh representation.

📕 [Paper (IEEE ISMAR 2022)](https://ieeexplore.ieee.org/document/9995104)
📶 [Poster abstract (ACM SIGGRAPH 2021)[https://dl.acm.org/doi/10.1145/3450618.3469144]
📷 [Project page](https://jonathanventura.github.io/PanoSynthVR/)
💻 [Code](https://github.com/jonathanventura/PanoSynthVR)

### View Synthesis In Casually Captured Scenes Using a Cylindrical Neural Radiance Field With Exposure Compensation

We extend Neural Radiance Fields (NeRF) with a cylindrical parameterization that enables rendering photorealistic novel views of 360-degree outward facing scenes. We further introduce a learned exposure compensation parameter to account for the varying exposure in training images that may occur from casually capturing a scene. We evaluate our method on a variety of 360-degree casually captured scenes.

📶 [Poster abstract (ACM SIGGRAPH 2021)](https://dl.acm.org/doi/10.1145/3450618.3469147)
📷 [Project page](https://wkhademi.github.io/CylindricalNeRF/)

