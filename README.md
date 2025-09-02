# Wyss Institute Protein Design Workshops
Welcome to the Wyss Institute protein design workshops covering the basics computational protein design, current workflows and de novo design strategies. 

# Workshop hardware requirements 
Before we can start, these following items are required for running software for this workshop!
1. Laptop or PC
2. ~70GB of available storage
3. Terminal authorization 

# Linux Command Line Cheat Sheet
Linux is used to navigate and download the necessary software through terminal on both Mac and Windows for this workshop. These are some key  commands which will be used throughout this workshop and for computational work in general:

*insert table*

[Here](https://www.geeksforgeeks.org/linux-unix/linux-commands-cheat-sheet/) is a comprehensive cheat sheet for reference 
And [here](https://gitlab.com/slackermedia/bashcrawl) is a game that helps you build up your Linux muscle memory! 

# Install Dependencies

Before downloading the 3 machine learning models which comprise the protein design pipeline (RFDiffusion, ProteinMPNN, Alphafold), a few packages need to be downloaded first:


## On Mac
1. Install [anaconda distributor](https://www.anaconda.com/download)
- follow the conda instructions for Mac
2. Install homebrew
- Open Terminal
- Navigate to folder where you want to store the software
  <pre> ``` cd /Users/jiasquared/Desktop/Wyss ``` </pre>
- Make and enter new directory
  <pre> ```mkdir protein_design_software && cd protein_design_software ``` </pre>
- Type   <pre> ```/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" ``` </pre> and enter
2. Install wget
- Type <pre> ```brew install wget``` </pre> and enter

## On Windows
1. Install [anaconda distributor](https://www.anaconda.com/download)
- follow the conda instructions for Windows
2. Install wget via [GNU](https://gnuwin32.sourceforge.net/packages/wget.htm)
- Make and enter new directory 
 <pre> ```mkdir protein_design_software && cd protein_design_software ``` </pre>


# Install RFDiffusion
1. Clone repo
git clone https://github.com/RosettaCommons/RFdiffusion.git
2. install model weights

cd RFdiffusion
mkdir models && cd models
wget http://files.ipd.uw.edu/pub/RFdiffusion/6f5902ac237024bdd0c176cb93063dc4/Base_ckpt.pt
wget http://files.ipd.uw.edu/pub/RFdiffusion/e29311f6f1bf1af907f9ef9f44b8328b/Complex_base_ckpt.pt
wget http://files.ipd.uw.edu/pub/RFdiffusion/60f09a193fb5e5ccdc4980417708dbab/Complex_Fold_base_ckpt.pt
wget http://files.ipd.uw.edu/pub/RFdiffusion/74f51cfb8b440f50d70878e05361d8f0/InpaintSeq_ckpt.pt
wget http://files.ipd.uw.edu/pub/RFdiffusion/76d00716416567174cdb7ca96e208296/InpaintSeq_Fold_ckpt.pt
wget http://files.ipd.uw.edu/pub/RFdiffusion/5532d2e1f3a4738decd58b19d633b3c3/ActiveSite_ckpt.pt
wget http://files.ipd.uw.edu/pub/RFdiffusion/12fc204edeae5b57713c5ad7dcb97d39/Base_epoch8_ckpt.pt

3. install nvidia se-3 transformer

*Note for Macs, NVIDIA CUDA is not supported after Catalina. You must adjust the yml file in the following way to be compatible*

vi env/SE3nv.yml
press i,*INSERT* should appear at the bottom of the screen 
edit the file to look like this:

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
      - dgl   # CPU-only DGL
press esc and type :wq to save and quit the file 
conda activate SE3nv, command line should look like this when you are in the SE3nv environment
<img width="319" height="17" alt="Screenshot 2025-09-02 at 11 30 04 AM" src="https://github.com/user-attachments/assets/fc1f19fa-3a16-4b2c-89ae-8ceb8aa56abc" />


# Install ProteinMPNN
git clone https://github.com/dauparas/ProteinMPNN.git

# Install Local Colabfold
brew install wget cmake
git clone https://github.com/YoshitakaMo/localcolabfold.git





## Running in Notebooks
### [RFDiffusion](https://colab.research.google.com/github/sokrypton/ColabDesign/blob/main/rf/examples/diffusion.ipynb)

### [Alphafold2](https://colab.research.google.com/github/sokrypton/ColabFold/blob/main/AlphaFold2.ipynb)

### [Alphafold3](https://alphafoldserver.com)

### Colabfold
ColabFold is an open source collaboration from Ovchinikov lab which is an open source alternative to alphafold. The repo is a great resource which includes links to multiple [notebooks](https://github.com/sokrypton/ColabFold)

to get updated version of docs, pull files from github(app) and open them in vscode. 
hello this is a test.

