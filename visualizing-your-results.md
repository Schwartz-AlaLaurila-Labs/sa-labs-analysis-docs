# 1.5 Visualizing your results

To visualize the analysis tree and its extracted features, run `openTreeBrowser.m` from the Matlab command line with your analysis project as an input argument.  
Let us use the example of the previously created analysis project Example-Analysis\_01.

`openTreeBrowse('Example-Analysis_01');`

![](/assets/tree_browser.png)

The user interface shows the epoch groups and the list of features available for each epoch group. The panel below the tree describes the parameter present at the selected node. The panel to right displays the registered plots available in the tree browser. In the example here, `epochGroupParameterPlot`is selected. It is similar to the `diaryPlot`in the Data Curator, however, it plots only the selected subset of epochs \(i.e. epoch group\).

To register a new plotting function for the tree browser, package your function under the directory `+sa_labs/+analysis/+treebrowser/+plots`

### Plot Feature

`plotFeature`is a default plotting function for visualizing stored features. Let us revisit the `psthExtractor`example: the `createFeature`function specifies the parameters required for plotting the extracted PSTH data. Hence, it is possible to plot this data by selecting `plotFeature `from the list of available plots.

![](/assets/psth_response.png)

Let us focus on the leafs of the tree browser, where the PSTH feature is computed and stored for different epoch groups. First, for the node`stimTime = 20` , and second for the node`stimTime = 500.`As explained in the Step 3 - Building the analysis, the computed feature is percolated to the upper nodes. Hence,  the node`intensity == 1`will have access to PSTH of both the groups.

On selecting the node `intensity == 1` and checking the `Iterate Features`, from Tree Browser. It is possible to iterate through two PSTH plot using `Next`and `Previous`button

![](/assets/tree_Browser_iteration.png)

