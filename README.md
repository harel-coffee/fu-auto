This code is based on the following two works：  
  - [DGL-LifeSci: An Open-Source Toolkit for Deep Learning on Graphs in Life Science](https://pubs.acs.org/doi/10.1021/acsomega.1c04017)
  * Hou's work [Could graph neural networks learn better molecular representation for drug discovery? A comparison study of descriptor-based and graph-based models](https://jcheminf.biomedcentral.com/articles/10.1186/s13321-020-00479-8) 

### Install dependencies　　
　　Python 3.6+, DGL 0.7.0+ and PyTorch 1.5.0+. For the complete code package list, please refer to the [dependencies.yaml](./dependencies.yaml)  
 
  ```
    Create a conda environment and install them for example by doing: 
    　　conda create -n dgllife python=3.6  
    　　conda activate dgllife  
    　　conda install ipykernel  
    　　pip install torch==1.8.1+cu111 torchvision==0.9.1+cu111 torchaudio==0.8.1 -f https://download.pytorch.org/whl/torch_stable.html  
    　　conda install -c dglteam dgl-cuda11.0  
    　　pip install dgllife  
    　　conda install -c rdkit rdkit==2018.09.3  
    　　pip install hyperopt  
 ```
### Instruction
#### Data
　　The data used in this study, including smiles for GNNs and descriptors for LGB, where the descriptors has been proportionally divided into training set, validation set and test set.
#### Examples
　　Contains the original AFP, GCN, GAT and LGB source code for this study. 
  - **In AFP GAT GCN.ipynb**
 ```
    # Adjust the parameters here, and refer to the cell above for the description of the parameters
      GPUNum = '0'
      repetitions = 50
      seed = 0 
      args = parser.parse_args(args=['--csv-path','data/0-CF-2274.csv',
                                     '--task-names','active_label',
                                     '--smiles-column','SMILES',
                                     '--result-path','result/CF-2274_NoAug_AFP_20220906',
                                     '--num-evals','50',
                                     '--num-epochs','300',
      #                              '--split-ratio',
                                     '--split','random',                     
                                     '--metric','roc_auc_score',
                                     '--model','AttentiveFP',
      #                              '--atom-featurizer-type','attentivefp',
      #                              '--bond-featurizer-type','attentivefp',
      #                              '--augmentation',
      #                              '--num-workers',
      #                              '--print-every',
                                        ]).__dict__
``` 
  * **In LGB.ipynb**
```
   # Similarly, the LGB operating parameters are adjusted here, including the hyper-parameters and their ranges.
      tasks_dic = {'0-CF-2274-desc-split.csv': ['activity']}
      file_name = '0-CF-2274-desc-split.csv'
      task_type = 'cla'  # 'reg' or 'cla'
      dataset_label = file_name.split('/')[-1].split('_')[0]  
      tasks = tasks_dic[dataset_label]
      OPT_ITERS = 50
      repetitions = 50
      num_pools = 5
      unbalance = True
      patience = 100
      space_ = {'num_leaves': hp.choice('num_leaves', range(100, 300,10)),
                'learning_rate': hp.uniform('learning_rate', 0.005, 0.3),
                'max_depth': hp.choice('max_depth', range(3, 12)),
                'n_estimators': hp.choice('n_estimators', [100,200,300, 400, 500, 1000]),
                'min_child_samples': hp.choice('min_child_samples', range(0, 100,10)),
                'max_bin': hp.choice('max_bin', range(300, 400,10))
                }
``` 
#### Results
　　Contains the original AFP, GCN, GAT and LGB training results of this study, including the optimal model, hyper-parameters and summary of experimental results
  
#### Cite
　　If it helps with your research, we would appreciate citations to the following paper:
```
@article{cao2022investigation,
  title={Investigation of the Binding Fraction of PFAS in Human Plasma and Underlying Mechanisms Based on Machine Learning and Molecular Dynamics Simulation},
  author={Cao, Huiming and Peng, Jianhua and Zhou, Zhen and Yang, Zeguo and Wang, Ling and Sun, Yuzhen and Wang, Yawei and Liang, Yong},
  journal={Environmental Science \& Technology},
  year={2022},
  publisher={ACS Publications}
}
``` 
