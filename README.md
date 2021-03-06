PyTorch model converter
---

A tool for converting [PyTorch](https://github.com/pytorch/pytorch) models into 
[MatConvNet](https://github.com/vlfeat/matconvnet). This is a work in progress.

### Imported pretrained models

Some of the useful pretrained models available in the `torchvision.models` module 
have been converted into MatConvNet and are available for download at the link
below: 

[Torchvision models](http://www.robots.ox.ac.uk/~albanie/models.html#pytorch-models)

The *ResNeXt* family of models have also been imported and are available for download:

[ResNeXt models](http://www.robots.ox.ac.uk/~albanie/models.html#resnext-models)

### Converting your own models

The conversion script requires Python (with PyTorch installed) and MATLAB. 
Converting models between frameworks tends to be a non-trivial task, so it is 
likely that modifications will be needed for unusual models.  To get started, 
see the `importer.sh` script (this can be modified to import new models).

### Installation

The easiest way to use this module is to install it with the `vl_contrib` 
package manager. `vl_contrib` is not yet part of the main MatConvNet 
distribution, but it can be easily obtained by using the 
[contrib branch](https://github.com/vlfeat/matconvnet/tree/contrib) of the 
github repo. To switch to this branch (after cloning), you can simply run 

`git checkout -b contrib origin/contrib`

from the root directory. Once this is done, `mcnPyTorch` can then be installed 
with the following three commands from the root directory of your MatConvNet 
installation:

```
vl_contrib('install', 'mcnPyTorch', 'contribUrl', 'github.com/albanie/matconvnet-contrib-test/') ;
vl_contrib('setup', 'mcnPyTorch', 'contribUrl', 'github.com/albanie/matconvnet-contrib-test/') ;
```

**Dependencies**: `Python3` and `PyTorch`, and a few other modules which should be easy to install with `conda`.


### Notes

* The normalisation used by the pretrained PyTorch models differs significantly from the typical matconvnet approach (see [here](https://github.com/albanie/mcnPyTorch/blob/master/benchmarks/cnn_imagenet_pt_mcn.m#L95) for an example).
* The weights in the converted model are modified slightly from the originals to compensate for differences in certain computational blocks.  For instance, PyTorch adds an `espilon` term to batch norm denominator during both training and inference.