🚀 BCDS: Blockchain Cloud Database System
A secure, hybrid cloud storage solution that combines AES-256 Encryption, AWS S3 Storage, and a Smart Contract Ledger to ensure data integrity, privacy, and automated access control.

🌟 Key Features
🔐 Military-Grade Encryption: Files are encrypted on the server (AES-256) before transmission, ensuring privacy even from cloud providers.

☁️ AWS S3 Integration: Scalable and durable object storage managed via the AWS SDK.

⛓️ Immutable Audit Ledger: Every file upload is hashed (SHA-256) and recorded in a blockchain ledger to prove data integrity.

🛡️ Smart Contract ACL: Access to shared workspaces is governed by a Blockchain Access Control List, verified on-chain before downloads are permitted.

💎 Subscription Management: Dynamic storage quotas (Basic, Premium, Enterprise) with real-time usage tracking and Stripe integration.

🛠️ Tech Stack
Runtime: Node.js

Framework: Express.js

Database: MongoDB Atlas

Storage: AWS S3

Security: JWT, BCrypt, Crypto

Web3: Ethers.js, Solidity (Smart Contracts), Ganache/Sepolia

Payments: Stripe API

📂 Project Structure
Plaintext
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
├── .env.example            # Template for environment variables
├── contractABI.json        # Smart Contract Interface
├── dashboard.html          # Main Application UI
├── login.html              # Authentication UI
├── server.js               # Express Server Entry Point
└── package.json            # Project Dependencies

⚙️ Installation & Setup
1. Prerequisites
Ensure you have the following installed:

Node.js (v14 or higher)

MongoDB Atlas account

AWS S3 Bucket

Stripe Developer Account

Ethereum Provider (e.g., Ganache or Infura)

2. Clone the Repository
Bash
git clone https://github.com/27cvxy/blockchain-cloud-database-system.git
cd blockchain-cloud-database-system
3. Configure Environment Variables
Create a file named .env in the root directory. Do not share this file. Use the following template and replace the placeholders with your actual credentials:

Code snippet
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
RPC_URL=your_ethereum_rpc_url (e.g., Infura or Ganache)
SERVER_PRIVATE_KEY=your_wallet_private_key

# Stripe Payments
STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_WEBHOOK_SECRET=your_stripe_webhook_signing_secret

4. Install Dependencies
Bash
npm install

6. Run the Server
Bash
node server.js
The server will start on the port specified in your .env file (default 5001).
