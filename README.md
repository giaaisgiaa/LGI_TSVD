# LGI_TSVD (for rPPG) 

The following github repository is containing a modification of the LGI (Local Group Invariance) algorithm for rPPG analysis under the 'methods.py' python file, implementing the Truncated Singular Value Decompostion (TSVD) as core for the blood volume pulse (BVP) and heart rate (BPM) extraction from face videos. 



How to download the PyVHR python environment?

1) Follow the link https://github.com/phuselab/pyVHR/tree/pyVHR_CPU, and make sure you are cloning the right branch of the code, namely "pyVHR_CPU" (NOT "Master").
2) Go through the README.md file to create the environment, BUT don't use the 'pyVHR_CPU_env.yml' file to install the required packages. Instead, use the updated version  'cpu_pyvhr.yml', found in this 'LGI_TSVD' github repository, under https://github.com/giaaisgiaa/LGI_TSVD.
3) Open 'cpu_pyvhr.yml', and at the bottom of it replace the given 'prefix:' with the actual path where you cloned the "pyVHR_CPU" repository.

How to run the 'SVD_vs_TSVD' notebook?

5) Now that you have pyVHR installed, you can download the "Notebook_SVD_vs_TSVD" folder and move all the content of it into the "Notebooks" folder of the already downloaded pyVHR repository.
6) Navigate in the pyVHR folder, and replace the 'methods.py' original file under 'pyVHR\BVP\methods.py' with the one provided by the current repository (still named 'methods.py'), containing the new 'cpu_LGI_TSVD' rPPG algorithm.
7) Run the 'SVD_vs_TSVD.ipynb' notebook under the "notebooks" folder.

## SVD vs TSVD notebook

1) WARNING 1:
In the "Computing overall DTW, delta BPM, cpu_runtime" section of the 'SVD_vs_TSVD.ipynb' notebook, the code is computing the overall DTW (dynamic time warping) between PPG and rPPG signals, the overall difference in BPM estimation, and the overall cpu_runtime for a given scenario where the candidate is put. Change the parameter 'T' to change the scenario. Pay attention to the 'method' variable, since it defines the rPPG algorithm in use, e.g. cpu_LGI, cpu_LGI_TSVD, cpu_CHROM, ... Change it to choose the algorithm you want to use for the rPPG extraction.

2) WARNING 2:
In the "Extracting BPM, with LGI_TSVD" section, the code is using the new modified LGI_TSVD algorithm to extract BPM, DTW, delta BPM, cpu_runtime, RMSE (NOT to trust in this case). Set the 'params' Stress variable to 'False' if the candidate is in a "resting" situation/scenario, 'True' for all the other scenarios. 
