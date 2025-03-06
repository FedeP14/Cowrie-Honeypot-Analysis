# Cowrie and Hydra Setup for Honeypot and Brute Force Attack

This document describes the steps I followed to set up Cowrie as a honeypot for defensive and analytical purposes, and Hydra with the `rockyou.txt` wordlist for simulating brute force attacks.

## 1. Setting Up Cowrie (Honeypot)

Cowrie is a medium interaction SSH and Telnet honeypot designed to log brute-force attacks and capture shell interaction attempts.

### Step 1: Installing Cowrie

I started by cloning the Cowrie repository from GitHub:

```bash
git clone https://github.com/cowrie/cowrie.git 
cd cowrie
```

### Step 2: Installing Dependencies

After cloning the repository, I created a virtual environment and installed the necessary dependencies with pip:

```bash
python3 -m venv cowrie-env
source cowrie-env/bin/activate
pip install -r requirements.txt
```

### Step 3: Configuring Cowrie

Next, I edited the cowrie.cfg configuration file to customize the honeypot's behavior. This includes setting the port for SSH (I chose port 2222 to avoid conflict with a real SSH service) and enabling logging

```bash
nano cowrie.cfg
```

In the configuration file, I made sure to set:
- **ssh_port = 2222** (to specify the custom port for the honeypot)
- **logfile = /var/log/cowrie/cowrie.log** (for logging attack details)

### Step 4: Running Cowrie

Once the configuration was complete, I started the honeypot with the following command:

```bash
bin/cowrie start
```

This started Cowrie and made it ready to capture any brute force attempts directed at the SSH service.

And finally i used the following command to keep an active log of attacks:

```bash
tail -f /var/log/cowrie/cowrie.log
```

## 2. Setting Up Hydra for Brute Force Attack

Hydra is a tool used for brute-force password cracking on remote systems. I used Hydra to simulate brute-force attacks on the Cowrie honeypot using the rockyou.txt wordlist.

### Step 1: Running Hydra with rockyou.txt

I ran Hydra to perform a brute-force attack against the Cowrie honeypot using the rockyou.txt wordlist, which contains common passwords:

hydra -l root -P /path/to/rockyou.txt ssh://<Honeypot-IP>:2222

In this command, I specified root as the login, and pointed Hydra to the rockyou.txt wordlist. The attack targeted the Cowrie honeypot running on port 2222.

## 3. Analyzing the Results

Once Hydra completed its brute-force attempts, I monitored the Cowrie logs to capture the attack details. The logs were stored at the location I specified in the cowrie.cfg file (/var/log/cowrie/cowrie.log).

```bash
tail -f /var/log/cowrie/cowrie.log
```

By reviewing the logs, I could see detailed information about each login attempt, including the usernames, passwords, and timestamps, See [analysis.md](analysis.md) for detailed findings.