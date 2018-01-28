MVA - Algorithms for Speech and NLP TD
======================================

## Contact Information
For any question/request related to this course, please send an email to this address: mva.speech.language@gmail.com

## TD
For this TD you will need python-anaconda, or virtualbox.
If you decide to use the virtual machine, please install it before coming to class, and try it out at least once before coming to class, as it may be slow.
If you encounter any problem, you can contact us and we can help you debug it.

# Dataset

Download the Google Speech Commands dataset here:
http://download.tensorflow.org/data/speech_commands_v0.01.tar.gz
and unpack it.

## Conda
For this TD, you will only need a few python packages.
### Packages installation
To install the necessary packages, download the file name TD1_requirements.yml, and launch, in command line,
```
    conda env create --file TD_1_requirements.yml
```
which creates an environment with the necessary packages. To activate this environnment, you can do
```
    source activate TD_1
```

Then, you still need one package for that environment,
```
    git clone https://github.com/bootphon/spectral.git
    cd spectral
    source activate TD_1 # if not already done
    python setup.py build
    python setup.py install
```

Install a jupyter kernel for this environment
```
python -m ipykernel install --user --name TD_1 --display-name "TD_1"
```
Download the "Speech_Commands.ipynb" notebook. Run Jupyter:
```
jupyter notebook --notebook-dir=~/
```
Then you can load the notebook, and select the kernel "TD_1". "test_tp1.ipynb" just allows you to test that your environment contains all needed packages.

## Virtual Machine
On this machine you will find all the necessary tools needed to complete the TD.
To download it, click [here](http://coml.lscp.ens.fr/owncloud/index.php/s/l52gd5FSaqdcLR2) to retrieve the .ova file, which you can use with Virtual Box.
The password to retrieve the file is "MVA".

### How to load the .ova
To load the .ova and start using your virtual machine, simply open virtualbox, click on *import appliance*, point to the .ova file, and you're ready to go.
Once the machine is ready, you can login with id:vagrant and password:vagrant.

### Load conda environment
To start using the pre installed tools in the virtual machine,
```
    source activate TD_1
    cd spectral
    python setup.py build
    python setup.py install
```

### Shared Folder

You can set up a shared folder between you personal computer and the virtual machine following [these instructions](https://www.techrepublic.com/article/how-to-share-folders-between-guest-and-host-in-virtualbox/).
