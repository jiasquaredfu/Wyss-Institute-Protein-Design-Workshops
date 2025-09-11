# Wyss Computational Protein Design Workshops
Welcome to the Wyss Institute protein design workshops! We are covering the basics computational protein design, current workflows and de novo design strategies. This is geared towards experimentalists who work in protein engineering who'd like to learn about the newest machine learning driven protein design tools. No prior experience needed!

<b> What to take away from this workshop: </b>
1. Understanding of cutting-edge machine learning models for protein design
2. Tools for the modern protein design pipeline downloaded on your computer
3. A *de novo* mini-binder protein you designed!

<b> The workshop will be split up into two sessions: </b>

Day 1, September 11th (1-2pm): downloading all the necessary packages for this courageous quest
Day 2, September 12th (1-2:30pm): designing our own mini binders and working through any installation problems

*** For day 2 of the workshop, please come with a specific target in mind so we can help you make your very own binder!

# Before the Workshop 
## Hardware requirements 
These following items are required for running software for this workshop!
1. Laptop or PC
2. 10-20GB of available storage
3. Terminal authorization 

## Command Line Cheat Sheet
Linux is used to navigate and download the necessary software through terminal on both Mac and Windows for this workshop. Conda is also a python environment hosting system which we will be using to load dependencies for our various models. Basic familiarity with these key commands will be very helpful for this workshop and for computational work in general (we will use them throughout the workshop, no need to memorize them!):

| Linux/VIM/Conda Command  | Function                                                |
|--------------------------|---------------------------------------------------------|
| `ls`                     | show contents of current directory                      |
| `cd <folder_name>`       | move into folder                                        |
| `cd ..`                  | move out of folder                                      |
| `pwd`                    | show current directory file path                        |
| `mv <file_name> <new_location>` | move file to new location                           |
| `mvdir <folder_name> <new_location>` | move folder to new location                     |
| `rm <file_name>`         | remove file                                             |
| `rmdir <folder_name>`    | remove folder                                           |
| `vi <file_name>`         | open VIM editor (press "i" key to enter editing mode)  |
| `:wq`                    | save and quit file                                      |
| `:q`                     | quit file without saving                                |
| `conda info`             | check conda status and version                          |
| `conda install PACKAGENAME`     | add package to conda                             | 
| `conda activate ENVNAME`     | activate conda environment                            | 
| `conda deactivate`     | deactivate current conda environment                            | 
| `conda env list`          | show conda environments                            | 
| `conda list`          | show packages on current conda environment                       |
| `conda rename -n OLD_ENV_NAME NEW_ENV_NAME`          | rename conda environment                       |
| `conda env remove --name ENVNAME`          | delete conda environment                       |




 

<b>Helpful Resources:</b><br>
- [Here](https://www.geeksforgeeks.org/linux-unix/linux-commands-cheat-sheet/) is a comprehensive Linux cheat sheet for reference <br>
- [Here](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf) is a comprehensive Conda cheat sheet for reference <br>
- [Here](https://gitlab.com/slackermedia/bashcrawl) is a game that helps you build up your Linux muscle memory! <br>


# Workshop Day 1 - Downloading Software (how fun!)
Check out these primer slides on the theory and pipeline structure for designing proteins from scratch [here](https://hu-my.sharepoint.com/:p:/g/personal/dawningjiaxi_fu_wyss_harvard_edu/EVwylZ5jwstJlKK3unATEh4BOkJ3t_kOPiGjVQT0rVE__A?e=bCCi2G).

# 1. Installing Dependencies
A few packages need to be installed before we can download and run the 3 machine learning models which comprise the protein design pipeline (RFDiffusion, ProteinMPNN, Alphafold, PyMol).

## On Mac
1. Install homebrew
- Navigate to directory where you want to work
- Type  <pre> /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" </pre> and enter
- Confirm homebrew has been properly installed by typing <pre> brew --version </pre> and enter (should be Homebrew 4.6.10)
- If not this version, type
<pre> brew update </pre> and check version again 
2. Install [anaconda distributor](https://www.anaconda.com/download)
- Follow the conda instructions for Mac
- Open Terminal 
- Confirm conda has been properly installed by typing <pre> conda --version </pre> and enter (should be 25.7.0)
- If not this version, type
<pre> conda update --all </pre> and check version again 
3. Install [Git](https://docs.github.com/en/get-started/git-basics/set-up-git)
- Follow download instructions for Mac (desktop app not necessary but helpful for beginners)
- Confirm git has been properly installed by typing <pre> git --version </pre> and enter (should be 2.51.0)
- If not this version, type
<pre>brew upgrade git</pre> and check version again 
4. Install wget
- Type <pre> brew install wget </pre> and enter (should be 1.25.0)
- If not this version, type
<pre> brew upgrade wget </pre> and check version again 
5. Install curl
- Type <pre> brew install curl </pre> and enter (should be 8.15.0)
- - If not this version, type
<pre> brew upgrade curl </pre> and check version again 
6. Install cmake
<pre> brew install cmake </pre> and enter (should be 4.1.1)
- If not this version, type
<pre> brew upgrade cmake </pre> and check version again 

## On Windows
1. Install [Git](https://docs.github.com/en/get-started/git-basics/set-up-git)
- Follow download instructions for Windows (desktop app not necessary)
- Confirm git has been properly installed by typing <pre> git --version </pre> and enter
- If not this version, type
- <pre>git update-git-for-windows</pre> and check version again 

2. Install [anaconda distributor](https://www.anaconda.com/download)
- Follow the conda instructions for Windows
- Open cmd or powershell
- Confirm conda has been properly installed by typing <pre> conda --version </pre> and enter
3. Download wget installer x64 [here](https://eternallybored.org/misc/wget/)
# 2. Install Machine Learning Models 
*all GitHub repos for the machine learning models are linked in the section header for detailed instructions if needed*
- Naviugate to a folder where you want to keep software
- This can be done manually or through the following commands quickly (change path to yours)
<pre> cd /Users/jiasquared/Desktop/Wyss </pre>
- Make a new folder to store everything (the name can be anything)
<pre> mkdir protein_design_software && cd protein_design_software </pre>
## 2a. Install [RFDiffusion](https://github.com/RosettaCommons/RFdiffusion)
1. Ensure you are in the directory you want <pre> cd protein_design_software </pre> 
2. Clone RFdiffusion git repo
<pre> git clone https://github.com/RosettaCommons/RFdiffusion.git </pre>
2. Install model weights (this step will take ~5 minutes, type the following code blocks into Terminal and enter one at a time)
<pre> cd RFdiffusion </pre>
<pre> mkdir models && cd models </pre>
<pre>
wget http://files.ipd.uw.edu/pub/RFdiffusion/6f5902ac237024bdd0c176cb93063dc4/Base_ckpt.pt
wget http://files.ipd.uw.edu/pub/RFdiffusion/e29311f6f1bf1af907f9ef9f44b8328b/Complex_base_ckpt.pt
wget http://files.ipd.uw.edu/pub/RFdiffusion/60f09a193fb5e5ccdc4980417708dbab/Complex_Fold_base_ckpt.pt
wget http://files.ipd.uw.edu/pub/RFdiffusion/74f51cfb8b440f50d70878e05361d8f0/InpaintSeq_ckpt.pt
wget http://files.ipd.uw.edu/pub/RFdiffusion/76d00716416567174cdb7ca96e208296/InpaintSeq_Fold_ckpt.pt
wget http://files.ipd.uw.edu/pub/RFdiffusion/5532d2e1f3a4738decd58b19d633b3c3/ActiveSite_ckpt.pt
wget http://files.ipd.uw.edu/pub/RFdiffusion/12fc204edeae5b57713c5ad7dcb97d39/Base_epoch8_ckpt.pt
</pre>
3. Install NVIDIA SE3nv transformer
*Note, NVIDIA CUDA GPUs which all 3 ML models utilize are not supported for Macs with Apple Silicon chips. The following instructions are to adjust RFDiffusion to be compatible with Macs (running solely on CPU), which means all predictions will be 5-10 times slower than with GPU.*
### On Mac
- Make sure you are in the RFdiffusion directory (exit the models folder)
  <pre> cd .. </pre>
- Right after the "create conda env" step, you can rename it to rfdiff or something like that to make it clearer as we will make a few more environments
 <pre> conda rename -n OLD_ENV_NAME NEW_ENV_NAME </pre>
- Follow the "All System Architecture except ARM (Apple Silicon) Architectures" Rosetta Beta [documentation](https://sites.google.com/omsf.io/rfdiffusion/getting-started/installation?authuser=0#h.t92xhy8bjdqc) if you have an Intel chip Mac <br>
- Follow the "ARM-Based (Apple Silicon) Architectures" Rosetta Beta [documentation](https://sites.google.com/omsf.io/rfdiffusion/getting-started/installation?authuser=0#h.t92xhy8bjdqc) if you have an M1-4 chip Mac <br>
- Copy and enter the following one at a time 
<pre>pip install torch==2.5.1 torchvision==0.20.1 torchaudio==2.5.1</pre> 
<pre>pip install numpy==2.1.3 </pre>
<pre> pip install hydra-core==1.3.2 omegaconf==2.3.0 </pre>
<pre> pip install dgl==1.1.2 </pre>
<pre>pip install e3nn==0.5.1 </pre>
- Open the util_module.py file in your RFdiffusion installation (make sure the path is for your computer, if you are already in RFdiffusion you can just navigate to the rfdiffusion/util_module.py)
<pre> vi /Users/jiasquared/Desktop/Wyss/protein_design_software/RFdiffusion/rfdiffusion/util_module.py </pre>
- Press the "i" key and *INSERT* should appear at the bottom of the screen <br>
- Copy paste the following into the top of the file before the other imports: <br>
<pre> #patch for graphbolt override
import sys
import types
sys.modules['dgl.graphbolt'] = types.ModuleType('graphbolt')
try:
    from dgl import graphbolt as gb
except ImportError:
    gb = None
</pre>
- Press esc and type <pre> :wq </pre> to save and quit the file
- install additional dependencies with correct versioning
<pre> pip install torch==2.5.1 torchvision==0.20.1 torchaudio==2.5.1</pre>
<pre>pip install numpy==1.26 hydra-core==1.3.2 omegaconf==2.3.0 </pre>
<pre>pip install dgl==1.1.2+cpu -f https://data.dgl.ai/wheels/repo.html </pre>
<pre> pip install e3nn==0.5.1 se3-transformer==0.1.0</pre>

- Verify download
<pre>python -c "import torch, e3nn, dgl; print(torch.__version__, e3nn.__version__)"</pre> and should show something like this <pre>2.5.1 0.5.1</pre>

### On Windows
- Follow RFDiffusion installation instructions [here](https://github.com/RosettaCommons/RFdiffusion)

4. *Optional* Rename conda env to rfdiffusion or something you'd like 
<pre> conda rename -n SE3nv rfdiff </pre>

## 2b. Install [ProteinMPNN](https://github.com/Kuhlman-Lab/proteinmpnn)
### On Mac
1. Create conda environment called pmpnn
<pre> conda create --name pmpnn </pre>
<pre> conda activate pmpnn </pre>
2. Add CPU only pytorch ML library 
<pre>conda install pytorch torchvision torchaudio cpuonly -c pytorch </pre>
3. Ensure you are in the protein_design_software directory <pre> cd protein_design_software </pre>
4. Clone ProteinMPNN git repo
<pre> git clone https://github.com/dauparas/ProteinMPNN.git </pre>

### On Windows
1. Create conda environment called pmpnn
<pre> conda create --name pmpnn </pre>
<pre> source activate pmpnn </pre>
2. Add CPU only pytorch ML library 
<pre>conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch </pre>
3. Ensure you are in the protein_design_software directory <pre> cd protein_design_software </pre>
4. Clone ProteinMPNN git repo
<pre> git clone https://github.com/dauparas/ProteinMPNN.git </pre>

## 2c. Install [Local Colabfold](https://github.com/YoshitakaMo/localcolabfold)
This is a local, open source version of AlphaFold which does not require downloading 3 Tb of protein databases to your computer!
### On Mac
1. Ensure you are in the protein_design_software directory <pre> cd protein_design_software </pre>
2. Clone Colabfold git repo
<pre> git clone https://github.com/YoshitakaMo/localcolabfold.git </pre>
3. Follow documentation instructions on the README.md file for either Intel or Apple Silicon M chip [here](https://github.com/YoshitakaMo/localcolabfold)
4. Edit some bash configs to get this to work
- Determine if you are in bash or zsh
<pre> echo $0</pre>
- Change the following commands to bash if you are on bash 
<pre> vi ~/.zshrc </pre> 
- Press i and copy the following (with your own path) at the bottom of the document. 
<pre># >>> localcolabfold setup >>>
export PATH="/Users/jiasquared/Desktop/Wyss/protein_design_software/localcolabfold/colabfold-conda/bin:$PATH"
# <<< localcolabfold setup <<< </pre>
- Press esc and type <pre> :wq </pre> to save and quit the file
- Reset zsh
<pre >source ~/.zshrc </pre>
- Confirm that the colabfold environment is active
  <pre> which colabfold_batch </pre> which should output 
<pre> /Users/jiasquared/Desktop/Wyss/protein_design_software/localcolabfold/colabfold-conda/bin/colabfold_batch </pre>

### On Windows
1. Ensure you are in the protein_design_software directory <pre> cd protein_design_software </pre>
2. Clone Colabfold git repo
<pre> git clone https://github.com/YoshitakaMo/localcolabfold.git </pre>
3. Follow documentation instructions on the README.md file for Linux [here](https://github.com/YoshitakaMo/localcolabfold)


## 3. Install PyMol
This is a software for visualizing and analyzing the protein you designed. <br>

1. Register for a PyMol educational license with your Wyss/MIT email [here](https://pymol.org/edu/)
2. Verify your email and follow installation instructions
3. Disregard warning that license not found and will expire in 30 days... its ok

 ### Congratulations!
You now have your very own local protein design pipeline installed and ready to rumble. Please think about a mini-binder (<65 aa long) target (preferably also <= 65aa for Mac people so you don't have to wait for 1 hr to generate an output!) you would like to design for. If you do not have one, never fear! We will be going through a small example built into RFDiffusion already. See ya tomorrow for the fun stuff :)

# Workshop Day 2: Designing your own *de novo* protein!
Check out these slides on best practices and target applications protein design can tackle [here](https://hu-my.sharepoint.com/:p:/g/personal/dawningjiaxi_fu_wyss_harvard_edu/EVwylZ5jwstJlKK3unATEh4BOkJ3t_kOPiGjVQT0rVE__A?e=bCCi2G).

<img width="844" height="559" alt="Screenshot 2025-09-05 at 11 26 31 AM" src="https://github.com/user-attachments/assets/7cdafdd3-ae5d-4a92-89c7-0b2677259545" />

Now that we did all the hard work setting up the protein design infrastructure, let's apply it! <br>

# 1. Backbone design with RFDiffusion
*If you don't have a binding target, just use the design_ppi one in the example scripts built into RFdiffusion*
- Add your target structure .pdb file into a folder called input_pdbs
- Make a copy of the binder example shell script in examples 
<pre> cp ./protein_design_software/RFdiffusion/examples/design_ppi.sh workshop_binder.sh </pre>
- Edit the contig information to fit your case (residue range, length of binder, hotspot residues, change the path), for example, here I kept them as short as possible and reduced to 1 output design to run in a reasonable timeframe:
 <pre>../scripts/run_inference.py inference.output_prefix=example_outputs/design_ppi inference.input_pdb=input_pdbs/insulin_target.pdb 'contigmap.contigs=[A1-150/0 1-10]' 'ppi.hotspot_res=[A59,A83,A91]' inference.num_designs=1 denoiser.noise_scale_ca=0 denoiser.noise_scale_frame=0</pre>
- Ensure path to inference.py and input file is correct
- Change file permissions to execute shell file 
  <pre> chmod +x workshop_binder.sh </pre>
- Run shell script (which runs RFdiffusion)
<pre> ./workshop_binder.sh </pre>
- It should show something like this and take 5-10 minutes for a ~10 aa binder to generate
<img width="2372" height="355" alt="Screenshot 2025-09-10 at 3 28 47 PM" src="https://github.com/user-attachments/assets/f62b7002-89f1-4e01-8e0b-1deedc79c708" />
- Now you should have a file ending in _0.pdb in the output folder specifed in the .sh script. You can open this design up in PyMol and visualize it! Note that the sequence is all Gs. This is where ProteinMPNN comes in...
<img width="654" height="452" alt="Screenshot 2025-09-10 at 3 43 21 PM" src="https://github.com/user-attachments/assets/2c514d7c-b9a0-4a43-a286-0dba310dcd6c" />

# 2. Sequence design with ProteinMPNN

## Additional Resources
These notebooks are hosted on the Google Colab server which allows you to run protein design software on the cloud instead of locally. 
- [Interactive Notebook](https://colab.research.google.com/github/sokrypton/ColabDesign/blob/main/rf/examples/diffusion.ipynb)
- [RFDiffusion](https://colab.research.google.com/github/sokrypton/ColabDesign/blob/main/rf/examples/diffusion.ipynb)
- [Alphafold2](https://colab.research.google.com/github/sokrypton/ColabFold/blob/main/AlphaFold2.ipynb)
- [Alphafold3](https://alphafoldserver.com)
- [Colabfold](https://github.com/sokrypton/ColabFold)

