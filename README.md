
# sBTC-ProofMint: Intellectual Property Protection Smart Contract

## Overview

This Clarity smart contract enables **secure registration, verification, transfer, and management of intellectual property (IP)** on a blockchain. It ensures **immutability and transparency** by registering hashed representations of IP content with optional expiration logic, allowing owners to extend, transfer, or update metadata securely.

## 📌 Features

* ✅ **IP Registration**
  Register unique IP using a 32-byte hash, with optional expiration block height.

* 🔍 **Ownership Verification**
  Check the registered owner of an IP ID.

* 🔑 **IP Transfer**
  Transfer ownership to another address (principal).

* 🔁 **IP Metadata Update**
  Update the hash of an IP entry (e.g., in case of updates to the IP content), with safety checks.

* ⏳ **Expiration Support**
  Set and extend expiration for IP records to limit registration duration.

* 📂 **Hash Uniqueness**
  Ensures that each IP hash is registered only once to prevent duplicate claims.

## 🔐 Security & Validation

* Ensures only the rightful owner can update or transfer an IP.
* Verifies valid input sizes and non-zero hashes.
* Rejects expired IP updates.
* Prevents hash collisions and duplicate registrations.

## 🧾 Data Structures

### Data Variables

* `owner`: The contract deployer and potential admin (not yet used in functions).
* `ip-counter`: Sequentially assigned ID for each IP.

### Maps

* `ip-registrations`:
  Stores IP records: owner, timestamp, hash, and optional expiration.

* `registered-hashes`:
  Ensures that each hash is only registered once.

## 🔧 Functions

### 1. `register-ip (ip-hash, expiration-block)`

Registers a new IP hash and returns a unique IP ID.

### 2. `check-ip-ownership (ip-id)`

Returns the principal address of the IP owner.

### 3. `verify-ip-hash (ip-id, hash-to-verify)`

Checks if a given hash matches the stored hash for an IP ID.

### 4. `transfer-ip (ip-id, new-owner)`

Allows the current owner to transfer IP ownership.

### 5. `extend-ip-registration (ip-id, new-expiration)`

Extends the expiration date of a registered IP.

### 6. `update-ip-metadata (ip-id, new-hash)`

Updates the IP’s hash (after verifying ownership, hash uniqueness, and expiration).

### 7. `is-hash-registered (ip-hash)`

Checks if a specific hash is already registered.

## ⚠️ Error Codes

| Code    | Meaning                     |
| ------- | --------------------------- |
| `u1000` | Not authorized              |
| `u1001` | Invalid hash length         |
| `u1002` | Hash is all zeros           |
| `u1003` | Hash already registered     |
| `u1004` | IP not found                |
| `u1005` | Invalid IP ID               |
| `u1006` | IP ID out of range          |
| `u1007` | IP expired                  |
| `u1008` | Invalid expiration provided |
| `u1009` | No expiration set           |

---
