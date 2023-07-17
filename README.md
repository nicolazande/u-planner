# u-planner (Uncertainty Planner)

u-planner is a Python project that implements an uncertainty-based path planning algorithm. It focuses on minimizing collision probability by bringing it below a specific threshold, which is determined based on the task requirements. The algorithm incorporates chance constraints to ensure probabilistic feasibility in the presence of uncertainty and process noise.

## Introduction

Traditional path planning algorithms often overlook the impact of uncertainty and probabilistic feasibility. u-planner introduces a risk-bounded approach that considers the frequency of uncertainty realization and builds probability distributions accordingly. The objective is to minimize the collision probability by satisfying specific chance constraints, thus ensuring safe and reliable path planning.

The underlying concept, inspired by CC-RRT* [21], combines ABIT* with chance constraints for probabilistic feasibility in linear systems subject to uncertainty. Assuming Gaussian noise, probabilistic feasibility is established by simulating the state conditional mean and evaluating linear constraints. The distribution of the state, represented as a random variable xt, follows a Gaussian distribution, and the dynamical system involving the mean x̂t and covariance Pxt is represented implicitly.

To ensure collision probability remains below a threshold (∆ = 1 - psafe), the algorithm checks the probability of collision with each obstacle individually. By representing obstacles as linear inequalities, the probability of satisfying a single constraint is shown to be greater than the probability of satisfying all constraints simultaneously. Thus, U-Planner aims to ensure that at least one constraint defining each obstacle is satisfied with a probability less than or equal to ∆/NB.

## Implementation

The U-Planner algorithm extends the ABIT* framework by considering uncertainty and probabilistic constraints. It introduces the concept of chance constraints, where the probability of collision with each obstacle is evaluated to maintain overall safety. The algorithm propagates mean and covariance values using simulations based on the available robot model and dynamics. The simulation ensures probabilistic feasibility and allows for additional safety bounds during collision checking. U-Planner provides two approaches: one in task space and another in joint space, each with its own advantages and considerations.

## Usage

To use U-Planner in your Python project, follow these steps:

1. Clone the repository:

   ```shell
   git clone https://github.com/nicolazande/u-planner.git
