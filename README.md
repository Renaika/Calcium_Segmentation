# Calcium Segmentation and Tracking Pipeline

This is a trial version of a calcium signalling segmentation and tracking pipeline for astrocytes which we constructed for the purpose of my master thesis. 
With this tool, you can easily load tif files of astrocyte data in 3D (x,y,t) and apply my pipeline using default or customized parameters.
Please note that the computation time may take some time, depending on the choice of parameters. 
Once the process is complete, the program will automatically open napari with all intermediate results, 
which you can view these results in a grid style or separately in Napari. 
It will also save an excel file "region_properties.xlsx" including properties of the labeled objects and 
the final result including all trajectories as "trajectory_plot.png" on a maximum intensity projection of the labeled data.  
If you wish to investigate further, you can use naparis functions or export the results as tif files (saving function in napari) and open them in Fiji or other software of your choice.

### How to Setup
Install [anaconda](https://docs.anaconda.com/anaconda/install/index.html),
or [miniconda](https://docs.conda.io/en/latest/miniconda.html) if you prefer a more lightweight setup.

Install [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
(On windows, this is included in anaconda and will be available in the anaconda prompt). 
There are many tutorials online, e.g. [this one](https://www.notion.so/zarkom/Introduction-to-Git-ac396a0697704709a12b6a0e545db049).

Clone this repo and navigate into it (if you have a Github account):
```bash
git clone https://github.com/Renaika/Calcium_Segmentation.git
cd Calcium_Segmentation
```
If you don't have a Github account, you only have to download the "Master Thesis - Python GUI_V1-Refactored.ipynb" file into a folder of your choice. 
Open the Anaconda terminal and go to the folder, where you saved the notebook file (Change "\Users\User\Downloads\" to your folder path)
```bash
cd \Users\User\Downloads\
```

Next, you should create a fresh conda environment:
```bash
conda create -n CalciumEnv
```

and to activate it
```bash
conda activate CalciumEnv
```

Now you have to install some packages in order for the notebook to run. The fastest way is via pip: 
```bash
pip install napari[all] tk scipy numpy pandas opencv-python connected-components-3d tifffile scikit-learn matplotlib ipywidgets scikit-image notebook openpyxl trackpy ipykernel
```

You should add the Kernel to the jupyter notebook by: 
```bash
ipython kernel install --user --name=CalciumEnv
```

Then you can start jupyter, which will open the folder where the notebook is located. 
```bash
jupyter notebook
```

Now you only have to open the notebook. Choose `Kernel=CalciumEnv` and run it for the GUI to open. 

### Test Dataset

In order to test the software, you can download a test dataset here: 

https://drive.google.com/drive/folders/1bOjGZciea4K_-7pFapMeM3odeY7O3FaH?usp=sharing

### Parameter Choice

This software includes various parameters. Here is a detailed explanation of each parameter, its default value, and recommended usage:
I would recommend setting the parameters `time_start = 350` and `time_end = 450` and `BKG_Neighbors = 20`,  if you're simply testing the program's functionality on your system and opening Napari to view the results. Once you've confirmed that it's working, you can experiment with larger values, keeping in mind that the computation time will increase accordingly.

- **`time_start` and `time_end`**: 
  - *Description*: Define the start and end frames for processing.
  - *Default*: `time_start = 0`, `time_end = -1` (processes until the last frame).

- **`y_start` and `y_end`**: 
  - *Description*: Specify the start and end coordinates along the Y-axis for cropping.
  - *Default*: `y_start = 0`, `y_end = -1` (extends to the end of the y axis).

- **`x_start` and `x_end`**: 
  - *Description*: Similar to `y_start` and `y_end`, but for the X-axis.
  - *Default*: `x_start = 0`, `x_end = -1`.

- **`threshold`**: 
  - *Description*: Threshold value for image segmentation.
  - *Default*: `7000`. 
  - *Note*: Adjust based on image contrast and brightness.

- **`median_filter_size`**: 
  - *Description*: Size of the median filter used for noise reduction for `(t, y, x)`.
  - *Default*: `(5, 3, 3)`. 
  - *Note*: Adjust based on the level of noise.

- **`BKG_Neighbors`**: 
  - *Description*: Number of neighboring frames used in background subtraction.
  - *Default*: `660`. 
  - *Note*: Increase or decrease based on the dataset. Recommened to choose the same value as `time_end`.

- **`Connectivity`**: 
  - *Description*: Used in connected component analysis.
  - *Default*: `26`. 
  - *Note*: Represents the connectivity criterion (6, 18, or 26 for 3D images).

- **`Structure Element`**: 
  - *Description*: Shape and size of the structuring element used for morphological operations.
  - *Default*: `(5, 2, 2)`.
  - *Note*: Adjust based on the size of the 3D rectangle `(t, y, x)`.

- **`Area Size`**: 
  - *Description*: Minimum size of areas to be considered in analysis.
  - *Default*: `100 pixels`. 
  - *Note*: Useful for filtering out noise or small artifacts.

- **`trackpy_memory`**: 
  - *Description*: Memory parameter for trackpy particle tracking.
  - *Default*: `2`. 
  - *Note*: Represents the number of frames to remember a particle that has temporarily disappeared.

- **`trackpy_search_range`**: 
  - *Description*: Search range for linking features across frames in trackpy.
  - *Default*: `3`. 
  - *Note*: Determines the maximum distance a particle can move between frames.

- **`trackpy_threshold`**: 
  - *Description*: Threshold for filtering short-lived particles in trackpy.
  - *Default*: `3`. 
  - *Note*: Particles tracked for fewer frames than this threshold are discarded.

Master Thesis: **Segmentation and Tracking of Calcium Signals in Astrocytes** by Mandy Kunfeld
