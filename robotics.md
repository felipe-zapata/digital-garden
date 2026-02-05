# Robotics

## Resources

<details>

<summary>VLA</summary>

I started from a solid background in ML so I was fine catching-up with the first papers. I did read quickly through a few robotics classes like the one you linked, which seems particularly complete.\
But I agree with you, there are many papers trying many things promising amazing results but which completely fail once you try to use it.

Assuming you're familiar with Transformers, how we build VLMs, and how diffusion models works, these papers are very good starts (and well written):\
\- RT-1 <- a first good paper for what I truly call "VLA"\
\- RT-2 <- the first truly big model (55B!)\
\- OpenVLA <- an open-source, very VLM-like model\
\- DiffusionPolicy/Octo <- how diffusion models can be very useful for learning actions\
\- Pi0 / Pi0.5 <- considered SotA\
\- OpenVLA-OFT <- goes into details on how to go from a VLM to a truly robotics dedicated VLA for maximum performances\
\- Open-X Embodiment / BridgeV2 / DROID <- 3 open-source datasets you need to be familiar with (the first includes the 2 other)

It also helps a lot being familiar with deep RL, especially the problem setting vocabulary (markov decision problems, policies, rewards), and the idea of behavior cloning / imitation learning.

VLA are also connected a lot to world models (there's a whole field dedicated to it) and simulation (classical simulators or learned simulators). There's also a big discussion on evaluation: it's practically impossible to replicate the real-life evaluation setting due to difference in environment and robot hardware, so we resort to simulated benchmark but it's not as good as real-life so most papers report results in simulated benchmarks AND real-life runs.\
Simulated benchmarks: CALVIN, LIBERO, SimplerEnv.

course(CS 326 - Topics in Advanced Robotic Manipulation) - [https://web.stanford.edu/class/cs326/](https://web.stanford.edu/class/cs326/)

[https://github.com/keon/awesome-physical-ai](https://github.com/keon/awesome-physical-ai)

</details>

## Kits

[https://github.com/TheRobotStudio/SO-ARM100](https://github.com/TheRobotStudio/SO-ARM100)
