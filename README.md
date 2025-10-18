# 📝 Issue Factory Smart Contract

A decentralized **Issue Tracking and Voting System** built with **Solidity**, allowing users to **create issues** on the blockchain and **vote** on them transparently.  

---

## 📌 Overview

This project consists of two smart contracts:

- **`IssueFactory`** – Responsible for deploying and managing individual issue contracts.
- **`Issue`** – Represents a single issue with metadata (title, description, image) and supports voting functionality.

This contract can be used as a foundation for:
- 🗳️ Decentralized feedback/voting platforms  
- 🧾 Transparent reporting & issue tracking  
- 🌐 DAO-based governance systems  

---

## ⚙️ Features

- ✅ **Create Issues** with title, description, and image URL  
- 🏗️ **Deploys new Issue contracts dynamically** for each created issue  
- 👤 **Stores owner address** for each issue  
- 🕒 Emits events with timestamps for easy indexing  
- 🗳️ **Vote** on individual issues (on-chain)  
- 📡 Event logging for frontend integration or indexing services like **The Graph**.

---

## 🧭 Smart Contract Structure

### 1. `IssueFactory.sol`

| Function | Description |
|----------|-------------|
| `CreateIssue(string _title, string _disc, string _img)` | Creates a new `Issue` contract instance |
| `Issueaddress` | Stores all deployed issue addresses |
| `saveIssue` *(event)* | Emitted after issue creation with metadata |

### 2. `Issue.sol`

| Function | Description |
|----------|-------------|
| `constructor(string _I_title, string _I_disc, string _I_img, address _Owner)` | Initializes a new issue |
| `VoteforIssue(uint256 _vote)` | Allows anyone to vote for the issue |
| `Showvote` *(event)* | Emitted when a vote is cast |

---

## 🧪 Example Usage

```solidity
// Deploy IssueFactory
IssueFactory factory = new IssueFactory();

// Create an issue
factory.CreateIssue(
    "UI Bug in Dashboard",
    "The dashboard page crashes when loading analytics.",
    "https://example.com/bug-screenshot.png"
);

// Fetch deployed issue address
address newIssue = factory.Issueaddress(0);

// Interact with the Issue contract
Issue issue = Issue(newIssue);
issue.VoteforIssue(10);
