# Box


## Simple Summary

Boxes, aka vaults, aka pools, etc., manage moving tokens to and from a system (deposit and withdraw). Users deposit into the `box` and benefit from what the `box` does with their funds. Common use cases include yield aggregators, lending pools, reward staking pools, etc.

Boxes may issue receipts in the form of ERC20 or ERC1155 tokens.

We choose the name `box` over the more common `vault` as vault implies that funds are locked inside. This is not the case for most DeFi `vault`s where funds are sent to connected ecosystem contracts.

## Roles

  - `Depositor`: Deposits tokens into, and withdraws tokens out of, `boxes`.
  - `Manager`: Sets current `instrument`, adjusts `box` parameters, and exits `instrument`s. - "I don't make the rules, I just think them up and write them down."
  - `Handler`: Handles the `box` when it `cycle`s the `box`'s `instrument`s.
  - `Collector`: Receives fees and related payouts.


## Definitions

  - `Instrument`: is a general term for a contract that handles deposited token through internal calculations (e.g. reward emissions) or by interacting with other ecosystem contracts (e.g. yield aggregation strategies).
  - `Child Box`: A `box` the attached `instrument`s may deposit into to be managed and processed separately.
  - `Process`: Executes the `instrument`'s core functionality. In other projects referred to as `harvest` (yearn), `rebalance` (vesper), `dohardwork` (harvest), `updateAccounting` (ampl's geyser), etc. 
  - 

## Specifications

#### `Public` Actions:

  - get underlying address
  - get children `box`es
  - get total underlying deposited
  - get underlying in `box` (available to be deposited into `instrument`)
  - get `instrument`s

#### `Depositor` Actions:

  - deposit underlying for self
  - deposit underlying for another address
  - withdraw underlying for self
  - when receipt is ERC20: all ERC20 token interactions (including `eip-2612`)
  - when receipt is ERC1155: all ERC115 token interactions

#### `Manager` Actions:

  - propose add `instrument`
  - add `instrument`
  - remove `instrument`
  - add `child box`
  - remove `child box`
  - set withdraw fee
  - set deposit ratio per `instrument`
  - set deposit cap
  - withdraw from `instrument`
  - set `Manager` address
  - set `Handler` address
  - set `Collector` address

#### `Handler` Actions:

  - `process` attached `instrument`(s)
  - `sweep` the `box` of unaccounted for tokens

#### `Collector` Actions:

  - None. Receives tokens only.

#### On Create

  - Receipt token contract created.
  - Underlying defined.
  - `Manager` defined.
  - `Handler` and `Collector` default to `Manager`.

#### On Deposit

  - Receipts are issued to track a `Depositor`'s share.
  - May deposit for self or depositFor another address.


#### On Withdraw

  - Receipts are converted into underlying pro rata.
  - Child box receipts, equal to the number of parent box receipts withdrawn, are `transferred` to the `Depositor`. (If a `Depositor` wishes to withdraw from a child vault they must do so by directly calling that vault.)

#### On Exit Instrument

  - all underlying moved from `instrument` to parent `box`.
  - If deposits in ecosystem contracts, they must be withdrawn as well.
  - If rewards, they must be claimed (when claiming enabled).


#### On Process Instrument

  - `Box` calls `process` on `instrument`.
  - If more than one active `instrument`, each are called in sequence.



## Attacks and Mitigations


### Locked Funds

### Faulty Instrument

### Miscalculated Share 

### Flash Loan / Whale Deposit 






