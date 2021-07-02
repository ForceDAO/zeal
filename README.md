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
  2. Define Public Interface
  3. Document with Natspec
  4. Define Placeholder Tests (e.g. [in Moka](https://mochajs.org/#pending-tests))
  5. Implement Feature
  6. Implement Tests
  7. Define Invariants Using Scribble
  8. Submit for Review

Test statements coverage of 100% is the minimum target; keeping in mind that some statements may require several tests to confirm the function adheres to spec.

## Setup

### Install

```
npm i
```

### Build

```
npx hardhat compile
```

### Test

```
npx hardhat test
```