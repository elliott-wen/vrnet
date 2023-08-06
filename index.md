---
layout: default
---

<img style="float: right;" src="assets/ahlab.png" alt="drawing" width="200"/>


# VR.net


## Introduction

<p style="text-align: justify;">
Researchers have used machine learning approaches to identify motion
sickness in VR experience. These approaches demand an accurately-labeled,
real-world, and diverse dataset for high accuracy and generalizability. As
a starting point to address this need, we introduce ‘VR.net’, a dataset
offering approximately 12-hour gameplay videos from ten real-world games
in 10 diverse genres. For each video frame, a rich set of motion sicknessrelated labels, such as camera/object movement, depth field, and motion
flow, are accurately assigned. Building such a dataset is challenging since
manual labeling would require an infeasible amount of time. Instead, we
utilize a tool to automatically and precisely extract ground truth data from
3D engines’ rendering pipelines without accessing VR games’ source code.
We illustrate the utility of VR.net through several applications, such as
risk factor detection and sickness level prediction. We continuously expand
VR.net and envision its next version offering 10X more data than the
current form. We believe that the scale, accuracy, and diversity of VR.net
can offer unparalleled opportunities for VR motion sickness research and
beyond.
</p>


## Dataset Format

For each game frame, our dataset provides the following types of data.

1. RGB Image for both eyes (JPG format, Same resolution to your VR Goggle)
![RGB](assets/rgb.jpg)

2. Motion Flow Image (JPG format. Its resolution has same width to your VR Goggle, but double the height since every motion vector is 2-dimensional).
![Motion Flow](assets/motion.jpg)

3. Depth Image from the Main Camera (JPG format. Same resolution to your VR Goggle)
![Depth Image](assets/depth3.jpg)

4. Pose Information for VR Headset and Controllers
```java
class TrackedDevicePose
{
	// position in tracker space
	float[4][4]  mDeviceToAbsoluteTracking; 
	// velocity in tracker space in m/s
	float[3]  vVelocity;		
	// angular velocity in radians/s
	float[3] vAngularVelocity;	
};
```

5. Controller Button/Trackpad Events
```java
class VRControllerState
{
	// bit flags for each of the buttons. 
	uint64_t ulButtonPressed;
	uint64_t ulButtonTouched;
	// Axis data for the controller's analog inputs
	VRControllerAxis_t rAxis[ k_unControllerStateAxisCount ];
};
```

6. Scene Object Data
```java
class ObjectData
{
	// Object Name
    public char[] name;
    // Object Boundary
    public float[6] bounds;
    // Model Matrix
    public float[4][4] localToWorldMatrix; 
}
``` 

7. Camera Data
```java
class CameraData
{
	// Camera Name
    public char[] name;
    // View Matrix
    public float[4][4] view;
    // Projection Matrix
    public float[4][4] projection; 
}
``` 

8. Light Source Data
```java
class LightData
{
	// Light Name
    public char[] name;
    // Light Materials (e.g., shadow & color)
    public float[13] Material;
    // Light Position Matrix
    public float[4][4] localToWorldMatrix; 
}
```

9. User Self Report From Microsoft Dial or Voice Commands.
![report](assets/self.png)

For more detailed information, please refer to our [Data Card](/report).




## Access To Dataset && License
You can download the current version of VR.net via this [link](/dataset). By downloading this dataset, you agree to our [conditions and terms](/policy) and the CC-BY-NC-SA license. 
Specifically, the material can be freely shared, redistributed, transformed, built upon and adapted for any purpose, but not for any commercial use. Anyone using the material must provide credit to the original authors and indicate any changes that were made. Anyone sharing the work or a derivative of it must do under the same license terms as it was originally shared. This prevents a derivative version being released under a more open licence that would allow commercial use.



## Citation:
The recommend citation for this system is 

```bibtex
@article{wen2023vr,
  title={VR. net: A Real-world Dataset for Virtual Reality Motion Sickness Research},
  author={Wen, Elliott and Gupta, Chitralekha and Sasikumar, Prasanth and Billinghurst, Mark and Wilmott, James and Skow, Emily and Dey, Arindam and Nanayakkara, Suranga},
  journal={arXiv preprint arXiv:2306.03381},
  year={2023}
}
```

<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-82644344-1"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-82644344-1');
</script>
