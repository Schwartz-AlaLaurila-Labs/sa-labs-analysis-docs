# 1.5 Visualizing your results

To visualize the analysis tree and created features, run `openTreeBrowser.m`from the matlab command line. It takes the analysis project as an input argument.

Let's open the analysis project **Example-Analysis\_01 **which we created in the analysis build pipeline,`openTreeBrowse('Example-Analysis_01').`The user interface shows the epoch group and the list of features available at each epoch group.

`epochGroupParameterPlot`It is similar to the diary plot in data curator, however, the difference is, it plots only the subset of epochs \(i.e epoch group\).

![](/assets/tree_browser.png)

## a\) Plot Feature

As we already specified the plot parameters for PSTH while creating the feature. It is possible to plot that by just clicking on plotFeature from available plots.  
![](/assets/psth_response.png)

#### Plotting multiple features

It is also possible to iterate and plot the feature one by one. For example, the AMP2\_EPOCH will have the recordings based on filter condition. Let's explore the amplifier recording which has stimTime 20 milliseconds.

One can iterate the feature by clicking on the Previous / Next button from the user interface.

![](/assets/feature_itereator.png)

