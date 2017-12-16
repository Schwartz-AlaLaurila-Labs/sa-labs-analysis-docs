# 1.3 Parsing your data

Data curator is the Matlab based GUI for parsing, pre-processing and visualizing the raw h5 data. It has following functionality,

* Pre-process cell or epoch data
* Visualize cell summary using diary plot \(or\) epoch
* Filter and delete epochs.
* Add / Remove parameter to epoch or cell data
* Registering your own plots and pre-processors

The detailed usage of data curator functionality is listed in [1.3.1](/parsing-your-data/data-curator-features.md)

a\) To open the curator user interface, run`openCurator`from Matlab command line.

![](/assets/curator_view.png)

> Before going further, Let's visit the analysis data directory structure.  Assuming `~` is your home directory, H5 files has to copied inside `~/data/rawDataFolder` and analysis directory will be inside `~/data/analysis` with following sub directories,
>
> ![](/assets/project_heirarchy.png)

b\) As a next step, copy the h5 file to be parsed inside `~/data/rawDataFolder` , then click on the `...`button from the curator interface & select the h5 file to be parsed.

![](/assets/select_h5.png)

c\) On click of open, the h5 data is parsed and the curator window is updated as below,

![](/assets/curator_with_data.png)

> Let's further explore the [data curator features](/parsing-your-data/data-curator-features.md)



