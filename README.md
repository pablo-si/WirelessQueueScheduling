# Wireless Queue Scheduling with Deep Reinforcement Learning

A Python simulation of **wireless packet scheduling for 12 users** with time-varying channel service rates and finite queues. The project develops a **Deep Q-Network (DQN)** scheduler and provides comparison experiments against conventional scheduling policies and a beam-search lookahead benchmark.

## Scheduling problem

At each time slot, the scheduler chooses **one user** to serve. Queue lengths evolve through packet arrivals and transmission, while channel service rates follow a synthetic 12-user trace. The objective balances delivered packets against packet losses:

$$
\mathrm{reward} = \mathrm{packets\ transmitted} - \lambda\times\mathrm{packets\ dropped}
$$

The simulation uses a queue capacity of **30 packets per user** and service-rate levels **1, 2, 3, 4, 6, 8, 10, and 12**.

## Compared scheduling policies

- **DQN:** learns a scheduling policy from queue lengths, channel rates, and potential throughput, using experience replay and a target network.
- **Longest Queue:** chooses the user with the most queued packets.
- **Max-Weight:** favors a large queue-length × service-rate product.
- **Greedy Throughput:** selects a user based on immediate transmission potential.
- **Best Nonempty Channel:** serves a nonempty queue with a strong channel.
- **Beam-Search Lookahead:** uses limited lookahead over future channel rates as a reference benchmark; it has information unavailable to the online policies.

## Project files

| File | Purpose |
|---|---|
| `Project.ipynb` | DQN implementation, baseline policies, beam-search reference, simulations, and plotting code. |
| `synthetic_12_user_service_rates.csv` | Synthetic channel service-rate trace for 12 users (10,000 time slots). |

**Tools:** Python, PyTorch, NumPy, Matplotlib.

## Interpretation

The aim is to study the trade-off between **throughput, packet drops, and queue occupancy** under changing wireless conditions. 
