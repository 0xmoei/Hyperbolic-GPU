# Hyperbolic-GPU
Step by step guide to Rent and Connect to Hyperbolic GPU servers

## Create a Public SSH using PowerShell
### 1- Open Windows PowerShell
In Windows Start Menu, Find **Windows PowerShell**, Right click on it and click on Run as Administrator

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

### 6- Create SSH KEY in Hyperbolic
* Register In [Hyperbolic Dashboard](https://app.hyperbolic.xyz/invite/gqYoHbUk7)
* then, Visit **Settings**
* Create a new Public SSH key and paste your pubkey into it and save it!

## Rent a GPU
* Choose a GPU (.eg RTX 4090) [here](https://app.hyperbolic.xyz/compute) and click on `Rent`
* Make sure you select `1` as `GPU Count`
* Select `pytorch` as `Template`
* Rent it

![image](https://github.com/user-attachments/assets/aa51051c-f6ed-4a6f-9080-d8247634bfc3)

## Copy the GPU SSH command
After your server is `Ready to Connect`, just click on `SSH` button as image below to copy the command

![image](https://github.com/user-attachments/assets/7662c39f-087c-49d1-b483-ae7a7d6c4616)

* It must copy a command like this:
```
ssh ubuntu@xxxxxx.hyperbolic.xyz -p 312452
```

## Connect to GPU server
* Paste the command you copied in `PowerShell` to access your server.
* Enter the password you set for SSH public key and press enter to open your GPU terminal
* You can add this flag: `-i $env:USERPROFILE\.ssh\id_rsa` in front of your command, to specify the ssh privatekey file.
