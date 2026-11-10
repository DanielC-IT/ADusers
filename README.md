
# Active Directory - Bulk User Creation with PowerShell

In this lab, I used PowerShell to automate the creation of multiple users within an Active Directory domain. The objective was to configure domain user access on a Windows client, create multiple user accounts through a PowerShell script, and verify that those accounts could successfully log into a domain-joined computer.

## Environments and Technologies Used

* Windows Server 2022 (Domain Controller)
* Active Directory Domain Services (AD DS)
* Active Directory Users and Computers (ADUC)
* PowerShell
* Remote Desktop Protocol (RDP)
* Microsoft Azure

## Operating Systems Used

* Windows Server 2022 (DC-1)
* Windows 11 (Client-1)

## List of Prerequisites

* A Windows Server virtual machine configured as a Domain Controller.
* A Windows client virtual machine joined to the Active Directory domain.
* An administrator account with permissions to create Active Directory users.
* An Organizational Unit (OU) created within Active Directory to store the new users.
* PowerShell with the Active Directory module installed.
* Remote Desktop enabled on Client-1.

Refer to the previous [repo](https://github.com/DanielC-IT/activedirectoryprep/tree/main)

## Installation Steps

### Step 1: Configure Remote Desktop Access on Client-1

Log in to Client-1 using the domain administrator account. In this case, we will be using **mydomain.com/jane_admin**

Right-click the Windows Start button and select System. Once the System window opens, navigate to the Remote Desktop settings.

Open the Remote Desktop Users section and select Add. Enter the Domain Users security group and click OK.

Adding Domain Users to the Remote Desktop Users group allows standard domain users to remotely access Client-1 without requiring local administrator privileges.

<img width="455" height="373" alt="1" src="https://github.com/user-attachments/assets/449fc7a8-a748-45f5-8166-611e439405d1" />

<img width="1199" height="934" alt="2" src="https://github.com/user-attachments/assets/d073e7b6-6200-4778-9d9f-883aaeec590d" />

<img width="1193" height="647" alt="3" src="https://github.com/user-attachments/assets/01869735-0820-4979-b5a1-c2e63b011c9e" />

<img width="467" height="283" alt="4" src="https://github.com/user-attachments/assets/afb948c5-0cea-4880-b69a-bcd71ab2a272" />

<img width="375" height="333" alt="5" src="https://github.com/user-attachments/assets/36d03d7c-92a4-4bbd-8b1f-6a2fa661625d" />

### Step 2: Log Into the Domain Controller

Log in to DC-1 using the domain administrator account: **mydomain.com\jane_admin**

Once logged in, open PowerShell ISE as Administrator.

Use PowerShell ISE to run the script that automatically generates multiple Active Directory user accounts.

<img width="280" height="236" alt="6" src="https://github.com/user-attachments/assets/739d0099-544d-4b49-b161-f47c28924b34" />

### Step 3: Create Multiple Active Directory Users Using PowerShell

[Download or copy the raw file](https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1) of the PowerShell user creation script into PowerShell ISE.

The script generates random first and last names, creates usernames, and automatically provisions user accounts within the designated **_EMPLOYEES** Organizational Unit.

Press the ▶️ button above to start the script

Once executed, PowerShell will display the usernames of the accounts being created.

<img width="1751" height="884" alt="7" src="https://github.com/user-attachments/assets/4cf9a33d-77f0-4937-a61b-f129099420b7" />

<img width="800" height="402" alt="8" src="https://github.com/user-attachments/assets/562449e2-6a52-40dd-89d5-b6e599d38033" />

### Step 4: Verify the Newly Created Users

After the script finishes executing, open the Start menu on DC-1.

Navigate to:

```text
Windows Administrative Tools
    → Active Directory Users and Computers
```

Once Active Directory Users and Computers opens, expand the mydomain.com domain and select the **_EMPLOYEES** Organizational Unit.

All newly generated user accounts should now appear inside this folder.

This confirms that the PowerShell script successfully created the accounts and placed them within the correct Organizational Unit.

<img width="644" height="415" alt="9" src="https://github.com/user-attachments/assets/12df62ea-cce6-4278-98cc-5af27e824bf4" />

<img width="754" height="527" alt="10" src="https://github.com/user-attachments/assets/4864fca1-e49a-4495-a79e-dc10c2fd9115" />

### Step 5: Test Logging Into Client-1 With a Newly Created User

To verify that the newly created accounts can authenticate on a domain-joined computer, select one of the users created by the PowerShell script.

For this example, I used the account:**mydomain\bava.joso**

with the password being: **Password1**

Enter the temporary password configured during the PowerShell script execution.

The user should now be able to authenticate and log into Client-1, provided the computer has domain connectivity and the account has the necessary logon permissions.

Successfully logging in confirms that the account was created correctly and can authenticate against the Active Directory domain.

<img width="457" height="581" alt="11" src="https://github.com/user-attachments/assets/a7352e49-6d3b-4820-bf92-93ef9c976e92" />

## Active Directory User Creation Completed!

In this lab, I successfully automated the creation of multiple Active Directory user accounts using PowerShell. I also configured Remote Desktop access for standard domain users and verified that newly created accounts could authenticate on a domain-joined Windows client.

This exercise helped me gain hands-on experience with Active Directory administration, PowerShell scripting, user account provisioning, Organizational Unit management, and domain authentication.

These are essential skills used by IT Support Technicians and System Administrators when managing user accounts and access within an organization's network.

