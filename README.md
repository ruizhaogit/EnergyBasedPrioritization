# Energy-Based Hindsight Experience Prioritization

Here is the code for our paper "Energy-Based Hindsight Experience Prioritization".  

The paper is published in 2018 Conference on Robot Learning (CoRL 2018) as oral presentation (7%).  

The paper is avaliable at Proceedings of Machine Learning Research: http://proceedings.mlr.press/v87/zhao18a.html  

The code was developed by Rui Zhao (Siemens AG & Ludwig Maximilian University of Munich).  

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

## Citation:

Citation of the paper:

```
@InProceedings{pmlr-v87-zhao18a,
  title =    {Energy-Based Hindsight Experience Prioritization},
  author =   {Zhao, Rui and Tresp, Volker},
  booktitle =    {Proceedings of The 2nd Conference on Robot Learning},
  pages =    {113--122},
  year =   {2018},
  editor =   {Billard, Aude and Dragan, Anca and Peters, Jan and Morimoto, Jun},
  volume =   {87},
  series =   {Proceedings of Machine Learning Research},
  address =    {},
  month =    {29--31 Oct},
  publisher =    {PMLR},
  pdf =    {http://proceedings.mlr.press/v87/zhao18a/zhao18a.pdf},
  url =    {http://proceedings.mlr.press/v87/zhao18a.html},
  abstract =   {In Hindsight Experience Replay (HER), a reinforcement learning agent is trained by treating whatever it has achieved as virtual goals. However, in pre- vious work, the experience was replayed at random, without considering which episode might be the most valuable for learning. In this paper, we develop an energy-based framework for prioritizing hindsight experience in robotic manipulation tasks. Our approach is inspired by the work-energy principle in physics. We define a trajectory energy function as the sum of the transition energy of the target object over the trajectory. We hypothesize that replaying episodes that have high trajectory energy is more effective for reinforcement learning in robotics. To verify our hypothesis, we designed a framework for hindsight experience prioritization based on the trajectory energy of goal states. The trajectory energy function takes the potential, kinetic, and rotational energy into consideration. We evaluate our Energy-Based Prioritization (EBP) approach on four challenging robotic manipulation tasks in simulation. Our empirical results show that our proposed method surpasses state-of-the-art approaches in terms of both performance and sample-efficiency on all four tasks, without increas- ing computational time. A video showing experimental results is available at https://youtu.be/jtsF2tTeUGQ. }
}
```

## Licence:

MIT