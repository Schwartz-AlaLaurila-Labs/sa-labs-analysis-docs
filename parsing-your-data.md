# 1.3 Parsing your data

Data Curator is a Matlab based GUI developed for parsing, pre-processing and visualizing the raw data. The raw data from acquired from the acquisition system is stored in the [HDF5 format](https://cafarm.gitbooks.io/symphony/content/File-Format.html). Data Curator facilitates parsing of the HDF5 properties and saves it as a [CellData](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-core/blob/master/src/main/matlab/%2Bsa_labs/%2Banalysis/%2Bentity/CellData.m) mat file. The CellData object is then used by the GUI for the funcitionality described in [Data Curator features Section](/parsing-your-data/data-curator-features.md)

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



