# *CommsCoder*
<p align="center">
Depicts autoencoders as end-to-end communication systems. 
</p>
 
## Communication Systems Overview 
In essence, any communication system is comprised of a source of information, a transmitter, a channel, a receiver and a destination.

![thinformation_1](https://user-images.githubusercontent.com/44330120/47400146-a98dcf00-d787-11e8-9675-75763431f109.jpg)

Mathematically, any communication system can be discribed by using the following formalism. The source of information, Bob, wants to transmit a uniformly chosen message 
**S**, such that 

<p align="center">
<a href="https://www.codecogs.com/eqnedit.php?latex=$S&space;\in&space;\mathcal{M}&space;=&space;\{1,....,M\}$" target="_blank"><img src="https://latex.codecogs.com/gif.latex?$S&space;\in&space;\mathcal{M}&space;=&space;\{1,....,M\}$" title="$S \in \mathcal{M} = \{1,....,M\}$" /></a>,
 </p>

in **n** discrete uses of the channel. To this end, a transmiter operates on the message to create a signal suitable for transmission and it generates a lower level representation of message **S** (i.e., converts the message **S** of size **M** to a message **T** of size **n**). As a result, the communication rate of the message is **R = k/n** [bits per channel use], where 

<p align="center">
<a href="https://www.codecogs.com/eqnedit.php?latex=$k&space;=&space;\log_2&space;M$" target="_blank"><img src="https://latex.codecogs.com/gif.latex?$k&space;=&space;\log_2&space;M$" title="$k = \log_2 M$" /></a>.
</p>

The transmiter imposes a power constraint on the message **T** (per bit, or on average), and the message **T** is then transmitted over the channel. The channel is the transmission medium and it is corrupted by Gaussian noise. The ratio between the input power and the power of the Gaussian noise is called the signal-to-noise ratio (SNR). As a result of the channel noise, the receiver receives a distorted version of the message **T**, denoted by **T'**. The receiver operates on the received message and generates a higher level representation of message **T'** (i.e., converts the message **T'** of size **n** to a message **S'** of size **M**). The destination, Alice, then decodes the transmitted message. 

## Communication Systems Revisited 

This project mimics a communication system with an autoencoder in TensorFlow. 

![thinformation_nn_v1](https://user-images.githubusercontent.com/44330120/47535971-825f0b00-d909-11e8-8c5c-0c85e36913c7.jpg)

The input layer, of size **M**, is a one-hot representation of the uniformly chosen message **S**. The first hidden layer, of size **n**, creates a lower level representation of **S**. The output of this hidden layer is then corrupted by Gaussian noise and is used as an input to the second hiddel layer of size **n**. The output layer, of size **M**, is a higher level representation of hidden layer 2. The decoded message is found as argmax(output layer).

The adopted metric is the bit-error-rate (BER), which quantifies how many bits of the one-hot representation of the output message differ from the one-hot representation of the input message. For higher SNR the BER is lower, and conversly, lower SNR means higher BER. For high enough SNR, the BER should be zero.

## Prerequisites 
The code requires:

* TensorFlow

`$ pip install TensorFlow`

* Numpy

`$ pip install numpy`

## Further reading
Check out http://math.harvard.edu/~ctm/home/text/others/shannon/entropy/entropy.pdf for further info on communication systems, and http://ufldl.stanford.edu/tutorial/unsupervised/Autoencoders/ for a very good and concise explination on autoencoders. 
