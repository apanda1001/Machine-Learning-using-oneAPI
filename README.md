# Please find the `intel-oneapi.ipynb` file at the root folder for the submission.
## Title
Machine Learning using oneAPI
  
## Preparation to run on Intel DevCloud

After the git clone operation:

```bash
mkdir MLoneAPI
cd MLoneAPI
source  /glob/development-tools/versions/oneapi/2022.3.1/inteloneapi/setvars.sh --force 
conda activate base
pip install ipykernel
python -m ipykernel install --user --name 2022.3.1 --display-name "oneAPI 2022.3.1"

git clone https://github.com/IntelSoftware/Machine-Learning-using-oneAPI.git
cd  Machine-Learning-using-oneAPI
pip install -r requirements.txt
```

## Currently Known Issues:

### Known issue: 
- SVC and KNN not currently available for GPU device using the dpctl library - the fit() function(s) for these two algorithm's state that they do not support the device
- for submitting to qsub, consider using gen9 rather than gpu in the qsub command. gen9 supports 64 bit GPU, and the node allocated for 32 bit gpu are currently not working correctly with this code - still in investigation - as work around submit to gen9


## Purpose
The Jupyter Notebooks in this training are intended to give instructors an accesible but challenging introduction to machine learning using oneAPI.  It enumerates and describes many commonly used Scikit-learn* allgorithms which are used  daily to address machine learning challenges.  The primary purpose is to accelerate commonly used Scikit-learn algorithms for Intel CPUs and GPU's using Intel Extensions for Scikit-learn* which is part of the Intel AI Analytics Toolkit powered by oneAPI.

This workshop is designed to be used on the DevCloud and includes details on submitting batch jobs on the DevCloud environment.

## License  
Code samples 
are licensed under the MIT license. See [License.txt](https://github.com/oneapi-src/oneAPI-samples/blob/master/License.txt) for details.
Third party program Licenses can be found here: [third-party-programs.txt](https://github.com/oneapi-src/oneAPI-samples/blob/master/third-party-programs.txt)

## Content Details

#### Pre-requisites

- Python* Programming
- Calculus
- Linear algebra
- Statistics


## Survey

Please fill out our survey to let us know hwo we can imporve or how it might impact your developer skills

https://intel.az1.qualtrics.com/jfe/form/SV_9uHKSYFaiC9Xjeu

![Survey.jpg](Survey.jpg)


## Syllabus

- 8 Modules (8 hours)
- 15 Lab Exercises

-----------------------
| Folder | Modules | Description | Duration |
| :--- | :--- | :------ | :------ |
| 01_Intel_Extensions_for_Scikit-learn_Patching_CPU|[01_01_Patching_Classifier_CPU](01_Intel_Extensions_for_Scikit-learn_Patching_CPU/01_01_Patching_Classifier_CPU.ipynb)| + Apply the simple patch to scikit-learn* KNN.| 15 min |
| 01_Intel_Extensions_for_Scikit-learn_Patching_CPU |[01_02_sklearnex_Motivation_Acceleration.ipynb](01_Intel_Extensions_for_Scikit-learn_Patching_CPU/01_02_sklearnex_Motivation_Acceleration.ipynb)| +Describe the basics of oneAPI AI Kit components, and where the Intel(R) Extensions for scikit-learn* fits in the broader package<br>+ Describe where to download and how to install the oneAPI AI Kit<br>+ Describe the advantages of one specific component of oneAPI AI Kit, Intel(R) Extensions for scikit-learn*, invoked via the sklearnex library<br>+ Apply the patch and unpatch functions with varying granularities including python scripts and also within Jupyter cells -from whole file applications to more surgical patches applied to a single algorithm.<br>+ Enumerate sklearn algorithms which have been optimized.| 15 min |
| 01_Intel_Extensions_for_Scikit-learn_Patching_CPU |[01_03_Coarse_Patching_Strategy.ipynb](01_Intel_Extensions_for_Scikit-learn_Patching_CPU/01_03_Coarse_Patching_Strategy.ipynb)|+ Describe how to import and apply patch_sklearn()<br>+ Describe how to import and apply unpatch_sklearn()<br>+ Describe method & apply the patch to an entire python program<br>+ Describe how to surgically unpatch specific optimized functions if needed<br>+ Describe a patching strategy that ensures that the Intel Extensions for scikit-learn runs as fast or faster than the stock algorithms it replaces<br>+Apply patch methodology to speed up KNN on CovType dataset| 15 min |
| 02_Applied_Patching_CPU |[02_01_Patching_Kmeans_CPU](02_Applied_Patching_CPU/02_01_Patching_Kmeans_CPU.ipynb)| + Describe the value of Intel® Extension for Scikit-learn methodology in extending scikit-learn optimization capabilites.<br> + Name key imports and function calls to use Intel Extension for Scikit-learn to target Kmeans.<br> + Build a Sklearn implementation of Kmeans targeting CPU using patching.<br> + Apply patching with dynamic versus lexical scope approaches.| 20 min |
| 02_Applied_Patching_CPU |[02_02_PatchingSVM_CPU](02_Applied_Patching_CPU/02_02_PatchingSVM_CPU.ipynb)| + Describe how to surgically unpatch specific optimized functions if needed.<br> + Describe differences in patching more globally versus more surgically.<br> + Apply patching to SVC algorithm.<br> + Describe acceleration for the covtype dataset usinf SVC. | 20 min |  
| 02_Applied_Patching_CPU |[02_03_Pairwise_DistanceVectorizedStockSImulationReadPortfolio](02_Applied_Patching_CPU/02_03_Pairwise_DistanceVectorizedStockSImulationReadPortfolio.ipynb)|+ Describe and apply the correct surgical patching method to patch pairwise_distance.<br> + Describe which distance metrics such as 'euclidean', 'mahattan', 'cosine', or 'correlation' are optimized by Intel Extensions for Scikit learn.<br> + Describe the application of pairwise_distance to the problem of finding all time series charts similar to a chosen pattern.| 20 min |
| 02_Applied_Patching_CPU |[02_04_TelcoCustomerChurn_OPTIONAL](02_Applied_Patching_CPU/02_04_TelcoCustomerChurn_OPTIONAL.ipynb)|+ Practicum: Apply patching strategy to Telco Customer churn code.<br> + Apply patch to PCA, DBSCAN, KMEANS, and classifier of your choice.| 20 min |
| 03_Applied_to_Image_Clustering_CPU |[03_01_Practicum_ImageClustering](03_Applied_to_Image_Clustering_CPU/03_01_Practicum_ImageClustering.ipynb)| + Explore and interpret the image dataset.<br> + Apply Intel® Extension for Scikit-learn* patches to Principal Components Analysis (PCA), Kmeans,and DBSCAN algorithms.<br> + Synthesize your understanding- searching for ways to patch or unpatch any applicable cells to maximize the performance of each cell.| 60 min |
| 04_Applied_to_Galaxy_Classification_CPU |[04_01_Practicum_AnalyzeGalaxyBatch](04_Applied_to_Galaxy_Classification_CPU/04_01_Practicum_AnalyzeGalaxyBatch.ipynb)| + Apply Multiple Classification Algorithms with GPU to classify stars belonging to each galaxy within a combined super galaxy to determine most accurate model.<br> + Apply Intel® Extension for Scikit-learn* patch and SYCL context to compute on available GPU resource.<br> Synthesize your compreshension by searching for opportunities in each cell to maximize performance. Investigate adding pairwise distance as a means for all the stars within 3 light years.| 60 min |
| 05_Introduction_dpctl_for_GPU |[05_01_Introduction_simple_gallery_dpctl_for_GPU](05_Introduction_dpctl_for_GPU/05_01_Introduction_simple_gallery_dpctl_for_GPU.ipynb)| + Apply patching while targeting an Intel GPU.<br> + Apply Intel Extension for Scikit-learn to KNeighborsClassifier on Intel GPU.| 30 min |
| 05_Introduction_dpctl_for_GPU|[05_02_PatchingClassifier_GPU](05_Introduction_dpctl_for_GPU/05_02_PatchingClassifier_GPU.ipynb)|+ Describe how to apply dpctl compute follows data in conjuction with patching.<br> + Apply patching to KNN algorithm on covtype dataset.| 20 min |
| 05_Introduction_dpctl_for_GPU|[05_03_Gallery_of_Functions_on_GPU](05_Introduction_dpctl_for_GPU/05_03_Gallery_of_Functions_on_GPU.ipynb)| + Apply the patch functions with varying granularities.<br> + Leverage the Compute Follows Data methodology using Intel DPCTL library to target Intel GPU.<br> + Apply DPCTL and Patching to variety of Scikit-learn Algorithsm in a simple test harness structure.<br> + For the current hardware configurationson the Intel DevCloud - we are NOT focusing on performance.| 30 min |
| 06_Applied_to_Image_Clustering_GPU|[06_01_Practicum_ImageClustering](06_Applied_to_Image_Clustering_GPU/06_01_Practicum_ImageClustering.ipynb)| + Explore and interpret the image dataset.<br> + Apply Intel® Extension for Scikit-learn* patches to Principal Components Analysis (PCA), Kmeans,and DBSCAN algorithms.<br> + Synthesize your understanding- searching for ways to patch or unpatch any applicable cells to maximize the performance of each cell.<br> + Apply a q.sh script to submit a job to another node that has a GPU on Intel DevCloud.| 60 min |  
| 07_Applied_to_Galaxy_Classification_GPU|[07_01_Practicum_AnalyzeGalaxyBatch](07_Applied_to_Galaxy_Classification_GPU/07_01_Practicum_AnalyzeGalaxyBatch.ipynb)| + Apply Multiple Classification Algorithms with GPU to classify stars belonging to each galaxy within a combined super galaxy to determine most accurate model.<br> + Apply Intel® Extension for Scikit-learn* patch and SYCL context to compute on available GPU resource.<br> + Synthesize your compreshension by searching for opportunities in each cell to maximize performance. | 60 min |  
| 08_Introduction_to_Numpy_powered_by_oneAPI|[08_01_Numpy_How_Fast_Are_Numpy_Ops](08_Introduction_to_Numpy_powered_by_oneAPI/08_01_Numpy_How_Fast_Are_Numpy_Ops.ipynb)| + Desribe why replacing inefficient code, such as time consuming loops, wastes resources, and time.<br> + Describe why using Python for highly repetitive small tasks is inefficient.<br> + Describe the additive value of leveraging packages such as Numpy which are powered by oneAPI in a cloud world.<br> + Describe the importance of keeping oneAPI and 3rd party package such as Numpy, Scipy and others is important.<br> + Enumerate ways in which Numpy accelerates code.<br> + Apply loop replacement methodologies in a variety of scenarios.| 60 min | 
| 08_Introduction_to_Numpy_powered_by_oneAPI |[08_02_PandasPoweredBy_oneAPI](08_Introduction_to_Numpy_powered_by_oneAPI/08_02_PandasPoweredBy_oneAPI.ipynb)| + Apply Numpy methods to dramatically speed up certain common Pandas bottlenecks.<br> + Apply WHERE or SELECT in Numpy powered by oneAPI.<br> + Avoid iterrows using Numpy techniques.<br> + Achieve better performacne by converting numerical columns to numpy arrays.| 20 min |  
#### Content Structure

Each module folder has a Jupyter Notebook file (`*.ipynb`), this can be opened in Jupyter Lab to view the training contant, edit code and compile/run. 

## Install Directions

The training content can be accessed locally on the computer after installing necessary tools, or you can directly access using Intel DevCloud without any installation.

#### Local Installation of JupyterLab and oneAPI Tools

The Jupyter Notebooks can be downloaded locally to computer and accessed:
- Install Jupyter Lab on local computer: [Installation Guide](https://jupyterlab.readthedocs.io/en/stable/getting_started/installation.html)
- Install Intel oneAPI Base Toolkit on local computer: [Installation Guide](https://www.intel.com/content/www/us/en/developer/tools/oneapi/base-toolkit-download.html) 
- git clone the repo and access the Notebooks using Jupyter Lab


#### Access using Intel DevCloud

The Jupyter notebooks are tested and can be run on Intel DevCloud without any installation necessary, below are the steps to access these Jupyter notebooks on Intel DevCloud:
1. Register on [Intel DevCloud](https://devcloud.intel.com/oneapi)
2. Login, Get Started and Launch Jupyter Lab
3. Open Terminal in Jupyter Lab and git clone the repo and access the Notebooks
