---
layout: post
title: Run IPython Remotely Using Jupyter Notebook
---

If you want to run a Python script on remote server, you can [run it through Screen or Byobu](https://yangcha.github.io/Byobu/). The only problem is that it is very slow to display the figures if the network connection is slow. The solution is to run the script in IPython remotely using Jupyter Notebook. 

IPython is an interactive commmand shell for Python. Jupyter Notebook(originally called IPython Notebook) is a web-based interactive computational environment for Python and other languages.

# Install Jupyter

A easy way to install Jupyter is to install Anaconda. Download Anaconda from [here](https://www.continuum.io/downloads). Install it on server and update it:

```bash
conda update conda
conda update anaconda
```

To run Jupyter Notebook:

```bash
jupyter notebook
```
Open `http://localhost:8888` in a web browser to connect to local Jupyter Notebook.


# Connect to Jupyter Notebook on a Remote Server

If you want to connect to Jupyter Notebook on a remote server in order to run Python scripts remotely, you can use SSH tunneling. Run the following command on a client machine:

```bash
ssh -L 8080:localhost:8888 username@server_address
```

If the client machine OS is Windows, you may install [mobaxterm](http://mobaxterm.mobatek.net/) first, then run the above command in mobaxterm local terminal. Here port number 8080 can be any number. Or if you prefer [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/), you may run the following command in Windows Command Prompt (cmd.exe) and keep cmd.exe running:

```
plink -ssh -L 8080:localhost:8888 username@server_address
```

Once SSH tunneling is established, you need to fire up the remote Jupyter Notebook by running command on remote server:

```bash
nohup jupyter notebook --no-browser > log.txt 2>&1 &
```

Or open a persistent terminal byobu on remote server, and run command:

```bash
byobu
jupyter notebook --no-browser
```

Finally, open `http://localhost:8080` in a web browser on your client machine.



