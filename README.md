# Disaster Relief UAV Route Optimization

AI-assisted UAV route planning and payload-aware decision support system for disaster response scenarios.

This repository contains a reinforcement learning based UAV navigation pipeline designed for simulated disaster environments. The project focuses on autonomous route planning, obstacle-aware navigation, and mission-oriented decision making for unmanned aerial vehicles operating in challenging environments.

## Overview

In disaster response operations, UAVs can support search, assessment, and delivery missions by reaching locations that may be dangerous or inaccessible for human teams. However, these missions require efficient route planning, safe navigation, and reliable decision making under environmental constraints.

This project explores how deep reinforcement learning can be used to train UAV agents in simulation environments. The system is built around AirSim-based UAV simulation, Gym-compatible environment structures, configurable training scenarios, and Stable-Baselines3 reinforcement learning algorithms.

## Key Features

* Reinforcement learning based UAV navigation
* AirSim-compatible simulation setup
* Gym-style custom environment integration
* Multirotor and fixed-wing configuration support
* 2D and 3D navigation scenario configuration
* Depth-based perception support
* PPO and TD3 based training options
* Training and evaluation scripts with visualization support
* Configurable environment, reward, model, and DRL parameters
* Experiment logging and model saving structure

## Project Structure

```text
.
├── airsim_settings/          # AirSim configuration files
├── configs/                  # Environment and training configuration files
├── gym_env/                  # Custom Gym environment package
├── resources/                # Maps, figures, results, and visual resources
├── scripts/                  # Training and evaluation scripts
├── stable-baselines3/        # Reinforcement learning framework submodule
├── tools/                    # Utility tools
├── README.md
└── .gitmodules
```

## Main Components

### Simulation Environment

The project uses AirSim-compatible settings and custom Gym environments to simulate UAV navigation tasks. The environment configuration files define parameters such as navigation type, perception mode, reward structure, vehicle dynamics, and reinforcement learning settings.

Example configuration options include:

* `dynamic_name = Multirotor`
* `navigation_3d = True`
* `perception = depth`
* `algo = PPO`
* `policy_name = CNN_GAP`
* `reward_type = reward_final`

### Reinforcement Learning Pipeline

The training pipeline supports deep reinforcement learning algorithms through Stable-Baselines3. The implementation includes model training, logging, environment interaction, and model saving.

Supported/used RL algorithms include:

* PPO
* TD3

The training setup can be configured with parameters such as:

* total timesteps
* learning rate
* discount factor
* batch size
* network architecture
* action noise
* perception type

### Visualization

The project includes PyQt-based visualization scripts for monitoring training and evaluation. These scripts can display UAV state, depth perception, rewards, and trajectory-related outputs during execution.

## Installation

Clone the repository:

```bash
git clone https://github.com/Atabeydem/Disaster-Relief-UAV-Route-Optimization-.git
cd Disaster-Relief-UAV-Route-Optimization-
```

Initialize submodules:

```bash
git submodule update --init --recursive
```

Install the local Gym environment package:

```bash
cd gym_env
pip install -e .
cd ..
```

Install the required Python dependencies according to your environment. The project uses Python-based reinforcement learning and simulation libraries such as:

```bash
pip install gym numpy torch pyqt5 wandb stable-baselines3
```

> Note: AirSim must be installed and configured separately. Make sure that the AirSim simulator is running with the appropriate UAV settings before starting training or evaluation.

## AirSim Configuration

AirSim setting files are located under:

```text
airsim_settings/
```

Example files:

```text
settings_multirotor.json
settings_simpledynamics.json
```

Copy the appropriate settings file into your AirSim settings directory before running the simulation.

## Training

To start the training interface:

```bash
python scripts/start_train_with_plot.py
```

The default training script uses a configuration file from the `configs/` directory. You can modify the selected configuration inside the script or adapt it to accept command-line arguments.

Example configuration file:

```text
configs/config_Maze_SimpleMultirotor_3D.ini
```

## Evaluation

To evaluate a trained model with visualization:

```bash
python scripts/start_evaluate_with_plot.py
```

Before running evaluation, make sure that the model path and configuration path inside the evaluation script match your trained model directory.

Example expected structure:

```text
experiment_folder/
├── config/
│   └── config.ini
└── models/
    └── model_sb3.zip
```

## Example Workflow

```bash
# 1. Clone repository
git clone https://github.com/Atabeydem/Disaster-Relief-UAV-Route-Optimization-.git
cd Disaster-Relief-UAV-Route-Optimization-

# 2. Initialize submodules
git submodule update --init --recursive

# 3. Install custom gym environment
cd gym_env
pip install -e .
cd ..

# 4. Start AirSim simulator

# 5. Run training
python scripts/start_train_with_plot.py

# 6. Run evaluation
python scripts/start_evaluate_with_plot.py
```

## Technologies Used

* Python
* AirSim
* OpenAI Gym
* Stable-Baselines3
* PyTorch
* NumPy
* PyQt5
* Weights & Biases
* Reinforcement Learning
* UAV Simulation

## Use Case

This project is designed as a research and development prototype for UAV-assisted disaster response scenarios. The system can be adapted for tasks such as:

* autonomous UAV route planning
* obstacle-aware navigation
* simulated emergency logistics
* disaster area exploration
* payload-aware mission planning
* reinforcement learning based flight policy optimization

## Results and Outputs

The repository includes folders for experiment resources, figures, maps, and results. Trained models and logs are generated during the training process and can be used for later evaluation and comparison.

## Future Improvements

Potential future development directions include:

* adding multi-UAV coordination
* improving payload constraint modeling
* integrating real-world map data
* adding dynamic obstacle scenarios
* improving reward design for mission-specific objectives
* adding benchmark comparisons between PPO, TD3, and SAC
* improving documentation for reproducible experiments
* containerizing the project with Docker

## Authors

- Recep Atabey Demir
- Bartu Hacılar
- Mert Akkan
- Adnan Avcı
- Bersay Yakıcı

## License

This repository does not currently specify a license. Please contact the author before using or redistributing the project.
