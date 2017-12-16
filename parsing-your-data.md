# 1.3 Parsing your data

Data curator is the MATLAB based GUI for parsing, pre-processing and visualizing the raw h5 data. It has following functionality,

* Pre-process cell or epoch data
* Visualize cell summary using diary plot \(or\) epoch
* Filter and delete epochs.
* Add / Remove parameter to epoch or cell data
* Registering your own plots and pre-processors

The detailed usage of functionality is listed in [data curator features](/parsing-your-data/data-curator-features.md)

a\) Run`openCurator`from MATLAB command line. It will open the Data Curator window as below.

![](/assets/curator_view.png)

> Before going further, Let's visit the analysis data directory structure.  Assuming `~` is your home directory, H5 files has to copied inside `~/data/rawDataFolder` and analysis related folders will be inside `~/data/analysis` with following structure,
>
> ![](/assets/project_heirarchy.png)

b\) Copy the h5 file to be parsed inside `~/data/rawDataFolder` . Click on the `...`button from the curator interface & select the h5 file to be parsed.

![](/assets/select_h5.png)

c\) On open, the data will be parsed and the curator window will be updated as below,

![](/assets/curator_with_data.png)

> Let's further explore the [data curator features](/parsing-your-data/data-curator-features.md)



