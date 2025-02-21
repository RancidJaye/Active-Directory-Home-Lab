<h1>Active Directory Home Lab - Enterprise Network Simulation</h1>

<h2>Description</h2>
This repository documents the **setup and configuration of a fully functional Active Directory (AD) environment** in a home lab. The lab simulates an **enterprise IT infrastructure** using Windows Server for domain management, Group Policy enforcement, and centralized authentication. This project provides hands-on experience in **user management, security policies, and network administration**.
<br />

<h2>Key Features & Configurations</h2>

- <b>Active Directory Domain Services (AD DS):</b> Configured a primary **Domain Controller (DC)** for centralized identity management.
- <b>DNS & DHCP Setup:</b> Integrated **Domain Name System (DNS) and Dynamic Host Configuration Protocol (DHCP)** for efficient network management.
- <b>Group Policy Object (GPO) Enforcement:</b> Implemented **security and access control policies** across users and computers.
- <b>User & Group Management:</b> Created **Organizational Units (OUs), user roles, and security groups** for domain users.
- <b>Remote Access & Administrative Tools:</b> Configured **RSAT (Remote Server Administration Tools) and RDP access**.
- <b>Event Logging & Auditing:</b> Enabled **Windows Event Viewer monitoring and audit policies** for security tracking.
- <b>Windows Firewall & Network Security:</b> Defined **firewall rules and security baselines** to protect domain assets.

<h2>Environments Used</h2>

- <b>Windows Server 2019 / 2022</b> (Domain Controller)
- <b>Windows 10 / 11</b> (Client Machines)
- <b>VMware Workstation / VirtualBox</b> (Virtualized Lab)
- <b>PowerShell & Active Directory Module</b> (Automation & Administration)

<h2>Project Walkthrough:</h2>

<p align="center">
Installing Windows Server: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Windows Server Installation"/>
<br />
<br />
Setting up Active Directory Domain Services (AD DS):  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="AD DS Setup"/>
<br />
<br />
Creating Organizational Units (OUs) & User Accounts: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="User Management"/>
<br />
<br />
Enforcing Group Policies via GPO:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Group Policy Enforcement"/>
</p>

<h2>Step-by-Step Implementation</h2>

<h3>1. Installing Windows Server & AD DS</h3>
<ul>
    <li>Install Windows Server 2019/2022 on a virtual machine.</li>
    <li>Add the **Active Directory Domain Services (AD DS)** role via Server Manager.</li>
    <li>Promote the server to a **Domain Controller (DC)** and configure the domain (e.g., `lab.local`).</li>
</ul>

<h3>2. Configuring DNS & DHCP</h3>
<ul>
    <li>Set up **DNS Forward Lookup Zones** for internal name resolution.</li>
    <li>Configure **DHCP Scopes** to assign dynamic IPs to domain-joined devices.</li>
</ul>

<h3>3. Creating Users & Organizational Units (OUs)</h3>
<ul>
    <li>Define **OUs for departments (IT, HR, Sales, etc.)**.</li>
    <li>Create **user accounts and assign them to security groups**.</li>
    <li>Use **PowerShell scripting** for bulk user creation:
        <pre><code>New-ADUser -Name "John Doe" -SamAccountName jdoe -UserPrincipalName jdoe@lab.local -AccountPassword (ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force) -Enabled $true</code></pre>
    </li>
</ul>

<h3>4. Enforcing Security Policies via Group Policy (GPO)</h3>
<ul>
    <li>Restrict **USB access, password policies, and login scripts**.</li>
    <li>Deploy **software and network drive mappings** via GPO.</li>
    <li>Run `gpupdate /force` to apply Group Policy settings immediately.</li>
</ul>

<h3>5. Monitoring & Logging</h3>
<ul>
    <li>Enable **Windows Event Viewer Auditing** for login tracking.</li>
    <li>Monitor Active Directory logs using:
        <pre><code>Get-EventLog -LogName Security -Newest 10</code></pre>
    </li>
</ul>

<h2>Example Output</h2>

```plaintext
----------------------------------------------
Active Directory Home Lab - Configuration Complete
----------------------------------------------
Domain Name: LAB.LOCAL
Number of Users: 50
Organizational Units: IT, HR, Sales, Admin
Group Policies Applied: Password Policy, USB Restriction, RDP Access
Event Logs Enabled: Yes
