# Computer-Science-Scalable-Duplicate-Detection-
This GitHub link belongs to the assignment to extend the literature on MSMP+ to address the scalability issue for duplicate detection for products on different Web Shops. The repository also includes notebooks for reproducing the baseline MSMP+ method and for comparing the performance of both approaches.

**Repository Structure**

1. Extended MSMP+ for product detection.ipynb

Implements the extended MSMP+ framework, including:
  - enhanced data cleaning (unit normalization, VESA regex, padded q-grams),
  - extraction of model words from titles, value attributes, and brand names,
  - construction of binary vectors and MinHash signatures,
  - LSH-based candidate pair selection,
  - MSM similarity computation with complete-linkage clustering,
  - evaluation of PQ, PC, F1, and F1*.

2. Replication Baseline MSMP+.ipynb

Provides a replication of the original MSMP+ method as described in the literature and serves as the baseline. 

4. Plotting baseline and extension to compare performance.ipynb
   
Generates the evaluation figures and metrics used in the accompanying analysis, including plots of PQ, PC, F1, and F1* as functions of the fraction of comparisons, as well as the area-under-curve values.

For running the tuning of the clustering threshold the following adjustments should be made to both extensions and baseline notebooks: 
1. Include a _threshold_grid = (0.40, 0.60, 16)_ such that it creates step size 0.02
2. Change the input of the bootstapevaluation _threshold_ into this _threshold_grid_
3. Right after going into the for loop inside this evaluation with different (r,b) combinations, also create a for loop over the _threshold_grid_

**Usage**
- To run the extended method, open: Extended MSMP+ for product detection.ipynb. Start by loading the corresponding JSON file and the list of brand names from Wikipedia. Secondly, define the _n_bootstraps_ and where you want to store the data. If you want to change the tuned threshold for clustering, change the _threshold_. Then you can run the file which will first print some summary output about the number of model words and the creation of the binary vector, and afterwards will start the bootstrap evaluation for different (r,b,t) combinations. 
- To reproduce the baseline results, open: Replication Baseline MSMP+.ipynb. Again start by loading the corresponding JSON file and define the number of bootstraps. Also the tuned threshold can be adapted. Also specify where you want to store these results, as you will later need them to compute the plots and AUC. 
- To generate plots and compare both methods, first run the 2 files above and store the results and afterwards open: Plotting baseline and extension to compare performance.ipynb. This will create 4 figures with the evaluation measures and also compute the AUC improvements for the extension compared to the baseline. 

**Requirements**
The notebooks require Python 3.9 or higher, Jupyter Notebook, and standard scientific libraries such as NumPy, Pandas, Matplotlib, and Regex.

**Summary of Results**
The extended MSMP+ demonstrates improved performance relative to the baseline across all evaluation metrics. 
Notable improvements include:
  
- an increase in maximum Pair Quality from 0.15 to 0.32,
- an increase in Pair Completeness from 89% to 96% at 20–25% of all pairwise comparisons,
- improvements of 9.77% and 10.54% in the area under the F1 and F1* curves, respectively.
