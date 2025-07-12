# WN10-SO-000255-STIG-IMPLEMENTATION

<img width="2418" height="1476" alt="image" src="https://github.com/user-attachments/assets/73b8599b-3f39-43e5-b041-f0756d3ac691" />


📌 WN10-SO-000255 — Why This Was Fixed
Requirement:
User Account Control (UAC) must automatically deny elevation requests for standard users.

Why fix this:
Allowing standard users to elevate privileges can let malicious software or unauthorized users gain administrative access, increasing the risk of system compromise. By automatically denying all elevation requests for standard users, you help enforce least privilege and prevent unauthorized privilege escalation, which protects system integrity and reduces the attack surface.

✅ Key benefit:
Stops standard accounts from running privileged operations — ensuring only authorized admins can perform tasks that require elevated permissions.

<img width="2422" height="1644" alt="image" src="https://github.com/user-attachments/assets/081ef2f8-74d0-44e4-b134-ffea42427d24" />

Powershell script used to fix: 

# WN10-SO-000255 - Fix: Deny elevation requests for standard users

# Run as Administrator!

# Set ConsentPromptBehaviorUser to 0 to automatically deny elevation requests
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" `
  -Name "ConsentPromptBehaviorUser" `
  -Type DWord `
  -Value 0

Write-Output "UAC behavior for standard users set to 'Automatically deny elevation requests'. STIG WN10-SO-000255 compliant."


