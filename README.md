# Federated Learning MNIST

This is an example of federated learning on the MNIST dataset using Flower and Scikit-Learn.

## Files

- `Logregclient.py` - The Flower client code that trains a local model and communicates with the server.
- `Logregserver.py` - The Flower server code that aggregates model updates from clients.
- `utils.py` - Utility functions for loading data, partitioning, and model parameters. 

## How it works

1. The server starts and waits for clients to connect.
2. The clients load the MNIST training data and partition it into 10 pieces. One partition is used for local training.
3. The clients train a LogisticRegression model locally for 1 epoch.  
4. After training, the updated model parameters are sent to the server.
5. The server aggregates the parameters from all clients using Federated Averaging.
6. Steps 3-5 repeat for 5 rounds of federated learning.
7. After each round, the server evaluates the global model on the test set.

## Usage

To run this example:

1. Start the server

    ```bash
    python Logregserver.py
    ```

2. In separate terminals, start each client

    ```bash
    python Logregclient.py
    ```

3. After 5 rounds, the server will print the global test accuracy.  

## Dependencies

- Python 3
- Flower (https://flower.dev/)
- Scikit-Learn
- Pandas
- NumPy
