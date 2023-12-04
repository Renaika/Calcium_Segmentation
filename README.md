# Calcium_Segmentation

This is a trial version of my calcium signalling segmentation and tracking baseline for astrocytes which I constructed for the purpose of my master thesis. 
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
If you don't have a Github account, you only have to download the "Master Thesis - Python GUI_V1.ipynb" file into a folder of your choice. 
Open the Anaconda terminal and go to the folder, where you saved the notebook file (Change "\Users\User\Downloads\" to your folder path)
```bash
cd \Users\User\Downloads\
```

Next, you should create a fresh conda environment:
```bash
conda create -n newenv CalciumEnv
```

and to activate it
```bash
conda activate CalciumEnv
```

Now you have to install some packages in order for the notebook to run. The fastest way is via pip: 
```bash
pip install napari[all] tk scipy numpy pandas opencv-python connected-components-3d tifffile scikit-learn matplotlib ipywidgets scikit-image notebook openpyxl trackpy
```

Then you can start jupyter, which will open the folder where the notebook is located. 
```bash
jupyter notebook
```

Now you only have to open the notebook and it for the GUI to open. 

In order to test the software, you can download a test Dataset here: 
https://drive.google.com/drive/folders/1bOjGZciea4K_-7pFapMeM3odeY7O3FaH?usp=sharing

I would recommend setting the parameters t_start=350 and t_end=450 and BKG_Neighbors=20, if you only want to test if the program runs. If you're sure, that it runs on your system and opens Napari with the results, then you can try to see how it works for bigger values, which will take a longer time to compute. 


### Parameter Choice

TODO: Add description of the parameters and recommended values for testing. 
