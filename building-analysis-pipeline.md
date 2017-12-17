# 1.4 Building an analysis pipeline

Building an analysis pipeline requires s[a-labs-analysis-core](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-core). It is an analysis framework which abstracts the data structure, storage hierarchy and provides a simplified API \(Application programming interface\) to build an analysis pipeline. The framework captures the information about analysis parameter and the source code while building the analysis.

Below are the steps involved in building an analysis pipeline,

#### Step 1- Creating an analysis project

The analysis project helps with organizing the `CellData`for a defined purpose. It stores the file names of the cell data and the results of the analysis. The`createAnalysisProject`function requires, a unique name for the project,  and a list of experiment date as mandatory input parameters. The experiment date can be of [Matlab regular expression](https://in.mathworks.com/help/matlab/ref/regexp.html) pattern. Based on experiments pattern, the `createAnalysisProject`checks whether`CellData`exists for this project \(i.e. the raw data has already been parsed previously\). If not, then it parses the raw data file and generates the cell-specific data from the raw data. Otherwise, it loads the already parsed cell data.

```Matlab
[project, offlineAnalysisManager] = createAnalysisProject(...
    'Example-Analysis_01',...            % Name of the project
    'experiments', {'101217Dc*Amp2'},... % Experiment date with amplifier channel 
    'override', true);                   % Would you like to override the project
```

The function saves a simple text file formatted as [JSON ](https://www.json.org/)with the following attributes.

```json
{
    "identifier": "Example-Analysis_01",
    "description": "Hope it will be defined later !",
    "experimentList": [
        "101217Dc*Amp2"
    ],
    "cellDataIdList": [
        "101217Dcc2_Amp2"
    ],
    "analysisDate": "20171215",
    "analysisResultIdList": [],
    "performedBy": "narayas2",
    "file": "C:\\Users\\narayas2\\data\\analysis\\Projects\\Example-Analysis_01\\project.json"
}
```

#### Step 2 - Defining an epoch filter

The epoch filter defines the hierarchy in which epochs are grouped together. As an example, we will focus on creating a filter definition to build a `Light Step`analysis pipeline. `Light Step`is a simple flash used to stimulate the neurons. The relevant stimulus parameters are `displayName`= the name of the stimulus protocol \(`Light Step`\), `intensity`= stimulus intensity and `simTime` = the duration of the stimulus display.

The epoch filter definition is programmed as Matlab structure with the following attributes,

* `type` -  An unique name for the filter definition

```Matlab
analysisFilter.type = 'LightStepAnalysis'
```

* `buildTreeBy`- defines the hierarchy in which the epochs have to be grouped based on epoch parameter names. 
  Let us assume the epoch has the parameters`displayName, intensity, and stimTime`. 

```
analysisFilter.buildTreeBy = {'displayName', 'intensity', 'stimTime'};
```

> Example:
>
> ```
>     '  displayName   '  First level grouping of filter. 
>     '                '  It matches all the epoch which has parameter name "displayName" 
>             |           and groups them according to its value.
>     
>     '   intensity    '  Second level grouping of filter. 
>                         It similarly matches the intensity parameter
>             |           and groups according to its value
>     '                '
>     '    stimTime    '  So on ...
> ```

It is also possible to group the epoch with different parameters at same level,

```
analysisFilter.buildTreeBy = {'displayName', 'intensity; probeAxis; textureAngle', 'devices'};
```

> ```
>     '            displayName             '
>     '     +----------++----------+       '
>     '     |          |           |       '
>     ' intensity  probeAxis textureAngle  ' 
>     '     |          |                   '
>     '     |          |           |       '
>     '  devices    devices     devices    '
> ```

* `splitValue`-  It further filters the epoch based on the epoch parameter values. Let us assume the epochs with `displayName`have values `LightStep, MovingBar, DriftingGrating`. The below code filters the epoch which has `displayName`equals \`Light Step. 
  \`

The code below follows our example of the LightStepAnalysis and filters the epochs which have `displayName`equals `Light Step`– the ones were a simple flash of light was presented to the cells.

```Matlab
analysisPreset.displayName.splitValue = {'Light Step'};
```

It is also possible to attach a function handle to `buildTree`and `splitValues`.

* `featureExtractor`- Attaches a function handle to the filtered epoch group for further evaluation \(the feature extractor will be explained in step4\). 

In summary, the complete filter definition for the example `LightStep`analysis is as follows,

```Matlab
analysisFilter = struct()
analysisFilter.type = 'LightStepAnalysis'
analysisFilter.buildTreeBy = {'displayName', 'intensity', 'stimTime'};
analysisPreset.displayName.splitValue = {'Light Step'};
```

#### Step 3 - Building the analysis

```Matlab
buildAnalysis('Example-Analysis',... % Name of the analysis project
                analysisFilter)      % Type of analysis filter(s)
```

The function `buildAnalysis`generates the analysis tree as defined by the epoch filter, and updates the project file with the analysis results. The project file then stores the analysis date and analysis result file name as additional attributes,

```json
{
   "identifier": "Example-Analysis",
    ... 
    ....

    "analysisDate": "20171215",
    "analysisResultIdList": [
        "LightStepAnalysis-101217Dcc2_Amp2"
    ],   ... 
   ...
    "file": "C:\\Users\\narayas2\\data\\analysis\\Projects\\Example-Analysis_01\\project.json"
}
```

> Example Ligt Step Analysis tree for cell data 101217Dcc2\_Amp2
>
> ```
>     '         project==Example-Analysis_01 (1)           '
>     '                                                    '
>     '                         |                          '
>     '  analysis==LightStepAnalysis-101217Dcc2_Amp2 (2)   '
>     '                                                    '
>     '                         |                          '
>     '            displayName==Light Step (3)             '
>     '                                                    '
>     '                         |                          '
>     '                 intensity==1 (4)                   '
>     '            +------------+------------+             '
>     '            |                         |             '
>     '    stimTime==20 (5)          stimTime==500 (6)     '
> ```

It is also possible to build the analysis for multiple filters. This is achieved by passing an array of analysis filter to the function `bulidAnalysis`.

### Step 4 - Attaching feature extractor & Rebuilding the analysis

The `featureExtractor` has the [function handle](https://in.mathworks.com/help/matlab/matlab_prog/creating-a-function-handle.html) to process group of epochs. To perform the feature extraction, assign the feature extractor function handle to the desired level in the analysis tree and rebuild the analysis. The example below assigns `psthExtractor `to the lowest node \(`stimTime`\)  in the example analysis tree built for the `LightStep `Analysis. This example feature extractor generates a peri-stimulus time histogram of the neuron’s responses in the selected epoch group.

```
analysisFilter.stimTime.featureExtractor = {@(analysis, epochGroup, analysisParameter)...
    sa_labs.analysis.common.extractors.psthExtractor(...
    analysis,...
    epochGroup,...
    analysisParameter)...
    };
```

Then rebuild the analysis,

```
buildAnalysis('Example-Analysis',... % Name of the analysis project
                analysisFilter)      % Type of analysis filter(s)
```

When building the analysis, the `psthExtractor`is executed and a Peri-Stimulus Time Histogram \(PSTH\) is saved for each epoch group that has a unique `stimTime`value as a parameter. In addition, the result is also be percolated up to the higher levels of the analysis tree for further processing and visualization.

**Advantages of having `featureExtractorhandle `in filter definition**: As the filter definition, source code and data are loosely coupled, It is possible to execute the analysis on any computer node which has access to data and get the analysis results synchronized. Hence, the data-intensive analysis can be performed in distributed \(or\) remote computer node. 

Please be aware of the arguments required in the feature extractor function. It is mandatory to include the input parameters: `analysis, epochGroup, analysisParameter`. Guidelines for [creating a feature extractor](/building-analysis-pipeline/creating-feature-extractor.md) are explained in the next section.



