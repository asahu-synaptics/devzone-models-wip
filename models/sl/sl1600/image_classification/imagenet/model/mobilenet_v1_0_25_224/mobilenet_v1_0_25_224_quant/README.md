---
library_name: synap
tags:
  - Image Classification
  - Astra SL
  - SL1600
  - MPU
---

  
# MobileNet V1 0.25 224 Quant

## Model Overview


A quantized MobileNet V1 model with a 0.25 width multiplier optimized for image classification on ImageNet at 224x224 resolution.


The MobileNet V1 0.25 224 Quant model  is developed and optimized for the Synaptics Astra™ **SL1680 processor** NPU and **SL1640 processor** NPU.

## Model Features
- **Model Type:** Image Classification
- **Input Size:** 224x224
- **Output Size:** 224x224

> **ℹ️ INFO:** 
> This model is ready to use on Synaptics Astra Machina boards. An NPU optimized version of the MobileNet V1 0.25 224 Quant is installed in the Astra SDK Image.


## Deployment on Synaptics Astra SL1600 Series 

This particular model is compiled for **Synaptics Astra SL1680** processor. You can find this model already pre-installed on Machina™ Dev kit with SL1680 processor. 

You can also find the same model compiled for **Synaptics Astra SL1640** processor pre-installed on Machina™ Dev kit with SL1640 processor.

Synaptics Astra Machina™ is Modular developer kit for Astra SL-Series of high-performance IoT processors with integrated Synaptics Veros™ wireless connectivity solution. Learn more [here](https://www.synaptics.com/products/embedded-processors/astra-machina-foundation-series)

### Application binary

The `synap_cli_ic` command line application available 
in the Synaptics Astra Machine SDK makes it easy to run image classification models like MobileNet V1 0.25 224 Quant.

Inputs:

* The converted synap model (`.synap` extension)
* One or more images (jpeg or png format)

Outputs:

* The top five most probable classes for each input image provided

Command line usage on Astra SL1680 and SL1640:

```
MODELS=/usr/share/synap/models/

cd $MODELS/image_classification/imagenet/model/mobilenet_v1_0.25_224/mobilenet_v1_0.25_224_quant/mobilenet_v1_0.25_224_quant

synap_cli_ic -m model.synap ../../sample/goldfish_224x224.jpg
```

Example output on SL1680:

```
Loading network: model.synap
Input image: ../../sample/goldfish_224x224.jpg
Classification time: 0.77 ms
Class  Confidence  Description
    1       18.99  goldfish, Carassius auratus
  112        9.30  conch
  927        8.70  trifle
   29        8.21  axolotl, mud puppy, Ambystoma mexicanum
  122        7.71  American lobster, Northern lobster, Maine lobster, Homarus americanus
```

> **ℹ️ INFO:**
> Input images are automatically resized to the size of the network input tensor by the software pre-processor. This is not included in the classification time displayed.



## Performance on NPU 

| Processors      | Inference Time (ms) |
|-------------|--------------------|
| SL1680  | 0.77   |
| SL1640  | 0.93   |




## Optimize and Customize the model

Advanced users may wish to customize the source model and recompile it for the Synaptics Astra NPU. 
Please refer to the [Bring Your Own Model](https://developer.synaptics.com/docs/sl/tutorials/bring-your-own-model) section for more information.


    For reference, the `.synap` format model provided on the firmware image was compiled for the Synaptics Astra NPU with the following `.yaml` settings:

```yaml
outputs:
  - dequantize: false
    format: confidence_array class_index_base=-1

```
    

## License

The source model is licensed under [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

The compiled model for on-device deployment is covered under the [Synaptics Astra EULA](https://github.com/synaptics-astra/doc/blob/main/EULA.rst).

## Learn More

- [Synaptics AI Developer Zone](https://developer.synaptics.com?utm_source=hf): Get started with documentation, tutorials and resources for your Edge AI journey.
- [Astra Support Portal](https://synacsm.atlassian.net/servicedesk/customer/portal/543?utm_source=hf): Connect with our engineering team and community.