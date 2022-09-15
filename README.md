##### Contact for Issues/Updates
Email: teamraar@gmail.com \
Author: Ranadeep Singh \
Github: https://github.com/ranadeepsingh 


# Steps to install pytorch for Arm Macs:
![image info](https://upload.wikimedia.org/wikipedia/commons/9/96/Pytorch_logo.png)
### Prerequisite:
* Have Arm based Mac
* MacOS 12.3+

### Run the following commands all in bash terminal:

1. Install Miniforge
    There are many ways to do this, but the one that worked for me was to download the latest package for OSX arm64 architecture from [Miniforge Github](https://github.com/conda-forge/miniforge). The downloaded file is expected to be: Miniforge3-MacOSX-arm64.sh 


    Install Miniforge using:
    ```
    bash <path_to_downloaded_file>/Miniforge3-MacOSX-arm64.sh
    # Accept all default settings
    ```
    Verify you have it install by running:
    ```
    which python
    ```
    Expected return:
    **/Users/<your_username>/miniforge3/bin/python**

2. Create new virtual environment using miniforge (comands are similar to conda) and activate it
    ```
    conda create --name <venv_name>
    conda activate <venv_name>
    ```

3. Verify your python is for compiled for arm architecture by running:
    ```
    python -c "import platform; print(platform.machine())"
    ```
    Expected return: \
    **arm64**

4. Install Pytorch Nighly (Experimental version) using:
    ```
    python -m pip install --pre torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/nightly/cpu
    ```

5. To verify if pytorch for Mac has been downloaded run:
    ```
    python -c "import torch; print(torch.backends.mps.is_available())"
    ```
    Expected return: \
    **True**

### Congratulations! Now leverage your Mac's GPUs for machine learning by replacing device as "cuda"/"cpu" with "mps"
```
device = torch.device("mps")
```
![image info](https://media.makeameme.org/created/the-power-is-5b5a12.jpg)

**Running ipynb files in VS Code**
1. To link your virtual environment with jupyter notebook:
```
conda install -c anaconda ipykernel
python -m ipykernel install --user --name=<venv_name>
```
2. To run ipynb Jupyter Notebooks in VS Code, install the "Jupyter" Extension.

3. If your ipynb Kernel keeps failing in VS Code, [clean uninstall your VS Code](https://code.visualstudio.com/docs/setup/uninstall#_clean-uninstall) and reinstall it.