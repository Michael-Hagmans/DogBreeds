# Classification of Dog Breeds - a Blog Post

In this blog post I would like to describe my journey on classifying dog images to the corresponding dog breed. My point of view is rather technical and I would like to discuss to approaches to solve this data science problem: designing a convolutional neural network (CNN) from scratch or using transfer learning to benefit from pre-trained networks.

**Why Dog Breeds?**

On the one hand my motivation is that I personally love dogs but it is hard for me to remember all the different dog breeds out there. That is why it would be wonderful to have a script that identifies dog breeds for me. On the other hand I like the technical challenge to distinguish dog images as two different dog breeds look pretty similar here and there. In the data set I used there are 133 different dog breeds present which is quite a lot.

**Convolutional Neural Networks from Scratch**

I started with designing an architecture for a CNN from scratch. The first layer is a convolutional layer with 16 filters that expects an input shape of 224 by 224 pixels with three color codes each. Is is followed by a max pooling layer that reduces the number of parameters in the model which makes overfitting to the training data less likely. This is because convolutional layers cause the model to have many parameters which makes it possible for the model to fit the training data well. A result might be the model does not work too well on new images which is called overfitting.
Afterwards another two combinations of convolutional layers and max pooling layers are added where the number of filters is doubled each time so that the third convolutional layer consists of 64 filters. For the filters the idea that they find simple edges and shapes with the early layers and then combine those simple shapes into more complex shapes which happens in the later layers. That is why the number of filters is increasing.
Another chance to avoid overfitting is to add a global average pooling layer in the end which was done in this architecture. Finally a fully connected dense layer with 133 nodes is added in the end. This has one node for each dog breed in the data set.
Even if the architecture sounds a bit complex it is not compared to pre-trained models that you can use in transfer learning. That might be a reason why the performance of this model is rather weak with about 1% accuracy. 1% is still better than just guessing which would result in an accuracy of about 0.75%, assuming that all breeds have a similar occurrence in the data set. So there is still much room for improvement and there are basically two chances for improvement: You could improve the model's architecture and play around with some of its parameters or you could try one of the pre-trained models out there from keras. To save some time I decided for transfer learning because training different architectures takes a lot of time even on GPU.

**Make Use of Transfer Learning**

In the end dog breed classification worked very well. With 133 different breeds, an accuracy of 1% is already better than guessing.
Thus an accuracy of about 80% is a very good result. This was reached using transfer learning.

**Summary**

**Acknowledgment**

When I was working on this project the things learned in the Udacity Data Scientist Nanodegree program were extremely helpful.
Furthermore I made use of those sources that helped me solving the problems:

https://gist.github.com/Thimira/6dc1da782b0dca43485958dbee12a757

https://keras.io/applications/#resnet