# near-api-py

*Status: super rough, APIs are subject to change*

A Python library for development of applications that are using NEAR platform.

# Installation

```bash
pip install near-api-py
```

# Usage example

## View method

```python
contract_id = "contract.youraccount.testnet"    # contract id
view_method_name = "get_counter"                # view method

# RPC Endpoint URL (You can change it to any? for example to mainnet: https://docs.near.org/docs/api/rpc#setup)
near_provider = near_api.providers.JsonProvider("https://rpc.testnet.near.org")

near_contract_account = near_api.account.Account(near_provider, contract_id)

out = near_contract_account.view_function(method_name)

print(out)

```


## Call method

```python
contract_id = "contract.youraccount.testnet"    # contract id
signer_id = "youraccount.testnet"               # signer id for call methods
call_method_name = "change_counter"             # call method
data = {"value": 1, "action": "increase"}       # run params

# RPC Endpoint URL (You can change it to any? for example to mainnet: https://docs.near.org/docs/api/rpc#setup)
near_provider = near_api.providers.JsonProvider("https://rpc.testnet.near.org")

# From wallet or .near-credentials dir in case you already use near-cli
key_pair = near_api.signer.KeyPair("ed25519:[SIGNER_PRIVATE_KEY]")
signer = near_api.signer.Signer(signer_id, key_pair)

near_contract_account = near_api.account.Account(near_provider, contract_id, signer)

out = near_contract_account.function_call(method_name, data)

print(out)

```


# Contribution

First, install the package in development mode:
```bash
python setup.py develop
```

To run tests, use nose (`pip install nose`):
```bash
nosetests
```

# License

This repository is distributed under the terms of both the MIT license and the Apache License (Version 2.0). See LICENSE and LICENSE-APACHE for details.
