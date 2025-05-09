# Contract Guard (Vyper)

A minimal smart contract written in Vyper that acts as a reusable security layer for other contracts. It restricts repeated calls from the same address within a short period and requires a minimum ETH payment.

## Features

- Rate-limiting: prevents spam or repeated calls within 60 seconds.
- Value check: requires a minimum of 0.01 ETH to process a request.
- Lightweight and easy to integrate with other contracts.
- Emits logs for accepted operations.

## How It Works

When a user calls the `protected_call()` function:

1. It checks if `msg.value` is at least 0.01 ETH.
2. It ensures that 60 seconds have passed since the last call from the same address.
3. If both checks pass, the function logs the successful call.

## Contract Interface

```python
@external
@payable
def protected_call():
    # Your business logic here (currently logs the call)
