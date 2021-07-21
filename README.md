# Project Zeal

DeFi component library with focus on vaults, rewards, and ecosystem interactions.

## Motivation

Open Source is meant to be forked. This is a belief we hold firmly and encourage others to benefit from. Unfortunately, not all projects are fork friendly; whether it's architecture, licensing, core developer shade, or lack of documentation and test coverage, there are many reasons a codebase should not be forked.

This library is designed from the ground up to be shared.


## Contribution Guidelines

To stay true to our goal of encouraging 3rd party use (import, fork, extend) we aim for all additions to be, well:

  - Specified
  - Documented
  - Tested
  - Reviewed

All new features should adhere to the following workflow:

  1. Complete Specification
  1. Define Public Interface
  1. Document with Natspec
  1. Define Placeholder Tests (e.g. [in Moka](https://mochajs.org/#pending-tests))
  1. Implement Feature
  1. Implement Tests
  1. Define Invariants Using [Scribble](https://github.com/ConsenSys/scribble) and [verX](http://verx.ch/docs/)
  1. Submit for Review

Test statements coverage of 100% is the minimum target; keeping in mind that some statements may require several tests to confirm the function adheres to spec.

## Setup

### Install

```
npm i
```

## Build

```
npx hardhat compile
```

## Test

```
npx hardhat test
```