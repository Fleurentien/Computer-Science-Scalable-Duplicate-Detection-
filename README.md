# Computer-Science-Scalable-Duplicate-Detection-
This GitHub link belongs to the assignment to extend the literature on MSMP+ to address the scalability issue for duplicate detection for products on different Web Shops. 


For running the tuning of the clustering threshold the following adjustments should be made to both code files: 
1. Include a _threshold_grid = (0.40, 0.60, 16)_ such that it creates step size 0.02
2. Change the input of the bootstapevaluation _threshold_ into this _threshold_grid_
3. After going into the for loop inside this evaluation with different (r,b) combinations, also create a for loop over the _threshold_grid_




