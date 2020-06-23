# Raspberry Pi based home surveillance

This repository contains the work done for RaspberryPi based surveillance. I followed a great [tutorial](https://www.pyimagesearch.com/2015/05/25/basic-motion-detection-and-tracking-with-python-and-opencv/) on motion detection
to get started with the code.

# Requirements and Dependencies:

* RaspberryPi 3, and PiCam
* Ubuntu Mate setup for Raspberry, can be found [here](https://linuxhint.com/install_ubuntu_mate_raspberry_pi/)
* Python 2.7, OpenCv
* Setup of PiCam, can be found [here](https://thepihut.com/blogs/raspberry-pi-tutorials/16021420-how-to-install-use-the-raspberry-pi-camera)

# Procedure:

Here only image processing and motion detection part is summarized.

* The captured frame is first resized to a custom width and then converted to grayscale.
* The gaussian smoothing is also applied to remove some noise. 
* The very first frame is assumed as a reference i.e. a static model of the background
* In order to detect the foreground, absolute difference is taken in between reference frame and every new frame.
* If there was any motion in curret frame then the absolute difference image would contain intensity difference. This difference is then magnified by using thresholding
* In last step, OpenCv based countour detection was use to detect the shapes in image. If the detected contour is of a area greater than predefined area then a 
bounding box was drawn over the countour. 