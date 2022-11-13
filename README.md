# Image Captioning Project
# 1. Introduction
This's a project about Image Captioning (aka Automated Image Generator) task. To put it simple, It's mean that you push into the model an image, the model will return a sentence described it. 
In this project, I'll use [Flickr 8k dataset](https://www.kaggle.com/datasets/adityajn105/flickr8k). Weights for VGG16 model is [here](https://github.com/fchollet/deep-learning-models/releases/download/v0.1/vgg16_weights_tf_dim_ordering_tf_kernels.h5), we need them to extract features from images. This's my notebook in [Kaggle](https://www.kaggle.com/code/biminhc/image-captioning-and-inference/notebook), It's easier to test.

For instance:
![image](https://miro.medium.com/max/1400/1*6BFOIdSHlk24Z3DFEakvnQ.png)

# 2. Data Preprocessing
In this project, I used Fickr 8k dataset downloaded from Kaggle. The dataset was handled by some steps following:
* Convert sentences into lowercase
* Remove special characters and numbers present in the text
* Remove extra spaces
* Remove single characters
* Add a starting and an ending tag to the sentences to indicate the beginning and the ending of a sentence

# 3. Tokenization and Encoded Representation
The words in a sentence are separated/tokenized and encoded in a one hot representation. These encodings are then passed to the embedding layer to generate word embedding

# 4. Image Feature Extraction
I used the VGG16 model (without the last layer) to extract features all the images in the dataset. 
This process is offline learning, which means we can extract before trained model, all features were stored in a Pickle file (features.pkl).

# 5. Modeling
The image embedding representations are concatenated with the first word of sentence ie. <starseq> and passed to the LSTM network.
The LSTM network starts generating words after each input thus forming a sentence at the end. <br />


A slight change has been made in the original model architecture to push the performance. The image feature embeds are added to the output of the LSTMs and then passed on to the fully connected layers.
This slightly improves the performance of the model originally proposed back in 2014: Show and Tell: A Neural Image Caption Generator (arxiv.org/pdf/1411.4555.pdf)



# 6. Reference
[QUADEER SHAIKH: Flickr8K Image Captioning](https://github.com/quadeer15sh/Flickr8K-Image-Captioning/blob/a3e31d345d5260980a653245c07e492bd4cdfb06/flickr8k-image-captioning-using-cnns-lstms.ipynb)


