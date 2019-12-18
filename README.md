# PPE Detector for Worker Safety
The PPE Detector for Worker Safety - is a real-time computer vision model for PPE non-compliance detection in the industrial setting. Trained on a synthetic dataset of 100,000 images and finetuned on Real World dataset, it analyzes live footage from high-resolution cameras to identify workers missing any of the PPE items specified in safety regulations. The solution detects seven object classes: Bare Head, Helmet, Ear Protection, Welding Mask, Bare Chest, High Visibility Vest, Person. The ML model can be used in manufacturing, construction, steel, oil & gas, and other industrial environments.

## Usage Information

Using our model for real time prediction is as simple as this:

```python
predictor = sage.predictor.RealTimePredictor(
    ' your endpoint name ',
    sagemaker_session=sagemaker.Session(),
    content_type="image/jpeg"
)

with open('data/sample_image.jpg', 'rb') as img:
    img_bytes = bytearray(img.read())
    result = predictor.predict(img_bytes).decode("utf-8")
```

Also we've published two notebooks showing how to use our model:
* [Using-PPE-Detector-Endpoint.ipynb](Using-Personal-Protection-Equipment-Detection-model.ipynb) notebook shows how you can use Python API to perform inference on endpoint created from the model
* [PPE-Detector-Full-Example.ipynb](Using-Personal-Protection-Equipment-Detection-model.ipynb) notebook shows how you can use Python API to run the full scenario:
    * deploy our model to create an endpoint
    * run Real Time inference on endpoint using local image
    * visualize  and save the prediction on original image
    * run Batch Transform job to perfom the inference on your data stored in Amazon S3 bucket

## Input\output data examples

* You can find sample input data in [demo_input](data/test_samples/demo_input) folder
* [demo_output_images](data/test_samples/demo_output_images) folder contains images with detections predicted by the model and visualized using `utils.visualize_detection` method
* [demo_raw_output](data/test_samples/demo_raw_output) folder contains raw output generated by our model using `Batch Transform` approach