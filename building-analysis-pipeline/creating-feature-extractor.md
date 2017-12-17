## 1.4.1 Creating a feature extractor

Here are some basic rules for creating a simple extractor:

1. Create a new extractor for any new feature you want to compute.
2. The feature extractor must have the following 3 input parameters,  
   1. `analysis` is an instance of the [`Analysis.m`](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-core/blob/master/src/main/matlab/+sa_labs/+analysis/+core/Analysis.m) class. It is not regularly used yet in current feature extractor functions; however, it is likely required for future expansions of the analysis functionality.  
   2. `epochGroup` is an instance of the [`EpochGroup.m`](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-core/blob/master/src/main/matlab/+sa_labs/+analysis/+entity/EpochGroup.m) class. It defines a group of epochs and facilitates adding new features to an existing epochGroup.  
   3. `analysisParameter`is a Matlab structure containing the parameters which are used in the feature extractor.

   > When creating your own feature extractor, always make sure to add comments that describe the role of each analysis parameter and its default value.

3. Finally, consider the visualization of the feature. Ideally specify plotting parameters, such as the x-axis, the axis labels and the title of the plot in the feature extractor function.

With these guidelines, let us create a `simpleExtractor`function which computes the average neuronal response in each epoch and adds it to the`epochGroup`instance.

```
function simpleExtractor(analysis, epochGroup, paramter)
% description : Compute the mean for a given epochGroup and add it to epochGroup
% ---

end
```

Then, compute the average response of each epoch and save it to the `epochGroup`instance

```
epochCell = epochGroup.getFeatureData('EPOCH'); % 
epoch = epochCell{1}; % List of epochs
meanResponse = mean(epoch); % Mean of epoch

epochGroup.createFeature('MEAN_RESPONSE', meanResponse);
```

The second example is the[`psthExtractor.m`](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-util/blob/master/src/main/matlab/%2Bsa_labs/%2Banalysis/%2Bcommon/%2Bextractors/psthExtractor.m) from our`LightStepAnalysis`, explained in the previous section. Let us focus on the line `epochGroup.createFeature.`

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

The PSTH feature contains all the required attributes to plot the results as a simple line plot, and can, therefore be easily used to visualize the PSTH. How to do this will be explained in next section -  [visualizing your results](/visualizing-your-results.md).

