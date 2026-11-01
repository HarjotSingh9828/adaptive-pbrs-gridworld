# Experiment 5: 90-Degree Rotated-Obstacle Ablation

## Objective
Evaluate the performance of Sparse Q-Learning, Fixed PBRS, and Adaptive PBRS using Manhattan and obstacle-aware potentials after rotating the original obstacles 90 degrees clockwise.

## Experimental Setup
- Grid size: 20 × 20
- Start: (0, 0)
- Goal: (19, 19)
- Obstacles: 57
- Rotation: 90° clockwise
- Episodes: 3,000
- Random seeds: 10
- Maximum steps per episode: 600
- Learning rate: 0.10
- Discount factor: 0.99
- Exploration: epsilon-greedy

## Results

| Method | Final Success Rate (%) | Episodes to 90% Success |
|---|---:|---:|
| Sparse Q-Learning | 100.00 | 430.60 |
| Fixed PBRS Manhattan | 0.15 | Not reached |
| Adaptive PBRS Manhattan | 10.00 | 727.00 |
| Fixed PBRS Obstacle-Aware | 100.00 | 86.10 |
| Adaptive PBRS Obstacle-Aware | 70.70 | 213.25 |

Convergence values are averaged only across seeds that reached the 90% rolling-success threshold.

## Key Observations
Fixed PBRS with obstacle-aware potential achieved 100% final success and the fastest reported convergence. Sparse Q-Learning also achieved 100% final success but required more episodes to reach the convergence threshold.

Manhattan-based shaping performed poorly in this rotated configuration, while adaptive obstacle-aware shaping exhibited substantial seed-to-seed variation.

## Files
- experiment5_summary.csv
- experiment5_seed_results.csv
- exp5.pdf (experiment output report)

These results describe Experiment 5 only and do not establish performance across all obstacle rotations.
