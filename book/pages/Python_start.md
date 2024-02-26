# Python installation instruction

[Python](https://python.org/) is a popular language for research computing, and great for general-purpose programming as well. Installing all of its research packages individually can be a bit difficult, so you're recommended to use [Anaconda](https://www.anaconda.com/products/individual), an all-in-one installer. To make sure you're on the same versions you can set up an 'environment'.


## Installation Anaconda
We will teach Python using the [Jupyter Notebook](https://jupyter.org/), a programming environment that runs in a web browser (Jupyter Notebook will be installed by Anaconda). For this to work you will need a reasonably up-to-date browser. The current versions of the Chrome, Safari and Firefox browsers are all [supported](https://jupyter-notebook.readthedocs.io/en/stable/notebook.html#browser-compatibility) (some older browsers, including Internet Explorer version 9 and below, are not). Notebooks can be run after you install Python and the appropriate packages.

````{tab-set}
```{tab-item} Installation on Windows
1.  https://www.anaconda.com/products/individual#download-section with your web browser.
2. Download the Anaconda for Windows installer with Python 3. (If you are not sure which version to choose, you probably want the 64-bit Graphical Installer Anaconda3-...-Windows-x86_64.exe)
3. Install Python 3 by running the Anaconda Installer, using all of the defaults for installation except make sure to check Add Anaconda to my PATH environment variable.

<iframe width="500" height="281" src="https://www.youtube.com/embed/xxQ0mzZ8UvA" title="SWC install Python on Windows" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```

```{tab-item} Installation on MAC
1. Open https://www.anaconda.com/products/individual#download-section with your web browser.
2. Download the Anaconda Installer with Python 3 for macOS (you can either use the Graphical or the Command Line Installer).
3. Install Python 3 by running the Anaconda Installer using all of the defaults for installation.

<iframe width="500" height="281" src="https://www.youtube.com/embed/TcSAln46u9U" title="SWC Install Python on Mac" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```

```{tab-item} Installation on Linux
1. Open https://www.anaconda.com/products/individual#download-section with your web browser.
2. Download the Anaconda Installer with Python 3 for Linux. 
(The installation requires using the shell. If you aren't comfortable doing the installation yourself stop here and request help at the workshop.)
3. Open a terminal window and navigate to the directory where the executable is downloaded (e.g., `cd ~/Downloads`).
4. Type `bash Anaconda3-` and then press `Tab` to autocomplete the full file name. The name of file you just downloaded should appear.
5. Press `Enter` (or Return depending on your keyboard). You will follow the text-only prompts. To move through the text, press `Spacebar`. Type yes and press enter to approve the license. Press `Enter` (or `Return`) to approve the default location for the files. Type yes and press `Enter` (or `Return`) to prepend Anaconda to your PATH (this makes the Anaconda distribution the default Python).
6. Close the terminal window.
```
````

:::{card}
<iframe src="https://tudelft.h5p.com/content/1292011161958921937/embed" aria-label="Check installation" width="1088" height="637" frameborder="0" allowfullscreen="allowfullscreen" allow="autoplay *; geolocation *; microphone *; camera *; midi *; encrypted-media *"></iframe><script src="https://tudelft.h5p.com/js/h5p-resizer.js" charset="UTF-8"></script>
:::

Source: {cite:ts}`carprentries_download`

## Set up the environment
Now we will make sure you have an environment to get started in this course. This year we will use Python 3.11, so we are going to make sure that’s installed and ready to go. Other Python packages that are not included in the base installation will be installed in your environment when we need to use them, to make sure we know exactly what is going on when working with code in this course.

The following steps will create an Anaconda environment called optimizatoin and install Python 3.11. Even if you already have Python 3.11, it is still good practice to create a dedicated Anaconda environment for each of your major projects. Please make sure you have upgraded Anaconda before proceeding with these steps:

1. Open Anaconda prompt from the start menu
2. Execute: `conda create -n optimization python=3.11 anaconda` (this may take several minutes)
3. Activate: `conda activate optimization`
4. Check: you should now see `optimization` displayed somewhere in the prompt between parenthesis, like this: `(optimization)`

One important reminder: throughout the semester you should be using the optimization environment every time you use Python, except when instructed otherwise. All you have to do is remember to use the command `conda activate optimization` prior to opening your files, or select the new environment in the Anaconda Navigoator prior to opening any python-program.

Source: {cite:ts}`mude_getting_started`