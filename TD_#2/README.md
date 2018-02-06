MVA - Algorithms for Speech and NLP TD
======================================

## Contact Information
For any question/request related to this course, please send an email to this address: mva.speech.language@gmail.com

## Handing the assignment

Send your notebook with your modifications, printed results and comments (in markdown cells) to mva.speech.language@gmail.com before the next class on Monday, February 12th. Please start the title of your email with "TP2".

## TD
For this TD you will need virtualbox. We *strongly* advise to use the virtualbox
to avoid the installation issues due to C++ bindings with Python. Please download the [virtual machine](http://coml.lscp.ens.fr/owncloud/index.php/s/uZHjspiB3k2sFHq/download) ([Dropbox mirror](https://www.dropbox.com/s/a9lb08sil6p0aov/TD2_MVA_SL.ova?dl=0) )
If you encounter any problem, you can contact us and we can help you debug it.

## Virtual Machine
On this machine you will find all the necessary tools needed to complete the TD.
The Virtual Machine is big, it has a size of 6.5 Go, so the download may be slow.

### How to load the .ova
To load the .ova and start using your virtual machine, simply open virtualbox, click on *import appliance*, point to the .ova file, and you're ready to go.
Once the machine is ready, you can login with id:Ubuntu and password:MVA2018.

One you are logged, you need to log as a Super User to the other user 'vagrant'. To do so, open a terminal :
- `su vagrant`
- Enter the password 'MVA2018'
- Type in the terminal `cd`
- You can launch the Jupyter kernel with all the loaded libraries with command `jupyter notebook`
- In `/home/vagrant` there are already the two necessary jupyter notebooks for the Practical work, one used for the slides, one for the 3 exercices.
- Open Firefox and enter the adress `localhost:8888`

If you have issues to execute any cell for the `Figure for slides` notebook, you can contact us and we can help you debug it.



# For the Kaldi/Abkhazia part


Once your decoding is finished, you will end up with a folder with a lot of files:
```
 decode.log        # abkhazia's log
 graph/            # the decoding graphs
 lat.1.gz
 lat.2.gz          # the lattices
 log/              # Kaldi's logs
 meta.txt
 num_jobs
 recipe/           # Some Kaldi conf files
 scoring_kaldi/    # the folder in which you will find the decoding
 trans.1
 trans.2           # the Fmllr transform
 wer_*             # A summary of the Word Error Rate for some parameters
```
and if you go inside `scoring_kaldi`, you will find:
```
 best_wer          # A summary telling you which decoding gave you the best Word Error Rate
 log/              
 penalty_*/        # The decoded transcriptions for different penalties and parameters
 test_filt.txt     
 wer_details/      # Details about the Word Error rate (per speaker WER, per utterance WER etc...)
```
If you look in best_wer, you will find which transcription is the best. For example, if my best_wer says :
```
  %WER 1.57 [ 50 / 3192, 1 ins, 32 del, 17 sub ] /home/vagrant/models/am_trisa_mot/decode_fmllr/wer_9_0.0
```
to find the best transcription, I need to look in penalty_0.0/ (wer_9_**0.0**)  at file 9.txt (wer_**9**_0.0).


## Installation without the VM: ** warning **
We do not support local installation outside the VM for each personal computer.

### Abkhazia
On the website, there is everything documented thoroughly : [here](https://github.com/bootphon/abkhazia)

### Openfst/Pywrapfst
Install Openfst/Pywrapfst on local because Abkhazia/Kaldi uses another version of Openfst which does not support python wrapper.

```
mkdir -p openfst/build
cd openfst
wget http://www.openfst.org/twiki/pub/FST/FstDownload/openfst-1.6.1.tar.gz
tar -xzf openfst-1.6.1.tar.gz
cd openfst-1.6.1/
./configure --prefix=/home/${user}/openfst/build  --enable-far
make
sudo make install
```

Then

```
pip install openfst --global-option=build_ext --global-option="-I/home/${user}/openfst/build/include" --global-option="-L/home/${user}/openfst/build/lib"
```

### Reported Issues with the Virtual machine

- Thanks **Budin Joseph**: If you have issues due to shared folder path between host and guest, go to configuration, 'shared folders' tab, and disable the default shared folder.

- Thanks ** Marin Scalbert**: If you have a Mac, you might encouter network issues like this one:

```
Could not start the machine old_vm because the following physical network interfaces were not found:

vboxnet0 (adapter 2), vboxnet0 (adapter 3)
```

You should change network2 and network3 option from 'network host' to 'no host'.
