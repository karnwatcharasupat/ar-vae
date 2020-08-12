[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-ff69b4.svg)](http://creativecommons.org/licenses/by-nc-sa/4.0/)

## AR-VAE: Attribute-based Regularization of VAE Latent Spaces

### About 
AR-VAE is a type of Variational Auto-Encoder (VAE) which uses a new supervised training method to create structured latent spaces where specific continuous-valued attributes are forced to be encoded along specific dimensions of the latent space. This repository contains the source for training and evaluating the AR-VAE models across different image and music-based datasets.

The figure below shows the main idea behind the AR-VAE model.
<p align="center">
    <img src=figs/motivation_arvae.svg width=500px><br>
</p>

This repository contains the source for training and evaluating the AR-VAE models across different image and music-based datasets. Please cite as follows if you are using the code in this repository in any manner.

> Ashis Pati, Alexander Lerch. "Attribute-based Regularization of Latent Spaces for Variational Auto-Encoders", Neural Computing and Applications. 2020.

```
@article{pati2020arvae,
  title={{Attribute-based Regularization of Latent Spaces for Variational Auto-Encoders}},
  author={Pati, Ashis and Lerch, Alexander},
  journal={Neural Computing and Applications},
  issn={1433-3058},
  doi={10.1007/s00521-020-05270-2},
  url={https://doi.org/10.1007/s00521-020-05270-2},
  year={2020},
}
```


### Results

**Manipulation of Image Attributes**

Manipulating attributes of 2-d shapes. Each row in the figure below represents a unique shape (from top to bottom): <i>square, heart, ellipse</i>. Each column corresponds to traversal along a regularized dimension which encodes a specific attribute (from left to right): *Shape, Scale, Orientation, x-position, y-position*.
<p align="center">
    <img src=figs/gif_interpolations_dsprites_0.gif><br>
    <img src=figs/gif_interpolations_dsprites_1.gif><br>
    <img src=figs/gif_interpolations_dsprites_4.gif><br>
   
</p>


Manipulating attributes of MNIST digits. Each row in the figure below represents a unique digit fronm 0 to 9. Each column corresponds to traversal along a regularized dimension which encodes a specific attribute (from left to right): *Area, Length, Thickness, Slant, Width, Height*.
<p align="center">
    <img src=figs/gif_interpolations_mnist_28.gif><br>
    <img src=figs/gif_interpolations_mnist_5.gif><br>
    <img src=figs/gif_interpolations_mnist_1.gif><br>
    <img src=figs/gif_interpolations_mnist_30.gif><br>
    <img src=figs/gif_interpolations_mnist_19.gif><br>
    <img src=figs/gif_interpolations_mnist_23.gif><br>
    <img src=figs/gif_interpolations_mnist_21.gif><br>
    <img src=figs/gif_interpolations_mnist_17.gif><br>
    <img src=figs/gif_interpolations_mnist_61.gif><br>
    <img src=figs/gif_interpolations_mnist_9.gif><br>
</p>

**Manipulation of Musical Attributes**

Manipulating attributes of monophonic measures of music. In the figure below, measures on each staff line are generated by traversal along a regularized dimension which encodes a specific musical attribute (shown on the extreme left).
<p align="center">
    <img src=figs/interp_score_15_11.svg><br>
</p>

Piano roll version of the figure above is shown below. Plots on the right of each pianoroll show the progression of attribute values.
<p align="center">
    <img src=figs/interp_pianoroll_15_11.svg><br>
</p>    


### Installation and Usage
Install `anaconda` or `miniconda` by following the instruction [here](https://docs.conda.io/projects/conda/en/latest/user-guide/install/).

Create a new conda environment using the `enviroment.yml` file located in the root folder of this repository. The instructions for the same can be found [here](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-from-an-environment-yml-file).

To install, either download / clone this repository. Open a new terminal, `cd` into the root folder of this repository and run the following command

    python setup.py develop

**Downloading Datasets:**

Follow the steps below to download the different datasets: 
* Create a folder named `mnist_data` in `ar-vae/data/` directory. Download the morpho-mist data from this [link](https://drive.google.com/uc?export=download&id=1-E3sbKtzN8NGNefUdky2NVniW1fAa5ZG) and copy the folder named `plain` to the created `mnist_data` folder.
* Create a folder named `dsprites` in `ar-vae/data/` directory. Clone [this](https://github.com/deepmind/dsprites-dataset) repository and copy its contents to the created `dpsrites` folder.
* Download the `.zip` file linked [here](https://drive.google.com/file/d/1yvkm0ebyG3XAZ97ZRaiumFUAmlXkY1bA/view?usp=sharing). Unzip it and place the `datasets` and `folk_raw_data` folders in the `ar-vae/data/` directory.

The final `ar-vae/data/` directory should have the following sub-directories:
```
ar-vae/data
    --> dataloaders
        --> morphomnist
    --> datasets
    --> dpsprites
    --> folk_raw_data
    --> mnist_data
        --> plain
```

### Contents
The contents of this repository are as follows: 
* `data`: contains the data and pytorch `dataloaders` for the different datasets.
* `imagevae`: module implementing the AR-VAE network and trainer for image datasets.
* `measurevae`: module implemening the AR-VAE network and trainer for music datasets. 
* `imagefader`: module implementing the fader network and trainer for image datasets.
* `figs`: contains figures and plots for different experiments.
* `utils`: module with utility classes and methods for model, training, evaluation and plotting.

* other scripts to train / test the models

