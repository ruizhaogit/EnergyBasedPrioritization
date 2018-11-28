# Energy-Based Hindsight Experience Prioritization

Here is the code for our paper "Energy-Based Hindsight Experience Prioritization".  

The paper is published in 2018 Conference on Robot Learning (CoRL 2018) as oral presentation (7%).  

The paper is avaliable at Proceedings of Machine Learning Research: http://proceedings.mlr.press/v87/zhao18a.html  

The code was developed by Rui Zhao (Siemens AG & Ludwig Maximilian University of Munich).  

For details on Energy-Based Hindsight Experience Prioritization (EBP), please read the published paper.  

The code is developed based on OpenAI Baselines (link: https://github.com/openai/baselines).   

## Prerequisites  

The code requires python3 (>=3.5) with the development headers. You'll also need system packages CMake, OpenMPI and zlib. Those can be installed as follows  

### Usage  
    
```bash
sudo apt-get update && sudo apt-get install cmake libopenmpi-dev python3-dev zlib1g-dev
```

To run the code, you need to install OpenAI Gym (link: https://github.com/openai/gym).  
We use the robotics environment in OpenAI Gym, which needs the MuJoCu physics engine (link: http://www.mujoco.org/).   

The experiments were carried out on a 20-CPUs server.  
We use 19 CPUs for training.  
If you are running the experiments on a laptop, please configure a smaller number of CPUs.  
Note that, with less CPUs, the performance will be effected.  

After the installaton of dependicies, you can reproduce the experimental results by running the following commnands:  
```
python baselines/her/experiment/train.py --env_name FetchPickAndPlace-v0 --prioritization none --n_epochs 50 --num_cpu 19 
python baselines/her/experiment/train.py --env_name FetchPickAndPlace-v0 --prioritization tderror --n_epochs 50 --num_cpu 19 
python baselines/her/experiment/train.py --env_name FetchPickAndPlace-v0 --prioritization energy --clip_energy 0.5 --n_epochs 50 --num_cpu 19 
```
For FetchPickAndPlace-v0, we use clip_energy parameter 0.5.  
For the other three hand environments, we use clip_energy 2.5.  

```
python baselines/her/experiment/train.py --env_name HandManipulateEggFull-v0 --prioritization none --n_epochs 200 --num_cpu 19 
python baselines/her/experiment/train.py --env_name HandManipulateEggFull-v0 --prioritization tderror --n_epochs 200 --num_cpu 19 
python baselines/her/experiment/train.py --env_name HandManipulateEggFull-v0 --prioritization energy --clip_energy 2.5 --n_epochs 200 --num_cpu 19 
```

To test the learned policies, you can run the command:  
```
python baselines/her/experiment/play.py /path/to/an/experiment/policy_latest.pkl
```

## Citation:

Citation of the arXiv version:

```
@article{zhao2018energy,
  title={Energy-Based Hindsight Experience Prioritization},
  author={Zhao, Rui and Tresp, Volker},
  journal={arXiv preprint arXiv:1810.01363},
  year={2018}
}
```

## Licence:

MIT
