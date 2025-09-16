INFORMATION ABOUT FILES INCLUDED
---------------------------------
Main Folder CSV Files:
----------------------

1. full_imidazole_arylation_data.csv is the full dataset that was converted from the ORD source. 
   It has some extra unused columns that includes non-dynamic variables (constant reagent/volume/mass/mole)

2. temp_90_150_ia.csv is the dataset of predicted yields for missing combinations of the various reaction variables (temperature 90 and solvent volume 150).

3. MLR.ipynb has the implementation of the MLR trials and the runs for the trials

HOW TO RUN MLR.ipynb
---------------------
1. Install the statsmodels package if you do not already have:
	pip install statsmodels

2. Make sure you have the full_imidazole_arylation_data.csv and temp_90_150_ia.csv files in the same folder as the ipynb

3. Run the ipynb cells 
---------------------


Converting Data Folder:
----------------------

1. Extracting_data.ipynb takes the ORD data and converts it to a json then a csv file.

HOW TO RUN Extracting_data.ipynb:
---------------------------------
1. Install ord-schema in edbo environment:
	pip install ord-schema
2. Make sure ord_dataset-0c75d67751634f0594b24b9f498b77c2.pb.gz is in the same file as the ipynb file:

3. Run the ipynb cells (will produce a full_imidazole_arylation_data.csv file (WARNING: Will replace existing file if in same folder))
---------------------------------

2. ord_dataset-0c75d67751634f0594b24b9f498b77c2.pb.gz is the compressed data file from ORD.

3. Estimate missing yields.ipynb uses full_imidazole_arylation_data.csv to estimate the missing data needed for the EDBO runs. 

HOW TO RUN Estimating missing yields.ipynb
-------------------------------------------
1. Make sure full_imidazole_arylation_data.csv is in the same folder as ipynb (can copy it to same folder)

2. Run the ipynb cells (will produe a temp_90_150_ia.csv file (WARNING: Will replace existing file if in same folder))
-------------------------------------------


IA_run_one_round_at_time Folder:
--------------------------------

descriptiors Folder:
--------------------

(All information of these files were calculated from WebMO)

1. IA_Catalyst.csv is a csv file that includes the dipole moment, molar mass, and number of atoms of the catalysts.

2. IA_Reagents.csv is a csv file that includes the dipole moment, molar mass, and number of atoms of the reagents.

3. IA_Solvent.csv is a csv file that includes the dipole moment, molar mass, and number of atoms of the solvents.

The Other Folders in this directory:

Formating is [initialization method]_[acquisition function]_[descriptor used]_[batch #]

Legend:
	kmean = k mean initialization method
	pam = k medoids initialization method
	rand = random initialization method
	EI = expected improvement function
	TS = Thompson Sampling function
	dipole = dipole, # atoms, and molar mass descriptors used
	default batch # = 7
	default descriptor = EDBO given descriptors

The dipole folders were us testing if those descriptors would change outcome -> not really so we didn't do much with them.

These folder includes the ipynb of each trial run and also a result folder that includes the csv with the results for each proposed experiments.

WARNING: Please create copies of these folders or rename the exported csv files in code before running it as running the ipynb files will replace existing csv files in with same name.

HOW TO RUN EDBO PACKAGE
---------------------------------
Full EDBO code can be found here: https://github.com/b-shields/edbo/tree/master
EDBO Documentation can be found here: https://b-shields.github.io/edbo/index.html\

To initialize EDBO (from their README):
1. Create anaconda environment using this command:
	conda create --name edbo python=3.7.5

2. Install rdkit, Mordred, and PyTorch by running these commands (one at a time):
	conda activate edbo
	conda install -c rdkit rdkit
	conda install -c rdkit -c mordred-descriptor mordred
	conda install -c pytorch pytorch=1.3.1

3. Install EDBO using this command:
	pip install edbo

4. Then open Jupyter Notebook or lab in enviroment, you can use this command:
	conda install jupyterlab
or 
	jupyter lab
---------------------------------

HOW TO RUN THE TRIAL IPYNBS
---------------------------
1. Have EDBO package installed and be running in edbo environment.

2. Run the import cell

3. When you are running a trial, you have to run all rounds before closing the env as I don't know how to save the progress of a trial run.

4. The trial run will replace any existing csv files of the existing name so please be careful in running the trial.

5. When an export_proposed is ran the csv file will be made.

6. Results were manually added to these files after they were copied to the results folder.

7. Once you have understood the above information, please go ahead in running the cells.

8. Run as many rounds are needed.
----------------------------------

archive381912.tar is the compressed files of the WebMO jobs.

