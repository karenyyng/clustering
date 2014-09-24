# 
Author: [Karen Ng](mailto:karenyng@ucdavis.edu)   
Institution: UC Davis

## project-specific goals
We want to find a statistical method to best   

* represent the underlying structure(s) of our data (i.e. merging
structures of galaxy clusters) 
* want to weight the variables (or apply prior) to reflect the underlying
physical properties such as luminosity of galaxies / uncertainties 
* validate our method or show it is consistent with estimates with other
well-known statistical methods

## Motivation 
Accurate representation of spatial distribution of galaxies in a merging
cluster is important in a sense that any noteworthy offset of galaxies / gas from
the dark matter component could be a sign of self-interacting dark matter.
Since astrophysicists know so little about dark matter, any further
concrete constraint on the dark matter self-interaction cross section will
help theoretical physicists rule out unlikely dark matter
candidates.
(think: Bullet Cluster)  

## Description of my data  
* we will have around 20 sets of (raw) data catalogs, each for one galaxy clusters 
* the galaxy clusters show signs of merging, so there exist several subclusters
within each data set 
* number of observations (galaxies)  of each data set is of the
order of  60 - 2000 
* number of useful variables are limited, i.e. ~ 10 
* origin of our data can be heterogenous, thus there can be missing
variables from observations, only 10% have spectroscopic redshifts  
* no training set is available, even if we can divide up our data set into
a training (observations with less missing variables) and a test set, the
training set may be too small to be useful- we may have to come up with
simulations to validate our method 

# Action plan
## Questions that need to be addressed 
* whether we have enough data for clustering and testing hypotheses 
* determine the number of subcluster(s) or put unwanted (foreground /
background) data in their own subclusters  
* assign membership of data points with some confidence / credible estimates  
* weight our data points to represent the underlying
physical properties / uncertainties 
* find best way(s) to represent the spatial distributions of each set of
data - maybe a KDE or some summary point statistics  


## variables to be included in the feature matrix for clustering 
* spatial coordinates (x and y) in the plane of the sky after correcting for
anarmorphic distortions (projection effects) 
* redshifts (only available for 10% of the data) or  the corresponding velocity dispersions 
* color (g-i band) etc.  
for details, see notes/data_preprocessing.md 

### proposed  methods for visualizing the structure of the data  


### kernel density estimation (KDE)
* bootstrap the galaxies
* minimize the mean integrated squared error (MISE) to find the band width
* find the peak(s) of the estimated density
* identify peaks 

### proposed method(s) for assigning membership of subclusters  
* bootstrap the samples, assign membership based on number density contours
* find the smallest band width that would allow the "signal-to-noise" 
within each subcluster to be higher than 3 or so 

* normal mixture model 

### Preliminary analyses 
* unweighted 2D KDE using statsmodel and visualization using seaborn
* Gaussian Mixture Model 

### future plan 
* I am fixing XDGMM so that it could "predict" which the most likely
Gaussian mixture that a data point should belong to  

#### proposed method 1  
* bootstrap the galaxies
* histogram each set of the bootstrapped data 
* smooth the map of data points with Gaussian filter 
* identify peaks 
