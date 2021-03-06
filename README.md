
![wikibanner](https://user-images.githubusercontent.com/23490060/107761196-e0a29880-6d22-11eb-9dfc-35028c9463f6.png)

[![Version](https://img.shields.io/badge/redpill-1.2.5-brightgreen.svg?maxAge=259200)]()
[![Stage](https://img.shields.io/badge/Release-Beta-orange.svg)]()
[![Build](https://img.shields.io/badge/Supported_OS-Windows-orange.svg)]()
![licence](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)
![Last Commit](https://img.shields.io/github/last-commit/r00t-3xp10it/redpill)
![Repo Size](https://img.shields.io/github/repo-size/r00t-3xp10it/redpill)
![Open issues](https://img.shields.io/bitbucket/issues/r00t-3xp10it/redpill)

<br />

## :octocat: Project Description
The redpill project aims to assist reverse tcp shells in post-exploration tasks. Often in redteam engagements we<br />
need to use unconventional ways to access target system, such as reverse tcp shells (<b><i>not metasploit in order</i></b>)<br />
to bypass the defenses implemented by the system administrator. After the first stage was successful compleated<br />
we face another type of problems: "I have (shell) access to the target system, and now what can I do with it?"<br />

This project consists of several PowerShell scripts that perform different post-exploitation functions and the<br />
main script <b><i>redpill.ps1</i></b> that is main work its to download/config/exe the scripts contained in this repository.<br />

The goal is to have a similar meterpreter experience in our reverse tcp shell prompt (meterpreter similar options)<br />

<br />

|Folder Name|Description|Notes|
|---|---|---|
|Bin|Contains redpill main modules|Sysinfo \| GetConnections \| Persiste \| Keylogger \| etc.|
|Bypass|Contains redpill bypass scripts|Manual Download/Execution required|
|modules|Contains redpill modules|Sherlock \| CredsPhish \| Webserver \| StartWebServer \| etc.|
|Utils|Contains BAT \| PS1 scripts| Manual execution required|

<br />

<details>
<summary>CmdLet Parameters syntax\examples</summary>

<br />

     This cmdlet belongs to the structure of venom v1.0.17.8 as a post-exploitation module. venom amsi evasion agents
     automatically uploads this CmdLet to %TMP% directory to be easily accessible in our reverse tcp shell ( shell ).

<br />

<i>To List All Parameters Available, execute in powershell prompt:</i>

     PS C:\> .\redpill.ps1 -Help Parameters

<br />

|CmdLet Parameter Name|Parameter Arguments|Description|
|---|---|---|
|-SysInfo| Enum \| Verbose |Quick System Info OR Verbose Enumeration|
|-GetConnections| Enum \| Verbose |Enumerate Remote Host Active TCP Connections|
|-GetDnsCache| Enum \| Clear |Enumerate\Clear remote host DNS cache entrys|
|-GetInstalled| Enum |Enumerate Remote Host Applications Installed|
|-GetProcess| Enum \| Kill |Enumerate OR Kill Remote Host Running Process(s)|
|-GetTasks| Enum \| Create \| Delete |Enumerate\Create\Delete Remote Host Running Tasks|
|-GetLogs| Enum \| Verbose \| Clear |Enumerate eventvwr logs OR Clear All event logs|
|-GetBrowsers| Enum \| Verbose |Enumerate Installed Browsers and Versions OR Verbose|
|-Screenshot| 1 |Capture 1 Desktop Screenshot and Store it on %TMP%|
|-Camera| Enum \| Snap |Enum computer webcams OR capture default webcam snapshot|
|-StartWebServer| Python \| Powershell |Downloads webserver to %TMP% and executes the WebServer|
|-Keylogger| Start \| Stop |Start OR Stop recording remote host keystrokes|
|-MouseLogger| Start |Capture Screenshots of Mouse Clicks for 10 seconds|
|-PhishCreds| Start |Promp current user for a valid credential and leak captures|
|-GetPasswords| Enum \| Dump |Enumerate passwords of diferent locations {Store\|Regedit\|Disk}|
|-WifiPasswords| Dump \| ZipDump |Enum Available SSIDs OR ZipDump All Wifi passwords|
|-EOP| Enum \| Verbose |Find Missing Software Patchs for Privilege Escalation|
|-ADS| Enum \| Create \| Exec \| Clear|Hidde scripts { bat \| ps1 \| exe } on $DATA records (ADS)|
|-BruteZip| $Env:TMP\archive.zip |Brute force sellected Zip archive with the help of 7z.exe|
|-Upload| script.ps1|Upload script.ps1 from attacker apache2 webroot|
|-Persiste| $Env:TMP\Script.ps1 |Persiste script.ps1 on every startup {BeaconHome}|
|-CleanTracks| Clear \| Paranoid |Clean disk artifacts left behind {clean system tracks}|
|-FileMace| $Env:TMP\test.txt |Change File Mace {CreationTime,LastAccessTime,LastWriteTime}|
|-MsgBox| "Hello World." |Spawns "Hello World." msgBox on local host {wscriptComObject}|
|-SpeakPrank| "Hello World." |Make remote host speak user input sentence {prank}|
|-NetTrace| Enum |Agressive Enumeration with the help of netsh {native}|
|-PingSweep| Enum |Enumerate Active IP Address and open ports on Local Lan|

<br />

<i>To Display Detailed information about each parameter execute:</i>

     Syntax : .\redpill.ps1 -Help [ Parameter Name ]
     Example: .\redpill.ps1 -Help WifiPasswords

![Parametershelp](https://user-images.githubusercontent.com/23490060/107767610-1e0c2380-6d2d-11eb-946e-ce4988087dca.png)

</details>

<br />

<details>
<summary>Instructions how to use the Cmdlet {<b><i>Local tests</i></b>}</summary>

<br />

     This cmdlet belongs to the structure of venom v1.0.17.8 as a post-exploitation module. venom amsi evasion agents
     automatically uploads this CmdLet to %TMP% directory to be easily accessible in our reverse tcp shell ( shell ).
          ==> 'But this section describes how to test this Cmdlet Locally without exploiting the target host'. <==

<br />

1º - Download CmdLet from GitHub repository to <b><i>'Local Disk'</i></b>

        PS C:\> iwr -Uri https://raw.githubusercontent.com/r00t-3xp10it/redpill/main/redpill.ps1 -OutFile redpill.ps1

<br />

2º - Set Powershell Execution Policy to <b><i>'UnRestricted'</i></b>

     PS C:\> Set-ExecutionPolicy UnRestricted -Scope CurrentUser

![ste](https://user-images.githubusercontent.com/23490060/106375669-f2308b80-6385-11eb-8cff-947178c52915.png)

<br />

3º -  Browse to <b><i>'redpill.ps1'</i></b> storage directory

     PS C:\> cd C:\Users\pedro\Desktop

![redpillpath](https://user-images.githubusercontent.com/23490060/107781146-76e4b780-6d3f-11eb-9a41-de1163086c70.png)

<br />

4º - Access CmdLet Help Menu {All Parameters}

     PS C:\> .\redpill.ps1 -Help Parameters

![menu](https://user-images.githubusercontent.com/23490060/107781666-0c804700-6d40-11eb-9fbc-4826705534e5.png)

<br />

5º - Access <b><i>[ -WifiPasswords ]</i></b> Detailed Parameter Help

     Syntax : .\redpill.ps1 -Help [ Parameter Name ]
     Example: .\redpill.ps1 -Help WifiPasswords

![Parametershelp](https://user-images.githubusercontent.com/23490060/107767610-1e0c2380-6d2d-11eb-946e-ce4988087dca.png)

<br />

6º - Running <b><i>[ -WifiPasswords ] [ Dump ]</i></b> Module 

     Syntax : .\redpill.ps1 [ -Parameter Name ] [ @argument ]
     Example: .\redpill.ps1 -WifiPasswords Dump

![wifidump](https://user-images.githubusercontent.com/23490060/107768059-c7531980-6d2d-11eb-9f2a-2e2f2e649f56.png)

</details>

<br />

<details>
<summary>Instructions how to use the CmdLet under <b><i>Venon v1.0.17.8</i></b></summary>

<br />

     This cmdlet belongs to the structure of venom v1.0.17.8 as a post-exploitation module. venom amsi evasion agents
     automatically uploads this CmdLet to %TMP% directory to be easily accessible in our reverse tcp shell ( shell ).

<br />

1º - execute in reverse tcp shell prompt

    [SKYNET] C:\Users\pedro\AppData\Local\Temp> powershell -File redpill.ps1 -Help Parameters

<br />

![menu](https://user-images.githubusercontent.com/23490060/107781666-0c804700-6d40-11eb-9fbc-4826705534e5.png)

<br />

2º - Access <b><i>[ -WifiPasswords ]</i></b> Detailed Parameter Help

     [SKYNET] C:\Users\pedro\AppData\Local\Temp> powershell -File redpill.ps1 -Help WifiPasswords

![Parametershelp](https://user-images.githubusercontent.com/23490060/107767610-1e0c2380-6d2d-11eb-946e-ce4988087dca.png)

<br />

3º - Running <b><i>[ -WifiPasswords ] [ Dump ]</i></b> Module 

     [SKYNET] C:\Users\pedro\AppData\Local\Temp> powershell -File redpill.ps1 -WifiPasswords Dump

![wifidump](https://user-images.githubusercontent.com/23490060/107768059-c7531980-6d2d-11eb-9f2a-2e2f2e649f56.png)

</details>

<br />

<details>
<summary>To Manual download the CmdLet for Local Tests, execute:</summary><br />

        PS C:\> iwr -Uri https://raw.githubusercontent.com/r00t-3xp10it/redpill/main/redpill.ps1 -OutFile redpill.ps1

</details>

<br />

## :octocat: Video Tutorials

<br />

## :octocat: Acknowledgments

|Name|Function|OS Flavor|
|---|---|---|
|<b><i>@youhacker55|For All the help Debugging this cmdlet (Testing BETA version)|Windows 7 x64bits</b>|
|<b><i>@0xyg3n|For All the help Debugging this cmdlet (Testing BETA version)|Windows 10 x64bits</b>|
|<b><i>@Shanty_Damayanti|For All the help Debugging this cmdlet (amsi string detection bypasses)|Windows 10 x64bits</b>|

![geolocation](https://user-images.githubusercontent.com/23490060/107866747-c7593380-6e6b-11eb-8e38-9ef3acdb3c01.png)<br /><br />
![pingverbose](https://user-images.githubusercontent.com/23490060/107841656-87834500-6db4-11eb-953c-22e2322577b6.png)
![eopmodule](https://user-images.githubusercontent.com/23490060/108617459-78347500-740e-11eb-8cce-90994c2e048a.png)


<br />

## SuspiciousShellActivity - RedTeam @2021
