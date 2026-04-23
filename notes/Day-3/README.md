# 🛠️ Foundry & Solidity Setup Guide (Mac, Windows, Linux)

Welcome to **Day 3 of Web3 Security Learning** 🚀
Today’s focus: setting up a **Solidity development environment** using **Foundry**, **VS Code**, and **Git** across different operating systems.

---

## 📌 Prerequisites

Before starting, make sure you have:

* Basic command line knowledge
* Internet connection
* Administrator/sudo access

---

# 🔧 1. Install Git

## ✅ Mac

```bash
brew install git
```

## ✅ Linux (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install git -y
```

## ✅ Windows

1. Download Git from: https://git-scm.com/
2. Run installer with default settings

## 🔍 Verify Installation

```bash
git --version
```

---

# ⚙️ 2. Install Foundry (Forge, Cast, Anvil)

Foundry is a blazing fast toolkit for Ethereum development.

## 🌍 All OS (Mac/Linux/WSL)

```bash
curl -L https://foundry.paradigm.xyz | bash
foundryup
```

## 🪟 Windows (Recommended via WSL)

1. Install WSL:

```bash
wsl --install
```

2. Open Ubuntu (WSL) and run:

```bash
curl -L https://foundry.paradigm.xyz | bash
foundryup
```

## 🔍 Verify Installation

```bash
forge --version
cast --version
anvil --version
```

---

# 🧑‍💻 3. Install VS Code

Download from: https://code.visualstudio.com/

## 🔌 Recommended Extensions

* Solidity (by Juan Blanco)
* Foundry Toolkit (if available)
* Prettier
* GitLens

---

# 🏗️ 4. Create Your First Foundry Project

```bash
forge init my-foundry-project
cd my-foundry-project
```

### Project Structure

```
my-foundry-project/
├── src/        # Smart contracts
├── test/       # Tests
├── script/     # Deployment scripts
├── lib/        # Dependencies
```

---

# 📝 5. Writing Your First Smart Contract

Create a file in `src/`:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract HelloWorld {
    string public message = "Hello, Web3!";

    function setMessage(string memory _msg) public {
        message = _msg;
    }
}
```

---

# 🧪 6. Compile & Test

## Compile

```bash
forge build
```

## Run Tests

```bash
forge test
```

---

# ⛓️ 7. Run Local Blockchain (Anvil)

```bash
anvil
```

This starts a local Ethereum node for testing.

---

# 🚀 8. Deploy Smart Contract

Example script:

```bash
forge create src/HelloWorld.sol:HelloWorld \
--private-key <YOUR_PRIVATE_KEY> \
--rpc-url http://127.0.0.1:8545
```

---

# 🧾 9. Git Setup for Your Project

## Initialize Repo

```bash
git init
```

## Add Files

```bash
git add .
git commit -m "Initial Foundry project setup"
```

## Connect to GitHub

```bash
git remote add origin https://github.com/your-username/your-repo.git
git push -u origin main
```

---

# 🖥️ OS-Specific Notes

## 🍎 Mac

* Install Homebrew if not installed:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## 🐧 Linux

* Ensure `curl` is installed:

```bash
sudo apt install curl
```

## 🪟 Windows

* Use **WSL (Ubuntu)** for best compatibility
* Avoid native Windows setup for Foundry

---

# 🔐 Security Notes (Important for Auditors)

* Never expose private keys
* Use `.env` files for secrets
* Always test locally before mainnet deployment
* Use static analysis tools later (Slither, Mythril)

---

# 🎯 Summary

You now have:

* ✅ Git installed
* ✅ Foundry setup (Forge, Cast, Anvil)
* ✅ VS Code configured
* ✅ First Solidity contract
* ✅ Local blockchain running
* ✅ GitHub integration

---

Happy Building & Securing Web3 🔐✨
