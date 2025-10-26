# Intel RealSense SR305 Camera: Detailed Research & Compatibility Analysis

## Key Takeaways

- The Intel RealSense SR305 is a **short-range structured-light 3D depth camera**, designed for affordable, entry-level depth sensing, especially for indoor applications such as facial tracking, hand/finger gesture recognition, scanning, mapping, and AR.
- **Intel RealSense SDK 2.0** was supported for the SR305 until version **2.50.0** (validated). The camera is now considered discontinued, and support was removed in SDK/Viewer version **2.51.1**. Later SDKs do not provide support for SR305.[1][2]
- **Raspberry Pi compatibility** is possible with effort, but USB 3.0 connection is required for stable, full bandwidth use, and software support is strictly limited to older SDK releases.[3][4]

***

## Intel RealSense SR305 Camera: Detailed Overview

### Hardware Features

- **Depth Technology:** Structured Light (Coded Light)
- **Depth Range:** 0.2 m to 1.5 m
- **Depth Resolution:** Up to 640 × 480 @ 60 fps
- **RGB Resolution:** 1920 × 1080 @ 30 fps
- **Field of View (FOV):**
  - Depth (H × V): 69° ± 3° × 54° ± 2°
  - RGB (H × V): 68° × 41.5° (±2°)
- **Sensor:** SR300 module (SR305 is a variant/rehousing of the SR300)[5][6][7]
- **Connectivity:** USB 3.1 Gen 1 Micro B
- **Best For Indoors:** Works best in controlled lighting; uses infrared projector for depth sensing and can function at 0 Lux.
- **Physical:** Compact (139 × 26.13 × 12 mm, 70 g camera unit)[7]

### Use Cases

- Facial analytics and tracking
- Hand/finger gesture recognition
- Scene segmentation
- Scanning, mapping (3D reconstruction)
- Augmented Reality development[8][9]

### Accuracy and Limitations

- **Very accurate at close range** with fine details for faces and hands, but limited maximum distance makes it unsuitable for large-area mapping.
- **Sensitivity to environmental conditions:** Like other structured light systems, SR305 performance can degrade in bright sunlight, reflective, transparent, or highly textured surfaces.
- **Not recommended for outdoor or large-room use**; optimally used within 1.5 meters indoors.[10][5]

***

## RealSense SDK 2.0 Support for SR305

### Version History

- **Supported SDK:** Intel RealSense SDK 2.0 (librealsense; open source, cross-platform)
- **Last Validated Release:** **Version 2.50.0** (full support)[2]
- **SDK 2.54.2:** Functional with SR305, but was NOT officially validated, so bugs or instability may appear.[2]
- **SDK/Viewer v2.51.1 and later:** SR305 (also SR300, L515) support **removed**. Cameras are classified as retired/discontinued.[1]
- **Legacy SDK (2016 R2/3):** Not officially supported for SR305; Windows Hello and other older features are unsupported for this device.[11][12]
- **Current Status:** Newest SDK releases (late 2025) support only D400 series, D455, and other non-structured-light cameras.

### Supported Platforms

- **SR305 with SDK 2.0:** Works with Windows and Linux up to SDK 2.50.0.
- **Raspberry Pi:** Experimental and **not officially supported**. Reports confirm limited, unstable streaming on Raspberry Pi 3B/4 with Ubuntu, restricted to USB 2.0 mode and lower resolutions/framerates. **USB 3.0 connection is ESSENTIAL** for high-res, stable streaming.[4][13][14][3]
- **Other Notes:** Newer operating systems (Ubuntu 24, Python ≥3.12) are not compatible with the deprecated camera profiles.

***

## Raspberry Pi Compatibility & Testing

### Feasibility

- **Compiling older SDKs:** Raspberry Pi 3/4 can compile SDK 2.0 up to version 2.50.0, but build failures and camera recognition issues are common.[13][3]
- **USB Bandwidth restrictions:** SR305 requires USB 3.0 for 640 × 480 depth streaming at 60 fps; using USB 2.0 drops to 480 × 270@30 fps and often fails to stream reliably.[15]
- **Linux (Ubuntu MATE, Raspbian):** Ubuntu MATE is recommended for SDK compilation; Raspbian often has hardware driver limitations with USB 3.[4][13]

### Common Issues

- **Camera not recognized or unstable streaming** due to kernel or driver compatibility.
- **Power and bandwidth supply:** Using multiple SR305s on a single Pi is problematic, even for IR streams only.[4]
- **Experimental:** Intel never officially supported Raspberry Pi for any RealSense camera; user forums describe solutions as hacky and unreliable for production.

### Developer Experience

- Python bindings (pyrealsense2) and code samples show **basic streaming (color, depth) does work** for SR305 on Raspberry Pi with SDK ≤2.50.0 and USB 3.0, but expect **limited resolution and high effort for setup**.[15]

***

## Comparison Table: SR305 vs. Other RealSense Cameras

| Feature      | SR305        | D415         | L515         |
| ------------ | ------------ | ------------ | ------------ |
| Depth Tech   | Structured Light | Active Stereo | Time-of-Flight |
| Max Range    | 1.5 m        | 10 m         | 9 m          |
| Resolution   | 640×480@60fps | 1280×720@90fps | 1024×768@30fps |
| RGB Sensor   | 1920×1080@30fps | 1920×1080@30fps | 1920×1080@30fps |
| Use Cases    | Face/hand tracking, scanning, AR | General mapping, robotics | Advanced mapping, LiDAR |
| SDK Support  | Up to 2.50.0 | Current      | Current      |

***

## Recommendations

- **SR305 is suitable for budget, short-range, indoor applications with simple depth requirements**. For advanced robotics or mapping, consider the D415, D435, or L515.
- For **Raspberry Pi**, use only SDK 2.50.0 or earlier. Prefer a Pi 4 with Ubuntu and USB 3.0 for best results, but expect limited stability and official support.
- **Do not start new projects with SR305** due to discontinued support and likely future incompatibilities.

***

## Summary

The Intel RealSense SR305 provided a low-cost option for structured-light depth sensing, but its official SDK and hardware support are now ended. For any compatibility-critical or long-term projects, switching to a currently maintained RealSense model is strongly advised. Raspberry Pi use is possible with older SDKs, but comes with bandwidth and driver limitations, especially beyond SDK 2.50.0.[12][11][3][13][1][15][2][4]

[1](https://github.com/IntelRealSense/librealsense/issues/13517)
[2](https://github.com/IntelRealSense/librealsense/wiki/Release-Notes)
[3](https://www.reddit.com/r/raspberry_pi/comments/1jucyhr/realsense_sdk_pi5_and_ai_hat/)
[4](https://github.com/IntelRealSense/librealsense/issues/5782)
[5](https://pmc.ncbi.nlm.nih.gov/articles/PMC9572012/)
[6](https://www.realsenseai.com/wp-content/uploads/2019/07/RealSense_SR30x_Product_Datasheet_Rev_002.pdf)
[7](https://www.tegakari.net/en/2019/07/intel_realsense_depth_camera_sr305/)
[8](https://next.reality.news/news/intel-makes-augmented-reality-production-more-accessible-with-affordable-new-realsense-standalone-depth-camera-0201400/)
[9](https://www.youyeetoo.com/products/intel-realsense-depth-camera-sr305)
[10](https://www.scitepress.org/Papers/2021/102542/102542.pdf)
[11](https://community.intel.com/t5/Items-with-no-label/Does-SR305-support-2016-version-SDK/td-p/698145?profile.language=en)
[12](https://community.intel.com/t5/Items-with-no-label/Does-SR305-support-2016-version-SDK/m-p/698145)
[13](https://github.com/IntelRealSense/librealsense/issues/4556)
[14](https://dev.realsenseai.com/docs/using-depth-camera-with-raspberry-pi-3)
[15](https://www.youtube.com/watch?v=CmDO-w56qso)
[16](https://www.youtube.com/watch?v=PluL7WTlKrM)
[17](https://www.windowscentral.com/intel-releases-new-realsense-camera-just-79)
[18](https://realsenseai.com/developers/sdk-2/)
[19](https://www.reddit.com/r/3DScanning/comments/cqysrc/i_hastily_ordered_a_intel_realsense_sr305_and_now/)
[20](https://venturebeat.com/ai/intels-realsense-sr305-camera-is-designed-for-low-cost-depth-tracking)
[21](https://www.intelrealsense.com/developers/software-for-intel-realsense/)
[22](https://github.com/IntelRealSense/librealsense/issues/4435)
[23](https://www.reddit.com/r/3DScanning/comments/d6pm0s/intel_realsense_d435_vs_sr305_dimensioner_advice/)
[24](https://venturebeat.com/ai/intels-realsense-sr305-camera-is-designed-for-low-cost-depth-tracking/amp/)
[25](https://www.fabtolab.com/intel-realsense-depth-camera-SR305)
[26](https://docs.ros.org/en/jazzy/p/librealsense2/doc/RaspberryPi3.html)
[27](https://forum.imfusion.com/t/recfusion-sdk-support-for-orbbec-femto-and-femto-mega/1687)
[28](https://github.com/IntelRealSense/librealsense/issues/7784)
[29](https://dev.realsenseai.com/docs/supported-features-matrix)
[30](https://dev.intelrealsense.com/docs/projection-in-intel-realsense-sdk-20)
[31](https://docs.derivative.ca/RealSense)
[32](https://stackoverflow.com/questions/tagged/realsense)
[33](https://news.ycombinator.com/item?id=28513298)
[34](https://community.intel.com/t5/Items-with-no-label/Discontinuation-of-RealSense-SDK-for-Windows/m-p/612060?profile.language=en)
[35](https://gzhls.at/blob/ldb/b/4/2/0/0228ac0c41baf61351b4b4f7c3fe811a6f5d.pdf)
[36](https://discourse.openrobotics.org/t/intel-cancelling-its-realsense-business-alternatives/21881)
[37](https://support.realsenseai.com/hc/en-us/community/posts/360044110313-SR305-on-OSX?page=1)
[38](https://derivative.ca/UserGuide/RealSense)
[39](https://support.realsenseai.com/hc/en-us/community/posts/360044304633-Is-depth-broken-in-my-SR305)
[40](https://github.com/IntelRealSense/librealsense/issues/5676)
[41](https://forums.developer.nvidia.com/t/realsense-camera-unstable/71798?page=2)
[42](https://www.reddit.com/r/ROS/comments/1hdxu8e/realsense_going_away/)
