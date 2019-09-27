# ConvDeNoise: A convolutional denoising autoencoder to denoise correlation functions

* **Edit 27/09/2019**: Small changes of the input data normalization and architecture. The new normalization of the SC functions should be between -1 and 1 (0 and 1 in the 1st version). The new autoencoder only has 4 hidden layers (6 layers in the first version). These two changes decrease the number of parameters to train for the same level of performance. **A revised version of the pre-print will soon be online.**

* Codes to reproduce Figure 7 (Figure 8 can also be plotted by changing two lines of the code) of the following paper:
  - Viens L. and Van Houtte C., Denoising ambient seismic field correlation functions with convolutional autoencoders (submitted to GJI). A preprint (not peer-reviewed) of the paper is available at https://eartharxiv.org/q4m2t/.
  
* The autoencoder is composed of an encoder part and a decoder part:
![Image of ConvDeNoise](https://github.com/lviens/ConvDeNoise/blob/master/ConvDeNoise_architecture.png)


* The **Codes** folder contains 5 files: 
  - The **Reproduce_Fig_7.py** file is the python code to reproduce Figure 7.
  - The **functions_for_autoencoders.py** file contains functions to bandpass filter the data with a Butterworth filter, denoise the SC functions with the SVDWF method (Moreau et al., 2017), and compute the stretching to retrieve dv/v measurements
  - The **ConvDeNoise_NS7M_station.h5** contains the weights of ConvDeNoise trained for the NS7M station (Requires Keras 2.2.4)
  - The **Test_data.mat** contains 16 days of raw SC functions at the NS7M station, reference waveforms to compute the dv/v,... (e.g., all the data required to reproduce Figure 7).
  - The **ConvDeNoise_core.py** file is the convolutional denoising autoencoder main code that was used to compute the **ConvDeNoise_NS7M_station.h5** file (requires the raw SC functions, please email me for the training set, file is too big for Github)
 
