# Trackr – Decentralized Supply Chain Tracking

**Trackr** is a decentralized application (dApp) built on the Stacks blockchain using Clarity smart contracts. It enables transparent and immutable tracking of products as they move through the supply chain, allowing manufacturers, distributors, retailers, and customers to interact with product data at each stage.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the Project](#running-the-project)
- [Contract Design](#contract-design)
  - [Functions](#functions)
  - [Data Structures](#data-structures)
- [Testing](#testing)
- [Deployment](#deployment)
- [License](#license)

## Overview
**Trackr** provides an immutable record of the movement of products from manufacturers to customers. This decentralized platform ensures transparency and trust by enabling all participants (manufacturers, distributors, retailers, and customers) to access and verify the history of a product at any point.

## Features
- **Product Creation**: Manufacturers can register new products on the blockchain.
- **Status Updates**: Distributors and retailers can update the location and status of products.
- **Product Verification**: Customers can view the full history and provenance of a product before purchase.
- **Immutable Records**: All records are stored on the blockchain, ensuring transparency and preventing tampering.

## Getting Started

### Prerequisites
- [Clarinet](https://github.com/hirosystems/clarinet) (for developing and testing Clarity smart contracts)
- [Stacks CLI](https://docs.hiro.so/get-started/stacks-cli) (for deploying contracts to the Stacks blockchain)
- Node.js (if you are building a frontend for user interaction)
  
### Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/trackr.git
   cd trackr
   ```

2. Install dependencies for development (Clarinet, Stacks CLI):
   ```bash
   clarinet check
   ```

3. Initialize Clarinet project (if not already):
   ```bash
   clarinet new trackr
   ```

### Running the Project
You can run the project locally for testing:
1. Run tests with Clarinet:
   ```bash
   clarinet test
   ```

2. Deploy the contract to the Stacks testnet:
   ```bash
   stacks-cli deploy ./contracts/trackr.clar
   ```

## Contract Design

### Functions
- `create-product`:
  - **Description**: Allows manufacturers to register a new product on the blockchain.
  - **Input**: Product details (name, serial number, date of manufacture, etc.)
  - **Output**: Confirms product creation.
  
- `update-product-status`:
  - **Description**: Distributors and retailers update the status or location of the product.
  - **Input**: Product ID, new status (e.g., shipped, in-transit, delivered).
  - **Output**: Confirms status update.
  
- `get-product-details`:
  - **Description**: Retrieves the current status and history of a product.
  - **Input**: Product ID.
  - **Output**: Full product history and current status.

### Data Structures
- **Product**:
  - `id` (uint): Unique identifier for each product.
  - `manufacturer` (principal): The address of the manufacturer.
  - `status` (enum): Current status of the product (e.g., manufactured, shipped, in-transit, delivered).
  - `history` (map): A record of all past status updates.
  - `metadata` (map): Additional data like product name, production date, etc.

- **User Roles**:
  - Only manufacturers can create products.
  - Distributors and retailers can update the status.
  - Customers can verify product details.

## Testing
1. Unit tests are written in Clarinet to ensure that each function works as intended:
   - Test product creation.
   - Test status updates by different supply chain actors.
   - Test that unauthorized users cannot perform restricted actions.

2. To run tests:
   ```bash
   clarinet test
   ```

## Deployment
Once the contract has passed all tests, you can deploy it to the Stacks mainnet or testnet.

1. Deploy the contract using Stacks CLI:
   ```bash
   stacks-cli deploy ./contracts/trackr.clar
   ```

2. Once deployed, the contract will be immutable and ready to use on the blockchain.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.