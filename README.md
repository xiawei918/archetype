# archetype
Skeleton for containerized project with Gradle managed tasks

# Getting Started

## Installing Prerequisites

### Installing Gradle
Archetype uses [Gradle](https://gradle.org/) as its task manager that standards all the task one can execute within archetype project. 

To start, first install Gradle by following the instructions [here](https://gradle.org/install/). Gradle requires a Java JDK or JRE version 8 or higher to be installed. To check, run `java -version`. 

If on MacOS, Gralde can be installed via homebrew

```brew install gradle```

### Installing Docker
Archetype leverages docker to containerize code for projects. Containers ensure the project can be always run in a independent and reliable environment, which will make the code easily reproducible and easy to run. 

If docker is not installed, please install docker by following the instruction [here](https://docs.docker.com/get-docker/).

## Building Project
Now that prerequisites are installed, one can create a docker image by running

```gradle docker```

The image will pull a Python 3.8.0 base image and install poetry that will install and manage Python related dependencies. The initial python dependencies included are:

* `python = "3.8.0"`
* `numpy = "1.19.0"`
* `dataclasses = "^0.6"`
* `matplotlib = "3.1.2"`
* `pandas = "1.0.0"`
* `jupyter = "*"`
* `jupyterlab = "*"`

And the project directories structure looks like the following:

```
└── project
    ├── src
    ├── data
    └── notebooks
```

If you are eager to dive into coding, one can run 
```gradle dockerRun```
to spin up a quick container with [Jupyterlab](https://jupyterlab.readthedocs.io/en/stable/). 

The directories `src`, `data` and `notebooks` are all automatically created (if not exists in the current directory) and mounted to the container under the same path, so and changes to the files under these directories during development will be reflected and saved on host and persist evening after container perishes.
