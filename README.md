# Self-Learning Exploration and Mapping for Mobile Robots via Deep Reinforcement Learning
This repository contains code for robot exploration with Deep Reinforcement Learning (DRL). The agent utilizes the local structure of the environment to predict robot’s optimal sensing action. A demonstration video can be found [here](https://www.youtube.com/watch?v=2gNF6efv12s).

<p align='center'>
    <img src="/doc/exploration.png" alt="drawing" width="1000"/>
</p>

<p align='center'>
    <img src="/doc/policy.gif" alt="drawing" width="1000"/>
</p>

## Dependency

The pybind11 should be install without anaconda virtual environment.

- [pybind11](https://github.com/pybind/pybind11) (pybind11 — Seamless operability between C++11 and Python)
  ```
  git clone https://github.com/pybind/pybind11.git
  cd pybind11
  mkdir build && cd build
  cmake ..
  sudo make install
  ```
## Compile

```
git clone https://github.com/RobustFieldAutonomyLab/DRL_robot_exploration.git

I merge the python dependencies in requirements.txt (in this repo), so you should download the requirments.txt or use the cmd below.

git clone https://github.com/hahakid/DRL_robot_exploration.git
```



First prepare anaconda envs:
```
cd DRL_robot_exploration
#for tf-gpu=2.1.0 
conda install cudatoolkit=10.1
conda install cudnn=7.6
pip install -r requirements.txt

```
Please ref below image for local tf version:

<p align='center'>
    <img src="/doc/tf.png" alt="drawing" width="1000"/>
</p>
Newest version can be found [tf_installation_problems](https://www.tensorflow.org/install/source#common_installation_problems)

```
changing the path to the conda Python in CMakeList.txt (make sure the second line is changed at least).
set(PYTHON_EXECUTABLE /home/local_machine_name/anaconda3/envs/your_virtual_env_name/bin/python3)

mkdir build && cd build
cmake ..
make
```



You can use the following commands to download and compile the package.
```
git clone https://github.com/RobustFieldAutonomyLab/DRL_robot_exploration.git
cd DRL_robot_exploration
mkdir build && cd build
cmake ..
make
```





## How to Run? (I use pycharm instead.)
- For the CNN policy:
    ```
    cd DRL_robot_exploration/scripts
    make sure TRAIN = Ture (Line 13)
    python tf_policy_cnn.py
    ```
- For the RNN policy:
    ```
    cd DRL_robot_exploration/scripts
    make sure TRAIN = Ture (Line 13)
    python tf_policy_rnn.py
    ```
- To select the running mode, at the beginning of the tf_policy code:
    ```
    # select mode
    TRAIN = False
    PLOT = True
    ```
  Set ``TRAIN=False`` to run the saved policy. You can train your own policy by setting ``TRAIN=True``. Set `` PLOT=True `` to show visualization plots.
 
- To show the average reward during the training:
    ```
    cd DRL_robot_exploration
    tensorboard --logdir=log
    ```

## Cite

Please cite [original paper](https://www.researchgate.net/profile/Fanfei_Chen/publication/330200308_Self-Learning_Exploration_and_Mapping_for_Mobile_Robots_via_Deep_Reinforcement_Learning/links/5d6e7ad4a6fdccf93d381d2e/Self-Learning-Exploration-and-Mapping-for-Mobile-Robots-via-Deep-Reinforcement-Learning.pdf) if you use any of this code: 
```
@inproceedings{ExplorDRL2019,
  title={Self-Learning Exploration and Mapping for Mobile Robots via Deep Reinforcement Learning},
  author={Chen, Fanfei and Bai, Shi and Shan, Tixiao and Englot, Brendan},
  booktitle={AIAA SciTech Forum},
  pages={0396},
  year={2019},
}
```

## Reference
- [DeepRL-Agents](https://github.com/awjuliani/DeepRL-Agents)
- [DeepLearningFlappyBird](https://github.com/yenchenlin/DeepLearningFlappyBird)
- [Random Dungeon Generator](http://perplexingtech.weebly.com/random-dungeon-demo.html)
- [PyAstar](https://github.com/hjweide/pyastar)
