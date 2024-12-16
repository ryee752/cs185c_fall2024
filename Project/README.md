# Investigating the Impact of Seasonal Monsoons on Ocean Stratification and Circulation in the Bay of Bengal

In this project, I will investigate the effects of seasonal monsoons on ocean stratification and circulation in the Bay of Bengal. Specifically, I will address the following science question:

**How do seasonal monsoons impact ocean stratification and circulation patterns in the Bay of Bengal?**

To investigate this question, I will construct a model of the Bay of Bengal and will run my model simulation for one year, focusing on the pre-monsoon season and the post-monsoon season. These two phases represent significant differences in rainfall and river discharge, which affect the freshwater input and, consequently, the stratification and circulation of the region. I anticipate that during the post-monsoon period, increased freshwater influx will lead to stronger vertical stratification and shallower mixed layers compared to the pre-monsoon period, where less freshwater inflow results in weaker stratification.

For initial conditions, I will use the state of the ECCO Version 5 Model in January of 2010. Similarly, I will construct boundary and external forcing conditions for this model from the ECCO Version 5 model output. To analyze the results, I will create a timeseries of temperature in the Bay of Bengal to observe the differences between the pre-monsoon and post-monsoon season. For visualization, I will create a movie illustrating changes in stratification and circulation from pre-monsoon to post-monsoon seasons.

# Reproducing Model Results
The following steps outline how to construct the model files, configure and run the model, and assess the model results.

## Step 1: Create the Model Files
Several input files need to be created to run the model. Generate the following list of files using the notebooks indicated in paratheses:

Model Grid (notebooks/Creating_the_Model_Grid.ipynb)
Bathymetry (notebooks/Creating_the_Bathymetry.ipynb)
Initial Conditions (notebooks/Creating_the_Initial_Conditions.ipynb)
External Forcing Conditions (notebooks/Creating_the_External_Forcing_Conditions.ipynb)
Boundary Conditions (notebooks/Creating_the_Boundary_Conditions.ipynb) The model files should be placed into the input directory.
## Step 2: Add files to the computing cluster
Once the input files have been created, the model files can be transferred to the computing cluster. Begin by cloning a copy of MITgcm into your scratch directory and make a folder for the configuration, .e.g.

mkdir MITgcm/configurations/ca_upwelling
Then, use the scp command to send the code, input, and namelist directories to your configuration directory.

Step 3: Compile the model
Once all of the files are on the computing cluster, the model can be compiled. Make a build directory in the configuration directory and run the following lines:

../../../tools/genmake2 -of ../../../tools/build_options/darwin_amd64_gfortran -mods ../code -mpi
make depend
make
## Step 4: Run the model with wind
After the compilation is complete, run the model with the wind. Move to the run directory, link everything from input and code, and the submit the job script:

sbatch cs185c16.slm

## Step 5: Analyze the Results
There are two notebooks provided for analysis:

Analyzing Model Results

This notebook is provided to have a quick look at spatial and temporal variations in the temperature, sea surface height, and velocity fields in the model. It also generates the visualization provided in the figures directory.

Answering the Science Question

This notebook provides analysis to address the science question posed above.
