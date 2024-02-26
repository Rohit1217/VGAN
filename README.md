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
* We simply run the trained generators to produce images from random noise

## Psuedocode(Training)
* Take an image(MNIST)
* We feed  this to discriminator and run forward pass
* Backprop on the loss to maximize the probability of correctly identifying this images
* Generate same number of images from Genrator using random noise
* Send this images to discriminator, run backprop to minimize the probability of correctly identifying these images.

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
