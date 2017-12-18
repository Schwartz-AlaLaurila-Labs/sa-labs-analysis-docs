# 1.3 Parsing your data

Data Curator is a Matlab based GUI developed for parsing, pre-processing and visualizing the raw data. The acquisition system stores the raw data in the [HDF5 format](https://cafarm.gitbooks.io/symphony/content/File-Format.html). Data Curator facilitates parsing of the HDF5 attributes and saves it as a[`CellData`](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-core/blob/master/src/main/matlab/%2Bsa_labs/%2Banalysis/%2Bentity/CellData.m)mat file. The`CellData`file is required by the  Data Curator and Analysis user interface for further processing of the data.

a\) To open the curator user interface, run`openCurator`from the Matlab command line.

![](/assets/curator_new_view.png)

Before continuing, let us review the directory structure required for the analysis toolbox. Assuming `~` is your home directory, the HDF5 files have to be copied inside `~/data/rawDataFolder` and the directory storing the results of the data analysis will be inside `~/data/analysis` with the following subdirectories,

![](/assets/project_heirarchy.png)

b\) As a next step, copy the HDF5 file to be parsed inside `~/data/rawDataFolder` , then click on the `...` button in the curator interface and select the HDF5 file to be parsed.

![](/assets/select_h5.png)

c\) After clicking `Open`, the HDF5 data is parsed and the curator window is updated as below,

![](/assets/curator_with_data.png)

In this example, the Data Curator shows the list of epochs recorded in a mouse retinal ganglion cell, which was subjected to different types of visual stimulation. An example of one such light stimulus is `Light Step` , where a simple flash of light is presented to the neurons. The neuron was recorded extracellularly, and the resulting action potentials during the flash of light are visible in the plot window of the Data Curator. 

Let us explore the [data curator features](/parsing-your-data/data-curator-features.md) further.

