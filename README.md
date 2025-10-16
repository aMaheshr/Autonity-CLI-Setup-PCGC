# Autonity-CLI-Setup-PCGC
<img width="1684" height="886" alt="auto" src="https://github.com/user-attachments/assets/50b3184e-8cd7-4383-912e-00d6e7630039" />

## Requirements :
🔹U need Linux to setup CLI :  Vps or Gitpod

---------------------------------------------------------------------------------------------------------

Lets Start 💻

## Step 1 . Update system packages

### Open Terminal 
```console
sudo apt update && sudo apt upgrade -y

```

## Step 2 : Install Python 3 and pip tools
  
```console
sudo apt install -y python3 python3-venv python3-pip build-essential

```

#### Check Version
```console
python3 --version

```

## Step 3: Install pipx (isolated CLI installs)

```console
python3 -m pip install --user pipx
python3 -m pipx ensurepath

```

#### Reload shell so pipx is on PATH
```console
source ~/.profile || exec bash

```

## Step 4: Install Autonity CLI via pipx
```console
pipx install autonity-cli

```

🔹Check installation:
```console
aut --version

```

## Step 5 : Create or use an Autonity Mainnet account

🔹Create Autonity Mainnet 

🔹Save Address

```console
mkdir -p keystore
aut account new --keyfile keystore/myaddress.key

```
🔹Enter a password for the keyfile.

🔹Copy your new Autonity address; it will be displayed after creation.

## Step 6 : Sign your PCGC claim message

#### sample format : Change with ur details 

◽aut account sign-message -k keystore/myaddress.key "MyUsername,0xYourAddress,email@example.com,unique security code"

🔹Paste entire CMd in ur Terminal

🔹Copy Signature & save

## Step 7: Submit the claim form

🔗https://winners.autonity.org/

🔹Submit ur Details with created wallet Address & Signature

## Setp 8 : Complete KYC
🔗https://eu.onfido.app/f/fca0ce9f-bae9-4b1d-965d-986066eb296c
🔹Team will Review and Update with your Mail

-----------------------------------------------------------------------------------------------------------------------------------

### Backup Private Key

```console

# install helper libs (local user)
python3 -m pip install --user eth-account eth-keys

# decrypt script (will prompt for password)
cat > decrypt_keystore.py <<'PY'
import json
from eth_account import Account
fn = 'keystore/myaddress.key'
pw = input("Enter keyfile password (not echoed): ")
with open(fn,'r') as f:
    data = json.load(f)
try:
    priv = Account.decrypt(data, pw)
    print("Private key (KEEP SECRET): 0x" + priv.hex())
except Exception as e:
    print("Error:", e)
PY

python3 decrypt_keystore.py


```

🔹 just copy & paste Cmd & Enter ur Password
🔹 Backup private key & wallet address


## Remove Everything 

```console
# Remove keyfiles, keystore folder, scripts, and any exported private key files
rm -rf keystore myprivatekey.txt decrypt_keystore.py *.key *.json

```

----------------------------------------------------------------------------------------------------------

## Clear terminal history (optional)

```console
# Clear current session history
history -c

# Overwrite the history file
history -w

```

### Restart Shell

```console
exec bash

```

## Remove installed CLI tools (optional, full reset)

```console
pipx uninstall autonity-cli
pip uninstall -y pipx eth-account eth-keys
sudo apt autoremove -y

```

## Thats it 🥳

## FOllow on X & Github : x.com/cryptocrocks
