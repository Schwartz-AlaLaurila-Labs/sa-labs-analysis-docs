# 1.1 Introduction

The scientific data lifecycle follows, acquiring the experimental data, analyzing it and visualizing the results. However,  to reproduce the life cycle steps with minimal efforts requires a sophisticated graphical user interface, disciplined data management, modular code and a simplified usage documentation.

SA-Labs-Analysis is the data analysis toolbox for multi-electrode patch clamp recordings. It provides a graphical user interface to pre-process, analyze, and visualize the acquired data. The raw data for the analysis is acquired using [symphony-das](http://symphony-das.github.io/) - a Matlab based data acquisition system for electrophysiologists. Furthermore, the analysis toolbox is designed to support both streaming and post-acquisition analysis by using shared libraries and data structure.

In this special assignment, I developed the SA-Labs-Analysis toolbox by primarily extending it from the [sa-labs-analysis-core](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-core) - a generic framework to build an analysis pipeline using Matlab. It also combines features from different Github repositories. For example, common analysis functions for performing electrophysiology data analysis is maintained in the [sa-labs-util](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-util.git) repository, and the master configuration for managing cell class, cell types are present in the [sa-labs-analysis-preference](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-preference.git) repository. In addition, this special assignment report serves as the usage documentation for the SA-Labs-Analysis toolbox.

As a way of promoting open science, the [source code](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis) for the SA-Labs-Analysis toolbox, dependent libraries, and [usage documentation](https://github.com/Schwartz-AlaLaurila-Labs/sa-labs-analysis-docs) is made open in Github and licensed under MIT. The user interface design is inspired by [Schwartz Lab Symphony Analysis](https://github.com/SchwartzNU/SymphonyAnalysis).

> Requirements - Matlab 2016a+, Windows 7/10 \(or\) OS-X \(or\) ubuntu 16+.  
>  [Continuous Integration](https://www.thoughtworks.com/continuous-integration) \(CI\) using [Jenkins ![](https://build.nbe.aalto.fi/buildStatus/icon?job=validateSALabsAnalysisCore)](https://build.nbe.aalto.fi/job/validateSALabsAnalysisCore/)
>
> Copyright \(c\) 2017 Schwartz-AlaLaurila-Labs



