[![Video_Clip_Thumbnail](images/video_clip_thumbnail.PNG)](https://youtu.be/2-Y8vzH2t5g)

# Learning in Growing Robots: Knowledge Transfer from Tadpole to Frog Robot

This is a part of an ongoing project exploring the relation between varying structure and learning. We use the growing process from a tadpole to a frog as the model. The task is to swim to a randomly generated target position. Between different growing stages, weights of both the policy and value networks are directly transferred. In this way, better parameter initialization provides an initial performance boost and accelerates convergence. It is interesting to see that transfer learning is beneficial even with robots with different structures.

Preliminary results can be found in [Learning in Growing Robots: Knowledge Transfer from Tadpole to Frog Robot](https://link.springer.com/chapter/10.1007/978-3-030-24741-6_42) 

# Cite This Work

@inproceedings{zhu2019learning,
  title={Learning in Growing Robots: Knowledge Transfer from Tadpole to Frog Robot},
  author={Zhu, Yiheng and Rossiter, Jonathan and Hauser, Helmut},
  booktitle={Conference on Biomimetic and Biohybrid Systems},
  pages={378--382},
  year={2019},
  organization={Springer}
}

# Installation

This has only been tested in Windows 10.

1. Install Unity (Simulation Engine)

Unity 2017.4.1 (version is important): https://unity3d.com/get-unity/download/archive

2. Install Anaconda (Python)

Python 3.6.8 (Anaconda 4.5.12): https://www.anaconda.com/distribution/

Please remember to add Anaconda to the `PATH` environment variable.

3. Install Tensorflow (Neural Network)

Open Anaconda Prompt and type

```
conda create -n growvenv python=3.6
activate growvenv
pip install tensorflow==1.7.1
```

4. Install ML-Agents Toolkit (Reinforcement Learning)

Make sure the virtual environment `growvenv` is activated.

```
git clone https://github.com/Unity-Technologies/ml-agents.git
cd ml-agents
pip install -e .
```

# Simulation Setup

You can use the our froglet model or create your own.

1. Open Unity and click "New". Name your project, select "3D" Template, and click "create project".

2. Open "Edit==>Project Settings==>Player". Under "Other Settings==>Configuration==>Scripting Runtime Version", change "Stable (.NET 3.5 Equivalent)" to "Experimental (.NET 4.6 Equivalent)" and confirm "Restart".

3. Choose "Assets==>Import Package==>Custom Package..." then navigate and open "froglet.unitypackage". With all items selected, click "Import".

4. In "Project==>Assets==>Scenes", open "froglet". Now the simulation is ready to run.

# Model Verification in Player Mode

You can modify model parameters until everything is right for you.

1. Choose "Hierarchy==>froglet==>Academy". In "Inspector==>Tadpole Academy (Script)==>Broadcast Hub==>Brain", untick the "control" box.

2. Choose "Hierarchy==>froglet==>Head". In "Inspector==>Tadpole Agent (Script)==>Brain", click the dartboard symbol and select "TadpolePlayer".

3. Press the play button. "s" and "d" for the neck joint, "z" and "x" for the left hip joint, and "c" and "v" for the right hip joint.

4. Press the play button again to finish the simulation.

In "Hierarchy==>froglet==>Head", you can change model parameters in "Inspector==>Tadpole Agent (Script)". Or you can change model parameters in code by opening "Project==>Assets==>Scripts==>TadpoleAgent.cs".

# Training from Scratch

You can train a decision making policy from scratch.

1. Choose "Hierarchy==>froglet==>Academy". In "Inspector==>Tadpole Academy (Script)==>Broadcast Hub==>Brain", tick the "control" box.

2. Choose "Hierarchy==>froglet==>Head". In "Inspector==>Tadpole Agent (Script)==>Brain", click the dartboard symbol and select "TadpoleBrain".

3. Open an Anaconda Prompt and navigate to the "Assets" folder in your project directory.

4. Activate the virtual environment by typing `activate growvenv`.

5. Start training by typing `mlagents-learn Config\config.yaml --run-id=tadpole_learn_id01 --keep-checkpoints=10000 --seed=1 --train`. After seeing the Unity icon and training information, press the play button in the Unity window.

6. Normally, you would wait the training to finish by itself. To interrupt the training, you can press the play button in the Unity window again, or "ctrl+c" in the Anaconda Prompt.

In "Project==>Assets==>Config", you can change the training parameters in "config.yaml". If you are familiar with Tensorflow, you can create your customized network structure in the "create_cc_actor_critic" function in "ml-agents/ml-agents/trainers/models.py".

# Testing

You can test your training result now.

1. Choose "Hierarchy==>froglet==>Academy". In "Inspector==>Tadpole Academy (Script)==>Broadcast Hub==>Brain", untick the "control" box.

2. Choose "Hierarchy==>froglet==>Head". In "Inspector==>Tadpole Agent (Script)==>Brain", click the dartboard symbol and select "TadpoleBrain".

3. Choose "Project==>Assets==>Brains", put a copy of "TadpoleBrain.nn" to "Inspector==>Model". "TadpoleBrain.nn" can be found in "project_name/Assets/models/tadpole_learn_id01/".

4. Press the play button and the froglet should swim using the trained policy.

5. Press the play button again to finish simulation.

# Continue Training from an Existing Model

You can train from an existing decision making policy.

1. Choose "Hierarchy==>froglet==>Academy". In "Inspector==>Tadpole Academy (Script)==>Broadcast Hub==>Brain", tick the "control" box.

2. Choose "Hierarchy==>froglet==>Head". In "Inspector==>Tadpole Agent (Script)==>Brain", click the dartboard symbol and select "TadpoleBrain".

3. Open an Anaconda Prompt and navigate to the "Assets" folder in your project directory.

4. Activate the virtual environment by typing `activate growvenv`.

5. In "Project==>Assets==>Config", you can change the "max_steps" to a larger number in "config.yaml".

6. Continue training by typing `mlagents-learn Config\config.yaml --run-id=tadpole_learn_id01 --keep-checkpoints=10000 --seed=1 --load --train`. After seeing the Unity icon and training information, press the play button in the Unity window.

6. Normally, you would wait the training to finish by itself. To interrupt the training, you can press the play button in the Unity window again, or "ctrl+c" in the Anaconda Prompt.

# License

MIT License
