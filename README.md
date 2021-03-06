# ConvDeNoise: A convolutional denoising autoencoder for seismic monitoring - [Viens and Van Houtte (2019, GJI)](https://academic.oup.com/gji/article/220/3/1521/5663618?guestAccessKey=f794ef77-e0ce-463d-bb70-c6478aa9ffec)

## Updates:
* **27/09/2019, Update 2**: About the hyperparameters of ConvDeNoise (**ConvDeNoise_core.py** file):
  - We recommend to set the number of filters (F_nb) to 30 or 40 to denoise SC functions.
  - We tried different kernel sizes (K_sz) between 100 and 150 and found that this parameter does not really impact the denoising performance.
  - For more details, see the manuscript and the supplementary material.

* **27/09/2019, Update 1**: Small changes of the input data normalization and architecture: 
  - We changed the amplitude normalization of the SC functions between -1 and 1 (0 and 1 in the 1st version). 
  - The new autoencoder only has 4 hidden layers (6 layers in the 1st version). 
  - The last activation function is the hyperbolic tangent activation (tanH) function to output the denoised SC function amplitudes between -1 and 1 (Sigmoid function in the 1st version). 
  - These three changes decrease the number of parameters to train for the same level of performance. 

  
## Description:
* Python codes to reproduce Figure 7 (Figure 8 can also be plotted by changing 1 line of the code) of [Viens L. and Van Houtte C. (2019), Denoising ambient seismic field correlation functions with convolutional autoencoders, Geophys. J. Int., 220, 1521–1535](https://academic.oup.com/gji/article/220/3/1521/5663618?guestAccessKey=f794ef77-e0ce-463d-bb70-c6478aa9ffec). Note that the published paper incorporates the modifications made on Sept. 27, 2019 (See above).

* The ConvDeNoise algorithm is a convolutional denoising autoencoder which is composed of an encoder and a decoder as:
![Image of ConvDeNoise](https://github.com/lviens/ConvDeNoise/blob/master/ConvDeNoise_architecture.png)


* The **Codes** folder contains 5 files: 
  - The **Reproduce_Fig_7.py** file is the python code to reproduce Figures 7 and 8 of the paper (Default: plot Figure 7, simply change "fig_choice = 7" to "fig_choice = 8" (L. 71) to plot Figure 8).
  - The **functions_for_autoencoders.py** file contains functions to bandpass filter the data with a Butterworth filter, denoise the SC functions with the SVDWF method (Moreau et al., 2017), and compute the stretching to retrieve dv/v measurements
  - The **ConvDeNoise_NS7M_station.h5** contains the weights of ConvDeNoise trained for the NS7M station (Requires Keras 2.2.4)
  - The **Test_data.mat** contains 16 days of raw SC functions at the NS7M station, reference waveforms to compute the dv/v,... (e.g., all the data required to reproduce Figure 7).
  - The **ConvDeNoise_core.py** file is the convolutional denoising autoencoder main code that was used to compute the **ConvDeNoise_NS7M_station.h5** file (requires the raw SC functions, please email me for the training set, file is too big for Github)
 
