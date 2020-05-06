# Python Remote

Grasshopper's python interface is called [Iron Python](https://ironpython.net/) which is not native python. This means it's difficult to use python libraries such as `numpy` and `scipy` which are super useful for engineers.

In our actual product, we will have **native python 3** available in the tool so you don't have to deal with all this nonsense but in the meantime, the python remote integration is a good work around.

## How Python Remote Works

It uses Anaconda to create a virtual python environment in Grasshopper. Any python2.x libraries can be added to this environment. The only limitation is including python 3 libraries. If you need python 3 libraries, contact Oliver on Slack as he has done this before.

## Installing Python Remote

The steps below are for Windows. If you have a Mac, please contact Eu Chian on Slack.

The python environment will have many common libraries installed already such as `numpy`, `scipy`, `matplotlib` and `aeropy` which should be sufficient for most of us. If you'd like to add a library which is not already installed, go to the last section of this README.

1. Install Anaconda ([Windows](https://repo.anaconda.com/archive/Anaconda3-2020.02-Windows-x86_64.exe)).
2. Follow the install instructions. Near the end of the install, make sure to check the option about adding Anaconda to your Windows path.
3. Download `rhinoremote.yml`.
4. In your Windows search bar, open Anaconda Navigator.
5. Select `Environments` on the left panel, click on `Import`, click on the file icon and select the `rhinoremote.yml` file. Once the import is successful, you can scroll through to see what libraries are installed.
6. Close Anaconda Navigator and download and unzip `gh-python-remote.zip`.
7. Go to Grasshopper, `File > Special Folders > User Object Folder` and paste the gh-python-remote folder in this directory.
8. Restart Rhino/grasshopper.

## Running Python Remote

1. Download and open the python remote template, `template-python-remote.gh`.
2. Copy and paste the `GHPythonRemote` block with its inputs/outputs into your own workflow.
3. When you're ready to start the environment, double click on the toggle from `false` to `true`. This will open a separate command prompt window **which you shouldnt close**. If you toggle it from `true` to `false`, this window will close automatically.

## Import Python Libraries In Grasshopper

In the template for running python remote, there's a panel connected to the `modules` input which has the list of python libraries that's activated for use in Grasshopper.

If you want to add more libraries (that has already been installed into your `rhinoremote` environment), double-click on the panel and type in your additional libraries.

**Note:** You'll notice that some libraries are called twice such as `scipy` and `scipy.interpolate`. This means that if you want to access any level of sub-libraries, you need to include it as part of the list.

On how to actually call these python libraries in the grasshopper python interface, see the template.

## Installing Additional Libraries

If you'd like to install additional libraries that are not already in the environment:

1. In your Windows search bar, open Anaconda Prompt (rhinoremote).
2. Either use `conda install <your library>` or `pip install <your library>`.
3. Restart Rhino/grasshopper.

