## 1.4.1 Creating feature extractor

Let's focus on creating a simple extractor. As a rule of thumb

1. Create a new extractor for any new feature you compute.
2. Feature extractor should have 3 input parameters, 
   1. analysis - It is an instance of the `Analysis.m` class. It is seldom used in feature extractor, however, it is good to have it for future use.
   2. epochGroup - As the name suggests, it is just a group of epochs and facilitates adding new features to the epochGroup. 
   3. analysisParameter - A simple Matlab structure contains the parameters used in feature extractor. 

   > Always add comments describing the role of analysis parameter and its default value.
3. As the last rule, think about visualizing the feature. If its a simple line plot then specify the x-axis, x label, y label and title of  plot while adding the feature. 

Now that we know our rules, let's create a `simpleExtractor`function which computes the mean of epoch and add it to the epochGroup

```
function simpleExtractor(analysis, epochGroup, paramter)
% description : Compute the mean for a given epochGroup and add it to epochGroup
% ---

end
```

As a next step, compute the mean response of epoch and save it back to the epochGroup.

```
epochCell = epochGroup.getFeatureData('EPOCH'); % 
epoch = epochCell{1}; % List of epochs
meanResponse = mean(epoch); % Mean of epoch

epochGroup.createFeature('MEAN_RESPONSE', meanResponse);
```

As another example to create feature, focus on the `createFeature` in[`psthExtractor.m`](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-util/blob/master/src/main/matlab/%2Bsa_labs/%2Banalysis/%2Bcommon/%2Bextractors/psthExtractor.m). 

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

The PSTH feature has all the required attributes for the plot and is used to visualize the PSTH. This will be explained in next section -  [visualizing your results](/visualizing-your-results.md). 

