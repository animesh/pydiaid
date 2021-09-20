![Pip installation](https://github.com/MannLabs/diaid_pasef/workflows/Default%20installation%20and%20tests/badge.svg)
![GUI and PyPi releases](https://github.com/MannLabs/diaid_pasef/workflows/Publish%20on%20PyPi%20and%20release%20on%20GitHub/badge.svg)

# diAID-PASEF
An open-source Python package of the AlphaPept ecosystem from the [Mann Labs at the Max Planck Institute of Biochemistry](https://www.biochem.mpg.de/mann). To enable all hyperlinks in this document, please view it at [GitHub](https://github.com/MannLabs/diaid_pasef).

* [**About**](#about)
* [**License**](#license)
* [**Installation**](#installation)
  * [**One-click GUI**](#one-click-gui)
  * [**Pip installer**](#pip)
  * [**Developer installer**](#developer)
* [**Usage**](#usage)
  * [**GUI**](#gui)
  * [**CLI**](#cli)
  * [**Python and jupyter notebooks**](#python-and-jupyter-notebooks)
* [**Troubleshooting**](#troubleshooting)
* [**Citations**](#citations)
* [**How to contribute**](#how-to-contribute)
* [**Changelog**](#changelog)

---
## About

An open-source Python package of the AlphaPept ecosystem from the [Mann Labs at the Max Planck Institute of Biochemistry](https://www.biochem.mpg.de/mann).

---
## License

diAID-PASEF was developed by the [Mann Labs at the Max Planck Institute of Biochemistry](https://www.biochem.mpg.de/mann) and is freely available with an [Apache License](LICENSE.txt). External Python packages (available in the [requirements](requirements) folder) have their own licenses, which can be consulted on their respective websites.

---
## Installation

diAID-PASEF can be installed and used on all major operating systems (Windows, macOS and Linux).
There are three different types of installation possible:

* [**One-click GUI installer:**](#one-click-gui) Choose this installation if you only want the GUI and/or keep things as simple as possible.
* [**Pip installer:**](#pip) Choose this installation if you want to use diAID-PASEF as a Python package in an existing Python 3.8 environment (e.g. a Jupyter notebook). If needed, the GUI and CLI can be installed with pip as well.
* [**Developer installer:**](#developer) Choose this installation if you are familiar with CLI tools, [conda](https://docs.conda.io/en/latest/) and Python. This installation allows access to all available features of diAID-PASEF and even allows to modify its source code directly. Generally, the developer version of diAID-PASEF outperforms the precompiled versions which makes this the installation of choice for high-throughput experiments.

### One-click GUI

The GUI of diAID-PASEF is a completely stand-alone tool that requires no knowledge of Python or CLI tools. Click on one of the links below to download the latest release for:

* [**Windows**](https://github.com/MannLabs/diaid_pasef/releases/latest/download/diaid_pasef_gui_installer_windows.exe)
* [**macOS**](https://github.com/MannLabs/diaid_pasef/releases/latest/download/diaid_pasef_gui_installer_macos.pkg)
* [**Linux**](https://github.com/MannLabs/diaid_pasef/releases/latest/download/diaid_pasef_gui_installer_linux.deb)

Older releases remain available on the [release page](https://github.com/MannLabs/diaid_pasef/releases), but no backwards compatibility is guaranteed.

### Pip

diAID-PASEF can be installed in an existing Python 3.8 environment with a single `bash` command. *This `bash` command can also be run directly from within a Jupyter notebook by prepending it with a `!`*:

```bash
pip install diaid_pasef
```

Installing diAID-PASEF like this avoids conflicts when integrating it in other tools, as this does not enforce strict versioning of dependancies. However, if new versions of dependancies are released, they are not guaranteed to be fully compatible with diAID-PASEF. While this should only occur in rare cases where dependencies are not backwards compatible, you can always force diAID-PASEF to use dependancy versions which are known to be compatible with:

```bash
pip install "diaid_pasef[stable]"
```

NOTE: You might need to run `pip install pip==21.0` before installing diAID-PASEF like this. Also note the double quotes `"`.

For those who are really adventurous, it is also possible to directly install any branch (e.g. `@development`) with any extras (e.g. `#egg=diaid_pasef[stable,development-stable]`) from GitHub with e.g.

```bash
pip install "git+https://github.com/MannLabs/diaid_pasef.git@development#egg=diaid_pasef[stable,development-stable]"
```

### Developer

diAID-PASEF can also be installed in editable (i.e. developer) mode with a few `bash` commands. This allows to fully customize the software and even modify the source code to your specific needs. When an editable Python package is installed, its source code is stored in a transparent location of your choice. While optional, it is advised to first (create and) navigate to e.g. a general software folder:

```bash
mkdir ~/folder/where/to/install/software
cd ~/folder/where/to/install/software
```

***The following commands assume you do not perform any additional `cd` commands anymore***.

Next, download the diAID-PASEF repository from GitHub either directly or with a `git` command. This creates a new diAID-PASEF subfolder in your current directory.

```bash
git clone https://github.com/MannLabs/diaid_pasef.git
```

For any Python package, it is highly recommended to use a separate [conda virtual environment](https://docs.conda.io/en/latest/), as otherwise *dependancy conflicts can occur with already existing packages*.

```bash
conda create --name diaid_pasef python=3.8 -y
conda activate diaid_pasef
```

Finally, diAID-PASEF and all its [dependancies](requirements) need to be installed. To take advantage of all features and allow development (with the `-e` flag), this is best done by also installing the [development dependencies](requirements/requirements_development.txt) instead of only the [core dependencies](requirements/requirements.txt):

```bash
pip install -e "./diaid_pasef[development]"
```

By default this installs loose dependancies (no explicit versioning), although it is also possible to use stable dependencies (e.g. `pip install -e "./diaid_pasef[stable,development-stable]"`).

***By using the editable flag `-e`, all modifications to the [diAID-PASEF source code folder](diaid_pasef) are directly reflected when running diAID-PASEF. Note that the diAID-PASEF folder cannot be moved and/or renamed if an editable version is installed.***

---
## Usage

There are three ways to use diAID-PASEF:

* [**GUI**](#gui)
* [**CLI**](#cli)
* [**Python**](#python-and-jupyter-notebooks)

NOTE: The first time you use a fresh installation of diAID-PASEF, it is often quite slow because some functions might still need compilation on your local operating system and architecture. Subsequent use should be a lot faster.

### GUI

If the GUI was not installed through a one-click GUI installer, it can be activate with the following `bash` command:

```bash
diaid_pasef gui
```

Note that this needs to be prepended with a `!` when you want to run this from within a Jupyter notebook. When the command is run directly from the command-line, make sure you use the right environment (activate it with e.g. `conda activate diaid_pasef` or set an alias to the binary executable (can be obtained with `where diaid_pasef` or `which diaid_pasef`)).

### CLI

The CLI can be run with the following command (after activating the `conda` environment with `conda activate diaid_pasef` or if an alias was set to the diaid_pasef executable):

```bash
diaid_pasef -h
```

It is possible to get help about each function and their (required) parameters by using the `-h` flag.

### Python and Jupyter notebooks

diAID-PASEF can be imported as a Python package into any Python script or notebook with the command `import diaid_pasef`.

A brief [Jupyter notebook tutorial](nbs/tutorial.ipynb) on how to use the API is also present in the [nbs folder](nbs).

---
## Troubleshooting

In case of issues, check out the following:

* [Issues](https://github.com/MannLabs/diaid_pasef/issues): Try a few different search terms to find out if a similar problem has been encountered before
* [Discussions](https://github.com/MannLabs/diaid_pasef/discussions): Check if your problem or feature requests has been discussed before.

---
## Citations

There are currently no plans to draft a manuscript.

---
## How to contribute

If you like this software, you can give us a [star](https://github.com/MannLabs/diaid_pasef/stargazers) to boost our visibility! All direct contributions are also welcome. Feel free to post a new [issue](https://github.com/MannLabs/diaid_pasef/issues) or clone the repository and create a [pull request](https://github.com/MannLabs/diaid_pasef/pulls) with a new branch. For an even more interactive participation, check out the [discussions](https://github.com/MannLabs/diaid_pasef/discussions) and the [the Contributors License Agreement](misc/CLA.md).

---
## Changelog

See the [HISTORY.md](HISTORY.md) for a full overview of the changes made in each version.
