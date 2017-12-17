## 1.3.1 Data Curator Features

#### a\) Visualize epoch parameters using`diaryPlot`

`diaryPlot`visualizes the epoch parameters `(Y axis)` for each epoch time \(or\) epoch number \(`X axis`\). It provides an overview of which parameters and stimuli were applied in the different epochs during the course of the experiment.

![](/assets/diary_plot.png)

#### b\) Pre-processor functions: detecting and visualizing action potentials

The pre-processor functions include a variety of pre-analysis that prepares the data to be comprehensively analyzed in the [analysis pipeline](/building-analysis-pipeline.md). Amongst them, the detection of action potentials here called spike detection is of central importance and will be used in the following as an example of the pre-processor functions. The functionality is available in the list of pre-processors. On click of `simpleSpikeDetector,` the parameters of the pre-processor function are displayed in the panel below. When selecting a `Threshold,` it detects the action potential on the press of `Execute`button.

![](/assets/spike_detection.png)

Similar pre-processor functions can be custom written and added to the pre-processor list. Let us carefully go through the parameter panel and the documentation of the `simpleSpikeDetector`function to understand how pre-processor functions should be documented and structured to function within the Data Curator Framework. The parameters documented in function `simpleSpikeDetector`are parsed by the Data Curator user interface and updated in the parameter panel.

```
function simpleSpikeDetector(epochs, parameter)

% description : Simple spike detection from SchwartzNU Analysis folder; 
% Refer https://github.com/SchwartzNU/SymphonyAnalysis/blob/master/GUIs/SpikeDetectorGUI.m
% mode:
%   default : Advanced
%   description: Type of spike detection, Example- 'Simple threshold' (or) 'Advanced'
% threshold:
%   default: -10
%   description: Threshold value to detect spikes
% overwrite:
%   default: false
%   description: Can override previously detected feature
% devices:
....
....
....
 % code to compute spike detection 
end
```

> Isn't it neat! So kindly write the documentation for your custom written pre-processor functions in the above [format](http://yaml.org/) and easily change those parameters from the user interface.

#### c\) Delete unwanted epochs

To delete an epoch that should not be included in the data analysis, select the epoch from epoch tree and click on `Tag To Delete (or) Ctrl +D` . To undo the tagging, use `Undo Delete Tag (or) Ctr + Z`. Once you are sure about the tagged epochs, Click on Delete Tagged. The epochs will now be excluded from the cell data, which is used for further analysis, but still remain in the raw data HDF5 file.

#### d\) Add Epoch/Cell Tags

To add a specific tag to an epoch or cell, click on Epoch / Cell from the data tree, then click on `Add Parameter` and specify the tag you want to add. To remove a parameter, click on the desired parameter from the grid and press `Remove Parameter`.

![](/assets/add_keyword.png)

#### e\) Filtering of epochs

Epochs can be filtered based on the parameters as search criteria. It is possible to list the filtered epochs in the data tree by enabling `Show Filtered Epochs`check box. In the example below, epochs are filtered by the `Property NDF`\(Neutral Density Filter wheel position\) with `value : 3.`The result is displayed in a scrollable text panel.

![](/assets/filtering.png)

In the next section, we will see how to [build an analysis pipeline](/building-analysis-pipeline.md).

