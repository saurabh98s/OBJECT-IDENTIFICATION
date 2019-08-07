# object-identification
# A simple image identification program
use "resnet50_coco_best_v2.0.1.h5"(download it) to train the image(in this case "image 2") in your working directory.
then each object which is identified will be displayed and marked and probability will be displayed along it's side.
this the image before you process it through your code:
![image before processing](https://github.com/saurabh98s/object-identification/blob/master/image3.jpg)

Now let us explain how the 10-line code works.

> from imageai.Detection
> import ObjectDetection
> import os

> execution_path = os.getcwd()

In the above 3 lines, we imported the ImageAI object detection class in the first line, imported the python os class in the second line and defined a variable to hold the path to the folder where our python file, RetinaNet model file and images are in the third line.

> detector = ObjectDetection()
> detector.setModelTypeAsRetinaNet()
> detector.setModelPath( os.path.join(execution_path , "resnet50_coco_best_v2.0.1.h5"))
> detector.loadModel()
> detections = detector.detectObjectsFromImage(input_image=os.path.join(execution_path , "image.jpg"),
> output_image_path=os.path.join(execution_path , "imagenew.jpg"))

In the 5 lines of code above, we defined our object detection class in the first line, set the model type to RetinaNet in the second line, set the model path to the path of our RetinaNet model in the third line, load the model into the object detection class in the fourth line, then we called the detection function and parsed in the input image path and the output image path in the fifth line.

In the above 2 lines of code, we iterate over all the results returned by the detector.detectObjectsFromImage function in the first line, then print out the name and percentage probability of the model on each object detected in the image in the second line.
ImageAI supports many powerful customization of the object detection process. One of it is the ability to extract the image of each object detected in the image. By simply parsing the extra parameter extract_detected_objects=True into the detectObjectsFromImage function as seen below, the object detection class will create a folder for the image objects, extract each image, save each to the new folder created and return an extra array that contains the path to each of the images.
> detections, extracted_images = detector.detectObjectsFromImage(input_image=os.path.join(execution_path , "image.jpg"),
> output_image_path=os.path.join(execution_path , "imagenew.jpg"), extract_detected_objects=True)

![after processsing the image will look like this](https://github.com/saurabh98s/object-identification/blob/master/imagenew.jpg)
