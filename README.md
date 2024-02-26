# VGAN
* The following is an implementation based on the original GAN paper by Goodfellow
* We have done many experiments to get the thing working, only the final details are included in this file

## Training Datset
* Only MNIST Dataset was used to test due to compute constraint. We have not reported log probabilities, it is a future work on test dataset

## Architecture Details
* 5 layers ( Each has 784 neurons)
* One single value is outputted
* Activation function used ReLU
* Output Activation Sigmoid
* LayerNorms are not used during training. This architecture seems really inefficient and we will tweak it to make it more efficient

## Inference
* We take a zero vector of size (B,784)
* We autoregressively generate one pixel at a time (i+1th pixel is generated at ith run)
* Doing this proccess for 783 times generates the required image

## Psuedocode(Training)
* Take an image(MNIST)
* Flatten it to from B,28,28 to B,28*28
* We feed this to the Neural Network
* Apply the mask to weights and do forward pass
* Train using backprop with Adam optimizer, hyperparameters can be found in the code.

## Training Details
* Trained for 18 epochs on colab RAM
* Achieved avg log likelihood on training dataset

## Mask Details
* Raster scan mask(Same as Transformers), the current pixel can look at only previous pixel, enforces autoregressive property
* The masking is done in the raster scan order 

## Samples Generated
 ![Samples](sample.jpeg)
 
## Future changes/work
* Cleaning the code to make it more readable and efficieent
* Trying softmax by quantization of pixel
* Scaling the method to generate color image (We have done it on GPT)
* Using regularization methods such as batchnorm, dropout and observing the results.
* Using multiple and different masks simialr to paper
* HyperParameter Search
