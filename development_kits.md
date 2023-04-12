---
sort: 4
---

# 4. CONFIGURERATION FILES
For convenience of evaluation, we provide configuration files of some well-known SLAM systems as below:

[A-LOAM](https://github.com/sjtuyinjie/toolkit/blob/main/config_files/aloam/aloam_velodyne_HDL_32.launch),

[LeGO-LOAM](https://github.com/sjtuyinjie/toolkit/blob/main/config_files/legoloam/run.launch),

[LINS](https://github.com/sjtuyinjie/toolkit/blob/main/config_files/lins/exp_port.yaml),

[LIO-SAM](https://github.com/sjtuyinjie/toolkit/blob/main/config_files/liosam/params.yaml),

[VINS-MONO](https://github.com/sjtuyinjie/toolkit/blob/main/config_files/vins/mytest.launch),

[ORB-Pinhole](https://github.com/sjtuyinjie/toolkit/blob/main/config_files/orb3/paperd435i.yaml),

[ORB-Fisheye](https://github.com/sjtuyinjie/toolkit/blob/main/config_files/orb3/paperleft.yaml),

[ORB-Thermal](https://github.com/sjtuyinjie/toolkit/blob/main/config_files/orb3/paperthermal.yaml),

[CUBMAPSLAM](https://github.com/sjtuyinjie/toolkit/blob/main/config_files/cubemapslam/runCubemapstreet_06.sh)

# 5.DEVELOPMENT TOOLKITS
## 5.1 Extracting Images
* For rosbag users, first make image view
~~~
roscd image_view
rosmake image_view
sudo apt-get install mjpegtools
~~~

open a terminal,type roscore.And then open another,type
~~~
rosrun image_transport republish compressed in:=/camera/color/image_raw raw out:=/camera/color/image_raw respawn="true"
~~~
* For non-rosbag users,just take advantage of following script  [export_tum](https://github.com/sjtuyinjie/toolkit/blob/main/export_tum.py),[export_euroc](https://github.com/sjtuyinjie/toolkit/blob/main/export_euroc.py) and [get_csv](https://github.com/sjtuyinjie/toolkit/blob/main/img2csv.py) to get data in formats of Tum or EuRoC.

## 5.2 Evaluation
We use open-source tool [evo](https://github.com/MichaelGrupp/evo) for evalutation.
To install evo,type
~~~
pip install evo --upgrade --no-binary evo
~~~
To evaluate monocular visual SLAM,type
~~~
evo_ape tum street_07.txt your_result.txt -vaps
~~~
To evaluate LIDAR SLAM,type
~~~
evo_ape tum street_07.txt your_result.txt -vap
~~~
To test GNSS based methods,type
~~~
evo_ape tum street_07.txt your_result.txt -vp
~~~

## 5.3 Calibration
For camera intrinsics,visit [Ocamcalib](http://sites.google.com/site/scarabotix/ocamcalib-toolbox) for omnidirectional model.
visit [Vins-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion) for pinhole and MEI model.
use [Opencv](https://opencv.org/) for Kannala Brandt model

For IMU intrinsics,visit [Imu_utils](https://github.com/gaowenliang/imu_utils)

For extrinsics between cameras and IMU,visit [Kalibr](https://github.com/ethz-asl/kalibr)
For extrinsics between Lidar and IMU,visit [Lidar_IMU_Calib](https://github.com/APRIL-ZJU/lidar_IMU_calib) 
For extrinsics between cameras and Lidar, visit [Autoware](https://github.com/Autoware-AI/autoware.ai) 
## 5.4 Getting RINEX files
For GNSS based methods like [RTKLIB](http://www.rtklib.com/),we usually need to get data in the format of RINEX. To make use of GNSS raw measurements, we use [Link](https://github.com/TakahashiJinxu/ublox2rinex) toolkit.

## 5.5 ROS drivers for UVC cameras 
We write a ROS driver for UVC cameras to record our thermal-infrared image. 
[UVC ROS driver](https://github.com/sjtuyinjie/toolkit/tree/main/thermal_ws/src)


# 6.FUTURE PLANS
In the future, we plan to update and extend our project from time to time, striving to build a comprehensive SLAM benchmark similar to the KITTI dataset for ground robots.
## If you have any suggestions or questions, do not hesitate to propose an issue. And if you find our dataset helpful in your research, a simple star is the best affirmation for us.

# 7.ACKNOWLEGEMENT
This work is supported by NSFC(62073214). Authors from SJTU hereby express our appreciation.

