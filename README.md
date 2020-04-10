# blocks
blocks is a python package with a framework for building deep learning models

## installation

#### using pip
* CPU version: `pip install ml-blocks[cpu]`

* GPU version: `pip install ml-blocks[gpu]`
    * _NOTE: this requires you to have your environment set up properly for pip installation of tensorflow-gpu. If you are having troule, consider [using conda](#using-conda-for-tensorflow-gpu) to install tensorflow-gpu and it's dependencies in your environment._

#### using poetry

* GPU Version:
```
git clone git@github.com:dholland42/blocks.git
cd blocks
poetry install -E "gpu"
```

* GPU Version:
```
git clone git@github.com:dholland42/blocks.git
cd blocks
poetry install -E "cpu"
```

#### using conda for tensorflow-gpu
```
# get tensorflow-gpu and all dependencies
conda install tensorflow-gpu~=2.1

# get blocks using pip...
pip install ml-blocks

# or from local, using poetry
git clone git@github.com:dholland42/blocks.git
cd blocks
poetry install
```

## what's a block?
The basic idea here is that deep learning models are often made up of blocks of code, which are tweaked, parameterized and combined in different ways during experimentation. Kind of like playing with legos, or stacking _blocks_ ;) in different ways.

The main classes of blocks we define are:
- [preprocessor](#preprocessor) - process input data
- [feature-extractor](#feature-extractor) - create representation of input
- [classifier](#classifier) - predict class(es) from feature representation(s)
- [regressor](#regressor) - predict value(s) from feature representation(s)
- [postprocessor](#postprocessor) - format predictions

## why?

#### Experimental Ease
Often times during experimentation, chunks of model code are swapped out and substituted for a new experimental version. We've found that a large portion of the time that chunk of code corresponds to a concept captured by these blocks. 

Many supervised deep learning models can be split up into
```
preprocessing > feature extraction > classification/regression > postprocessing
```
Some of these steps in the model can be several layers, or loops of layers, deep. This can make swapping out any individual piece in the pipeline a bit cumbersome. We endeavor to make that much simpler via abstraction, and provide some commonly used versions of each block class.

#### Deployment Consistency
While some blocks may be complicated loops and stacks of layers, others may not even be a single layer in current practice. Preprocessing and postprocessing, for example, are often done _outside_ the model, before data is passed in or returned to a user. This can lead to a consistency headache when deploying a model, as it is imperitive to ensure that data is processed in __exactly__ the same way in a production environment as it is during training, testing and evaluation.

In order to even get a model into a production environment we have seen others create custom abstractions that stitch together several different technologies in ways that are difficult to follow, cause dependency headaches, tend to be buggy and are often slow. On top of these issues, this practice creates an unnecessary barrier to entry for new members of a team looking to get their model deployed in a quick, safe and efficient way.

Our proposal is to bundle all the stages of a model together under one roof, in a modular way, using the same technology (where possible). This will both speed up experimentation, and facilitate production deployment.

## types of blocks
### preprocessor
[TODO]
### feature-extractor
[TODO]
### classifier
[TODO]
### regressor
[TODO]
### postprocessor
[TODO]