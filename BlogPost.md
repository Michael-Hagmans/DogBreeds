# Classification of Dog Breeds - a Blog Post

In this blog post I would like to describe my journey on classifying dog images to the corresponding dog breed. My point of view is rather technical and I would like to discuss two approaches to solve this data science problem: Is it worth designing a convolutional neural network (CNN) from scratch or is it reasonable to use transfer learning to benefit from pre-trained networks?

**Why Dog Breeds?**

On the one hand my motivation is that I personally love dogs but it is hard for me to remember all the different dog breeds out there. That is why it would be wonderful to have a script that identifies dog breeds for me. On the other hand I like the technical challenge to distinguish dog images as two different dog breeds look pretty similar here and there. In the data set I used there are 133 different dog breeds present which is quite a lot.

**Convolutional Neural Networks from Scratch**

I started with designing an architecture for a CNN from scratch. The first layer is a convolutional layer with 16 filters that expects an input shape of 224 by 224 pixels with three color codes each. It is followed by a max pooling layer that reduces the number of parameters in the model which makes overfitting to the training data less likely. This is because convolutional layers cause the model to have many parameters which makes it possible for the model to fit the training data well. A result might be that the model does not work too well on new images which is called overfitting.

Afterwards another two combinations of convolutional layers and max pooling layers are added where the number of filters is doubled each time so that the third convolutional layer consists of 64 filters. For the filters the idea that they find simple edges and shapes with the early layers and then combine those simple shapes into more complex shapes which happens in the later layers. That is why the number of filters is increasing.

Another chance to avoid overfitting is to add a global average pooling layer in the end which was done in this architecture. Finally a fully connected dense layer with 133 nodes is added in the end. This has one node for each dog breed in the data set.

![Testtext](https://github.com/Michael-Hagmans/DogBreeds/blob/master/models/model1.jpg?raw=true)


Even if the architecture sounds a bit complex it is not compared to pre-trained models that you can use in transfer learning. That might be a reason why the performance of this model is rather weak with about 1% accuracy. 1% is still better than just guessing which would result in an accuracy of about 0.75%, assuming that all breeds have a similar occurrence in the data set. So there is still much room for improvement and there are basically two chances for improvement: You could improve the model's architecture and play around with some of its parameters or you could try one of the pre-trained models out there from keras. To save some time I decided for transfer learning because training different architectures takes a lot of time even on GPU.

**Make Use of Transfer Learning**

I decided to use a pre-trained ResNet50 model which was trained on the imagenet data set. This data set contains various images but one part are dog images so the use case is at least similar. The data set used here contains only about 8000 images which is rather small, especially when you consider that we have 133 different dog breeds. So I am using a similar data set and a rather small data set. In such cases it is recommended to use a pre-trained model and just to adjust the final layer.

What I added in the end was a global average pooling layer to avoid overfitting and a dense layer with a node for each dog breed (133). All images were passed through the pre-trained ResNet50 network and the result (bottleneck features) was used to train the final layers. 

The ResNet50 network has 50 layers, including many convolutional layers. Those are capable to adapt many different shapes or even dog parts (eyes, ears, ...) so that a much better accuracy can be expected. 

This might be the reason why the model using transfer learning results in a much better accuracy of about 80% correctly classified dog images. 

**Summary**

When working on this project I found out that it is hard to come up with a CNN architecture that can compete with pre-trained models even if the use case is similar and the data set you train on is rather small. That is why I found out for me that I will give transfer learning a try in the future when it comes to classifying images. 


**Acknowledgment**

When I was working on this project the things learned in the Udacity Data Scientist Nanodegree program were extremely helpful.
Furthermore I made use of those sources that helped me solving the problems:

https://gist.github.com/Thimira/6dc1da782b0dca43485958dbee12a757

https://keras.io/applications/#resnet

https://www.quora.com/What-is-the-deep-neural-network-known-as-%E2%80%9CResNet-50%E2%80%9D

The data sets used to train the models can be found here:

https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/dogImages.zip

https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/lfw.zip
