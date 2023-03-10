# PhysiCell Studio tutorial

# Installation

Either:
* Download the Model Builder/Studio from https://github.com/PhysiCell-Tools/PhysiCell-model-builder/releases This option assumes you have installed a Python distribution with the necessary 3rd party modules needed for the Builder/Studio. It will also not contain an executable model that can be run, e.g., the `template` model. If you have downloaded PhysiCell and built an executable model there, you can use that one to run in the Studio.

or:
* Download a bundled PhysiCell Studio which includes the "template" executable model. Until we find a more permanent site for these bundles, they are currently on Dropbox:

  * for Windows: https://www.dropbox.com/s/wiwdd09f8pmmyyk/PhysiCell_Studio_win.zip?dl=0  (about 334 MB)
  * for Mac: https://www.dropbox.com/s/9e52bcupp663xci/PhysiCell_Studio.zip?dl=0   (about 227 MB)

You will run the Studio from the command line, e.g., Powershell on Windows; Terminal on Mac.

## Windows bundle
Navigate (via `cd` command) to the folder where you unzipped the Studio and then `cd` to the folder containing `PhysiCell_Studio.exe` and run it, e.g.:
```
PS C:\Users\Owner\PhysiCell_Studio_win\PhysiCell_Studio> .\PhysiCell_Studio.exe
(patiently wait...)
Matplotlib is building the font cache; this may take a moment.
self.current_dir =  C:\Users\Owner\PhysiCell_Studio_win\PhysiCell_Studio
self.pmb_root_dir =  C:\Users\Owner\PhysiCell_Studio_win
self.config_dir =  C:\Users\Owner\PhysiCell_Studio_win\PhysiCell_Studio\config
```

## MacOS bundle
Uncompress the .zip file, e.g., navigate to its directory and run `unzip PhysiCell_Studio.zip`. This will reveal a `PhysiCell_Studio.app` directory. 
Open a Finder window, navigate to this .app, right-click on it and select "Open". You'll be warned that "macOS cannot verify the developer...", but click the "Open" button on that warning dialog window. 
Then back in a Terminal window, navigate to the directory containing the `PhysiCell_Studio.app` and from there into `Contents/MacOS` and run the executable, e.g. :
```
~/PhysiCell_Studio.app/Contents/MacOS$ ./PhysiCell_Studio
```

## Linux installation                                                            
In the instruction below, we assume, your local libraries are installed at `~/.local/lib/` and your local binaries are at `~/.local/bin/`. Please adjust the commands if necessary.

1. Use the first option (Model Builder/Studio from https://github.com/PhysiCell-Tools/PhysiCell-model-builder/releases) to download Studio into `~/.local/lib/`,
    and navigate with `cd` into this directory.
2. Type `tar -xzvf PhysiCell-model-builder-2.10.1.tar.gz` to decompress the tar.gz file.
3. Type `ln -s PhysiCell-model-builder-2.10.1/ PhysiCell-model-builder`  to symbolically link the current version to a generic name.
4. Use `cd` to navigate into your local binary folder `~/.local/bin/`.
5. Write a `PhysiCell_Studio` executable file by typing `echo "python3 $HOME/.local/lib/PhysiCell-model-builder/bin/pmb.py --studio" > PhysiCell_Studio`.
6. Type `chmod 775 PhysiCell_Studio` to make the file executable.

Now you should be able to start `PhysiCell_Studio` from everywhere at the command line, by just typing `PhysiCell_Studio`.

# Getting Started

NOTE: if you do not use the menu `File -> Save as`, the .xml file that was loaded will be over-written when you run a simulation.

## Template model: default params

When the Studio displays, it will load the "template" sample model's parameters by default. And it will select `template[.exe]` as the executable in the `Run` tab. (Note, that the "Config" path in the `Run` tab will be different for Windows and Mac). But the first tab displayed is the `Config Basics` which defines the model's spatial domain, the simulation's Max Time, and various other high-level parameters, including how often output files are saved for plotting (`Save data(intervals)`).


![](images/studio_template_config.PNG)
* the Configuration Basics tab that defines the domain and various high-level simulation parameters
---

![](images/studio_template_microenv.PNG)
* the Microenvironment tab where substrates and signals are defined. Just one substrate is defined in the default `template` model, but it is not used (yet).
---

![](images/studio_template_celltypes.PNG)
* the Cell Types tab where different cell types can be defined to have different phenotypic behaviors. For the default `template` model, there is only one cell type defined (initially). Note, there are subtabs which define each cell type's phenotype. If you look at some of those subtabs, you'll see that the default `template` model allows cell death and mechanics, but no motility and no secretion/uptake of the substrate.
---


![](images/studio_template_run.PNG)
* click the `Run simulation`. Information about the overall model will quickly appear, followed by delayed output lines whenever output files are saved (based on the time intervals on the `Config Basics` tab).
---

![](images/studio_template_plot_t0.PNG)
* At time=0, we see the initial conditions: 5 cells positioned randomly in the domain. Note, the "5" is specified in the `User Params` tab as the "number_of_cells".
---

![](images/studio_template_plot_5days.PNG)
* Results (cells) at the end of the simulation (5 days).
---

## Template model: changing initial conditions

![](images/studio_template_ICs_disk.PNG)
* the `ICs` (Initial Conditions) tab lets us define some relatively simple starting positions for cells. The output will be a .csv file containing: `x,y,z,cell type` Here, we create a disk of hexagonally packed cells. Press `Plot` to see results and `->cells.csv` to write the .csv file. You will then provide this .csv filename on the Config Basics tab.
---

![](images/studio_template_config_ICs_enable_csv.PNG)
* In the `Config Basics` tab, we need to :heavy_check_mark: enable the cells.csv and change the folder to be "."
---

![](images/studio_template_user_params_no_random_cells.PNG)
* the `User Params` tab defines parameters considered to be "global" to a simulation (vs. `Custom Data`, the subtab in `Cell Types` which define parameters specific to cell types). Here, we change # of randomly placed cells to be 0 (because we only want to use the cells defined in the .csv file).
---

![](images/studio_template_run_disk.PNG)
* when we run the simulation now, we see there are 1150 cells initially (all from the cells.csv).
---

![](images/studio_template_plot_disk_20hr.PNG)
* results after 20 hours. Note, the cells are unrealistically overlapping, a situation we can adjust with additional edits to the model.
---

## Template model: diffusion

![](images/template_diffusion_config.png)
* In this version of the model, we will turn on diffusion of the substrate. First, in the Config tab, let's reduce the Max Time to 120 mins, set the Save intervals to 5 mins, and disable (uncheck) the cells.csv. Also, in the `User Params` tab, let's set the "number_of_cells" to 10 (not shown here).
---

![](images/template_diffusion_microenv.png)
* In the `Microenvironment` tab, set the diffusion coef=1000, decay rate=0, and Dirichlet Boundary Conditions=38. In the `Run` tab, run the simulation.
---

![](images/template_diffusion_plot5min.png)
* In the `Plot` tab, :heavy_check_mark: Substrates to display them and :heavy_check_mark: "fix" to fix absolute values for the color map (cmin=0, cmax=38, and press Enter after changing those values). Then plot the results at 5 mins.
* ---

![](images/template_diffusion_plot2hrs.png)
* Plot the results at the end of the simulation (2 hrs). Note, the substrate has diffused throughout the domain from the boundaries.

![](images/template_diffusion_plot2hrs_cmap2.png)
* Note, if you uncheck "fix", the colormap will have a dynamic range, using whatever is min/max in the substrate data.

