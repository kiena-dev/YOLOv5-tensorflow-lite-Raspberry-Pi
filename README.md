# YOLOv5-tensorflow-lite-Raspberry-Pi
This GitHub repository show real-time object detection using a Raspberry Pi, YOLOv5 TensorFlow Lite model, LED indicators, and an LCD display.

![Raspberry Pi](https://img.shields.io/badge/-RaspberryPi-C51A4A?style=for-the-badge&logo=Raspberry-Pi) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white) ![OpenCV](https://img.shields.io/badge/opencv-%23white.svg?style=for-the-badge&logo=opencv&logoColor=white)


This GitHub repository show real-time object detection using a Raspberry Pi, MobileNetSSDv2 TensorFlow Lite model, LED indicators, and an LCD display. the feature of this project include:

- Show fps for each detection
- Output the class using LED for each class (there is 5 classes: car, person, truck, bus, motorbike)
- Show CPU and temperature of raspberry pi using LCD 16x02.

## Demo
Below is the following demo video showcasing the Raspberry Pi in action. When real-time object detection processed, video frames show the fps, LED indicators will trun on based on detected classes, and CPU usage and temperature information displayed on the LCD screen.

<img src=".image/demo_video_gif.gif" alt="Overview" width="700">

## mAP

| Model             | mAP@50  | mAP@50:5:95 | FPS  |
|-------------------|---------|-------------|------|
| Yolov5s 640px fp32 | 94,7    | 74,1        | 0,5  |
| Yolov5s 416px fp32 | 91,8    | 72,5        | 1,1  |
| Yolov5s 320px fp32 | 90,5    | 69,8        | 1,87 |
| Yolov5n 640px fp32 | 91,4    | 67,3        | 1,5  |
| Yolov5n 416px fp32 | 89      | 66,3        | 3,7  |
| Yolov5n 320px fp32 | 86,7    | 63,7        | 5,7  |
| Yolov5s 640px int-8| 93,9    | 70,4        | 0,7  |
| Yolov5s 416px int-8| 90,5    | 67,5        | 1,7  |
| Yolov5s 320px int-8| 90,1    | 63,9        | 2,9  |
| Yolov5n 640px int-8| 90,7    | 64,4        | 1,9  |
| Yolov5n 416px int-8| 88,7    | 63,2        | 4,5  |
| Yolov5n 320px int-8| 85,9    | 59,3        | 7,2  |

## Prerequisites
- Raspberry Pi 4 (I'm using 8 GB version)
- Raspberry Pi OS 11 Bulleyes 64-bit
- Pi Camera v2/v1/Web-Camera
- PCB or PCB Dot
- LCD 16x2 Biru/Blue 1602 SPI I2C
- ✨ Wiring cable ✨

## Wiring Diagram

<img src="other/sketch_github_bb.png" alt="Overview" width="500">

Follow this organized table to establish the proper connections, you can also read the reference here [GPIO on Raspberry Pi4](https://pinout.xyz/).

<details>
<summary>LED Wiring - Raspberry Pi</summary>

| Wire Color | GPIO Pin |
|------------|----------|
| Red        | GPIO 17  |
| Green      | GPIO 18  |
| Yellow     | GPIO 23  |
| Cyan       | GPIO 27  |
| White      | GPIO 22  |
| Black (GND)| GND      |

</details>

<details>
<summary>I2C Wiring - Raspberry Pi</summary>

| Wire Color | Connection |
|------------|------------|
| Red        | 5V         |
| Black      | GND        |
| Purple     | SDA        |
| Brown      | SCL        |

</details>

## Installation

To run this project, you need [Python 3.5](https://docs.python.org/3/) or higher installed on your system. Follow these steps to get started:

- Clone the repository and navigate to the project directory: :
```bash
  git clone https://github.com/kiena-dev/YOLOv5-tensorflow-lite-Raspberry-Pi.git
  cd YOLOv5-tensorflow-lite-Raspberry-Pi
```

- Create a Python virtual environment (optional but recommended):
```bash
  python3 -m venv venv
```

- Activate the virtual environment:
```bash
  source venv/bin/activate
```

- Install the required dependencies using pip3:
```bash
  pip3 install -r requirements.txt
```

Now you have successfully installed the project and its dependencies.
    
## Usage

```bash
$ python detect.py --weights yolov5s.pt --source 0                                   # webcam
                                                     img.jpg                         # image
                                                     vid.mp4                         # video
                                                     path/                           # directory
                                                     'path/*.jpg'                    # glob
                                                     'https://youtu.be/Zgi9g1ksQHc'  # YouTube
                                                     'rtsp://example.com/media.mp4'  # RTSP, RTMP, HTTP stream
```


<details>
<summary>example video</summary>

Default (without LED/LCD):
```bash
  python detect.py --img 320 --weights yolov5n_320px-fp32.tflite --source video_test.mp4  
```

With LED/LCD:

```bash
  python detect_rpi_led.py --img 320 --weights yolov5n_320px-fp32.tflite --source video_test.mp4  
```

</details>


<details>
<summary>example webcam</summary>

Default (without LED/LCD):
```bash
  python detect.py --img 320 --weights yolov5n_320px-fp32.tflite --source 0
```

With LED/LCD:

```bash
  python detect_rpi_led.py --img 320 --weights yolov5n_320px-fp32.tflite --source 0
```

</details>


## Training Dataset

If you want to train your own model, you can utilize the resource provided below:

<a href="https://colab.research.google.com/github/EdjeElectronics/TensorFlow-Lite-Object-Detection-on-Android-and-Raspberry-Pi/blob/master/Train_TFLite2_Object_Detction_Model.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

Reference Jupyter Notebook File:

<a href="https://github.com/kiena-dev/Raspberry-PI-MobileNetSSDv2-tflite-LED/blob/main/MobinetV2_TFLite_training.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

Dataset from Roboflow:

<a href="https://universe.roboflow.com/devan-naratama-2xq45/skripsi-dtmyf"><img src="https://app.roboflow.com/images/download-dataset-badge.svg"></img></a>   <a href="https://universe.roboflow.com/devan-naratama-2xq45/skripsi-dtmyf/model/"><img src="https://app.roboflow.com/images/try-model-badge.svg"></img></a>

Be sure to make use of these resources to train your model and achieve optimal results!


## Authors

- [@kiena](https://github.com/kiena-dev)

## Reference
Special thanks to the following resources that inspired and contributed to this project:

- [QEngineering](https://qengineering.eu/)
- [Tensorflow](https://tensorflow.org/)
- [TensorFlow Lite Object Detection on Android and Raspberry Pi by EdjeElectronics](https://github.com/EdjeElectronics/TensorFlow-Lite-Object-Detection-on-Android-and-Raspberry-Pi)



