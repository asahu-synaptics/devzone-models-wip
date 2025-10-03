---
library_name: synap
tags:
  - Object Detection
  - Astra SL
  - SL1600
  - MPU
---

  
# YOLOv8s Pose

## Model Overview


A YOLOv8s model specialized for body pose estimation, optimized for real-time applications.


The YOLOv8s Pose model  is developed and optimized for the Synaptics Astra™ **SL1680 processor** NPU and **SL1640 processor** NPU.

## Model Features
- **Model Type:** Object Detection
- **Input Size:** 352x640
- **Output Size:** various resolutions based on model configuration

> **ℹ️ INFO:** 
> This model is ready to use on Synaptics Astra Machina boards. An NPU optimized version of the YOLOv8s Pose is installed in the Astra SDK Image.


## Deployment on Synaptics Astra SL1600 Series 

This particular model is compiled for **Synaptics Astra SL1680** processor. You can find this model already pre-installed on Machina™ Dev kit with SL1680 processor. 

You can also find the same model compiled for **Synaptics Astra SL1640** processor pre-installed on Machina™ Dev kit with SL1640 processor.

Synaptics Astra Machina™ is Modular developer kit for Astra SL-Series of high-performance IoT processors with integrated Synaptics Veros™ wireless connectivity solution. Learn more [here](https://www.synaptics.com/products/embedded-processors/astra-machina-foundation-series)

### Application binary

The `synap_cli_od` command line application allows running object detection models like YOLOv8s Pose.

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

cd $MODELS/object_detection/body_pose/model/yolo_v8/yolov8s-pose

synap_cli_od -m model.synap input_image.jpg
```


Example output on SL1680:

```
Input image: input_image.jpg (w = 640, h = 480, c = 3)
Detection time: 30.79 ms
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
| SL1680  | 30.79   |
| SL1640  | 54.59   |




## Optimize and Customize the model

Advanced users may wish to customize the source model and recompile it for the Synaptics Astra NPU. 
Please refer to the [Bring Your Own Model](https://developer.synaptics.com/docs/sl/tutorials/bring-your-own-model) section for more information.


    For reference, the `.synap` format model provided on the firmware image was compiled for the Synaptics Astra NPU with the following `.yaml` settings:

```yaml
inputs:
  - name: images
    shape:
      - 1
      - 3
      - 352
      - 640
    scale: 255
    format: RGB
outputs:
  - format: yolov8 landmarks=17 visibility=1 w_scale=640 h_scale=352
quantization:
  data_type:
    '*': uint8
    /model.22/Concat...: float16
    /model.22/Concat_4...: float16
  scheme: asymmetric_affine
  dataset:
    - ../../sample/*.jpg

```
    

## License

License for compiled model for on-device deployment is covered by under [Synaptics Astra EULA](https://github.com/synaptics-astra/doc/blob/main/EULA.rst).

## Learn More

- [Synaptics AI Developer Zone](https://developer.synaptics.com?utm_source=hf): Get started with documentation, tutorials and resources for your Edge AI journey.
- [Astra Support Portal](https://synacsm.atlassian.net/servicedesk/customer/portal/543?utm_source=hf): Connect with our engineering team and community.