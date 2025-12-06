# Healthcare-Records-Smart-Contract
🏥 HealthcareRecords
A Secure, Role-Based Medical Record System on the Ethereum Blockchain

HealthcareRecords is a Solidity smart contract that securely manages medical record metadata using blockchain technology. It provides role-based access control for doctors, supports patient self-records, and ensures all entries are immutable, auditable, and linked to off-chain storage (IPFS CIDs or other encrypted data sources).
This project was created for academic purposes to demonstrate secure authentication and trusted record management in decentralized systems.

🚀 Features
✔ Role-Based Access Control

Only the developer (contract deployer) can grant or revoke doctor permissions.

Doctors have specializations: Brain, Bone, or Lung.

✔ Secure Medical Records

Doctors and patients can create append-only medical records.

Each record includes:

recordId

Author (doctor/patient)

Timestamp

IPFS CID (or placeholder)

Metadata hash

Required doctor specialization

✔ Human-Readable Output

Doctor types return as strings (“Brain”, “Bone”, “Lung”) for easier frontend use.

✔ Complete Audit Trail

Every action emits events (DoctorGranted, DoctorRevoked, RecordAdded).

On-chain global log keeps a structured history of all added records.

✔ Privacy-Friendly

No personal health information (PHI) is stored on-chain.

The contract only stores metadata and off-chain pointers.

📦 Smart Contract Overview
File: HealthcareRecords.sol

Written in Solidity 0.8.20.

Key components:

enum DoctorType { Brain, Bone, Lung }

Developer-controlled doctor access

Patient-specific record indexing

Read-only view functions for:

Record count

Individual records

All patient records

Doctor specialization (string format)

🛠️ How to Use (Remix Instructions)

Open Remix IDE

Upload HealthcareRecords.sol

Select Solidity Compiler 0.8.20

Deploy contract using Injected Provider or Remix VM

As the deployer (developer), call:

grantDoctor(address, DoctorType)

Switch to the doctor account and call:

addRecord(patientAddr, ipfsCid, metaHash, requiredType)

Retrieve records using:

getRecord(patient, id)

getAllRecordsForPatient(patient)

🔒 Security Highlights

Only authorized doctors can add records.

Records are immutable once added.

Developer key controls role assignment (RBAC).

Full audit log stored on-chain + event-based logging.

📊 Performance Notes

addRecord costs ~80k–95k gas depending on string size.

View functions cost 0 gas when called off-chain.

Scales efficiently due to per-patient mappings.

📁 Project Purpose

This contract was developed as part of a university blockchain project to demonstrate:

Secure user authentication

Trusted data recording

Blockchain immutability

Role-based access with specialization

Smart contract auditing and analysis

🤝 Contributing

Feel free to fork, improve the contract, or build frontend integrations.

❤️ Acknowledgements

Ethereum & Solidity documentation

Remix IDE

AAST Blockchain Course Materials
