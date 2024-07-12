# LUMI-AI-example
Visual transformer model in PyTorch, serving as an example of how to run AI applications on LUMI. 

We use the [`torchvision vit_b_16`](https://pytorch.org/vision/main/models/generated/torchvision.models.vit_b_16.html#torchvision.models.vit_b_16) model and train it with the [tiny-imagenet](https://image-net.org/download-images.php) dataset. This project is meant to provide a sandbox for testing and benchmarking AI applications on LUMI and should eventually serve as an A-Z example as part of the LUMI AI documentation.

## TO DO
* [ ] Benchmark different storage options (LUMI-P, LUMI-F, LUMI-O, /tmp), file striping 
* [ ] Test different file formats to avoid the "many small files problem" (HDF5, arrow, WebDataset, TensorFlow's TFRecord, etc)
* [ ] Test different AI containers
* [ ] Benchmark CPU and GPU usage on a single-node and across multiple nodes
* [ ] Investigate Tensorboard visualization
* [ ] more points to be added soon

## HDF5 support
The imagenet dataset consists of hundreds of thousands of single jpg files. To avoid the "many small files" problem the datasets can be transformed into a single HDF5 file with the script `turn_into_hdf5.py`. Note, that this increases the size of the data by one order of magnitude as this script does not compress the data in any form. 

## Running script on LUMI
This github repo is cloned to `/project/project_462000002/LUMI-AI-example`. Training data, validation data, and the parameters of the model are in the same directory. The used container is extended via a virtual environment, as described [here](https://github.com/Lumi-supercomputer/Getting_Started_with_AI_workshop/blob/main/07_Extending_containers_with_virtual_environments_for_faster_testing/examples/extending_containers_with_venv.md), since `h5py` is not included in the container. Anyone is welcome to work in that directory in order to minimize data storage, but please create a new branch.
