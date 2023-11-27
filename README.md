# Calcium_Segmentation

trial version of my calcium signalling segmentation baseline for astrocytes.
You can load tif files of astrocyte data in 3D (x,y,t).
Then you can apply my baseline on it using default or costumized parameters for the different methods. 
It will take some time to compute (can be some minutes considering how many time frames you include)
The program will automatically open napari with all in between results until the final labelled data. 
You can look at all of them in the grid style or separatly. 
If you want to further investivate them, you can use napari or you can also export the results as tif files in napari and open them in Fiji or other software that you use. 

### Setup
Install [anaconda](https://docs.anaconda.com/anaconda/install/index.html),
or [miniconda](https://docs.conda.io/en/latest/miniconda.html) if you prefer a more lightweight setup.

Install [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
(On windows, this is included in anaconda and will be available in the anaconda prompt). 
There are many tutorials online, e.g. [this one](https://www.notion.so/zarkom/Introduction-to-Git-ac396a0697704709a12b6a0e545db049).

Clone this repo and navigate into it:
```bash
git clone https://github.com/hci-unihd/mlph_sheet01.git
cd mlph_sheet01
```

Next, to set up your conda environment, run
```bash
conda env create --file=environment.yml
```
and to activate it
```bash
conda activate mlph
```
Then you can start jupyter (run `jupyter notebook`).


CHECK DETAILS!
