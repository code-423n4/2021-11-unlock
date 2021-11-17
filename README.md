# ✨ So you want to sponsor a contest

This `README.md` contains a set of checklists for our contest collaboration.

Your contest will use two repos:
- **a _contest_ repo** (this one), which is used for scoping your contest and for providing information to contestants (wardens)
- **a _findings_ repo**, where issues are submitted.

Ultimately, when we launch the contest, this contest repo will be made public and will contain the smart contracts to be reviewed and all the information needed for contest participants. The findings repo will be made public after the contest is over and your team has mitigated the identified issues.

Some of the checklists in this doc are for **C4 (🐺)** and some of them are for **you as the contest sponsor (⭐️)**.

---

# Contest setup

## 🐺 C4: Set up repos
- [X] Create a new private repo named `YYYY-MM-sponsorname` using this repo as a template.
- [ ] Get GitHub handles from sponsor.
- [ ] Add sponsor to this private repo with 'maintain' level access.
- [ ] Send the sponsor contact the url for this repo to follow the instructions below and add contracts here.
- [ ] Delete this checklist and wait for sponsor to complete their checklist.

## ⭐️ Sponsor: Provide contest details

Under "SPONSORS ADD INFO HERE" heading below, include the following:

- [X] Name of each contract and:
  - [X] lines of code in each
  - [X] external contracts called in each
  - [X] libraries used in each
- [X] Describe any novel or unique curve logic or mathematical models implemented in the contracts
- [X] Does the token conform to the ERC-20 standard? In what specific ways does it differ?
- [X] Describe anything else that adds any special logic that makes your approach unique
- [X] Identify any areas of specific concern in reviewing the code
- [X] Add all of the code to this repo that you want reviewed
- [X] Create a PR to this repo with the above changes.

---

# ⭐️ Sponsor: Provide marketing details

- [X] [Your logo](https://github.com/unlock-protocol/unlock/blob/master/design/brand/1808-Unlock-Identity_Unlock-LogoMark-Circle.svg)
- [X] Your primary Twitter handle : [@unlockprotocol](https://twitter.com/unlockProtocol)
- [X] Any other Twitter handles we can/should tag in (e.g. organizers' personal accounts, etc.) : [@julien51](https://twitter.com/julien51)
- [X] [Your Discord URI](https://discord.com/invite/Ah6ZEJyTDp)
- [X] [Your website](https://unlock-protocol.com/)
- [NA] Optional: Do you have any quirks, recurring themes, iconic tweets, community "secret handshake" stuff we could work in? How do your people recognize each other, for example?
- [X] Optional: your logo in Discord emoji format

---

# Contest prep

## 🐺 C4: Contest prep
- [X] Rename this repo to reflect contest date (if applicable)
- [X] Rename contest H1 below
- [X] Add link to report form in contest details below
- [X] Update pot sizes
- [X] Fill in start and end times in contest bullets below.
- [X] Move any relevant information in "contest scope information" above to the bottom of this readme.
- [X] Add matching info to the [code423n4.com public contest data here](https://github.com/code-423n4/code423n4.com/blob/main/_data/contests/contests.csv))
- [ X] Delete this checklist.

## ⭐️ Sponsor: Contest prep
- [ ] Make sure your code is thoroughly commented using the [NatSpec format](https://docs.soliditylang.org/en/v0.5.10/natspec-format.html#natspec-format).
- [ ] Modify the bottom of this `README.md` file to describe how your code is supposed to work with links to any relevent documentation and any other criteria/details that the C4 Wardens should keep in mind when reviewing. ([Here's a well-constructed example.](https://github.com/code-423n4/2021-06-gro/blob/main/README.md))
- [X] Please have final versions of contracts and documentation added/updated in this repo **no less than 8 hours prior to contest start time.**
- [X] Ensure that you have access to the _findings_ repo where issues will be submitted.
- [X] Promote the contest on Twitter (optional: tag in relevant protocols, etc.)
- [X] Share it with your own communities (blog, Discord, Telegram, email newsletters, etc.)
- [ ] Optional: pre-record a high-level overview of your protocol (not just specific smart contract functions). This saves wardens a lot of time wading through documentation.
- [ ] Designate someone (or a team of people) to monitor DMs & questions in the C4 Discord (**#questions** channel) daily (Note: please *don't* discuss issues submitted by wardens in an open channel, as this could give hints to other wardens.)
- [ ] Delete this checklist and all text above the line below when you're ready.

---

# Unlock Protocol contest details
- $47,500 USDC main award pot
- $2,500 USDC gas optimization award pot
- Join [C4 Discord](https://discord.gg/code4rena) to register
- Submit findings [using the C4 form](https://code423n4.com/2021-11-unlock-protocol-contest/submit)
- [Read our guidelines for more details](https://docs.code4rena.com/roles/wardens)
- Starts November 18, 2021 00:00 UTC
- Ends November 24, 2021 23:59 UTC

[ ⭐️ SPONSORS ADD INFO HERE ]

Unlock is a protocol for memberships that lets creators of all kinds deploy a "membership contract" (we call that a Lock) and that lets them then sell memberships (keys, implemented as NFT).

## Contracts:

* [Unlock.sol](https://github.com/unlock-protocol/unlock/blob/master/smart-contracts/contracts/Unlock.sol) : a factory contract that deploys all locks. It is also called back by the lock on key purchases to mint/distribute new UDT tokens. This contract is deployed once on each network currently supported (Mainnet, xDAI, Polygon, BSC). It is upgradable and currently 'owned' by a Gnosis multisig but will eventually be transfered to the DAO.

* [PublicLock](https://github.com/unlock-protocol/unlock/blob/master/smart-contracts/contracts/PublicLock.sol): the actual "membership" contract that implements ERC721 and a few others. It is deployed multiple times by creators.

* [UnlockDiscountTokenV2](https://github.com/unlock-protocol/unlock/blob/master/smart-contracts/contracts/UnlockDiscountTokenV2.sol): the governance token contract (UDT). The only minter is the Unlock contract.


You can use the [Unlock Dashboard](https://app.unlock-protocol.com/dashboard) to deploy a lock on Rinkeby (connect your wallet to Rinkeby) and then purchase a key using our "Demo". [The following video shows the way to achieve this](https://share.getcloudapp.com/4guPNlvW).

[Smart contract docs are available on this page](https://docs.unlock-protocol.com/developers/smart-contracts).

[Governance docs are available on this page](https://docs.unlock-protocol.com/governance/the-unlock-token).

You can run test in the smart-contracts repo with `yarn run test` (make sure you run `yarn install` first to install all dependencies).

If you want to run the front-end applications, please check instruction [in the main Unlock repo](https://github.com/unlock-protocol/unlock).

Notes: the code being reviewed has not been deployed yet, even though it is an incremental upgrade on the existing deployed code. Similarly, the documentation reflects the current implementation, not the code being reviewed. You can find below the most significant change:
### Upgradable locks

The biggest change we introduced to the smart contract and that we hope to deploy in the next few weeks is to enable upgrades on the PublicLock smart contracts.
We want these locks to be upgradable when new versions of the protocol are released, but only by their "Lock Managers" ([See permission](https://docs.unlock-protocol.com/developers/smart-contracts/lock-api/access-control)).

The approach we took is to deploy a Proxy Admin as part of the Unlock.sol contract. We updated the `createLock` to deploy a lock proxy instead of the lock directly. We also introduced an `upgradeLock` function that can then be trigger by one of the lock's lock managers to update the implementation.

To support these uprgades, the Unlock contract will now keep a list of implementation, as well the corresponding version numbers as we only support incremental upgrades.

