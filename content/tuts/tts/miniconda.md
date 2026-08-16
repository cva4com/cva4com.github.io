---
linkTitle: Miniconda
title: Installing Miniconda
weight: 17
prev: /tts
# next: /tts/kokoro
cascade:
  type: docs
tags:
  - conda
  - Miniconda
  - Anaconda
---

## What Is Miniconda?

Miniconda is a free minimal installer for Conda. It is a smaller alternative to Anaconda. It includes Python, Conda, and essential dependencies.

With Miniconda, you can create isolated environments. This helps avoid conflicts between different projects. It is ideal for developers who need flexibility.


## Install Miniconda on Windows

{{< youtube AgnAs0nPEVg >}}

To install Miniconda on Windows, follow these 3 main steps: download the installer, run the setup wizard, and verify the installation via the command line.


### Step 1. Download the Official Installer

1. Navigate to [anaconda.com/download](https://www.anaconda.com/download), register with Anaconda or [Skip Registration](https://www.anaconda.com/download/success?reg=skipped)

<img src="/images/2026/screenshot-miniconda-01-download-page.png" style="width: 65%; height: auto;" alt="Download page">


2. Choose Your Download

For windows select **Windows 64-Bit Graphical Installer** under Miniconda.

<img src="/images/2026/screenshot-miniconda-02-download-page.png" style="width: 65%; height: auto;" alt="Choose Your Download">

Direct link: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe


### Step 2. Run the Installation Wizard

3. Go to your Downloads folder and double-click the `.exe` installer to launch.

<img src="/images/2026/screenshot-miniconda-03-download-file.png" style="width: 50%; height: auto;" alt="Start the installer">


4. Click **Next**.

<img src="/images/2026/screenshot-miniconda-04-execute.png" style="width: 50%; height: auto;" alt="Execute installer">


5. Read through [Miniconda’s End User License Agreement (EULA)](https://www.anaconda.com/legal/terms/miniconda) and select **I Agree** to agree to the terms. You can view [Anaconda’s Terms of Service (TOS)](https://www.anaconda.com/legal).

<img src="/images/2026/screenshot-miniconda-05-agree.png" style="width: 50%; height: auto;" alt="Terms of Service">


6. Select an installation option

- **Just Me (Recommended)**: Install only for your current Windows user account. This prevents administrative permission issues.
- **All Users**: Install for all users accounts on the computer (requires Windows Administrator privileges).

<img src="/images/2026/screenshot-miniconda-06-justme.png" style="width: 50%; height: auto;" alt="Installation option">

Select **Next**.


7. Select a destination folder to install Miniconda, then select **Next**.

<img src="/images/2026/screenshot-miniconda-07-installfolder.png" style="width: 50%; height: auto;" alt="Installation option">

Anaconda [recommends](https://www.anaconda.com/docs/getting-started/working-with-conda/reference/faq#in-what-folder-should-i-install-anaconda-on-windows) installing Miniconda in a directory with no spaces or special characters to avoid potential compatibility issues with open-source tools.


8. Customize your installation options

- **Create shortcuts**: Creates Start Menu shortcuts for the Anaconda Prompt packages. Deselecting this option skips creating these shortcuts.
- **Add Miniconda3 to my PATH environment variable**: Adds the path that contains the conda binaries to your PATH environment variable. <span style="color:red">Anaconda does not recommend selecting this option.</span>.
- **Register Miniconda3 as my default Python 3.14**: Selected by default. Registers the Python package in this install as the default Python for programs like VSCode, PyCharm, and so on.
- **Clear the package cache upon completion**: Runs `conda clean --all --force-pkgs-dirs` after the install finishes. For more information on these commands, see the conda command [documentation](https://docs.conda.io/projects/conda/en/stable/commands/clean.html).

<img src="/images/2026/screenshot-miniconda-08-pathanddefault.png" style="width: 50%; height: auto;" alt="Installation option">


9. Select **Install**. The installation might take a few minutes to complete. Select **Show details** to view the packages being installed. 

<img src="/images/2026/screenshot-miniconda-09-installing.png" style="width: 50%; height: auto;" alt="Start installing">


10. Select **Next** twice, then select **Finish** to close the installer. 

<img src="/images/2026/screenshot-miniconda-10-completed.png" style="width: 50%; height: auto;" alt="Install completed">

<img src="/images/2026/screenshot-miniconda-11-finish.png" style="width: 50%; height: auto;" alt="Install finish">

Once you click Finish with those boxes checked, the installer will close and your default web browser will automatically open two official documentation tabs:

* **Getting started with Conda**: This opens a [guide to help](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html) you learn basic Conda commands, such as creating environments and installing packages.
* **Welcome to Anaconda**: This opens a [landing page](https://www.anaconda.com/installation-success) introducing you to the Anaconda ecosystem, its community, and additional cloud resources.

If you do not want these web pages to open, simply uncheck both boxes before clicking Finish.


### Step 3: Verify the Installation

To open Anaconda Prompt, type “Anaconda Prompt” in the Windows search bar, then select the application.

<img src="/images/2026/anaconda_prompt.png" style="width: 50%; height: auto;" alt="Install finish">

Your window will display something like the following, with your base environment activated by default:

```bash
(base) C:\Users\{username>
```

To test if Conda is working by running this command:

```bash
conda --version
```

<img src="/images/2026/screenshot-miniconda-12-verify.png" style="width: 50%; height: auto;" alt="Verify">


## Install Miniconda on MacOS

{{< youtube QWta2QPUJ2E >}}

1. Navigate to [anaconda.com/download](https://www.anaconda.com/download), register with Anaconda or [Skip Registration](https://www.anaconda.com/download/success?reg=skipped)

2. Choose Your Download: **64-bit (Apple silicon) Graphical Installer** under Mac > Miniconda.
Direct link: https://anaconda.com/api/installers/Miniconda3-latest-MacOSX-arm64.pkg

3. Go to your Downloads folder and double-click the `.pkg ` file to launch.

4. Read through [Miniconda’s End User License Agreement (EULA)](https://www.anaconda.com/legal/terms/miniconda) and select **I Agree** to agree to the terms. You can view [Anaconda’s Terms of Service (TOS)](https://www.anaconda.com/legal).

5. Choose an install location

6. Select Install. When the installation finishes, open your terminal application. 


## Install Miniconda on Linux

{{< youtube D_KyOmeusrE >}}


<!-- {{< cards >}}
  {{< card link="tts" title="Text-to-Speech" icon="book-open" >}}
  {{< card link="kokoro" title="Kokoro 82M v1.0" icon="book-open" >}}
{{< /cards >}} -->


----

Reference:

- [Miniconda Windows graphical installer](https://www.anaconda.com/docs/getting-started/miniconda/install/windows-gui-install)
- [Miniconda MacOS graphical installer](https://www.anaconda.com/docs/getting-started/miniconda/install/mac-gui-install)
- [Miniconda Linux installer](https://www.anaconda.com/docs/getting-started/miniconda/install/linux-install)
- [Conda Installation Guide](https://courses.spatialthoughts.com/install-conda.html)
- [Setting up Python on Windows with Miniconda by Anaconda](https://katiekodes.com/setup-python-windows-miniconda/)