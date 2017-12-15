## 1.3.1 Data Curator Features

### a\) Visualize epoch parameter using diary plot

Diary plot allows us to visualize the** epoch Time** \(or\) **epoch Number **\(X-AXIS\)** **Versus **list of epoch parameters **\(Y-AXIS\).  
It provides an overview of the parameters of epoch changed over the experiment.

![](/assets/diary_plot.png)

### b\) Detect spikes and visualize the epoch with spike details.

Simple spike detector is registered as preprocessor function. Given a simple threshold, it will detect spikes from the data.

```
function simpleSpikeDetector(epochs, parameter)

% description : Simple spike detection from SchwartzNU Analysis folder; Refer https://github.com/SchwartzNU/SymphonyAnalysis/blob/master/GUIs/SpikeDetectorGUI.m
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

### ![](/assets/spike_detection_on_curator.png)

### c\) Delete bad epochs

To delete an epoch,  select an epoch from epoch tree. Click on _Tag To Delete _\(`ctrl+d`\) and to undo the tagging use _Undo Delete Tag_\(`ctr+z`\) . Once you are sure about the tagged epochs, Click on _Delete Tagged_.

### d\) Add Epoch/Cell Tags

Click on Epoch / Cell from data tree. Then click on add parameter to add the new tag. To remove a parameter click on the desired parameter from the grid and press remove parameter.

![](/assets/add_keyword.png)

### e\) Filtering of epochs

Epochs can be filtered based on the parameter as search criteria. It is possible to list the filtered epochs in data tree by enabling _Show Filtered Epochs_ check box. Below example, filters epoch which has NDF property and Value 3 and the result is displayed in a scrollable text pane.  
![](/assets/filtering.png)

> In the next sections we will see how to [build an analysis pipeline](/building-analysis-pipeline.md).



