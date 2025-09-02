# Wyss-Institute-Protein-Design-Workshops
Workshop series at the Wyss Institute covering the basics computational protein design, current workflows and de novo design strategies. 




# Linux Command Line Cheat Sheet
To navigate in terminal on either mac or windows, these are some key Linux commands which will be used throughout this workshop and are just helpful to know:

*insert table*



Here is a comprehensive cheat sheet for reference! https://www.geeksforgeeks.org/linux-unix/linux-commands-cheat-sheet/
And here is a game that helps you build up your Linux muscle memory! https://gitlab.com/slackermedia/bashcrawl

## Running Locally

# Install dependencies
1. install anaconda distributor
https://www.anaconda.com/download


# On Mac
1. install homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
2. install wget
brew install wget

# On Windows
1. install wget via gnu https://gnuwin32.sourceforge.net/packages/wget.htm

2. 

# Install RFDiffusion
1. clone repo
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





## Running in Notebooks
### [RFDiffusion](https://colab.research.google.com/github/sokrypton/ColabDesign/blob/main/rf/examples/diffusion.ipynb)

### [Alphafold2](https://colab.research.google.com/github/sokrypton/ColabFold/blob/main/AlphaFold2.ipynb)

### [Alphafold3](https://alphafoldserver.com)

### Colabfold
ColabFold is an open source collaboration from Ovchinikov lab which is an open source alternative to alphafold. The repo is a great resource which includes links to multiple [notebooks](https://github.com/sokrypton/ColabFold)

to get updated version of docs, pull files from github(app) and open them in vscode. 
hello this is a test.

