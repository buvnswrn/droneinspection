![Drone Inspection](Documentation/imgs/intro.PNG)

# droneinspection
[![License](https://img.shields.io/badge/license-Apache--2.0-green.svg)](LICENSE.md)
![Unity](https://img.shields.io/badge/unity-2020.3+-brightgreen)

This project was created as part of a Seminar - SupRTwin: Sensing, Understanding, and Provisioning of Robotic Digital Twins from Universitat Des Saarlandes

Original Repository: https://mrk40.dfki.de/drone-inspection-seminar/droneinspection


## Introduction
This repository contains the presentation files used for the final seminar presentation and some set of Experiment data.

The end to end flow looks like:

![End-To-End Flow](Documentation/imgs/end-to-end-flow.PNG)
### MQTT Drone API
The drone uses [MQTT Protocol](https://mqtt.org/) to communicate. In short, the following topics are of our interest 
- Mavic2/state/pose - Pose information obtained from markers of drone using a Motion Capture system (OptiTrack system) and published to MQTT through [Motive App](https://optitrack.com/software/motive/)
- Mavic2/state/physical - Current Physical State obtained using [DJI SDK](https://developer.dji.com/mobile-sdk-v4/) and [Android dronecontrol app](https://mrk40.dfki.de/mrk-4.0/androiddronecontrol)

![MQTT Drone API](Documentation/imgs/mqtt-drone-api.PNG)

### Drone Live Monitoring
The drone can be monitored live and inputs such as waypoints and certain commands such as starting live image can be provided to the drone through the Live Monitoring Web App.

![Drone Live Monitoring](Documentation/imgs/drone-live-monitoring.PNG)

### Drone Inspection Service API
- The project involves creation of two main services - Inspection Flight and Object Detection. They are created using [Flask-RestX](https://flask-restx.readthedocs.io/en/latest/).

![Drone Inspection API](Documentation/imgs/drone-inspection-api.png)
### Drone Object Detection
- We use custom trained [YoloV5](https://github.com/ultralytics/yolov5) model to detect the objects

![Object Detection](Documentation/imgs/object-detection.PNG)

### Pose Estimation
- We use inverse Homography technique to estimate the pose of the objects detected.
- The flow of the pose estimation is given below

![Pose Estimation Step 1](Documentation/imgs/pose-estimation-step1.PNG)
![Pose Estimation Step 2](Documentation/imgs/pose-estimation-step2.PNG)
![Pose Estimation Step 3](Documentation/imgs/pose-estimation-step3.PNG)
![Pose Estimation Step 4](Documentation/imgs/pose-estimation-step4.PNG)

### Process Control and States

- The process control is done with the help of Camunda Process Model and [PackML](https://www.omac.org/packml) standard is used to maintain robotic states across the PPR Dashboard along with other robots.
- The states can be monitored in PPR Dashboard or using [OPC UA Client](https://opcfoundation.org/about/opc-technologies/opc-ua/).
- The [PPR Dashboard](https://github.com/dfkibasys/ppr-dashboard) is a part of the BaSys project which looks like the one below
![PPR Dashboard](Documentation/imgs/ppr-dashboard1.PNG)

### Simulation
- The digital twin of the detected object is then visualized using simulation framework - SiMRK

![SiMRK](Documentation/imgs/simrk.PNG)

### Tech Stack : 
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=java&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-000?style=for-the-badge&logo=apachekafka)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![OpenCV](https://img.shields.io/badge/opencv-%23white.svg?style=for-the-badge&logo=opencv&logoColor=white)
![Flask](https://img.shields.io/badge/flask-%23000.svg?style=for-the-badge&logo=flask&logoColor=white)
![Apache Maven](https://img.shields.io/badge/Apache%20Maven-C71A36?style=for-the-badge&logo=Apache%20Maven&logoColor=white)
![Unity](https://img.shields.io/badge/unity-%23000000.svg?style=for-the-badge&logo=unity&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)

[//]: # (![Basys]&#40;https://www.ifak.eu/sites/default/files/BaSys4_2.png&#41;)
<img src="https://www.ifak.eu/sites/default/files/BaSys4_2.png" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="90" height="50" />
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/Apache_Avro_Logo.svg/1200px-Apache_Avro_Logo.svg.png" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="90" height="50" />
<img src="https://www3.djicdn.com/assets/images/products/djigo/logo-dfaa71b74b5b3c388c586d3155b2855e.png" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="50" height="50" />
<img src="https://flask-restx.readthedocs.io/en/latest/_static/logo-512.png" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="50" height="" />