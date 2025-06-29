# 🔁 Guide to Migrating Your Trap on Drosera

## ✅ Step 1: Backup Current Trap Configuration

```bash
cd ~/my-drosera-trap
nano drosera.toml
```
➡️ Copy all contents of the `drosera.toml` file and save them in a secure location.  
📌 **Very important — you will need this information later.**

---

## 🔻 Step 2: Remove Old Drosera Project

```bash
cd ~/Drosera-Network
docker compose down -v

cd ~
rm -rf my-drosera-network
```

---

## 📦 Step 3: Recreate Directory and Configure Git

```bash
mkdir my-drosera-trap
cd ~/my-drosera-trap
```
```bash
git config --global user.email "Github_Email"
```
```bash
git config --global user.name "Github_Username"
```

---

## ⚙️ Step 4: Initialize Trap Again

```bash
forge init -t drosera-network/trap-foundry-template
```

---

## 🚀 Step 5: Install Bun Tool and Build

```bash
curl -fsSL https://bun.sh/install | bash
source /root/.bashrc
bun install
forge build
```

---

## 🔄 Step 6: Restore the `drosera.toml` Configuration File

```bash
rm drosera.toml
nano drosera.toml
```
➡️ Paste your previously backed up content into the `drosera.toml` file.

---

## 🛠 Step 7: Update RPC Configuration

Replace the following lines in `drosera.toml`:

```toml
drosera_rpc = "https://relay.testnet.drosera.io"
eth_chain_id = 17000
drosera_address = "0xea08f7d533C2b9A62F40D5326214f39a8E3A32F8"
```
➡️ with:

```toml
drosera_rpc = "https://relay.hoodi.drosera.io"
eth_chain_id = 560048
drosera_address = "0x91cB447BaFc6e0EA0F4Fe056F5a9b1F14bb06e5D"
```

---

## 🔐 Step 8: Apply the New Trap

```bash
DROSERA_PRIVATE_KEY=your_private_key drosera apply
```

---

## 🔁 Step 9: Restart Drosera Operator

```bash
cd ~/Drosera-Network
docker pull ghcr.io/drosera-network/drosera-operator:latest
docker compose up -d
```

---

## 📍 Done!

Your trap has been successfully migrated to the new network.
