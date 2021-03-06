# Intro

This repository holds collected notes and code snippets to help in preparing for an
[Ethereum](https://www.ethereum.org) based crowdsale.

Some of the things you will need include:

- A **Wallet** to manage funds.
- One or more **tokens**, if you don't intend to trade raw ether.
- A mysteriously named "Decentralized Autonomous Organization" (or **DAO**).
- A **crowdsale** or **crowd equity**.

# Wallet

This is the easiest part. Your wallet is just an app attached to your Ethereum account.
You need a wallet to hold or transfer funds.  You can associate more than one account
with a single wallet.

Just download and install the wallet app for your OS ([MacOS version here](https://github.com/ethereum/mist/releases/download/v0.11.1/Ethereum-Wallet-macosx-0-11-1.dmg)),
add an account, and **be sure to use a strong password you won't forget** (this protects your money!).

Aside from managing funds, the wallet app also lets you deploy contracts. The official wallet
app should be enough to get started, but is just one option. There are a number of
[software and hardware based solutions](https://coinsutra.com/best-etherum-wallets).
**Remember that if you loose your wallet or access to the computer it is on you will loose your funds!**

# Token

[ERC-20](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md) (Ethereum Request for
Comment #20) is more about [standardization](https://ethereum.stackexchange.com/questions/33956/are-there-any-other-smart-contract-standards-like-erc20) than security. As an emerging standard, it documents
a proposed API for tokens. With everyone creating custom tokens, this helps ensure
compatibility and makes exchange easier.

For an [ERC-20 compliant token](https://theethereum.wiki/w/index.php/ERC20_Token_Standard),
you can just use [token.sol](https://github.com/deadlysyn/ethereum-experiment/blob/master/token.sol) in this
repository as a starting point. Deploy it with the wallet app (Deploy New Contract, paste Solidity code).
[Detailed directions](https://www.ethereum.org/token) are in the docs. When you deploy the token contract
you have to specify the following:

- Initial supply: How many tokens to initially create
- Token name: The name of your token
- Decimal units: 18 is a common default
- Token symbol: A symbol for your token

Note: "Know Your Customer" for token purchasers is not addressed by ERC-20. You should discuss this with an advisor.
There are other emerging token "standards" like [ST-20](https://polymath.network/st20.html) which attempt to
solve the KYC problem. Unfortunately, [as this thread implies](https://www.reddit.com/r/ethereum/comments/7vkm3m/can_kyc_be_baked_into_security_tokens_on_ethereum),
there are mixed views -- you will need an expert opinion on whether it is legally suitable.
[KYC for token owners is becoming easier](https://foundico.com/kyc), simply requiring
founders to submit to interviews and provide proof of identity.

# DAO

In Ethereum, a "DAO" or Decentralized Autonomous Organization is -- as the name implies -- a
representation of a decentralized and democratic organization on the blockchain.  Like a
real organization, the DAO has a CEO that decides on membership and voting rules.

A DAO can take many forms as [detailed in the docs](https://www.ethereum.org/dao). The
example [dao.sol](https://github.com/deadlysyn/ethereum-experiment/blob/master/dao.sol)
in this repository implements the "shareholder association" contract,
which mimics a typical shareholder organization with your tokens as shares.

Deploy the contract via the wallet app... you'll need to customize a few things:

- Minimum quorum for proposals: Votes needed to execute a proposal
- Minutes for debate: Amount of time that must pass before new proposal is executed
- Margin of votes for majority: Proposals pass if more than 50% of votes + margin.
- Shares token address: Address of your token

# Crowdsale

**NOTE: The starting contract provided here needs refined to be used in production.
As described toward the bottom of the [related documentation](https://www.ethereum.org/crowdsale),
there is potential for hostile takeover. One solution would be ensuring when a token is bought,
the same quantity of tokens are sent to the founder's account so that they always control 50% of the project.**

Once you've issued your token and deployed an organization, you need to attract investors
and be able to trade virtual shares in your company. You do this in Ethereum with a crowdsale contract.
You can use [crowdsale.sol](https://github.com/deadlysyn/ethereum-experiment/blob/master/crowdsale.sol) in this repository as a starting point.

Once again, deploy the contract using the wallet app and provide values for the following:

- If successful send to: Address of your DAO
- Funding goal in ethers: Amount to raise
- Duration in minutes: Crowdsale duration (typically 30 days or less)
- Cost of each token: Ehter value of each token
- Token reward address: Address of your token

# Summary

With a bit of tuning, the above could get your crowdsale started.  However, the devil
is in the details. For a small project (experimentation, startup) or on a relaxed timeline the
community is evolving enough that one could feel their way through this process. For
larger projects ($$$ at risk), more due diligence is required.

Key concerns:

The relative immaturity of the market along with rapidly evolving standards and legislation
make KYC and other concerns specific to regulated commodities a moving target. More
market research and expert opinion is required to know how best to proceed.

Contracts are written in Solidity, a new language with immature tooling, testing and
other best practices which evolve in more mature languages over time. Tokens, organizations,
crowdsales, etc. -- everything is described via contracts.  Contracts are just programs written
in Solidity. To reduce the likelihood of bugs (which could loose money or allow malicious actors to
steal funds), contracts need to be thoroughly tested and audited by a third party.

Managing cost is a concern. As a programming language, Solidity performs work. That work has
a cost, measured in [gas](https://ethereum.stackexchange.com/questions/3/what-is-meant-by-the-term-gas).
Think of this as transaction fees. Contracts need to be as simple as possible to reduce costs.
This is another area where consultation in contract design would be helpful.

Managing wallets, contracts, etc. feels like overhead best shipped to an e-2-e platform.
Manually deploying and managing contracts is a way to get started, but it feels clunky.
Ideally, a platform would manage all of these things for you so you could focus on your business
vs being distracted by the underlying technology.

The sensitivity of the wallet and associated account is a security concern. No different
than a bank or investment account, but these must be carefully guarded.

## Resources

- https://ethereum.org
- https://blocktrade.com
- https://www.coinbase.com
- https://cobinhood.com
- https://etherscan.io
- https://foundico.com
- https://www.clearify.io
- https://www.icoalert.com
- https://www.forbes.com/sites/michaeldelcastillo/2018/10/15/fidelity-launches-institutional-platform-for-bitcoin-and-ethereum
- https://medium.com/coinfi/how-to-create-your-ethereum-address-323d176e5aab
- https://medium.com/smarttaylor/heres-how-to-create-your-ethereum-wallet-fa975b26b9fe
- https://medium.com/@trustwallet/ethereum-tokens-how-acquire-store-and-trade-them-f8cd191fc841
