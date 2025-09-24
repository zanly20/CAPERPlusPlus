# CAPER++

This repository is the official implementation of the paper CAPER++. 

![Overview](assets/pipeline.png)
![Visulization](assets/results.png)

## Datasets

[the dataset](https://1drv.ms/u/s!As7BgFXGjZFgmRnf80as8a35G2v6?e=SZfD5e) dataset contains the synthetic images generated from Unity along with the following annotations:

- RGB image
- depth map
- part mask
- part pose

This dataset also contains **URDF** articulated object models of five categories from PartNet-Mobility,
which is re-annotated by us to align the rest state in the same category.

## Usage

### Installation

Environments:

- Python >= 3.8
- Pytorch > 1.12.0
- CUDA >= 11.3
- open3d >= 0.13.0

```bash
git clone https://github.com/xxx.git
cd CAPER++
conda create -n caper python=3.8 -y
conda activate caper
```

Install the dependencies listed in ``requirements.txt``

```
pip install -r requirements.txt
```

Then, compile CUDA module - index_max:

```bash
cd model/index_max_ext
python setup.py install
```

And, building only the CUDA kernels:

```bash
cd model/Pointnet2_PyTorch_master
pip install pointnet2_ops_lib/.
```

Finally, download [the dataset1](https://1drv.ms/u/s!As7BgFXGjZFgmRnf80as8a35G2v6?e=SZfD5e)Dataset and put it in `your_dir` folder. And remember to modify the dataset_root in train_CAPERplus.py.

Now you are ready to go!

### Training

```bash
python train_CAPERplus.py --category 1 --num_parts 2 --symtype shape 
```

### Testing

```bash
cd video_funcs
python new_tpami_12_video_T1T2.py --cate_id 1 --num_parts 2 --symtype shape --pth_path your_path --data_tag val
```
