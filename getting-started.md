# 1.2 Getting Started

## Installation

1\) Open Matlab and go to its home directory using `cd(userpath());` Create a projects folder in the home directory using `mkdir('projects')`

![](/assets/installation_1.png)

2\) As a next step, open the terminal and clone the git repo using `git clone https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis.git` into `<userpath>\projects\sa-labs-analysis` directory

![](/assets/installation_2.png)

3\) Download and install [ToolboxToolbox](https://github.com/ToolboxHub/ToolboxToolbox) by following the [installation instructions](https://github.com/ToolboxHub/ToolboxToolbox#installation). Restart the MATLAB

4\) Run the function `tbUseProject('sa-labs-analysis');` in Matlab command window. It will start installing the data analysis toolbox with required dependency. To verify the installation, check the last few lines of Matlab console. It should look like below, 

```
Checking for "sa-labs-analysis" local hook.
Checking for "sa-labs-analysis-core" local hook.
Checking for "sa-labs-util" local hook.
Checking for "preference" local hook.
Checking for "yamlmatlab" local hook.
Checking for "app-toolboxes" local hook.
Checking for "JavaTreeWrapper_v1.0" local hook.
Checking for "JavaTableWrapper_v1.0" local hook.
Checking for "MatlabPropertyGrid_v1.0" local hook.
Checking for "mdepin_v1.0" local hook.
Checking for "MatlabPersistence_v1.0" local hook.
Checking for "mmockito_v1.0" local hook.
Checking for "appbox" local hook.
Checking for "for-each-iterator" local hook.
Checking for "logging4matlab" local hook.
Checking for "MatlabQuery" local hook.
Checking for "matlab-tree" local hook.
Checking for "jsonlab_v1.2" local hook.
Evaluating general-purpose hook for "yamlmatlab": "javaaddpath(fullfile(getfield(what('+yaml'), 'path'), 'external', 'snakeyaml-1.9.jar'))".
  OK
.Looks good: 18 resolved toolboxes deployed OK.
```

> Now that we have analysis toolbox installed let's [parse some data](/parsing-your-data.md).



