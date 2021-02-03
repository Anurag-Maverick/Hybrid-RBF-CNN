# Hybrid-RBF-CNN

Electrocardiogram (ECG) signal monitoring is the most popular practice in medical science to analyse the heart’s function and hence, diagnose abnormal heartbeats. Hence, there has been an increasing interest towards fast and accurate classification of heartbeats.This problem is a multiclass classification of heart-beats into 4 abnormal (diseases) and 1 normal class (total 5 classes). 

In ECG classification problem, 1D-signal segments are in time domain. Now, this 1D signal suffers from being too noisy and too less information to be extracted. This becomes even less effective when you have very large number of samples, as, apart from the peaks and troughs, the entire series is almost similar for all the samples. Apart from this, many authors have also gained significant success by utilising frequency domain features by performing FFT on the dataset. In this method, the temporal variation is lost completely.

Hence, to retain maximum amount of information, wavelet analysis has been implemented in this work.

Dataset is available at: https://www.kaggle.com/shayanfazeli/heartbeat (PhysioNet MIT-BIH Arrhythmia dataset)

Preprocessing: 

  1. Denoising ECG SIgnal
  Python’s Skimage library has the BayesShrink algorithm, which is an adaptive approach to wavelet soft thresholding where a unique threshold is estimated for each wavelet sub-     band. Here, a symplet 8 (i.e. Daubechies’ least-asymmetric wavelet having 8 vanishing moments) has been used for denoising purpose.
  
  2. Wavelet Packet Decomposition Power Spectrum
  Wavelet Packet Decomposition (WPD) is a wavelet transform where the discrete-time (sampled) signal is passed through more filters than the discrete wavelet transform (DWT).       Further read is available at: https://www.mathworks.com/help/wavelet/ug/wavelet-packets-decomposing-the-details.html
  in this work, level 3 sub-bands of db3 wavelets (i.e. Daubechies’ extremal phase wavelets having 3 vanishing moments) have been extracted and stacked one over another to give a   8x29x1 dimensional image for each beat. Thus a 2D time-frequency representational feature space has been successfully extracted here.
  
 Classifiers:
  The classifiers studied here are : CNN (with Residual units), RBFNN and Hybrid RBFNN-CNN networks for comparison. While in CNN, the entire 8x29x1 dimensional image is taken as     input, in the latter 2, we only take the approximate band (29x1 dimensional) as input feature.

