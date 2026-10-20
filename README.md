# Python Multithreading for BCM Testing

## Description
A Python project that simulates automotive Body Control Module (BCM) testing using multithreading. It runs four tasks concurrently to monitor CAN messages, check voltage and temperature limits, and simulate a diagnostic test sequence.

## Features
- CAN message monitoring simulation
- BCM voltage threshold validation (11 V)
- Temperature threshold validation (80°C)
- Simulated diagnostic test sequence
- Thread creation and synchronization using Python's `threading` module

## Technologies
Python 3, `threading`, `time`

## How to Run
```bash
python bcm_multithreading.py
```

## Note
This is a simulation for learning automotive software testing concepts. It does not communicate with a real BCM or CAN bus.
