# 1.5 Visualizing your results

To visualize the analysis tree and its extracted features, run `openTreeBrowser.m` from the Matlab command line with your analysis project as an input argument. Let us use the example of the previously created analysis project Example-Analysis\_01.

`openTreeBrowse('Example-Analysis_01');`

![](/assets/tree_browser.png)

The user interface shows the epoch groups and the list of features available for each epoch group. The panel below the tree describes the parameter present at the selected node. The panel to right displays the registered plots available in the tree browser. In the example here, `epochGroupParameterPlot `is selected. It is similar to the `diaryPlot `in the Data Curator, however, it plots only the selected subset of epochs \(i.e epoch group\). 

To register a new plotting function for the tree browser, package your function under the directory `+sa_labs/+analysis/+treebrowser/+plots`

### a\) Plot Feature

`plotFeature`is a default plot for visualizing stored feature. Let's revisit the [`psthExtractor` ](/building-analysis-pipeline/creating-feature-extractor.md)example.  The `createFeature`function specifies the plot parameters required for visualizing PSTH. Hence, It is possible to plot that by selecting `plotFeature`from available plots.  
![](/assets/psth_response.png)

#### Plotting multiple features

It is also possible to iterate and plot the feature one by one. For example, AMP2\_EPOCH will have the epoch response recorded from amplifier channel 'Amp2'. To explore the AMP2\_EPOCH which has 20 milliseconds of stimTime, select it from the tree panel. After that check on Iterate Feature from the user interface. If the selected node has more than one recording then next and previous button will be enabled.  
![](/assets/feature_itereator.png)

