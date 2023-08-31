![Python 3.8 3.9](https://github.com/f1tenth/f1tenth_gym/actions/workflows/ci.yml/badge.svg)
![Docker](https://github.com/f1tenth/f1tenth_gym/actions/workflows/docker.yml/badge.svg)
# F1TENTH Simulator

This is the repository of the F1TENTH Simulator. This simulator is OpenAI Gym based and contains a 2D Simulator for the F1TENTH autonomous
racecar that is using [2D maps of racetracks](https://github.com/f1tenth/f1tenth_racetracks).

![F1TENTH GYM overview](docs/figs/gym_overview.png)


This project is still under heavy developement.

The F1TENTH Gym communicates with your autonomous vehicle software via actions and observations. You can find a detailed [documentation](https://f1tenth-gym.readthedocs.io/en/latest/) of the F1TENTH Gym here.

## Quickstart
We recommend installing the simulation inside a virtualenv. You can install the environment by running:

```bash
virtualenv gym_env
source gym_env/bin/activate
git clone https://github.com/f1tenth/f1tenth_gym.git
cd f1tenth_gym
pip install -e .
```

Then you can run a quick waypoint follow example by:
```bash
cd examples
python3 waypoint_follow.py
```

A Dockerfile is also provided with support for the GUI with nvidia-docker (nvidia GPU required):
```bash
docker build -t f1tenth_gym_container -f Dockerfile .
docker run --gpus all -it -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix f1tenth_gym_container
````
Then the same example can be ran.

## Known issues
- Library support issues on Windows. You must use Python 3.8 as of 10-2021
- On MacOS Big Sur and above, when rendering is turned on, you might encounter the error:
```
ImportError: Can't find framework /System/Library/Frameworks/OpenGL.framework.
```
You can fix the error by installing a newer version of pyglet:
```bash
$ pip3 install pyglet==1.5.11
```
And you might see an error similar to
```
gym 0.17.3 requires pyglet<=1.5.0,>=1.4.0, but you'll have pyglet 1.5.11 which is incompatible.
```
which could be ignored. The environment should still work without error.

## Citing
The F1TENTH Gym is explained in the paper ["F1TENTH: An Open-source Evaluation Environment for Continuous Control and Reinforcement Learning"](https://proceedings.mlr.press/v123/o-kelly20a.html) and ["Teaching Autonomous Systems Hands-On: Leveraging Modular Small-Scale Hardware in the Robotics Classroom"](https://proceedings.mlr.press/v123/o-kelly20a.html). If you find the information in this repository useful we would be happy if you cite it based on the following definition:

```
@inproceedings{okelly2020f1tenth,
  title={F1TENTH: An Open-source Evaluation Environment for Continuous Control and Reinforcement Learning},
  author={O’Kelly, Matthew and Zheng, Hongrui and Karthik, Dhruv and Mangharam, Rahul},
  booktitle={NeurIPS 2019 Competition and Demonstration Track},
  pages={77--89},
  year={2020},
  organization={PMLR}
}

@article{betz2022_f1tenth,
Author = {Johannes Betz and Hongrui Zheng and Zirui Zang and Florian Sauerbeck and Krzysztof Walas and Velin Dimitrov and Madhur Behl and Rosa Zheng and Joydeep Biswas and Venkat Krovi and Rahul Mangharam},
Title = {Teaching Autonomous Systems Hands-On: Leveraging Modular Small-Scale Hardware in the Robotics Classroom},
Year = {2022},
Eprint = {arXiv:2209.11181},
}

```
