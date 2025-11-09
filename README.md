# Queueing Systems Python Library

This project implements several classical queueing theory models in Python, including:

- **BaseQueue** — foundational queue class with validation + shared metric computation behavior
- **MM1Queue** — M/M/1 single server queue
- **MD1Queue** — M/D/1 deterministic service queue
- **MG1Queue** — M/G/1 general service distribution queue
- **MMcPriorityQueue** — M/M/c priority queue extension (requires `MMcQueue`)

All queue classes validate arrival rates (`λ`) and service rates (`μ`), compute feasibility (ρ < 1), and expose standard performance metrics including:

| Symbol | Meaning |
|--------|---------|
| λ      | arrival rate |
| μ      | service rate |
| ρ      | traffic intensity |
| Lq     | expected # of customers in queue |
| L      | expected # of customers in system |
| Wq     | expected wait time in queue |
| W      | expected time in system |
| p0     | probability system is empty |

## Project Structure

BaseQueue.py
MM1Queue.py
MD1Queue.py
MG1Queue.py
MMcPriorityQueue.py
BaseQueue_Test.py

## Usage

```python
from MM1Queue import MM1Queue

q = MM1Queue(lamda=20.0, mu=25.0)

print(q.lq)      # average # in queue
print(q.w)       # total system wait time
print(q.utilization)   # traffic intensity
```

Each object automatically recalculates metrics when λ or μ is modified.
Validation / Feasibility
A queue is valid if λ and μ are numeric and > 0
A queue is feasible if ρ = λ / μ < 1
If invalid → metrics return NaN
If feasible=false (ρ ≥ 1) → metrics return inf
Testing
Unit tests are provided via the standard unittest module.
Run tests:
python BaseQueue_Test.py

Requirements
Python 3.x
standard library only (math, numbers, unittest)
Notes
MMcPriorityQueue relies on MMcQueue (not included in this snippet)
These implementations are meant for educational + assignment correctness, not production simulation speed.
Author
Queueing Models Project – Tyler Crosbie
