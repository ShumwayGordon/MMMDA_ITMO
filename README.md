## Goal
Sampling of multivariate random variables

## Dataset description
“Ozone Level Detection Data Set” was used in this work.
Columns 'WSR_PK', 'WSR_AV' (wind speed ratio peak and average), 'T_PK', 'T_AV' (temperature peak and average), 'KI' (K-index), 'TT' (T-Totals), 'Precp' (Precipitation) were used as features. 'SLP' (sea pressure level) column was chosen as the target. All used variables are continuous.

## Step 1. Choosing variables for sampling from dataset
First of all, 10 features were selected from the original dataset, 3 of which became target values, and the rest became predictors.
### Predictors:
- T85: continuous. T at 850 hpa level (or about 1500 m height)
- U70: continuous. U wind - east-west direction wind at 700 hpa
- HT50: continuous. Geopotential height at 500 hpa, it is about the same as height at low altitude
- T70: continuous. T at 700 hpa level
- T8: continuous. 8-th measured temperature of a day
- V85: continuous. V wind - N-S direction wind at 850
- KI: continuous. K-Index
### Target:
- T_AV: continuous. Average T
- T_PK: continuous. Peak T
- T0: continuous. First measured temperature of a day

## Step 2. Sampling of chosen target variables
In the first part of the second step, it was necessary to sample the target values using the inverse transform method. In the first part of the second step, it was necessary to sample the target values using the inverse transform method. Figure 1 shows the histograms of the distributions of target values - the blue color represents the initial data from the dataset, and the orange color represents the generated values using inverse transform sampling.

<p align="center">
<img src="https://user-images.githubusercontent.com/33491221/181291035-87581c5d-5187-4031-96fd-3550c924616a.png">

Figure 1 - results of sampling target values using inverse transform method (blue - original data, orange - sampled data)
</p>

Next, in the second step, it was necessary to sample the target values using the Accept-Reject method. To do this, it was necessary to select a function similar to the target value distribution and multiply this function by the Scale Factor so that the target value distribution is completely below it. Figure 2 shows the target function distribution values and the selected functions that are required for the Accept-Reject method.

<p align="center">
<img src="https://user-images.githubusercontent.com/33491221/181291147-33df03d8-a301-4ae7-8e2e-9df7c5205fab.png">

Figure 2 - target functions distributions values t(x) (blue) and chosen functions h(x) (orange); ‘M‘ in the title stands for the Scale Factor value
</p>
 
Figure 3 shows histograms of the distributions of the initial and generated target values.

<p align="center">
<img src="https://user-images.githubusercontent.com/33491221/181291251-b2e33294-a669-433f-9409-267ed515fe9a.png">

Figure 3 - results of sampling target values using accept-reject method
</p>
 
## Step 3. Estimation of relations between predictors and chosen target variables
At the third step, it was necessary to assess the relationship between target and predictor values. For this, a heatmap (Figure 4) was built with the corresponding values of the correlation between all the considered quantities.

<p align="center">
<img src="https://user-images.githubusercontent.com/33491221/181291470-bb178f1f-081e-4c66-b493-7614a6ba2614.png">

Figure 4 - heatmap of absolute correlation coefficients for all considered values
</p>
 
## Step 4. Building a Bayesian network for a chosen set of variables. Structure is based on multivariate analysis.

At the fourth step, a Bayesian network was built based on a multivariate analysis of the selected features. The data for analysis was taken from the previous step, namely from the heatmap with correlation values. Figure 5 shows a graph that reflects the structure of the constructed Bayesian network.

<p align="center">
<img src="https://user-images.githubusercontent.com/33491221/181291588-2d352e6e-bfce-42d2-842a-fcd355d65cfb.png">

Figure 5 - Graph of Bayesian network with a structure based on multivariate analysis
</p>

## Step 5. Building a Bayesian network for the same set of variables using 2 algorithms for structural learning
The fifth step was to build a Bayesian network using algorithms for structural learning. The first network was built using K2 and the Hill Climb algorithm. Figure 6 shows a graph that reflects the structure of the constructed Bayesian  network.

<p align="center">
<img src="https://user-images.githubusercontent.com/33491221/181291725-b02c7ea5-bb64-48f1-a959-305f2777137f.png">

Figure 6 - Graph of BN made with using Hill Climb algorithm and K2
</p>

The second network was built using the evolutionary algorithm and MI. Figure 7 shows a graph that reflects the structure of the constructed Bayesian network.

<p align="center">
<img src="https://user-images.githubusercontent.com/33491221/181291783-56a1c0ad-77af-4452-83ba-d81e5a4a7846.png">

Figure 7 - Graph of BN made with using Evolutionary algorithm and MI
</p>

## Step 6. Analyzing quality of sampled target variables from the point of view of synthetic generation

At the sixth step, it was necessary to analyze the quality of the sampled target variables, for which the histograms of the initial and generated data were built. Figure 8-9 shows histograms of the original and synthetically generated target values.

<p align="center">
<img src="https://user-images.githubusercontent.com/33491221/181291926-e3dcba21-3238-4aac-b6e8-395cc736e7f2.png">

Figure 8 - Results of sampling target values using Bayesian network made with multivariate analysis
</p>


<p align="center">
<img src="https://user-images.githubusercontent.com/33491221/181291946-d71d908b-5710-4d66-902a-7f617dbe4376.png">

Figure 9 - Results of sampling target values using Bayesian network made with structure-learning methods
</p>

## Conclusion
As a result of the work, various sampling methods were investigated and implemented for the ozone dataset. In the course of comparing the results of sampling by various methods, it was revealed that each of the methods made it possible to obtain high-quality synthetic data for the dataset under consideration.
