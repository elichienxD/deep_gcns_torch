# GIANT-XRT+RevGAT

This is the repository for reproducing the results in our paper: [[Node Feature Extraction by Self-Supervised Multi-scale Neighborhood Prediction]](https://arxiv.org/pdf/2111.00064.pdf) for the combination of GIANT-XRT+RevGAT.

## Step 0: Install GIANT and get GIANT-XRT node features.
Please follow the instruction in [[GIANT]](https://github.com/amzn/pecos/tree/mainline/examples/giant-xrt) to get the GIANT-XRT node features. Note that if you generate your own pretrained node features from GIANT-XRT, you should be aware of your save path and modify the --pretrain_path (below in Step 3) accordingly.

## Step 1: Git clone this repo.
After following the steps in [[GIANT]](https://github.com/amzn/pecos/tree/mainline/examples/giant-xrt), go to the folder
`pecos/examples/giant-xrt`

Then git clone this repo in the folder `giant-xrt` directly.

## Step 2: Install additional packages.
If you install and run GIANT correctly, you should only need to additionally install [dgl>=0.5.3](https://github.com/dmlc/dgl).

## Step 3: Run the experiment.
Go to the folder `deep_gcns_torch`.

Run `Runexp_RevGAT_ogbnarxiv.sh` for reproducing our results for ogbn-arxiv dataset with GIANT-XRT features.

```
New arguments

--data_root_dir: path to save ogb datasets.
--pretrain_path: path to load GIANT-XRT features. Set it to 'None' for using ogb default features.
``` 

## Results
If execute correctly, you should have the following performance (using our pretrained GIANT-XRT features).

Teacher model (RevGAT):
* Average val accuracy: 77.12 ± 0.07
* Average test accuracy: 75.82 ± 0.13
* Number of params: 3081296

Student model (RevGAT+KD):
* Average val accuracy: 77.27 ± 0.07
* Average test accuracy: 76.09 ± 0.15
* Number of params: 3081296

**Remark:** We do not fine-tune RevGAT for our GIANT-XRT. It is possible to achieve higher performance by fine-tune it more carefully. We encourage readers to do so for the best performance.

For more details about RevGAT, please check the original README.

## Citation
If you find our code useful, please cite both our GIANT paper and the RevGAT references provided in the original repo.

Our GIANT paper:
```
@article{chien2021node,
  title={Node Feature Extraction by Self-Supervised Multi-scale Neighborhood Prediction},
  author={Eli Chien and Wei-Cheng Chang and Cho-Jui Hsieh and Hsiang-Fu Yu and Jiong Zhang and Olgica Milenkovic and Inderjit S Dhillon},
  journal={arXiv preprint arXiv:2111.00064},
  year={2021}
}
```

RevGAT paper:

```
@InProceedings{li2021gnn1000,
    title={Training Graph Neural Networks with 1000 layers},
    author={Guohao Li and Matthias Müller and Bernard Ghanem and Vladlen Koltun},
    booktitle={International Conference on Machine Learning (ICML)},
    year={2021}
}
```

Feel free to email me (ichien3@illinois.edu) if you have further questions. My notification of the Github issue does not work properly so make sure to drop me an email when you open a new issue.
