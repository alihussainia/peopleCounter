# Project Write-Up

You can use this document as a template for providing your project write-up. However, if you
have a different format you prefer, feel free to use it as long as you answer all required
questions.

## Explaining Custom Layers

The process behind converting custom layers involves...

Custom layers are a necessary and important to have feature of the OpenVINO™ Toolkit, although one shouldn’t have to use it very often, if at all, due to all of the supported layers. 

The list of supported layers relates to whether a given layer is a custom layer. Any layer not in that list is automatically classified as a custom layer by the Model Optimizer.

To actually add custom layers, there are a few differences depending on the original model framework. 

You have three options for TensorFlow* models with custom layers:

- Register those layers as extensions to the Model Optimizer. In this case, the Model Optimizer generates a valid and optimized Intermediate Representation.
- If you have sub-graphs that should not be expressed with the analogous sub-graph in the Intermediate Representation, but another sub-graph should appear in the model, the Model Optimizer provides such an option. This feature is helpful for many TensorFlow models. To read more, see Sub-graph Replacement in the Model Optimizer.
- Experimental feature of registering definite sub-graphs of the model as those that should be offloaded to TensorFlow during inference. In this case, the Model Optimizer produces an Intermediate Representation that:

 - Can be inferred only on CPU 
 - Reflects each sub-graph as a single custom layer in the Intermediate Representation


Some of the potential reasons for handling custom layers are...

Model Optimizer searches for each layer of the input model in the list of known layers before building the model's internal representation, optimizing the model, and producing the Intermediate Representation.

The list of known layers is different for each of supported frameworks. To see the layers supported by your framework, refer to the corresponding section.

Custom layers are layers that are not included into a list of known layers. If your topology contains any layers that are not in the list of known layers, the Model Optimizer classifies them as custom.

## Comparing Model Performance

My method(s) to compare models before and after conversion to Intermediate Representations
were...


## Comparing Model Performance


**First I downloaded the SSD Mobile Net Model which came as tensorflow frozen_graph. I used wget http://download.tensorflow.org/models/object_detection/ssd_mobilenet_v2_coco_2018_03_29.tar.gz**

**Then I switched directory to the ssd_mobilenet_v2_coco_2018_03_29 directory**

**Then I typed in the terminal to convert the frozen graph into an IR:
***python /opt/intel/openvino/deployment_tools/model_optimizer/mo.py --input_model frozen_inference_graph.pb --tensorflow_object_detection_api_pipeline_config pipeline.config --reverse_input_channels --tensorflow_use_custom_operations_config /opt/intel/openvino/deployment_tools/model_optimizer/extensions/front/tf/ssd_v2_support.json***

## Assess Model Use Cases

Some of the potential use cases of the people counter app are...

**No of customers daily visiting the store**
 
Each of these use cases would be useful because...

This web app can be beneficial for a store owner to know how many customers visited the store via watching the count metric.

## Assess Effects on End User Needs

**Model Matters More**

Lighting, model accuracy, and camera focal length/image size have different effects on a
deployed edge model. The potential effects of each of these are as follows...

Since my model was not specifically trained to recognized people, but it did quite well on still person, but didn't perform well when a person tried to move. So I would say that on one hand if Lighting, model accuracy, and camera focal length/image size matters, the best training of the model matters too, so that it can perform very well even in the low resource environments.

The difference between model accuracy pre- and post-conversion was...

** Not Applied in my case **
The size of the model pre- and post-conversion was...
** Not Applied in my case **
The inference time of the model pre- and post-conversion was...
** Not Applied in my case **

## Model Research

[This heading is only required if a suitable model was not found after trying out at least three
different models. However, you may also use this heading to detail how you converted 
a successful model.]

In investigating potential people counter models, I tried each of the following three models:

- Model 1: [Name]
  - [Model Source]
  - I converted the model to an Intermediate Representation with the following arguments...
  - The model was insufficient for the app because...
  - I tried to improve the model for the app by...
  
- Model 2: [Name]
  - [Model Source]
  - I converted the model to an Intermediate Representation with the following arguments...
  - The model was insufficient for the app because...
  - I tried to improve the model for the app by...

- Model 3: [Name]
  - [Model Source]
  - I converted the model to an Intermediate Representation with the following arguments...
  - The model was insufficient for the app because...
  - I tried to improve the model for the app by...
