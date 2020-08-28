# cloud_detection
## Introduction
Shallow clouds play a huge role in determining the Earth's climate. They’re also difficult to understand and to represent in climate models. By classifying different types of cloud organization, researchers at Max Planck hope to improve our physical understanding of these clouds, which in turn will help us build better climate models.

## Project goals
**The challenge is to segment satellite images into one of four classes: Sugar, Flower, Fish and Gravel**. These clouds look benign compared to big thunderstorms but, in fact, for the Earth’s climate they play a huge role. The reason is that they reflect a lot of sunlight back into space, thereby cooling our planet, while only contributing marginally to the greenhouse effect. This means that it’s really important to figure out how these clouds will change as our planet warms.

## Approach
In this notebook, I tried to solve the problem with 2 approach ways: **Multi-label classification approach** and **Multi-class classification approach**. 
- For **multi-label classification approach**: *Our model just achieved about 47.6% accuracy on the test set*, which is very low for a classification problem. I think the main reason for the low accuracy is there are overlapped region between labels in an image, which would make the model harder to classify. But this seems the easiest way to handle the problem. 
- For **multi-class classification approach**: By cropping out the mask of each label in images and save them as a new image, our problem would become a multi-class classification problem. Therefore, *the accuracy achieved by this way has significantly increased up to 67-68%*. But this approach still do not handle well with the overlapped area, which limit the accuracy of the model. Furthermore, this way also set out one more task for us: *We need to detect if there is any special cloud-organization in an image first and then let model predict what kind of cloud-organization that area belongs to.*

## What we learned
- The tf.data.Dataset improves the training process significantly in term of time value and is RAM storage-wise.
- Threshold - the unique problem of multi-label classification problem. In this project, we still did not figured out the best threshold to choose for each label yet. By default, we assumed all the threshold has value as 0.5.

## Future works
- Collect more images so that model can learn better.
- Tuning the threshold level for each label that could improve the overall performance.
- Attempt on CNN model combined with Random Forest for better learning.
- Detect the location of the cloud-organization in each image
