# Super Mario Reinforcement Learning
 The purpose of this code is to train a reinforcement learning (RL) agent to play the Super Mario Bros video game. RL is a branch of machine learning that involves an agent interacting with an environment and learning through trial and error to maximize a reward signal. In the case of Super Mario Bros, the agent's goal is to score as many points as possible by navigating through the game and avoiding obstacles while collecting coins and power-ups.

The Stable Baselines 3 library is used to implement the Proximal Policy Optimization (PPO) algorithm for training the RL agent. PPO is a popular RL algorithm that has been shown to work well on a variety of environments, including Super Mario Bros.

To interact with the game environment, the OpenAI Gym library is used. Gym provides a standardized interface for interacting with RL environments, which makes it easy to switch between different environments and algorithms.

Before training the agent, the game environment is wrapped in several custom wrappers to preprocess the observations and actions. The SkipFrame wrapper reduces the frame rate by returning only every skip-th frame of the original environment. This can help speed up training by reducing the amount of computation needed to process each frame. The GrayScaleObservation wrapper converts the RGB observation image into a grayscale image, which reduces the dimensionality of the observation space. This can help the agent learn faster by simplifying the input data. The ResizeObservation wrapper downsamples the grayscale image to a smaller size of 84x84 pixels. This further reduces the dimensionality of the observation space and makes it easier for the agent to learn. The FrameStack wrapper stacks multiple observation frames to provide the agent with temporal information about the game state. This can help the agent learn to anticipate future events in the game.

After the environment is fully preprocessed, it is wrapped with the JoypadSpace wrapper to simplify the controls. This wrapper maps the available actions in the environment to a smaller set of actions that are easier for the agent to learn. The DummyVecEnv wrapper is used to vectorize the environment for parallel execution. This can help speed up training by allowing the agent to process multiple observations at once. The VecFrameStack wrapper is used again to stack frames in the vectorized environment.

The code defines a custom TrainAndLoggingCallback class that inherits from the BaseCallback class of Stable Baselines 3. This callback saves the trained model every check_freq number of training steps in the specified directory. This can be useful for resuming training later or for testing the trained model on new data.

Finally, the code trains the agent using the PPO algorithm and logs the progress using the TrainAndLoggingCallback class. After training, the agent is ready to play Super Mario Bros using the learned policy. The policy is essentially a mapping from observations to actions that the agent has learned during training. The policy can be used to play the game autonomously or to control the agent in a human-in-the-loop setting. Overall, this code provides a useful example of how RL can be used to train agents for complex tasks like playing video games.

https://user-images.githubusercontent.com/43640144/225727366-4628e954-655a-46c6-8ccc-4d6ca7f773be.mp4


