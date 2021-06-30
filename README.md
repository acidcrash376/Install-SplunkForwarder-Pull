# Deploy-SplunkForwarder-Pull
A Splunk Forwarder deployment tool to pull the installer rather than push via WinRM

# Usage
## Batchfile
@ECHO OFF
PowerShell -NoProfile -ExecutionPolicy Bypass -Command "& {Start-Process PowerShell -ArgumentList '-NoProfile -ExecutionPolicy Bypass -File """"\\Path\To\Share\Install-SplunkForwarder.ps1"""" -verbosemode' -Verb RunAs}";

## GPO
New Group Policy Object
Computer Configuration > Preferences > Control Panel Settings > Scheduled Task
- New Task
- New Immediate Task (Windows 7)

### General
  Name: Install-SplunkForwarder
  User: <yourdomain>\<your account with install privileges>
### Actions
  Script: \\Path\To\Your\batchfile.bat
### Common
  [x] Apply once and do not reapply
  
Apply the GPO to the appropriate Org Unit, then either Gpupdate /force or let the Group Policy sync itself over time
