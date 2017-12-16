## 1.4.1 Creating feature extractor

Let's focus on creating a simple extractor. As a rule of thumb

1. Create a new extractor for any new feature you compute.
2. Feature extractor should have 3 input parameters, 
   1. analysis - It is an instance of the `Analysis.m` class. It is seldom used in feature extractor, however, it is good to have it for future use.
   2. epochGroup - As the name suggests, it is just a group of epochs and facilitates adding new features to the epochGroup. 
   3. analysisParameter - A simple Matlab structure contains the parameters used in feature extractor. 

   > Always add comments describing the role of analysis parameter and its default value.
3. As the last rule, think about visualizing the feature. If its a simple line plot then specify the x-axis, x label, y label and title of the plot while adding the feature. 

```
function simpleExtractor(analysis, epochGroup, paramter)
% description : a brief
% param1:
%   default : value1
%   description: what is the role of param1 in analysis?
% param2:
%   default: value2
%   description: what is the role of param2 in analysis?
% ---

end
```

As a next step, Let's compute the mean response of epoch and save it back to the epochGroup.

```
epochCell = epochGroup.getFeatureData('EPOCH'); % 
epoch = epochCell{1}; % List of epochs
meanResponse = mean(epoch); % Mean of epoch

epochGroup.createFeature('MEAN_RESPONSE', meanResponse);
```

As another example, Let's focus on the `createFeature` in[`psthExtractor.m`](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-util/blob/master/src/main/matlab/%2Bsa_labs/%2Banalysis/%2Bcommon/%2Bextractors/psthExtractor.m). The PSTH feature can be easily visualized using Matlab `plot`. All the required attributes for the plot can be passed assigned while creating the feature.

```
function psthExtractor(~, epochGroup, paramter)

% description : Extracts Peri-Stimuls histogram from the epochGroup. Below are the list of parameters
% binWidthPSTH:
%   default : 0.01
%   description: bin width in seconds to estimate the PSTH
% smoothingWindowPSTH:
%   default: 0
%   description: Guassian smoothing window for smoothening the PSTH
% ---
% epochGroup: see @sa_labs.analysis.entity.EpochGroup
% 

... 
..... % code to compute the PSTH
.......

    epochGroup.createFeature('PSTH', count, ...
        'xAxis', x, ...
        'xLabel', 'Time (s)', ...
        'yLabel', 'PSTH', ...
        'binWidthPSTH', binWidthPSTH, ...
        'smoothingWindowPSTH', smoothingWindowPSTH);
end
```



