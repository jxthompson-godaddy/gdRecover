# gdRecover

gdRecover v3.6
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

1. To setup powershell, here is a great local article - https://confluence.godaddy.com/display/EB/Powershell+Script+Execution+Guide
2. Make sure to set the execution policy (covered above as well) - Set-ExecutionPolicy RemoteSigned
3. Make sure to add gdhosting to the trusted hosts list - Set-Item -Path WSMan:\localhost\Client\TrustedHosts -Value '*.gdhosting.gdg' -Force | Out-Null
