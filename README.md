# PhysiCell_Studio_edu
Learning PhysiCell Studio

Download a bundled PhysiCell Studio with the "template" executable model. Until we find a more permanent site for these bundles, they are currently on Dropbox:
* for Windows: https://www.dropbox.com/s/wiwdd09f8pmmyyk/PhysiCell_Studio_win.zip?dl=0  (about 334 MB)
* for Mac: https://www.dropbox.com/s/9e52bcupp663xci/PhysiCell_Studio.zip?dl=0   (about 227 MB)

You will run the Studio from the command line, e.g., Powershell on Windows; Terminal on Mac.

# On Windows
Navigate (via `cd` command) to the folder where you unzipped the Studio and then `cd` to the folder containing `PhysiCell_Studio.exe` and run it, e.g.:
```
PS C:\Users\Owner\PhysiCell_Studio_win\PhysiCell_Studio> .\PhysiCell_Studio.exe
(patiently wait...)
Matplotlib is building the font cache; this may take a moment.
self.current_dir =  C:\Users\Owner\PhysiCell_Studio_win\PhysiCell_Studio
self.pmb_root_dir =  C:\Users\Owner\PhysiCell_Studio_win
self.config_dir =  C:\Users\Owner\PhysiCell_Studio_win\PhysiCell_Studio\config
```

# On MacOS
Uncompress the .zip file, e.g., navigate to its directory and run `unzip PhysiCell_Studio.zip`. This will reveal a `PhysiCell_Studio.app` directory. 
Open a Finder window, navigate to this .app, right-click on it and select "Open". You'll be warned that "macOS cannot verify the developer...", but click the "Open" button on that warning dialog window. 
Then back in a Terminal window, navigate to the directory containing the `PhysiCell_Studio.app` and from there into `Contents/MacOS` and run the executable, e.g. :
```
~/PhysiCell_Studio.app/Contents/MacOS$ ./PhysiCell_Studio
```

# Getting Started

NOTE: if you do not use the menu `File -> Save as`, the .xml file that was loaded will be over-written when you run a simulation.

## Template model: default params

When the Studio displays, it will load the "template" sample model's parameters by default. And it will select `template[.exe]` as the executable in the `Run` tab. (Note that the "Config" path in the `Run` tab will be different for Windows and Mac). But the first tab displayed is the `Config Basics` which defines the model's spatial domain, the simulation's Max Time, and various other high-level parameters, including how often output files are saved for plotting (`Save data(intervals)`).


![](images/studio_template_config.PNG)

![](images/studio_template_run.PNG)

---

![](images/studio_template_run.PNG)
* click the `Run simulation`. Information about the overall model will quickly appear, followed by delayed output lines whenever output files are saved (based on the time intervals on the `Config Basics` tab).
---

![](images/studio_template_plot_t0.PNG)
* At time=0, we see the initial conditions: 5 cells positioned randomly in the domain. Note the "5" is specified in the `User Params` tab as the "number_of_cells".
---

![](images/studio_template_plot_5days.PNG)
* Results (cells) at the end of the simulation (5 days).
---

## Template model: changing initial conditions

![](images/studio_template_ICs_disk.PNG)
* In the `ICs` (Initial Conditions) tab, create a disk of hexagonally packed cells by specifying the parameters shown here. Then press `Plot` and `->cells.csv`.
---

![](images/studio_template_config_ICs_enable_csv.PNG)
* We need to enable the cells.csv and change the folder to be "."
---

![](images/studio_template_user_params_no_random_cells.PNG)
* in the `User Params` tab, change # of randomly placed cells to be 0 (we just want to use the cells in the ICs .csv).
---

![](images/studio_template_run_disk.PNG)
* when we run the simulation now, we see there are 1150 cells initially.
---

![](images/studio_template_plot_disk_20hr.PNG)
* results after 20 hours.
---


