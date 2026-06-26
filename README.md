# MammoTrainer: Train your tumor detection and classification skills

Created by Reyna Geluk, Aryan Müller, Stan Bakker, Mieke Fraters \& Rutger Bleeker as part of the course Systeemproject for the Bsc Informatiekunde UvA (2nd year)



### Dataset

The dataset used for this project is called *CDD-CESM | Categorized Digital Database for Low energy and Subtracted Contrast Enhanced Spectral Mammography* images and can be found [here.](https://www.cancerimagingarchive.net/collection/cdd-cesm/) It contains 2006 mammograms from 326 subjects and extra information about the patients and pathologies. You need to have the images in this dataset installed for MammoTrainer to work.



### Summary

Our goal was to create an application which medical students could use to practice identifying and classifying cases of breast cancer. In the **BACKENDFILENAMES** files, the back-end model was trained to predict the tumor region(s). 



By running the cells in the **FRONTfilename** file and by making sure you have the correct file path set for the notebook to read the images, Mammotrainer will launch. By pressing the link provided by the output cell, it opens in a separate window for MammoTrainer.



You will first be shown a short tutorial gif showing how to annotate circles on the scans. First, click on the **center** of the tumor you identified. Then, click on either the **top or bottom edge** of the tumor region. Finally, click on either the **left or right edge** to fully complete the circle. This creates a mask, which will be compared to the model's prediction of the tumor region for the same image. The classification of the tumor is either 'benign', 'malignant' or 'normal', which can be selected by using their respective buttons. The user can then decide to check their answer. MammoTrainer will tell the user if their classification is correct or incorrect. The Dice Score is given as a metric, showing how well the user has annotated the tumor region. The user can manually compare their annotated region to the model's predicted region by pressing the 'Show tumor area' button. The user can also request hints via the hint button, which will display extra information relating to the current patient. 

