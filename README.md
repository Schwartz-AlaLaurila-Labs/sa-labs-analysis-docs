# 1.1 Introduction

SA-Labs-Analysis is the data analysis toolbox for multi-electrode patch clamp recordings. It is designed to support both streaming and post-acquisition analysis by using shared libraries and data structure. The raw data for the analysis is acquired using [symphony-das](http://symphony-das.github.io/) - a Matlab based data acquisition system for electrophysiologists.

SA-Labs-Analysis combines feature from different Github repositories. For example, the data structure and storage is defined in [sa-labs-analysis-core](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-core), common analysis functions are maintained in [sa-labs-util](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-util.git), and the master configuration for managing cell class, cell types are present in [sa-labs-analysis-preference](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-preference.git). In addition, it provides a graphical user interface to pre-process, analyze, and visualize the acquired data.

The user interface design for the toolbox is inspired by [Schwartz Lab Symphony Analysis](https://github.com/SchwartzNU/SymphonyAnalysis).

> Requirements - Matlab 2016a+, Windows 7/10 \(or\) OS-X \(or\) ubuntu 16+.  
>  [Continuous Integration](https://www.thoughtworks.com/continuous-integration) \(CI\) using [Jenkins ![](https://build.nbe.aalto.fi/buildStatus/icon?job=validateSALabsAnalysisCore)](https://build.nbe.aalto.fi/job/validateSALabsAnalysisCore/)
>
> The source code can be found in github repository[ https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis). It is licensed under MIT. 
>
> Copyright \(c\) 2017 Schwartz-AlaLaurila-Labs



