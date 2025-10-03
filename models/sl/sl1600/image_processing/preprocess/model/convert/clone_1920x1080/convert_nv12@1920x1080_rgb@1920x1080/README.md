---
library_name: synap
tags:
  - Image Processing
  - Astra SL
  - SL1600
  - MPU
---

  
# Convert NV12@1920x1080 to RGB@1920x1080

## Model Overview


A preprocessing model to convert NV12 formatted images from 1920x1080 resolution to RGB format at the same resolution.


The Convert NV12@1920x1080 to RGB@1920x1080 model  is developed and optimized for the Synaptics Astra™ **SL1680 processor** NPU and **SL1640 processor** NPU.

## Model Features
- **Model Type:** Image Processing
- **Input Size:** NV12@1920x1080
- **Output Size:** RGB@1920x1080

> **ℹ️ INFO:** 
> This model is ready to use on Synaptics Astra Machina boards. An NPU optimized version of the Convert NV12@1920x1080 to RGB@1920x1080 is installed in the Astra SDK Image.


## Deployment on Synaptics Astra SL1600 Series 

This particular model is compiled for **Synaptics Astra SL1680** processor. You can find this model already pre-installed on Machina™ Dev kit with SL1680 processor. 

You can also find the same model compiled for **Synaptics Astra SL1640** processor pre-installed on Machina™ Dev kit with SL1640 processor.

Synaptics Astra Machina™ is Modular developer kit for Astra SL-Series of high-performance IoT processors with integrated Synaptics Veros™ wireless connectivity solution. Learn more [here](https://www.synaptics.com/products/embedded-processors/astra-machina-foundation-series)
    
### Application binary
    
The `synap_cli_ip` command line application supports image processing models like Convert NV12@1920x1080 to RGB@1920x1080, including super-resolution.
    
Inputs:
    
* The converted synap model (`.synap` extension)
* Optionally, a region of interest in the image (if supported by the model)
* One or more raw images (`nv12`, `nv21`, `rgb`, `bgr`, `bgra`, `gray`, or `bin` formats)
    
Outputs:
    
* Processed image files named `outimage<i>_<W>x<H>.<ext>`, where:
      - `<i>` is the input file index
      - `<W>x<H>` are the output dimensions
      - `<ext>` is the output format (e.g., `nv12` or `rgb`)
    
Command line usage on Astra SL1680 and SL1640:
    
```
MODELS=/usr/share/synap/models/

cd $MODELS/image_processing/preprocess/model/convert/clone_1920x1080/convert_nv12@1920x1080_rgb@1920x1080

synap_cli_ip -m model.synap ../../sample/ref_1920x1080.nv12
```
    
Example output on SL1680:
    
```    
Input image: ../../sample/ref_1920x1080.nv12
Inference time: 30.81 ms
Writing output to file: outimage0_1920x1080.rgb
```
    
> **💡NOTE:**
> Input images are resized to the network input tensor size, except for `nv12`, where input files must match the network’s expected dimensions.

    
> **💡NOTE:**
> Use `image_to_raw` from the SyNAP toolkit to convert JPEG/PNG images to raw formats (e.g., `nv12`).


## Performance on NPU 

| Processors      | Inference Time (ms) |
|-------------|--------------------|
| SL1680  | 30.81   |
| SL1640  | 34.49   |




## Optimize and Customize the model

Advanced users may wish to customize the source model and recompile it for the Synaptics Astra NPU. 
Please refer to the [Bring Your Own Model](https://developer.synaptics.com/docs/sl/tutorials/bring-your-own-model) section for more information.


    For reference, the `.synap` format model provided on the firmware image was compiled for the Synaptics Astra NPU with the following `.yaml` settings:

```yaml
security:
  secure: ${ENV:SYNAP_SECURITY_ENABLED}
  file: ../../../../../security.yaml
inputs:
  - preprocess:
      type: NV12
      size:
        - 1920
        - 1080

```
    

## License

License for compiled model for on-device deployment is covered by under [Synaptics Astra EULA](https://github.com/synaptics-astra/doc/blob/main/EULA.rst).

## Learn More

- [Synaptics AI Developer Zone](https://developer.synaptics.com?utm_source=hf): Get started with documentation, tutorials and resources for your Edge AI journey.
- [Astra Support Portal](https://synacsm.atlassian.net/servicedesk/customer/portal/543?utm_source=hf): Connect with our engineering team and community.