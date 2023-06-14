# gdRecover
Will PSRemote to a windows host to clear top running procs by mem usage. w3wp.exe. php-cgi.exe and dump processes.

Change Log v3.7
=========

Used for Windows Shared Hosting to recover HARD alerting servers.

gdRecover was designed to use with a Windows 2008 (and up) Server that is unreachable via traditional RDP. The script does use PsRemote to connect to the remote server in question, and allow you to run a set of commands to asssist in the recovery of the server, and allow you to gain access via RDP by killing off select w3wp.exe and php-cgi.exe processes.

Version Information:

  3.6 : Added Variable Cleaning

  3.5 : Added password management for gdhosting

  3.1 : Removed PSEXEC and replaced with Invoke-Command.

  3.0 : Minor Changes, Added Encrypted password Support
  
  2.2 : Added an additional Paramater to specify the amount of memeory to be used when checking which procs to kill.
  
  2.0 : Base version allowed you to specify a server name to kill a pre specified list of procs against a given server.

gdRecover does this by running a TaskKill against the w3wp.exe and php-cgi.exe process's. To maintain system uptime and our provisioning system gdRecover will ignore all w3wp.exe’s and php-cgi.exe procs with the users SYSTEM, LOCAL SERVICE, NETWORK SERVICE and Iusr_gridweb.

If you have any issues running this script, please follow the below.

To setup powershell, here is a great local article - https://confluence.godaddy.com/display/EB/Powershell+Script+Execution+Guide

Make sure to set the execution policy (covered above as well) - Set-ExecutionPolicy RemoteSigned

Make sure to add gdhosting to the trusted hosts list - Set-Item -Path WSMan:\localhost\Client\TrustedHosts -Value '*.gdhosting.gdg' -Force | Out-Null

If you still have problems with the above and getting the same error. Just manually update your systems Registry with "regedit"

In Regedit you can paste this into find to open it up
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WinRM\Client]

Delete what you have for domains and replace with this.
*.jomax.paholdings.com,*.dc1.corp.gd,*.int.godaddy.com,*.prod.iad2.gdg,*.prod.iad2.secureserver.net,*.iad2.gdg,*.gdhosting.gdg,*.phx3.gdhosting.gdg,*.ams1.gdhosting.gdg,*.sin2.gdhosting.gdg,*.prod.phx3.gdg,*.cloud.phx3.gdg

If your seeing a Kerberos Authentication Error, then run - KList purge
