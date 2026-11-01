# Experiment 6: 180-Degree Rotated-Obstacle Ablation Study

## Objective

Experiment 6 investigates the robustness of Sparse Q-Learning and Potential-Based Reward Shaping (PBRS) methods under a 180-degree rotation of the original Experiment 4 obstacle configuration.

Only the obstacle coordinates are rotated. The start position, goal position, learning algorithms, hyperparameters, and training budget remain unchanged.

## Experimental Configuration

- Grid size: 20 × 20
- Start position: (0, 0)
- Goal position: (19, 19)
- Obstacles: 57
- Obstacle rotation: 180° from the original Experiment 4 configuration
- Shortest valid path: 38 steps
- Training episodes: 3,000
- Random seeds: 10
- Maximum steps per episode: 600
- Learning rate: 0.10
- Discount factor: 0.99
- Epsilon start: 1.0
- Epsilon minimum: 0.05
- Epsilon decay: 0.997
- Initial shaping weight: 1.0
- Success evaluation window: 50 episodes

## Compared Methods

1. Sparse Q-Learning
2. Fixed PBRS with Manhattan Potential
3. Adaptive PBRS with Manhattan Potential
4. Fixed PBRS with Obstacle-Aware Potential
5. Adaptive PBRS with Obstacle-Aware Potential

## Experimental Results

| Method | Final Success Rate (%) | Success SD | Average Steps to Goal | Seeds Reaching 90% | Episodes to 90% Success |
|---|---:|---:|---:|---:|---:|
| Sparse Q-Learning | 100.00 | 0.00 | 41.46 | 10 | 336.20 |
| Fixed PBRS Manhattan | 50.10 | 52.60 | 40.02 | 5 | 222.20 |
| Adaptive PBRS Manhattan | 60.00 | 51.64 | 40.69 | 6 | 309.83 |
| Fixed PBRS Obstacle-Aware | 100.00 | 0.00 | 40.24 | 10 | 84.70 |
| Adaptive PBRS Obstacle-Aware | 100.00 | 0.00 | 41.11 | 10 | 80.80 |

Note: Episodes to 90% Success are averaged only across seeds that reached the threshold.

## Key Findings

- Adaptive PBRS Obstacle-Aware achieved the fastest mean convergence at 80.80 episodes.
- Fixed PBRS Obstacle-Aware achieved a mean convergence of 84.70 episodes.
- Both obstacle-aware methods achieved 100% final success across all 10 seeds.
- Sparse Q-Learning also achieved 100% final success but required 336.20 episodes on average to reach the convergence threshold.
- Manhattan-based methods exhibited substantial variation across random seeds and lower final success rates.

## Conclusion

Experiment 6 demonstrates that obstacle-aware potential functions support faster convergence and consistent final success in the evaluated 180-degree rotated obstacle configuration.

The findings support further comparison across the original, 90-degree, and 270-degree configurations to assess robustness under different obstacle orientations.

## Reproducibility

The experiment uses the original Experiment 4 obstacle coordinates, transformed using:

`(row, col) -> (19 - row, 19 - col)`

All other experimental parameters are retained.

## Experiment Files

- `Experiments6.ipynb` — Experiment 6 implementation
- `experiment6_summary.csv` — Aggregated performance metrics
- `experiment6_seed_results.csv` — Individual seed-level results
- `exp6.pdf` — Experimental output, graphs, and environment visualization
