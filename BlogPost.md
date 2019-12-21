# Classification of Dog Breeds - a Blog Post

In this blog post I would like to describe my journey on classifying dog images to the corresponding dog breed. My point of view is rather technical and I would like to discuss to approaches to solve this data science problem: designing a CNN from scratch or using transfer learning to benefit from pre-trained networks.

**Why Dog Breeds?**

On the one hand my motivation is that I personally love dogs but it is hard for me to remember all the different dog breeds out there. That is why it would be wonderful to have a script that identifies dog breeds for me. On the other hand I like the technical challenge to distinguish dog images as two different dog breeds look pretty similar here and there. In the data set I used there are 133 different dog breeds present which is quite a lot.

**Convolutional Neural Networks from Scratch**

dog_app.ipynb is the Jupyter Notebook I used to classify dog breeds.
The README.md is the file you are just looking at which describes the project.

**Make Use of Transfer Learning**

In the end dog breed classification worked very well. With 133 different breeds, an accuracy of 1% is already better than guessing.
Thus an accuracy of about 80% is a very good result. This was reached using transfer learning.

**Summary**

**Acknowledgment**

When I was working on this project the things learned in the Udacity Data Scientist Nanodegree program were extremely helpful.
Furthermore I made use of those sources that helped me solving the problems:

https://gist.github.com/Thimira/6dc1da782b0dca43485958dbee12a757

https://keras.io/applications/#resnet