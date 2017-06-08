# wcpatchreporting
A small collection of Windows scripts that can be run, from one CMD file, daily, to help track progress in patching Windows computers against WannaCry and post the results on a website. 

Purpose: Scan for and report Windows Computers that are vulnerable to WannaCry due to missing patches
Operation: Runs on single Windows server with IIS. Archives previous results, Resets the main web page, Scans all computers that have windows objects in AD and writes a log file, Parses log file for unpatched and available but fail to properly respond to patch query(trouble children).
Assumes:
Folder Structure: C:\scripts\logs, C:\scripts\ps\Patchchecker, C:\inetpub\reports, C:\inetpub\reports\archive
Runs under an AD account with full local admin permissions to all Windows devices. Technically whatever permissions allow remote WMI query.
You will find and replace the server name references in following scripts:
wc-logparser.ps1
wc-reset.ps1
They will look like this: {replace with FQDN of script host here} or {replace with short name of script host here}
Obviously remove the {} brackets as well.

This script, running in a windows scheduler on a domain joined windows server that also was runnign IIS, can give your staff/management a easy reference to check every morning to see your progress in patching against this malware. Could be re-used for future issues like this one by simply changing the KBs it's scanning for.
