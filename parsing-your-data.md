# 1.3 Parsing your data

Data Curator is a Matlab based GUI developed for parsing, pre-processing and visualizing the raw data. The acquisition system stores the raw data in the [HDF5 format](https://cafarm.gitbooks.io/symphony/content/File-Format.html). Data Curator facilitates parsing of the HDF5 attributes and saves it as a[**`CellData`**](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-core/blob/master/src/main/matlab/%2Bsa_labs/%2Banalysis/%2Bentity/CellData.m)mat file. The**`CellData`**file is required by the user interface for the functionality described in [Data Curator features Section](/parsing-your-data/data-curator-features.md)

a\) To open the curator user interface, run**`openCurator`**from the Matlab command line.

![](/assets/data_curator)

Before going further, Let us review the directory structure required for the analysis toolbox.  Assuming **`~`** is your home directory, the HDF5 files have to be copied inside **`~/data/rawDataFolder`** and the analysis directory storing the results of the data analysis will be inside **`~/data/analysis`** with following subdirectories,

![](/assets/project_heirarchy.png)

b\) As a next step, copy the h5 file to be parsed inside **`~/data/rawDataFolder`** , then click on the **`...`** button from the curator interface & select the h5 file to be parsed.

![](/assets/select_h5.png)

c\) After clicking **`Open`**, the HDF5 data is parsed and the curator window is updated as below,

![](/assets/curator_with_data.png)

Let us explore the [data curator features](/parsing-your-data/data-curator-features.md) further.

