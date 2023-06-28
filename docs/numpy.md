# **NumPy**
**POWERFUL N-DIMENSIONAL ARRAYS**

NumPy (Numerical Python). Numpy is a fast and versatiile. The NumPy vectorization, indexing, and broadcasting concepts are the defacto standards of array computing today.

**NUMERICAL COMPUTING TOOLS**

NumPy offers comprehensive mathematical functions, random number generators, linear algebra routimes, Fourier transform, and more.

**OPEN SOURCE**

Distributed under liberal BSD license, NumPy is developed and maintained publicly on GitHub by a vibran, responsive, and diverse community.

**INTEROPERABLE**

NumPy supporst a wide range of hardware and computing platforms, and plays well with distributed, GPU, and sparse array libraries.

**PERFORMANT**

The core of NumPy is well-optimized C code. Enjoy the flexibility of Python with the speed of compiled code.

**EASY TO USE**

NumPy's high level syntax make it accessible and productive for programmers form any background or experience level.

## **Installing NumPy**
The only prerequisite for installing NumPy is Python itself. If don't have Python yet and want the simplest way to get started, we recommend you use the Anaconda Distribution - it includes Python, Numpy, and many other commonly used packages for scientific computing and data science.  
Numpy can be installed with `conda`, with `pip`, with a package manager on macOS and Linux, or [from source](https://numpy.org/devdocs/user/building.html).</br>

**CONDA**

If you use `conda`, you can install NumPy from the `defaults` or `conda-forge` channels.

    # Best practice, use an environment rather than install in the base environment
    
    conda create -n my-env
    conda activate my-env

    # if you want to install form conda-forge

    conda config --env --add channels conda-forge

    # The actual install command

    conda install numpy

**PIP**

If you use `pip`, you can install NumPy with:

    pip install numpy
Also when using pip, it's good practice to use a virtual environment

## **Python and NumPy installation guide**

Installing and managin packages in Python is complicated, there are a number of alternative solutions forn most task. This Guide tries to give the reader a sense of the best (or most popular) solutions, and give clear recommendations. It focuses on users of Python, NumPy, and the PyData (or numerical computing) stack on common operating systems and hardware.

### **Recommendations**

We'll start with recommendatons based on the user's experience level and operating system of interest. If you're in between "beginning" and "advanced", please go with "beginning" if you want to keep things simple, and with "advanced" if you want to work according to best practices that go a longer way in the future.

**Beginnging users**

On all of Windows, macOS and Linux
- Install [Anaconda](https://www.anaconda.com/distribution/) (it installs all packages you need and all other tools mentioned below)
- For writing and executing code, use notebooks in [JupyterLab](https://jupyterlab.readthedocs.io/en/stable/index.html) for exploratory and interactive computing, and [Spyder](https://www.spyder-ide.org/) or [Visual Studio Code](https://code.visualstudio.com/) for writing scripts and packages.
- Use [Anaconda Navigator](https://docs.anaconda.com/anaconda/navigator/) to manage your package and start JupyterLab, Spyder, or Visual Studio Code.

**Advanced users**

*conda*
- Install [Miniforge](https://github.com/conda-forge/miniforge).
- Keep the `base` conda environment minimal, and use one or more [conda environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) to install the package you need for the task or project you're working on.

*Alternative if you prefer pip/PyPI*

For user who know, from personal preference or reading about the main differences between conda and pip below, they prefer a pip/PyPI-based solution, we recommend:

- Install Python from [python.org](https://www.python.org/downloads/), [Homebrew](https://brew.sh/), or your linux package manager.
- Use [Poetry](https://python-poetry.org/) as the most well-maintained tool that provides a dependency resolver and environment management capablities in a similiar fashion as conda does.

### **Python package management**

Managing packages is a challenging problem, and, as a result, there are lots of tools.</br>
For web and general purpose Python development there's a whole [host of tools](https://packaging.python.org/guides/tool-recommendations/) complementary with pip. For high-performance computing (HPC), [Spack](https://github.com/spack/spack) is worth considering. For most NumPy users though, [conda](https://conda.io/en/latest/) and [pip](https://pip.pypa.io/en/stable/) are the two most popular tools.

**Pip & conda**

The two main tools that install Python packages are `pip` and `conda`. Their functionality partially overlaps (e.g. both can install `numpy`), however, they can also work together. We'll discuss the major differences between pip and conda here.

The first difference is that conda is cross-language and it can install Python, while pip is installed for a particular Python on your system and install other packages to that same Python install only. This also means conda can install non-Python libraries and tools you may need (e.g. compilers, CUDA, HDF5), while pip can't.

The second difference is that pip installs from the Python Packages Index (PyPI), while conda installs from its own channels (typicallty "defaults" or "conda-forge"). PyPI is the largest collection of packages by far, however, all popular packages are available for conda as well.

The third difference is that conda is an integrated solution for managing packages, dependencies and environments, while pip you may need another tool (there are many!) for dealing with environments or complex dependencies.

**Reproducible installs**

As libreries get updated, results from running your code can change, or your code can break completely. It's important to be able to reconstruct the set of packages and versions you're using. Best practice is to:

1. use a different environment per project you're working on,
2. record packages names and versions using your package installer; each has its own metadata format for this:
    - Conda: [conda environmets and environment.yml](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)
    - Pip: [virtual environments](https://docs.python.org/3/tutorial/venv.html) and [requirements.txt](https://pip.readthedocs.io/en/latest/user_guide/#requirements-files)
    - Poetry: [virtual environments and pyproject.toml](https://python-poetry.org/docs/basic-usage/)

### **NumPy Packages & accelerated linear algebra libraries**
NumPy doesn't depend on any other Python packages, however, it does depend on an accelerated linear algebra library - typically [Intel MKL](https://software.intel.com/en-us/mkl) or [OpenBLAS](https://www.openblas.net/). Users don't have to worry about installing those (they're automatically included in all NumPy install methods). Power users may still want to know details, because the used BLAS can affect performance, behavior and size on disk:
- The NumPy wheels on PyPI, which is what pip installs, are built with OpenBLAS. The OpenBLAS libraries are included inthe wheel. This make the wheel larger, and if a user install (for exmaple) SciPy as well, they will now have two copies of OpenBLAS on disk.
- In the conda defaults channel, NumPy is built against Intel MKL. MKL is a separate package that will be installed in the users environment when they install NumPy.
- In the conda-forge channel, NumPy is built against a dummy "BLAS" package. Whe a user installs NumPy from conda-forge, that BLAS package then gets installed together with the actual library - this defaults to OpenBLAS, but it can also be MKL (from the defaults channel), or even [BLIS](https://github.com/flame/blis) or reference BLAS.
- The MKL package is a lot larger that OpenBLAS, it's about 700 MB on disk while OpenBLAS is about 30 MB.
- MKL is typically a little faster and more robust then OpenBLAS.

Besides install sizes, performance and robustness, there are two more things to consider.

- Intel MKL is not open source. For normal use this is not a problem, but if a user need to redistribute an application built whit NumPy, this could be an issue.
- Booth MKL and OpenBLAS will use multi-threading for function calls like `np.dot`, with the number of threads being determined by both a build-time option and an environment variable. Often all CPU cores will be used. This is sometimes unexpected for users; NumPy itself doesn't auto-parallelize any function calls. It typically yields better performance, but can also be harmful - for example when using another level parallelization with Dask, scikit-learn or multiprocessing.
