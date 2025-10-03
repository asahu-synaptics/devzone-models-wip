---
license: apache-2.0
library_name: tflite
pipeline_tag: image-segmentation
tags:
    - Astra SR
    - SR100
    - MCU
    - Person Segmentation
---
# Person Segmentation 256x480 (SR100 Series)

## Model Overview

The **Person Segmentation 256x480** model developed by Synaptics, is a lightweight quantized `tflite` model developed for the **SR100 processor** in the Synaptics Astra™  SR MCU Series. 

The output includes segmented regions that represent the exact shape of each person in the image, providing both segmentation and confidence-level insights for each detection.

## Model Features

- **Model Type:** Person Segmentation
- **Input Size:** 256x480
- **Output:** For each detected person, a segmentation mask outlining along with confidence scores for each region.
- **Classes:** Single class (person); specifically designed for person segmentation.


## Deployment on Astra

You can optimize this model for Synaptics Astra SR100 MCU using our our hosted [SR100 Model Compiler HF Space](https://huggingface.co/spaces/Synaptics/SR100-Model-Compiler).

- **Processor:**  Astra™ SR100 MCU
- **Platform:**  Astra™ Machina Micro Dev Kit
- **Quantization:** INT8 (fully quantized)
- **Compiler:** [SR100 Model Compiler](https://huggingface.co/spaces/Synaptics/SR100-Model-Compiler)
- **Preprocessing:** Input images must be resized and quantized to match model requirements

## Intended Applications

This model enables **real-time person segmentation** for embedded edge devices. Example use cases include:

- Human presence and activity monitoring
- Fitness and wellness tracking
- Smart home automation
- Interactive user interfaces


## Evaluate Model

You can evaluate and test this model directly in our hosted [Hugging Face Space](https://huggingface.co/spaces/Synaptics/SR100-Model-Compiler),  optimized for **Synaptics SR110** MCU. This space provides a seamless sandbox for model evaluation using hardware-specific quantization and runtime settings.

For a detailed walkthrough on how to optimize and evaluate a model, please see our [Evaluate Model Guide](https://developer.synaptics.com/docs/sr/sr100/evaluate-sr?utm_source=hf) page.

To get started quickly with Astra SR Series, visit our [SR Quick Start](https://developer.synaptics.com/docs/sr/sr110/quick-start?utm_source=hf) page.

## License

Distributed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0), allowing flexible use, modification, and distribution.

## Learn More

- [Synaptics AI Developer Zone](https://developer.synaptics.com?utm_source=hf): Get started with documentation, tutorials and resources for your Edge AI journey.
- [Astra Support Portal](https://synacsm.atlassian.net/servicedesk/customer/portal/543?utm_source=hf): Connect with our engineering team and community.