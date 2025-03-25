# CreditTalent Contracts

This repository contains the smart contracts for the CreditTalent platform, which enables underwriters to provide credit lines to users through a decentralized lending protocol.

## Overview

The CreditTalent platform consists of several key contracts:

1. **CreditTalentCenter**: The main contract that manages credit applications, underwriters, and credit approvals.
2. **CreditPoints**: An ERC20 token that represents the credit line provided to users.
3. **FixedRateIrm**: A contract that implements a fixed interest rate model for loans.
4. **UICreditTalentHelper**: A helper contract for UI integration that provides user loan information.
5. **CreditTalentCenterUpgradeable**: An upgradeable version of the CreditTalentCenter contract.

## Prerequisites

- [Foundry](https://book.getfoundry.sh/getting-started/installation)
- [Node.js](https://nodejs.org/en/download/)
- [Yarn](https://yarnpkg.com/getting-started/install)

## Setup

1. Clone the repository:
```bash
git clone <repository-url>
cd <repository-directory>/packages/foundry
```

2. Install dependencies:
```bash
forge install
```

3. Create a `.env` file based on `.env.example` and fill in the required values:
```bash
cp .env.example .env
```

## Compilation

Compile the contracts:

```bash
forge build
```

## Testing

Run the tests:

```bash
forge test
```

## Deployment

The contracts can be deployed using the deployment scripts in the `script` directory.

### Deploy the CreditTalentCenter Contract

```bash
forge script script/Deploy.s.sol:Deploy --rpc-url <RPC_URL> --private-key <PRIVATE_KEY> --broadcast
```

### Deploy the Upgradeable CreditTalentCenter Contract

```bash
forge script script/deployUpgradeable.s.sol:DeployUpgradeable --rpc-url <RPC_URL> --private-key <PRIVATE_KEY> --broadcast
```

## Contract Interactions

### CreditTalentCenter

#### Apply for Credit

Users can apply for credit by calling the `applyToCredit` function:

```solidity
function applyToCredit(bytes32 dataHash_) public;
```

#### Apply to Underwrite

Underwriters can apply to provide credit by calling the `applyToUnderwrite` function:

```solidity
function applyToUnderwrite(uint256 amount_) external;
```

#### Approve Credit

Underwriters can approve credit applications by calling the `approveCredit` function:

```solidity
function approveCredit(address user_, uint256 applicationId_, uint256 amount_, uint256 iRateWad_) external;
```

#### Reject Credit

Underwriters can reject credit applications by calling the `rejectCredit` function:

```solidity
function rejectCredit(address user_, uint256 applicationId_, string memory reason_) external;
```

### CreditPoints

#### Set Approved Receiver

The owner can set approved receivers for the credit points:

```solidity
function setApprovedReceiver(address receiver_, bool approved_) public onlyOwner;
```

#### Mint Credit Points

The owner can mint credit points:

```solidity
function mint(address to, uint256 amount) public onlyOwner;
```

#### Burn Credit Points

The owner can burn credit points:

```solidity
function burn(address from, uint256 amount) public onlyOwner;
```

### UICreditTalentHelper

#### Get User Loan Information

Get information about a user's loan:

```solidity
function getUserLoanInfo(address creditCenter, address user) external view returns (uint256 creditLine, uint256 debtBalance, uint256 interestRatePerSecond);
```

## Contract Addresses

The contract addresses for different networks are defined in the deployment scripts:

- **CREDIT_TOKEN_IMPL**: The implementation address for the CreditPoints contract.
- **UNDERWRITING_XOC**: The address for the XOC token used as underwriting asset.
- **UNDERWRITING_USDC**: The address for the USDC token used as underwriting asset.
- **UNDERWRITING_TALENT**: The address for the TALENT token used as underwriting asset.
- **MORPHO**: The address for the Morpho protocol.
- **ADAPTIV_IRM**: The address for the adaptive interest rate model.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
