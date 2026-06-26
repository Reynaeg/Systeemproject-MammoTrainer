# MammoTrainer: Train your tumor detection and classification skills
*Created by Reyna Geluk, Aryan Müller, Stan Bakker, Mieke Fraters \& Rutger Bleeker as part of the course Systeemproject for the Bsc Informatiekunde UvA (2nd year)*



### Dataset

The dataset used for this project is called *CDD-CESM | Categorized Digital Database for Low energy and Subtracted Contrast Enhanced Spectral Mammography* images and can be found [here.](https://www.cancerimagingarchive.net/collection/cdd-cesm/) It contains 2006 mammograms from 326 subjects and extra information about the patients and pathologies. You need to have the images in this dataset installed for MammoTrainer to work. All other files are contained in this repository.

### Summary

Our goal was to create an application which medical students could use to practice identifying and classifying cases of breast cancer in mammograms. Oncologists and radiologists may also find this program useful. 

In the back-end related files, the U-Net model was trained to predict the location and size of the tumor region(s). This process, and the initial data-cleaning, can be seen in ```LowEnergyFinal.ipynb``` and ```SubtractedFinal.ipynb```. For our final product, we've only used subtracted images as they are usually easier for the human eye to analyze and the model struggling with all the noise in low energy scans. Running the file will cause the ground-truth masks to be recalculated and a model to be trained, so it's recommended to not run them unless necessary as it is very slow.

By running all cells in ```MammoTrainer.ipynb``` and by making sure all the ncessary packages are installed + the correct file path is set for the notebook to read the images, Mammotrainer will launch. By pressing the link provided by the output cell, MammoTrainer opens in a separate window.

The user will first be shown a short tutorial gif showing how to annotate circles on the scans. If a tumor is identified, annotating goes as follows:
* First, click on the **center** of the tumor identified.
* Then, click on either the **top or bottom edge** of the tumor region.
* Finally, click on either the **left or right edge** to fully complete the circle.
This process creates a mask, which will be compared to the model's prediction of the tumor region for the same image.

The classification of the tumor is either 'benign', 'malignant' or 'normal', which can be selected by using their respective buttons. The user can then decide to check their answer using the 'Show answer' button. MammoTrainer will tell the user if their classification is correct or incorrect. The Dice Score corresponding to the annottated ellipses is given as a metric, showing how well the user has annotated the tumor region. The user can manually compare their annotated region to the model's predicted region by pressing the 'Show tumor area' button. The user can also request hints via the hint button, which will display extra information relating to the current patient. 

A progress bar is shown on top of the screen. The user can go to the previous/next image by using the 'Back' and 'Next' buttons respectively. A new session can be started by pressing the 'New session' button, which will cause the program to reset all progress and pick 5 new images to display.

### Discussion: What could have been improved?
Overal, the back-end U-Net model could use some improvement. The model evaluation metrics score pretty well, and for this prototype it's definitely adequate, but it could definitely be improved upon. Although we've tried different tactics, such as image morpoholy and self-attention, our PCs could not handle the constant load of training models, and the models we did train with these methods, did not necessarily improve much compared to the models trained without these methods.

We also chose Gradio as our package to create our application with. Gradio's documentation is sadly a little iffy, and we've experienced lots of bugs and unintuitive methods of creating certain functions. Gradio does not allow for simple annotations on an image, such as clicking and moving your mouse around to create a circle (similar to Microsoft Paint's circle tool), instead opting for methods like pressing 3 times to select coördinates to create a circle. Although it works fine enough for this prototype, for future projects we probably would not use Gradio but find an alternative way of creating our application.

