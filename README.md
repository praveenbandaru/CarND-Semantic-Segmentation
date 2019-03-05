
# Semantic Segmentation

[//]: # (Image References)

[image1]: ./runs/latest/um_000032.png "Sample 1"
[image2]: ./runs/latest/um_000068.png "Sample 2"
[image3]: ./runs/latest/umm_000051.png "Sample 3"
[image4]: ./runs/latest/uu_000026.png "Sample 4"
[image5]: ./runs/latest/uu_000097.png "Sample 5"

### Introduction
The goal of this project is to label the pixels of a road in images using a Fully Convolutional Network (FCN) as described in the [Fully Convolutional Networks for Semantic Segmentation](https://people.eecs.berkeley.edu/~jonlong/long_shelhamer_fcn.pdf) by Jonathan Long, Even Shelhamer, and Trevor Darrel. This uses a VGG-16 based FCN model and is trained on the [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php). The project is based on the starter code provided by Udacity in this [repo](https://github.com/udacity/CarND-Semantic-Segmentation).

### Architecture
The Fully Convolutional Network (FCN) is based on a pre-trained VGG-16 image classification network. The VGG-16 network acts as a encoder. In order to implement the decoder, I extracted the layers 3, 4 and 7 from the VGG-16 network and implemented several up-sampling and skip connections as shown below ([`main.py`  line 61 - 97](https://github.com/praveenbandaru/CarND-Semantic-Segmentation/blob/a45c872e729559afb735ae2e5cdc81a024267305/main.py#L61)):


### Results
The above implemented Fully Convolutional Network (FCN) was able to classify the road area very well in most scenarios. It is not perfect but failed to detect properly in some edge cases where shadows were predominant. This is due to the presence of a smaller training set (around 289 images). By augmenting the training set the performance could be further improved.

Below are some sample images:

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]

### Setup
##### GPU
`main.py` will check to make sure you are using GPU - if you don't have a GPU on your system, you can use AWS or another cloud computing platform.
##### Frameworks and Packages
Make sure you have the following is installed:
 - [Python 3](https://www.python.org/)
 - [TensorFlow](https://www.tensorflow.org/)
 - [NumPy](http://www.numpy.org/)
 - [SciPy](https://www.scipy.org/)

You may also need [Python Image Library (PIL)](https://pillow.readthedocs.io/) for SciPy's `imresize` function.

##### Dataset
Download the [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) from [here](http://www.cvlibs.net/download.php?file=data_road.zip).  Extract the dataset in the `data` folder.  This will create the folder `data_road` with all the training a test images.

### Start
##### Run
Run the following command to run the project:
```
python main.py
```
**Note:** If running this in Jupyter Notebook system messages, such as those regarding test status, may appear in the terminal rather than the notebook.
