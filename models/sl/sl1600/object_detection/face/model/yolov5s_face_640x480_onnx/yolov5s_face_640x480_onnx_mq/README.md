---
library_name: synap
tags:
  - Object Detection
  - Astra SL
  - SL1600
  - MPU
---

  
# YOLOv5s Face 640x480 ONNX MQ

## Model Overview


A YOLOv5s model specialized for face detection, optimized for 640x480 resolution using ONNX with mixed quantization.


The YOLOv5s Face 640x480 ONNX MQ model  is developed and optimized for the Synaptics Astra™ **SL1680 processor** NPU and **SL1640 processor** NPU.

## Model Features
- **Model Type:** Object Detection
- **Input Size:** 640x480
- **Output Size:** various resolutions based on model configuration

> **ℹ️ INFO:** 
> This model is ready to use on Synaptics Astra Machina boards. An NPU optimized version of the YOLOv5s Face 640x480 ONNX MQ is installed in the Astra SDK Image.


## Deployment on Synaptics Astra SL1600 Series 

This particular model is compiled for **Synaptics Astra SL1680** processor. You can find this model already pre-installed on Machina™ Dev kit with SL1680 processor. 

You can also find the same model compiled for **Synaptics Astra SL1640** processor pre-installed on Machina™ Dev kit with SL1640 processor.

Synaptics Astra Machina™ is Modular developer kit for Astra SL-Series of high-performance IoT processors with integrated Synaptics Veros™ wireless connectivity solution. Learn more [here](https://www.synaptics.com/products/embedded-processors/astra-machina-foundation-series)

### Application binary

The `synap_cli_od` command line application allows running object detection models like YOLOv5s Face 640x480 ONNX MQ.

Inputs:

* The converted synap model (`.synap` extension)
* Optionally, a confidence threshold for detected objects
* One or more images (jpeg or png format)

Outputs:

* A list of detected objects for each input image, including:
  - Bounding box
  - Class index
  - Confidence score

Command line usage on Astra SL1680 and SL1640:

```
MODELS=/usr/share/synap/models/

cd $MODELS/object_detection/face/model/yolov5s_face_640x480_onnx/yolov5s_face_640x480_onnx_mq

synap_cli_od -m model.synap input_image.jpg
```


Example output on SL1680:

```
Input image: input_image.jpg (w = 640, h = 480, c = 3)
Detection time: 31.88 ms
#   Score  Class  Position  Size     Description
0   0.95       0   94,193    62,143  person
```

> **ℹ️ INFO:**
> JPEG/PNG input images are resized in software to the network input tensor size. 


> **💡NOTE:**
> Ensure the output format is defined during model conversion. Missing format details can result in errors such as *"Failed to initialize detector"*.



## Performance on NPU 

| Processors      | Inference Time (ms) |
|-------------|--------------------|
| SL1680  | 31.88   |
| SL1640  | 59.63   |




## Optimize and Customize the model

Advanced users may wish to customize the source model and recompile it for the Synaptics Astra NPU. 
Please refer to the [Bring Your Own Model](https://developer.synaptics.com/docs/sl/tutorials/bring-your-own-model) section for more information.


    For reference, the `.synap` format model provided on the firmware image was compiled for the Synaptics Astra NPU with the following `.yaml` settings:

```yaml
data_layout: default
inputs:
  - means:
      - 0
      - 0
      - 0
    scale: 255
outputs:
  - dequantize: true
    name: '349'
    format: >-
      yolov5 landmarks=5 transposed=1
      anchors=[[],[],[],[4,5,8,10,13,16],[23,29,43,55,73,105],[146,217,231,300,335,433]]
  - dequantize: true
    name: '369'
    format: yolov5
  - dequantize: true
    name: '389'
    format: yolov5
quantization:
  data_type:
    '*': uint8
    Concat_155...: int16
  dataset:
    - ../../widerface/WIDER_val/images/[1-2]*/*.jpg

```
    

## License

Both the source model and the compiled model for on-device deployment are licensed under [AGPL-3.0](https://github.com/ultralytics/ultralytics/blob/main/LICENSE).

## Learn More

- [Synaptics AI Developer Zone](https://developer.synaptics.com?utm_source=hf): Get started with documentation, tutorials and resources for your Edge AI journey.
- [Astra Support Portal](https://synacsm.atlassian.net/servicedesk/customer/portal/543?utm_source=hf): Connect with our engineering team and community.