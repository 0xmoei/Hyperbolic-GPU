# Rent and Setup GPU
Step by step guide to Rent, Setup and Connect to GPU servers.

# Step 1. Create a Public SSH using PowerShell
### 1- Open Windows PowerShell
In Windows Start Menu, Find **Windows PowerShell**, Right click on it and click on **Run as Administrator**.

### 2- In the terminal run:
```bash
ssh-keygen -t rsa -b 4096
```
* You'll see:
```
Generating public/private rsa key pair.
Enter file in which to save the key (C:\Users\YourUsername\.ssh\id_rsa):
```
* Press `Enter` to accept the default location (C:\Users\YourUsername\.ssh\id_rsa). This ensures the private key is named id_rsa and the public key is id_rsa.pub.

### 3- Set a Passphrase (Optional but Recommended)
* Output will look like:
```
Your identification has been saved in C:\Users\YourUsername\.ssh\id_rsa.
Your public key has been saved in C:\Users\YourUsername\.ssh\id_rsa.pub.
The key fingerprint is: SHA256:...
```

### 4- Navigate to `.ssh` directory
```
cd $env:USERPROFILE\.ssh
```

### 5- Copy the `id_rsa.pub` file content in clipboard
```
Get-Content id_rsa.pub | Set-Clipboard
```
* Your public key is now copied into your `clipboard`

# Step 2. Add SSH KEY to GPU Provider Site
### [Vast.ai:](https://cloud.vast.ai/?ref_id=228875) (Recommended for better performance)
* 1- Register in [Vast.ai](https://cloud.vast.ai/?ref_id=228875)
* 2- Create an SSH key session by going to `three-lines > Keys > SSH Keys` [here](https://cloud.vast.ai/manage-keys/)
* 3- Paste Public SSH key created in your local pc in previous steps.

### [Hyperbolic:](https://app.hyperbolic.xyz/invite/gqYoHbUk7)
* Register In [Hyperbolic Dashboard](https://app.hyperbolic.xyz/invite/gqYoHbUk7)
* then, Visit **Settings**
* Create a new Public SSH key and paste your pubkey into it and save it!

# Step 3. Rent a GPU & Get your GPU's SSH Command
* I use [Vast.ai](https://cloud.vast.ai/?ref_id=228875) & [Hyperbolic](https://app.hyperbolic.xyz/invite/gqYoHbUk7) since they have **crypto payments**
* I recommend Vast because of better performance
### [Vast.ai:](https://cloud.vast.ai/?ref_id=228875)
* 1- Select Pytorch(Vast) template [here](https://cloud.vast.ai/?ref_id=62897&creator_id=62897&name=PyTorch%20(Vast))
* 2- Choose a supported GPU (I recommend =24GB GPU vRAM, but Gensyn now supporting even 8GB GPU vRAM)
* 3- Increase `Disk Space` slidebar to `50GB`
* 4- Top-up credits with crypto and rent it.
* 5- Go to [instances](https://cloud.vast.ai/instances/), refresh the page, click on `key` button.
* 6- If you don't see a ssh command in `Direct ssh connect:` section, then you have to press on Add SSH Key.
* 7- Copy SSH Command, and Replace `-L 3000:localhost:3000` in front of the command.

### [Hyperbolic:](https://app.hyperbolic.xyz/invite/gqYoHbUk7)
* 1- Choose a GPU (.eg RTX 4090) [here](https://app.hyperbolic.xyz/invite/gqYoHbUk7) by going to `Home > GPU List ` and click on `Rent`
* 2- Make sure you select `1` as `GPU Count`.
* 3- Select `pytorch` as `Template`.
* 4- Rent it.
* 5- By clicking on your gpu instance, if gives you a SSH command to connect to your GPU terminal.
* 5- Add this flag: `-L 3000:localhost:3000` in front of your Hyperbolic's SSH command, this will allow you to access to port 3000 on your local system.

# Step 4. Connect to GPU server using SSH Command
* You must get a command like this. For example, it's hyperbolic's SSH Command:
```
ssh ubuntu@xxxxxx.hyperbolic.xyz -p 312452
```
* You can add this flag: `-L 3000:localhost:3000` in front of you command to get access to apps running on port 3000 from your local pc.
* Paste and Enter the command you copied in `Windows PowerShell` to access your server.
* Enter the password you set for SSH public key (if you set before) and press enter to open your GPU terminal
* Optionaly, you can add this flag: `-i $env:USERPROFILE\.ssh\id_rsa` in front of your command, to specify the ssh privatekey file.
