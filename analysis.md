# Analysis of Cowrie Honeypot Logs

## 1. Overview of the Attack
This document provides an analysis of the attacks recorded by Cowrie, a medium-interaction SSH honeypot. The attacks were conducted in a controlled lab environment, with a separate VM running Hydra for brute-force testing.

### Key Statistics
- **Total login attempts:** `1740`
- **Total unique attacker IPs:** `1 (Internal test: 192.168.1.98)`
- **Total successful logins:** `0`

## 2. Brute-Force Attack Details
- **Username used in all attempts:** `kali`
- **Password list source:** `rockyou.txt`
- **Total passwords tested:** `1659`
- **Successful logins with tested passwords:** `0`
- **Success rate:** `0%`


## 3. Attack Timeline
The attack attempts were distributed over a period of 5 minutes, with a total of 1740 attempts.

## 4. Attacker's IP Address
- **Attacker’s IP:** `192.168.1.98` (Internal network)
- **Geolocation:** Not applicable (Internal test environment)

