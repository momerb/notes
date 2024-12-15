download [homebrew](https://brew.sh) <br><br>

```other
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

<br>



download 'miniforge3' for conda 

```other
brew install miniforge
```

<br>

or alternatively from [Download Miniforge3](https://github.com/conda-forge/miniforge/blob/main/README.md) and install 'miniforge3' into home directory <br><br>


```other
chmod +x ~/Downloads/Miniforge3-MacOSX-arm64.sh
sh ~/Downloads/Miniforge3-MacOSX-arm64.sh
source ~/miniforge3/bin/activate
```

<br>
download 'Visual Studio Code' <br><br>
close the current terminal <br><br>
open the terminal in VS Code from Terminal -> New Terminal <br><br>
create a directory to setup an environment <br><br>

```other
mkdir _DIRECTORYNAME_
cd _DIRECTORYNAME_
```

<br>
now within the current directory _DIRECTORYNAME_ create an environment <br><br>

```other
conda create -n _ENVIRONMENTNAME_ python=3.11 numpy pandas datasets matlotlib scikit-learn tqdm anaconda::ipykernel
```

Alternatively, you can also do the following in order to save the env folder within the working directory instead of the .conda default path:

```other
conda create -p ./env python=3.11 numpy pandas matplotlib anaconda::ipykernel
```



<br>

```other
conda install pytorch::pytorch torchvision torchaudio -c pytorch
```

<br>

```other
conda activate _ENVIRONMENTNAME_
```

<br>
CMD + SHIFT + P -> Reload Window <br><br>
CMD + SHIFT + P -> Select Interpreter <br><br>

```other
conda list
```

<br>

```other
conda env list
```

<br>

```python
import torch
import numpy as np
import pandas as pd
import sklearn
import matplotlib.pyplot as plt

print(f"PyTorch version: {torch.__version__}")

# Check PyTorch has access to MPS (Metal Performance Shader, Apple's GPU architecture)
print(f"Is MPS (Metal Performance Shader) built? {torch.backends.mps.is_built()}")
print(f"Is MPS available? {torch.backends.mps.is_available()}")

# Set the device      
device = "mps" if torch.backends.mps.is_available() else "cpu"
print(f"Using device: {device}")
```

<br>

```other
PyTorch version: 1.12.0
Is MPS (Metal Performance Shader) built? True
Is MPS available? True
Using device: mps
```

<br>
to run data/models on an Apple Silicon GPU, use the PyTorch device name `"mps"` with `.to("mps")`. MPS stands for *Metal Performance Shaders*, [Metal is Apple's GPU framework](https://developer.apple.com/metal/). <br><br>

```python
import torch

# Set the device
device = "mps" if torch.backends.mps.is_available() else "cpu"

# Create data and send it to the device
x = torch.rand(size=(3, 4)).to(device)
x
```
<br>

install git <br>

```other
brew install git
```
<br>

```other
git config --global user.name NAME
git config --globar user.email EMAIL
git config --global init.default branch main
```
<br>

open the directory that needs to tracked <br>

```other
git init
```
<br>

```other
git status
```

<br>

To create a .gitignore file and at the same time add "*.txt" files to .gitignore:

```other
echo "*.txt" > .gitignore
```

<br>

To update the already present .gitignore file and add "*.csv" file to it:

```other
echo "*.csv" >> .gitignore
```

<br>

<br>

To remove __pycache__/ files from all the subfolders in the current folder

```other
echo "**/__pycache__/" > .gitignore
```

<br>

Note: One ">" means to update the current .gitignore file, however two ">>" means overwrite the .gitignore file if it exists

<br>

To add all files to track:
```other
git add --all
```

To commit all files from tracking:
```other
git commit -m "MESSAGE"
```

To add and commit the files at the same time:
```other
git commit -a -m "..."
```
<br>

```other
git remote add origin https://github.com/momerb/temporary.git
git branch -M main
git push -u origin main
```

!!!Git LFS is not very useful in the long run!!!

```other
brew install git-lfs
```

In user account:
```
git lfs install
```

In the required environment/repository:
```other
git lfs track "*.csv"
git add .gitattributes
```

```bash
git add file.csv
git commit -m "Message"
git push origin main
```

<br>

##### How to work with a Branch in git?

```bash
git branch
git branch BRANCH_NAME # to create a branch
git checkout BRANCH_NAME | git switch BRANCH_NAME # to switch to the branch
# make changes in this branch ...
git add --all
git commit -m "Message"
git push origin BRANCH_NAME # to upload to the remote repo
git checkout main | git switch main # switch to main
git branch # confirm if you are in the main branch
git pull origin main # fetch the newest version from the origin branch of the remote repo
git merge BRANCH_NAME # merge the newly created branch to the main branch
git status # check the status if everything is okay
git push origin main # to upload the current main branch to the origin branch of the remote repo
git branch -d BRANCH_NAME #  to delete the newly created branch from the local git -D instead for force delete
git push origin --delete BRANCH_NAME # to also delete this branch from the remote repo
```
<<<<<<< HEAD
=======

<br>
How to pull when there is a conflict between origin and main

```bash
git pull --rebase # Add the changes from the origin to main in an order as they were made
git pull --no-rebase # Add the changed from the origin to main BUT at the end of the main
```
>>>>>>> aba577e (pull)
