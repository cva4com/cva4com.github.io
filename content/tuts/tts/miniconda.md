---
linkTitle: Miniconda
title: Installing Miniconda
weight: 5
prev: /tts
# next: /tts/kokoro
cascade:
  type: docs
tags:
  - conda
  - Miniconda
  - Anaconda
---

## Installing Miniconda

{{< youtube AgnAs0nPEVg >}}


## What Is Miniconda?

Miniconda is a free minimal installer for Conda. It is a smaller alternative to Anaconda. It includes Python, Conda, and essential dependencies.

With Miniconda, you can create isolated environments. This helps avoid conflicts between different projects. It is ideal for developers who need flexibility.


### Download Miniconda

Follow these steps to download Miniconda:

1. Visit the [official Miniconda](https://www.anaconda.com) [download page](https://www.anaconda.com/download).
2. Choose the [installer](https://www.anaconda.com/download/success) for your OS.
<!-- 3. Select the Python version (3.x recommended). -->

For Windows, download the .exe file. For macOS and Linux, choose the appropriate shell script.

Direct link: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe


### Install on Windows

Follow these steps for Windows installation:

1. Double-click the downloaded .exe file.
2. Follow the setup wizard instructions.
3. Check "Add Miniconda to PATH" if prompted.
4. Complete the installation.

To verify, open Command Prompt and run:

```bash
conda --version
```


### Install on macOS/Linux

{{< youtube WdXdl0C0jfE >}}

For macOS and Linux, use the terminal:

1. Open a terminal window.
2. Navigate to the download directory.
3. Run the shell script:

```bash
bash Miniconda3-latest-MacOSX-x86_64.sh
```

{{< youtube D_KyOmeusrE >}}

<!--more-->

{{< cards >}}
  {{< card link="tts" title="Text-to-Speech" icon="book-open" >}}
  {{< card link="kokoro" title="Kokoro 82M v1.0" icon="book-open" >}}
{{< /cards >}}