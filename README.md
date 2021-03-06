# Object-Tracking
## This object tracking library is optimized by using Eigen3 and openMP
- &emsp;&emsp;*Author: Haibo Wang*<br>
- &emsp;&emsp;*Email: dasuda2015@163.com*
- &emsp;&emsp;*This is an open source Object-Tracking library, The development language is C++, The classic and mainstream object tracking algorithms and related algorithms are reproduced(For example, RANSAC, least squares and so on). Of course, these are optimized by Eigen3 and openMP.*
## Hardware platform:
- &emsp;&emsp;*CPU: intel i7 6700K*<br>
- &emsp;&emsp;*Memory:8G x 2 DDR4*
## Performance:
- **RANSAC**: Linear Fitting, 600 sample point, 500 iteration, Time consuming:*100us *<br>
- **Kalman Filter**: Two dimensional coordinate tracking, System state variable is [x,y,dx,dy],prediction+update,Mean time consuming:*8us*<br>
- **MeanShift**:using kernel function,refactoring with Eigen3 and openMP.
## 1.Camera calibration(If you want to do something good, you mast sharpen it firstly)<br>
- Use opencv's own calibration tool to calculate the internal parameters of the camera, the chessboard picture has been given, fool-style operation, take a look.
### Location:<br>
		DasudaRunner/Object-Tracking/calibration_camera
### Requirments:<br>
		opencv: >=3.3.0 or >=3.0.0
		python: >=2.7
		python-opencv:
### Quick Start:<br>
#### 1.1 Connecte Camera, get images containing checkerboard.
		python getChecker.py # press 's' to save image
#### 1.2 get images list file
		./create_imagelist imagelist.yaml *.jpg
#### 1.3 Calculate the internal parameters of the camera.
		./calibration -w=7 -h=7 imagelist.yaml
#### 1.4 Of course, I encapsulated these commands<1.2,1.3> into a script file, and you can also run the following command.
		sudo sh calibration_camera.sh
&emsp;&emsp;get out_camera_data.yml , this is a file that contains your camera's internal reference.
#### 1.5 You can run ./demo, and get corrected images.
		./demo
