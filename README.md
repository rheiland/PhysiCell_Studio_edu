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
When the Studio GUI displays, it will load the "template" sample model's parameters by default. And it will select `template[.exe]` as the executable in the `Run` tab. (Note that the "Config" path in the `Run` tab will be different for Windows and Mac).

