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

```other
git add file.csv
git commit -m "Message"
git push origin main
```

To document the dependencies in an environment.yml file using conda

```other
conda env export > environment.yml
```

Find the path of the command: (This should be the folder where the command exists not the command file itself)
```sh
which code
```

It should show something like this:
```sh
/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code
```

Just take the part until bis and add :$PATH as the end so it looks something like this:

```sh
PATH="/Applications/Visual Studio Code.app/Contents/Resources/app/bin:$PATH"
```

Type the following command to open your .zshrc file in the nano text editor:
```sh
nano ~/.zshrc
```

In the nano editor, navigate to the bottom of the file using the arrow keys.
Add the following line at the end of the file: (This is not a command but a text to add in the path file in order to make it executable)

```sh
export PATH="/Applications/Visual Studio Code.app/Contents/Resources/app/bin:$PATH"
```

To save the changes, press Ctrl + O (that's the letter "O", not zero).
Press Enter to confirm the filename (which should be .zshrc).
To exit nano, press Ctrl + X

To make the changes take effect immediately, type the following command in the Terminal:
```sh
source ~/.zshrc
```
This command reloads your .zshrc file, applying the changes you made.

Check if the command is successfully installed in the path:
```sh
code --version
```

#FOR WINDOWS

Install Conda using Windows PowerShell (Administrator)

```PowerShell
curl https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe -o miniconda.exe
Start-Process -FilePath ".\miniconda.exe" -ArgumentList "/S" -Wait
del miniconda.exe
``` 

Check:
```PowerShell
conda --version
```

If it does not work, then it needs to be added in PATH manually:
Suchen -> "Umgebungsvariablen" -> Erweitert -> Umgebungsvariablen -> "Benutzervariablen für "BenutzerName" -> Path -> Bearbeiten -> 

```
1. C:\Users\<BenutzerName>\Miniconda3\Scripts\
2. C:\Users\<BenutzerName>\Miniconda3\condabin\
```

