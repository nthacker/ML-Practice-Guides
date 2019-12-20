# Reinforcement learning

The reinforcement learning approach is concerned with optimizing the actions of a software agent operating in a given environment such that a given reward function is optimized.

Reinforcement learning differs from supervised learning by the fact that labeled cases are not needed for training. It also differs from unsupervised learning by the goal (objective) function. The most important thing that differentiates reinforcement learning from both supervised and unsupervised learning is its active characteristic. Supervised and unsupervised learning are passive approaches where learning is performed without any actions that could influence what data could be observed in the future. Reinforcement learning is an active approach where the actions of the agent influence the environment, hence the data that could be observed in the future, hence its own potential future states.

These properties make reinforcement learning appropriate in scenarios like game and control theory, robotics, and autonomous driving.

In most cases, the environment is modeled as a Markov Decision Process (MDP). Algorithms do not assume an exact knowledge of the MDP and that's the very fact that makes them suitable for scenarios like the above mentioned ones, where identifying an exact mathematical model of the MDP is infeasible.