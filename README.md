# Decentralized Course Archive: Web3 Academic Resource Management

The Decentralized Course Archive is a Web3 application (dApp) engineered for secure,
transparent, and censorship-resistant preservation of academic curricula and pedagogical resources.
The system leverages the Ethereum blockchain and the InterPlanetary File System (IPFS)
to achieve cryptographic data sovereignty, immutability, and decentralized access governance.

---

## Technical Architecture

```text
+---------------------------------------------------------------+
|                      Client Presentation                      |
|   React.js Single-Page Application (course-archive-frontend)  |
+---------------------------------------------------------------+
            |                                       |
            | EIP-1193 RPC                          | Pinning Gateway (REST)
            v                                       v
+-----------------------+               +-----------------------+
|  MetaMask Provider    |               |  IPFS Storage Network |
|  - Cryptographic Auth |               |  - Content Addressed  |
|  - Transaction Sign   |               |  - Immutable CIDs     |
+-----------------------+               +-----------------------+
            |                                       ^
            v                                       | (IPFS CID Mapping)
+---------------------------------------------------+-----------+
|                     On-Chain Smart Contract                   |
|   Solidity ^0.8.x (course-archive/contracts)                  |
|   - Granular RBAC (Admin, Teacher, Student)                   |
|   - Immutable Resource Registry (Title, Faculty, IPFS CID)   |
|   - Event Emission for Verifiable Audit Logging               |
+---------------------------------------------------------------+
```

---

## Core Implementations

### 1. Decentralized Identity & Access Governance (RBAC)
- **Cryptographic Sign-In:** Password-less authentication leveraging asymmetric ECDSA key pairs through MetaMask.
- **On-Chain Access Matrix:** Enforces granular role-based permissions (Administrator, Faculty, Enrolled Student) directly inside smart contract modifiers.

### 2. Hybrid Storage Architecture
- **On-Chain Metadata Persistence:** Retains metadata (hashes, course codes, timestamps, author public addresses) on the Ethereum blockchain for deterministic indexing.
- **Off-Chain IPFS Content Addressing:** Preserves large course syllabi, slides, and datasets across distributed IPFS nodes, referencing them via immutable cryptographic CIDs.

### 3. Event-Driven Auditing
- **EVM Event Emission:** Broadcasts Solidity events (`CourseUploaded`, `AccessGranted`, `ResourceRevoked`) to provide an immutable and publicly verifiable audit trail.

---

## Project Structure

```text
decentralized-course-archive/
├── README.md                          # Technical specification and system architecture
├── package.json                       # Workspace dependency configuration
├── course-archive/                    # Truffle smart contract suite
│   ├── contracts/                     # Solidity smart contract sources (.sol)
│   ├── migrations/                    # Deployment migration scripts
│   └── truffle-config.js              # Network configurations (Ganache, Sepolia)
└── course-archive-frontend/           # Decentralized client interface
    ├── src/                           # React components, Web3 hooks, and contract ABIs
    └── package.json                   # Frontend dependencies (React, Web3.js)
```

---

## Deployment & Setup

### Prerequisites
- Node.js 18+ & npm
- Truffle Suite (`npm install -g truffle`)
- Ganache (Local Blockchain CLI or Desktop)
- MetaMask Browser Extension

### 1. Deploy Smart Contracts
```bash
git clone git@github.com:ind4x/decentralized-course-archive.git
cd decentralized-course-archive/course-archive
truffle migrate --reset
```

### 2. Launch Client Interface
```bash
cd ../course-archive-frontend
npm install
npm start
```
Open `http://localhost:3000` and connect your MetaMask wallet to the local Ganache RPC endpoint (`http://127.0.0.1:7545` or `8545`).

---

## Technology Stack

- **Smart Contracts:** Solidity ^0.8.x
- **Development & Testing:** Truffle Suite, Ganache
- **Blockchain Bridge:** Web3.js
- **Distributed Storage:** IPFS (InterPlanetary File System)
- **Frontend Framework:** React.js, SCSS
- **Wallet Standard:** MetaMask (EIP-1193)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Author

- **Author:** Youssef Fellah ([ind4x_](https://github.com/ind4x))
- **Institution:** Mundiapolis University, Engineering Cycle
