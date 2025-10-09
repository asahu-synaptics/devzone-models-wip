---
library_name: synap
tags:
  - Object Detection
  - Astra SL
  - SL1600
  - MPU
---

  
# MobileNet224 Full1

## Model Overview


A lightweight MobileNet model optimized for people detection on high-resolution images.


The MobileNet224 Full1 model  is developed and optimized for the Synaptics Astra™ **SL1680 processor** NPU and **SL1640 processor** NPU.

## Model Features
- **Model Type:** Object Detection
- **Input Size:** 224x224
- **Output Size:** 640x480

> **ℹ️ INFO:** 
> This model is ready to use on Synaptics Astra Machina boards. An NPU optimized version of the MobileNet224 Full1 is installed in the Astra SDK Image.


## Deployment on Synaptics Astra SL1600 Series 

This particular model is compiled for **Synaptics Astra SL1680** processor. You can find this model already pre-installed on Machina™ Dev kit with SL1680 processor. 

You can also find the same model compiled for **Synaptics Astra SL1640** processor pre-installed on Machina™ Dev kit with SL1640 processor.

Synaptics Astra Machina™ is Modular developer kit for Astra SL-Series of high-performance IoT processors with integrated Synaptics Veros™ wireless connectivity solution. Learn more [here](https://www.synaptics.com/products/embedded-processors/astra-machina-foundation-series)

### Application binary

The `synap_cli_od` command line application allows running object detection models like MobileNet224 Full1.

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

cd $MODELS/object_detection/people/model/mobilenet224_full1/mobilenet224_full1/mobilenet224_full1

synap_cli_od -m model.synap input_image.jpg
```


Example output on SL1680:

```
Input image: input_image.jpg (w = 640, h = 480, c = 3)
Detection time: 14.23 ms
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
| SL1680  | 14.23   |
| SL1640  | 36.53   |




## Optimize and Customize the model

Advanced users may wish to customize the source model and recompile it for the Synaptics Astra NPU. 
Please refer to the [Bring Your Own Model](https://developer.synaptics.com/docs/sl/tutorials/bring-your-own-model) section for more information.


    For reference, the `.synap` format model provided on the firmware image was compiled for the Synaptics Astra NPU with the following `.yaml` settings:

```yaml
security:
  secure: ${ENV:SYNAP_SECURITY_ENABLED}
  file: ../../../../../security.yaml
outputs:
  - dequantize: true
    format: retinanet_boxes w_scale=640 h_scale=480 anchors=${FILE:../anchors.json}
  - dequantize: true
    format: per_class_confidence

```
    

## License

The source model is licensed under [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

The compiled model for on-device deployment is covered under the [Synaptics Astra EULA](https://github.com/synaptics-astra/doc/blob/main/EULA.rst).

## Learn More

- [Synaptics AI Developer Zone](https://developer.synaptics.com?utm_source=hf): Get started with documentation, tutorials and resources for your Edge AI journey.
- [Astra Support Portal](https://synacsm.atlassian.net/servicedesk/customer/portal/543?utm_source=hf): Connect with our engineering team and community.