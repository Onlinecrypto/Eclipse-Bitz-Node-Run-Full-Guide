# Bitz Node Miner – Full Setup Guide (PC / VPS / macOS)

> **Official Docs:** Still being updated...  
> **CA (Eclipse):** `64mggk2nXg6vHC1qCdsZdEFzd5QGN4id54Vbho4PswCF`  
> **Wallet Needed:** [Backpack Wallet](https://chromewebstore.google.com/detail/backpack/aflkmfhebedbjioipglgcbcmnbpgliof)  
> **Fund Wallet:** Minimum `0.005 ETH` on Eclipse

---

## 🛠️ Step 1: Install Dependencies

**For Windows (WSL) / Linux / VPS:**
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl nano build-essential -y
```

**For macOS:**
```bash
brew install git curl wget nano tmux htop jq make gcc autoconf automake pkg-config openssl leveldb lz4 coreutils
```

---

## ⚙️ Step 2: Install Rust, Node.js, Yarn

**For WSL / VPS:**
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
rustc --version
sudo apt-get update && curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt-get install -y nodejs
node -v && npm -v
sudo npm install -g yarn
yarn -v
```

**For macOS:**
```bash
brew install curl node yarn rust
```

---

## 🔧 Step 3: Install Solana CLI

**For WSL / VPS:**
```bash
curl --proto '=https' --tlsv1.2 -sSfL https://solana-install.solana.workers.dev | bash
source $HOME/.bashrc
solana --version
```

**If "solana" not found (WSL fix):**
```bash
echo 'export PATH="/root/.local/share/solana/install/active_release/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

**For macOS:**
```bash
sh -c "$(curl -sSfL https://solana-install.solana.workers.dev)"
source $HOME/.bash_profile
solana --version
```

**For VPS:**
```bash
reboot
```

---

## 🔁 Step 4: Configure RPC for Eclipse

```bash
solana config set --url https://mainnetbeta-rpc.eclipse.xyz/
```

---

## 🔐 Step 5: Create a New Wallet

```bash
solana-keygen new
```
> Press ENTER and securely save your generated seed phrase.

---

## 🔑 Step 6: Export Private Key

```bash
cat ~/.config/solana/id.json
```
> Copy the list of numbers and import it into your Backpack Wallet under "Private Key".  
> Fund the wallet with at least 0.005 ETH on Eclipse.

---

## 🚀 Step 7: Install Bitz CLI

```bash
cargo install bitz
```

**For VPS Only:**
```bash
apt install screen -y
screen -S bitz
```

---

## ⚒️ Step 8: Start Mining

**Normal (Default Single Core):**
```bash
bitz collect
```

**Using 4 Cores:**
```bash
bitz collect --cores 4
```

**VPS Tip:** Press `CTRL + A + D` to detach the screen and keep mining running in background.  
**Reconnect:**  
```bash
screen -r bitz
```

---

## ⛏️ Claiming Rewards

```bash
bitz claim
```

---

## 📊 Check Wallet Status

```bash
bitz account
```

---

## 🔄 Daily Use (Next Day)

> Just open terminal again and run:
```bash
bitz collect
```

---

## ❌ Delete Node/Wallet Files (if needed)

```bash
rm -rf ~/.config/solana
```

---

**Made with love by ArunCryptoVerse**
