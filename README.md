# SmartChainGuard: Confidentiality-Preserving Distributed Ledger Primitives

SmartChainGuard is a forward-thinking project focused on advancing the capabilities of distributed ledgers by integrating secure multi-party computation (MPC) and zero-knowledge succinct non-interactive arguments of knowledge (zk-SNARKs). The primary objective is to enhance smart contract confidentiality and enable verifiable, privacy-preserving state transitions within decentralized networks. We aim to provide developers with the tools and frameworks necessary to build a new generation of privacy-focused decentralized applications.

The project addresses the critical need for enhanced data privacy within smart contracts. Publicly visible state transitions, a common feature of many blockchains, often expose sensitive information, hindering the adoption of decentralized applications in scenarios requiring data protection. SmartChainGuard offers a solution by leveraging MPC to allow multiple parties to jointly compute a function without revealing their individual inputs. zk-SNARKs are then utilized to prove the integrity and correctness of state transitions without disclosing the underlying data. This synergistic approach unlocks the potential for applications in areas such as confidential voting, private auctions, and secure supply chain management.

SmartChainGuard strives to be modular and extensible, allowing developers to easily integrate its components into existing blockchain infrastructures. The framework is built with performance in mind, utilizing optimized cryptographic libraries and efficient computation techniques. The project aims to provide a comprehensive suite of tools, including smart contract libraries, off-chain computation engines, and developer-friendly interfaces, to facilitate the seamless integration of privacy-preserving features into decentralized applications. We are committed to building a robust and secure foundation for the future of confidential distributed ledger technology.

## Key Features

*   **Secure Multi-Party Computation (MPC) Integration:** Implements a threshold ECDSA-based MPC protocol allowing multiple parties to jointly sign transactions or compute functions without revealing their individual private keys or data. This includes a robust key generation and distribution mechanism.
*   **zk-SNARK Based State Transitions:** Utilizes the Groth16 proving system to generate succinct proofs of state transitions. These proofs can be verified on-chain, ensuring the validity of the transition without revealing the input state, output state, or any intermediate computations.
*   **Hybrid MPC-zkSNARK Smart Contracts:** Enables the creation of smart contracts that combine the strengths of both MPC and zk-SNARKs. For example, MPC can be used to jointly generate inputs for a zk-SNARK circuit, ensuring that no single party has access to the entire input data.
*   **Optimized Cryptographic Libraries:** Employs highly optimized cryptographic libraries, such as circomlibjs and noble-secp256k1, to minimize computation overhead and ensure efficient proof generation and verification. Specific functions are carefully chosen based on performance benchmarks.
*   **Modular and Extensible Architecture:** Designed with a modular architecture that allows developers to easily integrate individual components into their existing projects. The framework provides well-defined interfaces and APIs for seamless integration.
*   **TypeScript Based Implementation:** Written in TypeScript, providing strong typing and enhanced code maintainability. TypeScript allows for efficient collaboration and reduces the likelihood of runtime errors.
*   **Comprehensive Testing Suite:** Includes a comprehensive suite of unit and integration tests to ensure the correctness and security of the implemented protocols. Fuzzing and formal verification techniques are also being explored.

## Technology Stack

*   **TypeScript:** Primary programming language providing type safety and improved code organization.
*   **circomlibjs:** JavaScript implementation of common cryptographic gadgets for zk-SNARK circuits.
*   **snarkjs:** JavaScript library for compiling, proving, and verifying zk-SNARK circuits.
*   **noble-secp256k1:** High-performance JavaScript implementation of the secp256k1 elliptic curve, used for ECDSA and MPC protocols.
*   **Node.js:** Runtime environment for executing JavaScript and TypeScript code.
*   **ethers.js/web3.js:** Libraries for interacting with Ethereum and other EVM-compatible blockchains.

## Installation

1.  **Clone the repository:**
    git clone https://github.com/jjfhwang/SmartChainGuard.git
    cd SmartChainGuard

2.  **Install dependencies:**
    npm install

3.  **Install snarkjs globally (if not already installed):**
    npm install -g snarkjs

4.  **Build the project:**
    npm run build

## Configuration

The project utilizes environment variables for configuration. Create a `.env` file in the root directory of the project and define the following variables:

*   `NODE_ENV`: Set to `development` or `production` depending on the environment.
*   `ETHEREUM_PROVIDER_URL`: URL of the Ethereum provider (e.g., Infura, Alchemy).
*   `CONTRACT_ADDRESS`: Address of the deployed smart contract (if applicable).
*   `PRIVATE_KEY`: Private key of the account used to interact with the smart contract.

Example `.env` file:
NODE_ENV=development
ETHEREUM_PROVIDER_URL=https://eth-goerli.g.alchemy.com/v2/YOUR_API_KEY
CONTRACT_ADDRESS=0xYourContractAddress
PRIVATE_KEY=0xYourPrivateKey

## Usage

Detailed usage examples and API documentation are available in the `docs` directory (currently under development). Here's a basic example of using the zk-SNARK proving functionality:

First, compile your circuit using circom:
circom circuit.circom --r1cs --wasm --sym

Then generate the proving key and verification key:
snarkjs plonk setup circuit.r1cs pot12_0001.ptau circuit_0001.zkey

Generate a proof:
snarkjs plonk prove circuit_0001.zkey input.json proof.json public.json

Verify the proof:
snarkjs plonk verify verification_key.json public.json proof.json

For MPC examples, refer to the `examples` directory, which demonstrates the creation of a multi-party ECDSA signature. The documentation provides detailed explanations of the API functions and their parameters.

## Contributing

We welcome contributions to SmartChainGuard! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write clear and concise commit messages.
4.  Submit a pull request with a detailed description of your changes.
5.  Ensure that all tests pass before submitting the pull request.
6.  Adhere to the code style and conventions used in the project.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/jjfhwang/SmartChainGuard/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to acknowledge the contributions of the open-source community to the cryptographic libraries and tools used in this project. Specifically, we extend our gratitude to the developers of circomlibjs, snarkjs, and noble-secp256k1.