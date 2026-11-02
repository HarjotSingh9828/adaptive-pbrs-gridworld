# Experiment 7: 270-Degree Clockwise Rotated-Obstacle Ablation

## Objective

Experiment 7 evaluates the robustness of five Q-Learning and Potential-Based Reward Shaping (PBRS) methods under a 270-degree clockwise rotation of the original Experiment 4 obstacle configuration.

The rotation is applied directly to the original Experiment 4 obstacles, not to the obstacles of Experiments 5 or 6.

## Experimental Setup

- Grid size: 20 × 20
- Start: (0, 0)
- Goal: (19, 19)
- Number of obstacles: 57
- Rotation: 270° clockwise
- Shortest valid path: 38 steps
- Training episodes: 3,000
- Random seeds: 10
- Maximum steps per episode: 600
- Learning rate: 0.10
- Discount factor: 0.99
- Initial epsilon: 1.0
- Minimum epsilon: 0.05
- Epsilon decay: 0.997
- Initial shaping weight: 1.0
- Success adaptation window: 50 episodes
- Final evaluation window: 200 episodes

## Compared Methods

1. Sparse Q-Learning
2. Fixed PBRS Manhattan
3. Adaptive PBRS Manhattan
4. Fixed PBRS Obstacle-Aware
5. Adaptive PBRS Obstacle-Aware

## Experimental Results

| Method | Final Success (%) | Success SD | Average Steps | Seeds Reaching 90% | Episodes to 90% |
|---|---:|---:|---:|---:|---:|
| Sparse Q-Learning | 100.0 | 0.0 | 41.51 | 10 | 406.8 |
| Fixed PBRS Manhattan | 0.0 | 0.0 | N/A | 0 | N/A |
| Adaptive PBRS Manhattan | 30.0 | 48.3 | 40.25 | 3 | 581.0 |
| Fixed PBRS Obstacle-Aware | 100.0 | 0.0 | 40.17 | 10 | 82.3 |
| Adaptive PBRS Obstacle-Aware | 100.0 | 0.0 | 40.30 | 10 | 286.2 |

Convergence averages are calculated only over seeds reaching the 90% rolling-success threshold.

## Key Findings

- Fixed PBRS Obstacle-Aware achieved the fastest mean convergence at 82.3 episodes.
- Adaptive PBRS Obstacle-Aware achieved 100% final success with convergence at 286.2 episodes.
- Sparse Q-Learning achieved 100% final success but converged more slowly at 406.8 episodes.
- Fixed PBRS Manhattan achieved 0% final success and did not reach the 90% convergence threshold in any seed.
- Adaptive PBRS Manhattan achieved 30% final success, indicating substantial sensitivity to the rotated obstacle configuration.

## Conclusion

The 270-degree rotated environment demonstrates the effectiveness of obstacle-aware potential functions for achieving consistent final success.

Fixed PBRS Obstacle-Aware achieved the fastest convergence in this experiment, while both obstacle-aware methods achieved 100% final success across all seeds.

These findings highlight the importance of potential-function selection and motivate comparison across the original, 90-degree, 180-degree, and 270-degree obstacle configurations.

## Reproducibility

The original Experiment 4 obstacles are transformed using:

`(row, col) -> (19 - col, row)`

The learning algorithms, hyperparameters, training budgets, and evaluation procedures remain unchanged.

## Files

- `Experiments7.ipynb` — Experiment 7 code
- `experiment7_summary.csv` — Aggregated results
- `experiment7_seed_results.csv` — Results for all 10 seeds per method
- `exp7.pdf` — Experimental outputs and visualizations
