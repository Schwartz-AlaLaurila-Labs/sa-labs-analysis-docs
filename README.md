# 1.1 Introduction

SA-Labs-Analysis is the data analysis toolbox for Multi-electrode patch clamp recordings. It is designed to support both online and offline analysis by using shared libraries and data structure. The raw data for the analysis is acquired using symphony-das [http://symphony-das.github.io/](http://symphony-das.github.io/) which is a MATLAB based data acquisition system for electrophysiologists.

The core analysis framework lives in [sa-labs-analysis-core](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-core) and facilitates the data storage and data sharing. The common analysis functions will be maintained in [sa-labs-util](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-util.git). The master configuration for managing cell class, cell types, etc is present in [sa-labs-analysis-preference](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-preference.git).

The user interface design for the toolbox is inspired by [Schwartz Lab Symphony Analysis](https://github.com/SchwartzNU/SymphonyAnalysis).

> Requirements - Matlab 2016a+, Windows 7/10 \(or\) OS-X \(or\) ubuntu 16+.  
>  [Continuous Integration](https://www.thoughtworks.com/continuous-integration) \(CI\) using [Jenkins ![](https://build.nbe.aalto.fi/buildStatus/icon?job=validateSALabsAnalysisCore)](https://build.nbe.aalto.fi/job/validateSALabsAnalysisCore/)
>
> The source code can be found in github repository[ https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis). It is licensed under MIT.
>
> Copyright \(c\) 2017 Schwartz-AlaLaurila-Labs



