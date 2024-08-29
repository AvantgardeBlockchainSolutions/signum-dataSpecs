# Signum Data Specifications

This repository contains specifications of data requested from, reported to, and retrieved from Signum oracles. Each specification is called a `Query`.

- [For Signum Users](#for-tellor-users)
- [For Signum Reporters](#for-signum-reporters)
- [Create new Query type](#create-new-query-type)

## For Signum Users:

### **Price data**:

First check if the price data is already being reported [here](https://github.com/AvantgardeBlockchainSolutions/signum-feeds/tree/main/src/telliot_feeds/feeds). If it is not, [please fill this out.](https://github.com/tellor-io/telliot-feeds/issues/new/choose)

Need a spot price from Signum? Generate a unique identifier, or query ID, for the `asset/currency` pair using [this tool](https://queryidbuilder.herokuapp.com/). After, use that ID to [pay reporters](https://github.com/AvantgardeBlockchainSolutions/signum-autoPay) to put that data on-chain. Then retrieve the reported spot price from the oracle [like this](https://docs.signum.run/getting-data/introduction).

### **Custom data**:

First, check in [`/types`](./types/) if there's already a query type that defines the data you need.

If not, [create a new query type](#create-new-query-type), [pay reporters](https://github.com/AvantgardeBlockchainSolutions/signum-autoPay) to put that data on-chain, and retrieve that data from a Signum oracle [like this](https://docs.signum.run/getting-data/introduction).

## For Signum Reporters:

To find out what data to report, there's two options:

- Use our [reporter client](https://github.com/AvantgardeBlockchainSolutions/signum-feed-examples) to automatically report the expected response of queries that Signum users are funding.
- Check for newly funded queries, then refer to that query's expected response in [`/types`](./types/) for the required data to report. Be sure to read the dispute considerations section for that query.

### Encoding Practices

When reporting data to the Signum oracle, it is crucial to encode the values correctly as defined in the relevant data spec document. Proper encoding is critical for user contracts to correctly decode and use the data.

For example, with a query type response defined as:

- `abi_type`: ufixed256x18 (18 decimals of precision)
- `packed`: false

and a `uint256` value of `12345000000000000000000`, the reported value should be encoded as `0x00000000000000000000000000000000000000000000029d394a5d6305440000`. This value can be encoded in solidity as `abi.encode(uint256(12345000000000000000000))`.

By following these encoding practices, you ensure that the data remains consistent and can be accurately decoded by user contracts.

## Create New Query Type

To create a new Query, or specification, for custom data you need from Signum oracles, there's two options:

- Make an issue with [this template](https://github.com/AvantgardeBlockchainSolutions/signum-dataSpecs/issues/new?assignees=&labels=&template=new_query_type.yaml&title=%5BNew+Query+Type%5D%3A+) and the Signum team will help with the next steps.

After creating the new query type in this repo, [here](https://github.com/AvantgardeBlockchainSolutions/signum-feeds/issues/new/choose) are some next steps for getting reporters to support your data.

## Contribute<a name="how2contribute"> </a>

Join our [Telegram](https://t.me/GoSignum), help us with issues here on Github, or feel free to reach out anytime [info@signum.run](mailto:info@signum.run).

## Copyright

Signum Inc. 2024
