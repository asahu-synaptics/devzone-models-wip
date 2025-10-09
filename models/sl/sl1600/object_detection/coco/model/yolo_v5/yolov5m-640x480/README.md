---
library_name: synap
tags:
  - Object Detection
  - Astra SL
  - SL1600
  - MPU
---

  
# YOLOv5m 640x480

## Model Overview


A YOLOv5m model for object detection optimized for 640x480 resolution, offering a balance between speed and accuracy.


The YOLOv5m 640x480 model  is developed and optimized for the Synaptics Astra™ **SL1680 processor** NPU and **SL1640 processor** NPU.

## Model Features
- **Model Type:** Object Detection
- **Input Size:** 640x480
- **Output Size:** 640x480

> **ℹ️ INFO:** 
> This model is ready to use on Synaptics Astra Machina boards. An NPU optimized version of the YOLOv5m 640x480 is installed in the Astra SDK Image.


## Deployment on Synaptics Astra SL1600 Series 

This particular model is compiled for **Synaptics Astra SL1680** processor. You can find this model already pre-installed on Machina™ Dev kit with SL1680 processor. 

You can also find the same model compiled for **Synaptics Astra SL1640** processor pre-installed on Machina™ Dev kit with SL1640 processor.

Synaptics Astra Machina™ is Modular developer kit for Astra SL-Series of high-performance IoT processors with integrated Synaptics Veros™ wireless connectivity solution. Learn more [here](https://www.synaptics.com/products/embedded-processors/astra-machina-foundation-series)

### Application binary

The `synap_cli_od` command line application allows running object detection models like YOLOv5m 640x480.

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

cd $MODELS/object_detection/coco/model/yolo_v5/yolov5m-640x480

synap_cli_od -m model.synap input_image.jpg
```


Example output on SL1680:

```
Input image: input_image.jpg (w = 640, h = 480, c = 3)
Detection time: 118.82 ms
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
| SL1680  | 118.82   |
| SL1640  | 178   |




## Optimize and Customize the model

Advanced users may wish to customize the source model and recompile it for the Synaptics Astra NPU. 
Please refer to the [Bring Your Own Model](https://developer.synaptics.com/docs/sl/tutorials/bring-your-own-model) section for more information.


    For reference, the `.synap` format model provided on the firmware image was compiled for the Synaptics Astra NPU with the following `.yaml` settings:

```yaml
data_layout: default
outputs:
  - dequantize: true
    format: yolov5

```
    

## License

Both the source model and the compiled model for on-device deployment are licensed under [AGPL-3.0](https://github.com/ultralytics/ultralytics/blob/main/LICENSE).

## Learn More

- [Synaptics AI Developer Zone](https://developer.synaptics.com?utm_source=hf): Get started with documentation, tutorials and resources for your Edge AI journey.
- [Astra Support Portal](https://synacsm.atlassian.net/servicedesk/customer/portal/543?utm_source=hf): Connect with our engineering team and community.