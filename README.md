# 🚀 BCDS: Blockchain Cloud Database System

A secure, hybrid cloud storage solution that combines **AES-256 Encryption**, **AWS S3 Storage**, and a **Smart Contract Ledger** to ensure data integrity, privacy, and automated access control.

![Project Status](https://img.shields.io/badge/Status-Active-success)
![License](https://img.shields.io/badge/License-MIT-blue)

## 🌟 Key Features

* **🔐 Military-Grade Encryption**: Files are encrypted on the server (AES-256) before transmission, ensuring privacy even from cloud providers.
* **☁️ AWS S3 Integration**: Scalable and durable object storage managed via the AWS SDK.
* **⛓️ Immutable Audit Ledger**: Every file upload is hashed (SHA-256) and recorded in a blockchain ledger to prove data integrity.
* **🛡️ Smart Contract ACL**: Access to shared workspaces is governed by a Blockchain Access Control List, verified on-chain before downloads are permitted.
* **💎 Subscription Management**: Dynamic storage quotas (Basic, Premium, Enterprise) with real-time usage tracking and Stripe integration.

---

## 🛠️ Tech Stack

* **Runtime**: Node.js
* **Framework**: Express.js
* **Database**: MongoDB Atlas
* **Storage**: AWS S3
* **Security**: JWT, BCrypt, Crypto
* **Web3**: Ethers.js, Solidity (Smart Contracts), Ganache/Sepolia
* **Payments**: Stripe API

---

## 📂 Project Structure

```text
blockchain-cloud-database-system/
├── middleware/
│   └── auth.js             # JWT Verification Middleware
├── models/
│   ├── Activity.js         # Activity Log Schema
│   ├── Block.js            # Blockchain Block Schema
│   ├── File.js             # File Metadata Schema
│   ├── Invitation.js       # Workspace Invitation Schema
│   └── User.js             # User & Subscription Schema
├── routes/
│   ├── activity.js         # User Activity Feed logic
│   ├── auth.js             # Registration & Password Management
│   ├── blockchain.js       # Ledger & Ethereum Anchoring
│   ├── reports.js          # Enterprise Analytics & Audit Exports
│   ├── storage.js          # S3 Upload/Download & ACL Enforcement
│   └── subscription.js     # Stripe Checkout & Workspace Management
├── contractABI.json        # Smart Contract Interface
├── dashboard.html          # Main Application UI
├── login.html              # Authentication UI
├── server.js               # Express Server Entry Point
└── package.json            # Project Dependencies
```

---

## ⚙️ Installation & Setup

**1. Prerequisites**
Ensure you have the following installed:

Node.js (v14 or higher)

MongoDB Atlas account

AWS S3 Bucket

Stripe Developer Account

Ethereum Provider (e.g., Ganache or Infura)

**2. Clone the Repository**

```text
git clone [https://github.com/27cvxy/blockchain-cloud-database-system.git](https://github.com/27cvxy/blockchain-cloud-database-system.git)
cd blockchain-cloud-database-system
```

**3. Configure Environment Variables**
Create a file named .env in the root directory. Use the template below and replace the placeholders with your actual credentials:

```text
PORT=5001
MONGO_URI=your_mongodb_connection_string

# AWS Credentials
AWS_ACCESS_KEY_ID=your_aws_access_key
AWS_SECRET_ACCESS_KEY=your_aws_secret_key
AWS_BUCKET_NAME=your_s3_bucket_name
AWS_REGION=your_aws_region

# Security & Encryption
ENCRYPTION_KEY=your_32_character_encryption_key
JWT_SECRET=your_jwt_secret_token

# Blockchain Configuration
CONTRACT_ADDRESS=your_deployed_smart_contract_address
RPC_URL=your_ethereum_rpc_url
SERVER_PRIVATE_KEY=your_wallet_private_key

# Stripe Payments
STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_WEBHOOK_SECRET=your_stripe_webhook_signing_secret
```

**4. Install Dependencies**

```text
npm install
```

**5. Run the Server**

```text
node server.js
```

---

## 🛠️ Advanced Service Setup

1. Stripe (Payment Gateway)
- To handle subscription upgrades and storage limit updates, follow these steps:

- API Keys: Log in to your Stripe Dashboard and copy your Secret Key from the Developers > API keys section.

- Webhook Forwarding: Since your local server cannot receive external webhooks directly, install the Stripe CLI and run:

Bash
- stripe listen --forward-to localhost:5001/api/subscription/webhook
- Signing Secret: Copy the whsec_ secret provided by the CLI and add it to your .env file.
  
- Product Setup: Create "Premium" and "Enterprise" products in your Stripe Dashboard and ensure their Price IDs match the configuration in your backend logic.

2. Ganache (Local Blockchain)
- The system uses a smart contract for Access Control Lists (ACL) and file integrity.

- Launch Ganache: Open the Ganache GUI or run ganache via CLI on port 7545.

- RPC URL: Ensure your .env matches the Ganache RPC server address (default: http://127.0.0.1:7545).

- Private Key: Copy one of the private keys from Ganache and paste it into SERVER_PRIVATE_KEY in your .env. This allows the server to grant/revoke file access on-chain.

- Contract Deployment: Deploy your access control contract and paste the resulting address into the CONTRACT_ADDRESS field in your .env.

3. AWS S3 (Cloud Storage)
- Create an S3 Bucket and ensure the IAM user associated with your AWS_ACCESS_KEY_ID has AmazonS3FullAccess permissions.

- Ensure the AWS_REGION in your .env matches your bucket's physical location.
