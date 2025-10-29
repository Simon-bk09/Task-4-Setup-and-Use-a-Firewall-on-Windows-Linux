# Task-4-Setup-and-Use-a-Firewall-on-Windows-Linux

# Table of Contents

- [Objective](#objective)
- [Tools Used](#tools-used)
- [Windows Firewall Inbound Rule Configuration](#windows-firewall-inbound-rule-configuration)
- [Windows Firewall Outbound Rule Configuration](#windows-firewall-outbound-rule-configuration)
- [Proof of Concept (PoC) of Firewall Blocking Rule](#proof-of-concept-poc-of-firewall-blocking-rule)
- [Linux Firewall Inbound Rule Configuration with `ufw`](#linux-firewall-inbound-rule-configuration-with-ufw)
- [Conclusion](#conclusion)


## Objective
Configure and test basic **firewall rules** to allow or block specific **programs**. This helps control how applications communicate over the network and enhances security awareness.

## Tools Used
- **Windows Firewall (Advanced Security)**
- **UFW (Uncomplicated Firewall)** on Linux

## Windows Firewall Inbound rule configuration

### Step 1 : Before adding firewall rule PoC
1. Lunching `Chrome`
<img width="1365" height="767" alt="Screenshot 2025-10-29 155321" src="https://github.com/user-attachments/assets/0d3ba0aa-af11-4e7a-93b2-1ea1cdc938c1" />

### Step 2: Open Firewall Console
1. Press `Windows + R`
2. Type: `control firewall.cpl`
3. Press Enter → opens 
<img width="406" height="203" alt="Lunching Windows Defender FireWall" src="https://github.com/user-attachments/assets/b131adb4-0670-4dc4-8210-4ee9c7d14f28" />

4. Lunch **Windows Defender Firewall with Advanced Security**
<img width="1128" height="590" alt="Window Defender Firewall home page" src="https://github.com/user-attachments/assets/23518058-cef6-4c11-ae95-6f168ce53914" />

   
### Step 3: View Current Rules
- Go to **Inbound Rules** → lists all active program and service rules.
<img width="1042" height="647" alt="in" src="https://github.com/user-attachments/assets/96165aa1-cf74-4213-be58-5eea24edcb90" />

### Step 4: Create a Rule to Block a Program
1. Click **New Rule…**
2. Select **Program** → Next
   
<img width="712" height="579" alt="Screenshot 2025-10-29 154243" src="https://github.com/user-attachments/assets/502edad8-7775-4b2e-a946-f3b36af6f226" />

3. Choose **This program path:** and browse to your app :
<img width="709" height="577" alt="Screenshot 2025-10-29 154437" src="https://github.com/user-attachments/assets/578d50d4-fac8-4184-9c86-9f6a2c5f9cc3" />

4. Select BLock The Connection
<img width="715" height="576" alt="Screenshot 2025-10-29 154505" src="https://github.com/user-attachments/assets/6e6addb8-c7a7-4f83-ae9f-94ffd70a1043" />

5. Selecting  all the profile and Naming the program and hitting Finish.
<img width="709" height="586" alt="Screenshot 2025-10-29 154525" src="https://github.com/user-attachments/assets/ffeb5fcc-2fb1-4643-8d53-21d0459b0985" />
<img width="707" height="572" alt="Screenshot 2025-10-29 162030" src="https://github.com/user-attachments/assets/65e113c4-60bb-49be-9974-73361316030e" />

## Windows Firewall Outbound rule configuration

### Step 1: View Current Rules
- Go to **Outbound Rules** → lists all active program and service rules.
<img width="1049" height="651" alt="out" src="https://github.com/user-attachments/assets/b2b4a93d-e520-4123-a013-f3a571a08564" />


### Step 2: Create a Rule to Block a Program
1. Click **New Rule…**
2. Select **Program** → Next<img width="715" height="577" alt="Screenshot 2025-10-29 155348" src="https://github.com/user-attachments/assets/dc72e285-c494-45f0-97e3-526b93176c1e" />

3. Choose **This program path:** and browse to your app :
<img width="714" height="581" alt="Screenshot 2025-10-29 155534" src="https://github.com/user-attachments/assets/3b553d55-533e-4f9b-9cd6-5b2eabb836d1" />

4. Select BLock The Connection
<img width="714" height="577" alt="Screenshot 2025-10-29 155553" src="https://github.com/user-attachments/assets/efd05c75-1449-4d00-8a05-4c62269d00af" />

5. Selecting  all the profile and Naming the program and hitting Finish.
<img width="708" height="576" alt="Screenshot 2025-10-29 155612" src="https://github.com/user-attachments/assets/5d578d6f-33c5-48df-8597-578bee4e135a" />
<img width="720" height="578" alt="Screenshot 2025-10-29 155657" src="https://github.com/user-attachments/assets/f223f492-318a-4aa8-b2ec-e560fd21d8c4" />

# Proof of Concept (PoC) of Firewall Blocking Rule 
<img width="1243" height="767" alt="Screenshot 2025-10-29 155711" src="https://github.com/user-attachments/assets/0028b8a6-0d0d-49c8-bdb8-094bb1bc6fad" />

## Linux Firewall Inbound rule configuration with `ufw`

### step 1:  Check Firewall Status
- To verify the current status of the firewall, using `sudo ufw status verbose` command:
<img width="1366" height="768" alt="1" src="https://github.com/user-attachments/assets/ebc5c17b-75c4-4207-8073-72f8781ffc5a" />

### Step 2: Enable Firewall
- To activate the firewall, run: `sudo ufw enable` .
<img width="1366" height="768" alt="2" src="https://github.com/user-attachments/assets/7e7f1670-32a7-4546-9ffa-2da0fc9d173d" />

### Step 3 : Block Port 23 (Telnet)
- To block the command, run: `sudo ufw deny 23/tcp`. This command add rules in firewall
<img width="1366" height="768" alt="4" src="https://github.com/user-attachments/assets/631e1843-026c-4aa5-8086-fc70d2238d36" />

### Step 4 : Verify Rules
- To verify the rules runL `sudo ufw status numbered`. This command shows all the rules of firewall
<img width="1366" height="768" alt="6" src="https://github.com/user-attachments/assets/d8d6d7c3-847e-4fee-a572-fe37fe6a1167" />

### Step 5 : Testing firewall rules
- To verify the rule, run `telnet localhost 23`.
<img width="1366" height="768" alt="7" src="https://github.com/user-attachments/assets/704fa740-c291-4528-b412-8fb7a89d08fc" />

# Conclusion 
This task demonstrated the setup, configuration, and testing of firewall rules on both Windows and Linux systems.On Windows, inbound and outbound rules were applied using Windows Defender Firewall to block application access (e.g., Chrome).On Linux (Kali), UFW was used to deny Telnet (port 23), preventing unauthorized network communication.Testing confirmed that blocked connections were successfully refused, showing that the rules worked correctly.Overall, the activity provided hands-on experience with how firewalls filter traffic, control program permissions, and enhance system security.





