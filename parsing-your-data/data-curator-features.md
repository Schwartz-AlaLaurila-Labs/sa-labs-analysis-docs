## 1.3.1 Data Curator Features

#### a\) Visualize epoch parameters using`diaryPlot`

`diaryPlot`visualizes the epoch parameters `(Y axis)` for each epoch time \(or\) epoch number \(`X axis`\). It provides an overview of which parameters and stimuli were applied in the different epochs during the course of the experiment.

![](/assets/diary_plot.png)

#### b\) Pre-processor functions: detecting and visualizing action potentials

Spike detection functionality is available in the list of pre-processor along with other registered pre-processor. On click of `simpleSpikeDetector`, its parameters are displayed in the panel below. Given a simple threshold, it will detect the spikes from the data on the press of execute button.

![](/assets/spike_detection_on_curator.png)

Now let's carefully go through the parameter panel and documentation of `simpleSpikeDetector`function. The parameters documented in  `function simpleSpikeDetector ...`is parsed by the data curator user interface and updated in the above parameter panel.

```
function simpleSpikeDetector(epochs, parameter)

% description : Simple spike detection from SchwartzNU Analysis folder; 
Refer https://github.com/SchwartzNU/SymphonyAnalysis/blob/master/GUIs/SpikeDetectorGUI.m
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
```

> Isn't it cool! so kindly write the documentation for the functions in above format[^1] and easily change those parameters from the user interface.

### c\) Delete bad epochs

To delete an epoch,  select an epoch from epoch tree. Click on _Tag To Delete _\(`ctrl+d`\) and to undo the tagging use _Undo Delete Tag_\(`ctr+z`\) . Once you are sure about the tagged epochs, Click on _Delete Tagged_.

### d\) Add Epoch/Cell Tags

To add a specific tag, click on Epoch / Cell from data tree, then click on add parameter to add the new tag. To remove a parameter click on the desired parameter from the grid and press remove parameter.

![](/assets/add_keyword.png)

### e\) Filtering of epochs

Epochs can be filtered based on the parameter as search criteria. It is possible to list the filtered epochs in data tree by enabling _Show Filtered Epochs_ check box. Below example, filters the epoch which has NDF property and Value 3 and the result is displayed in a scrollable text pane.  
![](/assets/filtering.png)

> In the next sections we will see how to [build an analysis pipeline](/building-analysis-pipeline.md).



