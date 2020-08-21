# OMGSwap-subgraph

[OMGSwap](https://omgswao.com/) is a decentralized protocol for automated token exchange on Ethereum.

This Subgraph dynamically tracks any exchange created by the uniswap factory. Any exchange, any user of the protocol, and any transaction of the protocol can be queried.

## Running Locally

Make sure to update package.json settings to point to your own graph account.

## Important Info

- USD values are based on the Compound Finance DAI oracle, which gets its prices from the Maker oracle.
- You can find the profit of a liquidity provider with the following information:
  - Find the ratio of total tokens owned by the user out of all tokens:
    - `(liquidityTokensMinted - liquidityTokensBurned) / totalLiquidityTokens = ratio`
  - With that ratio, figure out how much ETH and token could be withdrawn. You must take the tokens and convert to ETH for total ETH they could withdraw:
    - `ratio * ethBalance = ethWithdrawable`
    - `ratio * tokenBalance * tokenPrice = tokenWithdrawableInEth`
    - `ethWithdrawable + tokenWithdrawable = totalWithdrawable`
  - Now take `ethDeposited - ethWithdrawn = totalEth`
  - And `(tokenDeposited - tokenWithdrawn) * tokenPrice = totalTokensInEth`
  - Current Liquidity profit is:
    - `profit = totalWithdrawable - totalEth - totalTokensInEth`


## Queries

Below are a few ways to show how to query the uniswap-subgraph for data. The queries show most of the information that is queryable, but there are many other filtering options that can be used, just check out the [querying api](https://thegraph.com/docs/graphql-api). These queries can be used locally or in The Graph Explorer playground.



