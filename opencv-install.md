## Installing OpenCV in Ubuntu Linux 

### Install packages
---

	sudo apt-get update
	sudo apt-get upgrade
	sudo apt-get install build-essential cmake pkg-config
	sudo apt-get install python-dev python-numpy python-scipy
	sudo apt-get install git libgtk2.0-dev libavcodec-dev libavformat-dev libswscale-dev
	sudo apt-get install libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev

### Download OpenCV
---

Download the zip file from: [http://opencv.org/downloads.html](http://opencv.org/downloads.html)

	~/Documents/OCV$ unzip opencv-3.1.0.zip


### Download OpenCV extra modules
---

Download the zip file from [https://github.com/Itseez/opencv_contrib](https://github.com/Itseez/opencv_contrib) to ```~/Documents/OCV```.

	~/Documents/OCV$ unzip opencv_contrib-master.zip


### Build
---

	~/Documents/OCV/opencv-3.1.0$ mkdir build && cd build
	~/Documents/OCV/opencv-3.1.0/build$ sudo cmake -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-master/modules/ -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local -D INSTALL_PYTHON_EXAMPLES=ON ..


---

	-- General configuration for OpenCV 3.1.0 =====================================
	--   OpenCV modules:
	--     To be built:                 core flann imgproc ml photo reg surface_matching video dnn fuzzy imgcodecs shape videoio highgui objdetect plot superres ts xobjdetect xphoto bgsegm bioinspired dpm face features2d line_descriptor saliency text calib3d ccalib datasets rgbd stereo structured_light tracking videostab xfeatures2d ximgproc aruco optflow stitching python2



### Make install
---

	sudo make -j5
	sudo make install
	sudo ldconfig



---

### References <a id="ref"></a>

1. OpenCV Tutorials [http://docs.opencv.org/master/d7/d9f/tutorial_linux_install.html](http://docs.opencv.org/master/d7/d9f/tutorial_linux_install.html)
2. [http://www.askaswiss.com/2016/01/how-to-install-opencv-3-1-python-ubuntu-14-04.html](http://www.askaswiss.com/2016/01/how-to-install-opencv-3-1-python-ubuntu-14-04.html)
3. [https://scivision.co/compiling-opencv3-with-extra-contributed-modules/](https://scivision.co/compiling-opencv3-with-extra-contributed-modules/)
