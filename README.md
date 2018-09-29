# Energy-Based Hindsight Experience Prioritization

Here is the code for our CoRL-18 paper "Energy-Based Hindsight Experience Prioritization".  

For details on Energy-Based Hindsight Experience Prioritization (EBP), please read the accepted paper (forthcoming).  

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

## Licence:

MIT