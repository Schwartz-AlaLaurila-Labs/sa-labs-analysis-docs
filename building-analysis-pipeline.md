# 1.4 Building an analysis pipeline

To build an analysis pipeline requires 4 steps,

### Step 1- Creating an analysis project

Analysis project helps with organizing the cells for a defined purpose. It has the file names of cell data and its analyzed result.

```Matlab
[project, offlineAnalysisManager] = createAnalysisProject(...
    'Example-Analysis_01',...            % Name of the project
    'experiments', {'101217Dc*Amp2'},... % Experiment date with amplifier channel 
    'override', true);                   % Would you like to override the project
```

Based on experiments pattern, the `createAnalysisProject` checks whether it has the already parsed raw data files. If not then it parses the raw data file and generates the cell-specific data from the raw data. Otherwise, it loads the already parsed cell data.

The function saves a simple text file formatted as JSON[^1] with following attributes.

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

### Step 2 - Defining an epoch filter

Epoch filter defines the hierarchy in which epochs will be grouped together. It is a Matlab structure with following attributes,

* type -  An unique name for the filter definition

```Matlab
analysisFilter.type = 'LightStepAnalysis'
```

* buildTreeBy - defines the hierarchy in which the epochs have to be grouped based on _epoch parameter names. _
  Let's assume the epoch has the parameters displayName, intensity, and stimTime. 

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

It is also possible to build the epoch grouping with different parameters under the same level.

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

* splitValue -  It further filters the epoch based on the _epoch parameter values_. Let's assume the epochs with displayName has values LightStep, MovingBar, DriftingGrating. The below code filters the epoch which has _displayName equals Light Step_.  

```Matlab
analysisPreset.displayName.splitValue = {'Light Step'};
```

It is also possible to attach a function handle to buildTree & splitValues.

* featureExtractor - Attaches a function handle to filtered epoch group for further evaluation, more on the feature extractor will be explained in step4. 

In summary, the complete filter definition to build a light step analysis is as follows,

```Matlab
analysisFilter = struct()
analysisFilter.type = 'LightStepAnalysis'
analysisFilter.buildTreeBy = {'displayName', 'intensity', 'stimTime'};
analysisPreset.displayName.splitValue = {'Light Step'};
```

### Step 3 - Building the analysis

```Matlab
buildAnalysis('Example-Analysis',... % Name of the analysis project
                analysisFilter)      % Type of analysis filter(s)
```

The function `buildAnalysis` generates the analysis tree as per the filter definition and updates the project file with analysis results. The  project file after analysis will have analysis date and analysis result file name as additional attributes,

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

It is also possible to build the analysis for multiple filters. In that case, passing an array of analysis filter to the function`bulidAnalysis` will do the job. 

### Step 4 - Attaching feature extractor & Rebuilding the analysis

The feature extractor extracts features from epoch \(or\) group of epochs. To perform the feature extraction, assign the feature extractor function handle to desired tree level and rebuild the analysis. Below example assigns `psthExtractor `to the stimTime node. 

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

During the build of analysis, the`psthExtractor `is executed and  Pre-Stimulus Time Histogram \(PSTH\) is saved for each epoch group have stimTime has the parameter. In addition, it will also be percolated up on the higher level of analysis tree for further processing and visualization.

> Please make a note of arguments in the feature extractor function. It is mandatory to have featureExtractor function signature with input parameters`analysis, epochGroup, analysisParameter.`Guidelines for creating a [feature extractor](/building-analysis-pipeline/creating-feature-extractor.md) is explained in next section.



