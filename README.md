This code is based on the following two works：  
  - [DGL-LifeSci: An Open-Source Toolkit for Deep Learning on Graphs in Life Science](https://pubs.acs.org/doi/10.1021/acsomega.1c04017)
  * Hou's work [Could graph neural networks learn better molecular representation for drug discovery? A comparison study of descriptor-based and graph-based models](https://jcheminf.biomedcentral.com/articles/10.1186/s13321-020-00479-8) 

### Install dependencies　　
　　python 3.6+, DGL 0.7.0+ and PyTorch 1.5.0+. For the complete code package list, please refer to the [dependencies.yaml](./dependencies.yaml)  
 
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
　　The data used in this study, including Smiles for GNNs and descriptors for LGB, where the descriptors has been proportionally divided into training set, validation set and test set.
#### Examples
　　Contains the original AFP, GCN, GAT and LGB source code for this study.
#### Results
　　Contains the original AFP, GCN, GAT and LGB training results of this study, including the optimal model, hyper-parameters and summary of experimental results
  

