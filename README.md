# Intent AVS

![image](https://github.com/user-attachments/assets/07647238-eea9-45a0-a000-3318c4e4b466)


## Introduction

The Intent AVS is a AVS designed to facilitate cross-chain bridging using cross chain intents. It leverages AVS smart contracts to create intents for bridging tokens from a source chain to a destination chain. The system consists of several components, including the Intent AVS (AVS Contract), Intent Filler Contract, and AVS Operators, which work together to ensure secure and efficient token transfers.

## Architecture

![image](https://github.com/user-attachments/assets/96d16317-36c5-4ddc-9a19-92f86eac4bd4)


### Components

1. **Intent AVS Provider (AVS Contract)**
   - A smart contract where users create intents to bridge tokens from a source chain to a destination chain.

2. **Intent Filler Contract**
   - Deployed on the destination chain, this contract listens for events from the AVS contract and facilitates the transfer of destination tokens to the user.

3. **AVS Operators**
   - Entities that listen to events emitted by the Intent Filler contract to verify the correctness of the fill data and complete the intent by sending source tokens to the filler on the source chain.

### Workflow

1. **User Interaction**
   - Users interact with the Intent AVS Provider to create intents specifying the source and destination tokens and chains.

2. **Event Emission**
   - The AVS contract emits events when a new intent is created.

3. **Intent Filling**
   - The Intent Filler contract on the destination chain listens for these events and transfers the specified amount of destination tokens to the user.

4. **Verification and Completion**
   - AVS Operators listen to events from the Intent Filler contract, verify the transaction details, and complete the intent by transferring source tokens to the filler on the source chain.

## Running the Project

### Prerequisites

- **Node.js**: Ensure you have Node.js installed on your system.
- **npm**: Node Package Manager is required to install dependencies.
- **TypeScript**: The project is written in TypeScript, so ensure you have it installed globally.

### Installation

1. **Clone the Repository**

   ```bash
   git clone https://github.com/your-repo/bridge-intent-service.git
   cd bridge-intent-service
   ```

2. **Install Dependencies**

   ```bash
   npm install
   ```

3. **Environment Setup**

   - Create a `.env` file in the root directory and add the following environment variables:

     ```env
     WS_RPC_URL=wss://your-websocket-rpc-url
     DESTINATION_WS_RPC_URL=wss://your-destination-websocket-rpc-url
     PRIVATE_KEY=your-private-key
     ```

### Running the Services

1. **Start the Filler Service**

   ```bash
   npm run start:filler
   ```

2. **Start the Operator Service**

   ```bash
   npm run start:operator
   ```

### Testing

- Ensure you have a local blockchain or testnet setup to test the contracts and services.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request for any improvements or bug fixes.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
