In addition to the original repository, I further provide addtional trained networks with Collision Avoidance guidance. 
The performance is shown below for some test datasets which were not seen during training.
In most of the cases as below, its observed that the trained DDPG RL policy fits very closely to the optimal policy solved by MPC.

The architecture is changed as compared to the architecture in the original repository. Two hidden layers of 30 Neurons each with ReLU activation function are used for all Actor-Critic Evaluation & Target Networks to achieve the below performance. Collision avoidance guidance is activated and TTC is kept same. 

LV--> Leading Vehicle <br/>
SV--> Simulated Vehicle/ FOllower Vehicle <br/>
RL--> using DDPG Reinforcement Learning <br/>
MPC--> Using Model predictive control <br/>

![image](https://user-images.githubusercontent.com/83720464/147878177-0584e828-ccec-4bb0-b73a-d632bcc5ad67.png)

![image](https://user-images.githubusercontent.com/83720464/147878190-c573c5d1-7d57-4bcc-a456-69583d45c07c.png)

![image](https://user-images.githubusercontent.com/83720464/147878195-43143b3b-d012-4a16-8023-66640312cc0d.png)

However, In the below case, its observed that the trained DDPG RL policy largely differs from the optimal policy solved by MPC even if the Objective function is kept identical.
The possible reasons could be that the control solution from MPC is optimal under the assumption that the N-step future Prediction of the states is correctly pursued by the Leading and the Following vehicle which ofcourse is not guaranteed to happen in the data. In this regard, the reinforcement learning approach is more promising as it doesnt need the N-step future prediction of the states and infact calculates the optimal policy using only the current state information. 

![image](https://user-images.githubusercontent.com/83720464/147878227-66a2d71d-1c97-41bd-abb4-a5131e4c9d4d.png)

This is the modified version of the Original Repository.

# Below the contents from the [Original](https://github.com/MeixinZhu/Velocity_control) Repository

# Safe, efficient, and comfortable velocity control based on reinforcement learning for autonomous driving
Source code for paper Zhu, M., Wang, Y., Pu, Z., Hu, J., Wang, X., & Ke, R. (2020). Safe, efficient, and comfortable velocity control based on reinforcement learning for autonomous driving. Transportation Research Part C: Emerging Technologies, 117, 102662. https://www.sciencedirect.com/science/article/pii/S0968090X20305775 

## Description
Use DDPG for car following velocity control. The key part is the design of reward function. If the reward is not properly designed, the vehicle will either has poor jerk performances or stop there with zero speed (in this case the jerk is zero). So the weights between different objectives are important.

## Data format
Each element (cell or matrix) in the trainSet.mat and testSet.mat describes a car-following event. For each matrix (event), the columns are spacing, following vehicle speed, relative speed, leading vehilce speed. Events may have different durations. 

## How to run
- Set up python environment by installing the required packages according to requirements.txt
- Directly run Main.ipynb
- simulation_env is the simulaition environment for car following
- MPC_acc is the MPC based ACC implementation. This is a baseline. 

## Citation 
@article{zhu2020safe,
  title={Safe, efficient, and comfortable velocity control based on reinforcement learning for autonomous driving},
  author={Zhu, Meixin and Wang, Yinhai and Pu, Ziyuan and Hu, Jingyun and Wang, Xuesong and Ke, Ruimin},
  journal={Transportation Research Part C: Emerging Technologies},
  volume={117},
  pages={102662},
  year={2020},
  publisher={Elsevier
}
