# Wyss Computational Protein Design Workshops
Welcome to the Wyss Institute protein design workshops! We are covering the basics computational protein design, current workflows and de novo design strategies. This is geared towards experimentalists who work in protein engineering who'd like to learn about the newest machine learning driven protein design tools. No prior experience needed!

<b> What to take away from this workshop: </b>
1. Understanding of cutting-edge machine learning models for protein design
2. Tools for the modern protein design pipeline downloaded on your computer
3. A *de novo* mini-binder protein you designed! 

# Before the Workshop 
## Hardware requirements 
These following items are required for running software for this workshop!
1. Laptop or PC
2. 10-20GB of available storage
3. Terminal authorization 

## Linux Command Line Cheat Sheet
Linux is used to navigate and download the necessary software through terminal on both Mac and Windows for this workshop. Basic familiarity with these key commands will be very helpful for this workshop and for computational work in general (we will use them throughout the workshop, no need to memorize them!):

| Linux/VIM Command        | Function                                                |
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
 

<b>Helpful Resources:</b><br>
- [Here](https://www.geeksforgeeks.org/linux-unix/linux-commands-cheat-sheet/) is a comprehensive cheat sheet for reference <br>
- [Here](https://gitlab.com/slackermedia/bashcrawl) is a game that helps you build up your Linux muscle memory! <br>


# Workshop Day 1 - Downloading Software (how fun!)
# Installing Dependencies
<b> A few packages need to be installed before we can download and run the 3 machine learning models which comprise the protein design pipeline (RFDiffusion, ProteinMPNN, Alphafold): </b>

## On Mac
1. Install [anaconda distributor](https://www.anaconda.com/download)
- Follow the conda instructions for Mac
- Open Terminal 
- Confirm conda has been properly installed by typing <pre> conda --version </pre> and enter
2. Install homebrew
- Navigate to directory where you want to work
  <pre> cd /Users/jiasquared/Desktop/Wyss </pre>
- Make a new folder where you want to keep software
-   <pre> mkdir protein_design_software && cd protein_design_software </pre>
- Type  <pre> /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" </pre> and enter
- Confirm homebrew has been properly installed by typing <pre> brew --version </pre> and enter
2. Install wget
- Type <pre> brew install wget </pre> and enter

## On Windows
1. Install [anaconda distributor](https://www.anaconda.com/download)
- follow the conda instructions for Windows
2. Install wget via [GNU](https://gnuwin32.sourceforge.net/packages/wget.htm)
- Make and enter new directory 
 <pre> mkdir protein_design_software && cd protein_design_software </pre>

# Install Machine Learning Models 
## Install RFDiffusion
1. Ensure you are in the protein_design_software directory <pre> cd protein_design_software </pre>
2. Clone RFdiffusion git repo
<pre> git clone https://github.com/RosettaCommons/RFdiffusion.git </pre>
2. Install model weights (this step will take ~5 minutes)
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
*Note, NVIDIA CUDA GPUS are not supported for Macs. The following instructions are to adjust RFDiffusion to be compatible with MacOS, which means running solely on CPU, which is slower than with GPU.*
### On Mac
- Ensure you are in the RFdiffusion directory <pre> cd RFdiffusion </pre>
<pre> conda env create -f env/SE3nv.yml </pre>
<pre> rm env/SE3nv.yml </pre>
<pre> vi env/SE3nv.yml  </pre>
- A new file will open up. Press the "i" key and *INSERT* should appear at the bottom of the screen <br>
- Copy the following code into the file:
<pre>
name: SE3nv
channels:
  - conda-forge
  - defaults
dependencies:
  - python=3.9
  - pip
  - numpy
  - scipy
  - pytorch
  - torchvision
  - torchaudio
  - pip:
      - dgl   
</pre>
- Press esc and type <pre> :wq </pre> to save and quit the file
<pre> conda activate SE3nv </pre>
- The command line should look like this when you are in the SE3nv environment
<img width="319" height="17" alt="Screenshot 2025-09-02 at 11 30 04 AM" src="https://github.com/user-attachments/assets/fc1f19fa-3a16-4b2c-89ae-8ceb8aa56abc" />
<pre>cd env/SE3Transformer</pre>
<pre>pip install --no-cache-dir -r requirements.txt</pre>
<pre>python setup.py install</pre>
<pre> cd ../..</pre>
<pre> pip install -e . </pre>

### On Windows
- Ensure you are in the RFdiffusion directory <pre> cd RFdiffusion </pre>
<pre> conda env create -f env/SE3nv.yml </pre>
<pre> conda activate SE3nv </pre>
- The command line should look like this when you are in the SE3nv environment
<img width="319" height="17" alt="Screenshot 2025-09-02 at 11 30 04 AM" src="https://github.com/user-attachments/assets/fc1f19fa-3a16-4b2c-89ae-8ceb8aa56abc" />
<pre>cd env/SE3Transformer</pre>
<pre>pip install --no-cache-dir -r requirements.txt</pre>
<pre>python setup.py install</pre>
<pre> cd ../..</pre>
<pre> pip install -e . </pre>

## Install ProteinMPNN
1. Ensure you are in the protein_design_software directory <pre> cd protein_design_software </pre>
2. Clone ProteinMPNN git repo
<pre> git clone https://github.com/dauparas/ProteinMPNN.git </pre>

## Install Local Colabfold
This is a local, open source version of AlphaFold which does not require downloading 3 Tb of protein databases to your computer!
### On Mac
1. Ensure you are in the protein_design_software directory <pre> cd protein_design_software </pre>
2. Install cmake
<pre> brew install cmake </pre>
3. Clone Colabfold git repo
<pre> git clone https://github.com/YoshitakaMo/localcolabfold.git </pre>

### On Windows
1. Ensure you are in the protein_design_software directory <pre> cd protein_design_software </pre>
2. Clone Colabfold git repo
<pre> git clone https://github.com/YoshitakaMo/localcolabfold.git </pre>

# Workshop Day 2: Designing your own *de novo* protein!

## [Theory Presentation](https://docs.google.com/presentation/d/1kaDj9Jek2pOlp9u5BuWBrlPiCu8cP5Phw2dSMDV3gFA/edit?usp=sharing)
This is a short presentation on the theory behind designing proteins from scratch.

## Additional Resources
These notebooks are hosted on the Google Colab server which allows you to run protein design software on the cloud instead of locally. 
- [Interactive Notebook](https://colab.research.google.com/github/sokrypton/ColabDesign/blob/main/rf/examples/diffusion.ipynb)
- [RFDiffusion](https://colab.research.google.com/github/sokrypton/ColabDesign/blob/main/rf/examples/diffusion.ipynb)
- [Alphafold2](https://colab.research.google.com/github/sokrypton/ColabFold/blob/main/AlphaFold2.ipynb)
- [Alphafold3](https://alphafoldserver.com)
- [Colabfold](https://github.com/sokrypton/ColabFold)

