
# PowerShell Documentation

A brief description of PowerShell introduction


## Installation

Download PowerShell 7:

a. Go to the official PowerShell GitHub releases page to download the latest stable version of PowerShell 7: PowerShell GitHub Releases

b. Select the version that corresponds to your Windows version (usually an x64 MSI package) and click to download it.

Run the Installer:

a. Once the download is complete, run the MSI installer you downloaded. Follow the on-screen instructions to install PowerShell 7.

b. Accept the license agreement.
Choose the installation location.
You can select whether to add PowerShell 7 to your PATH environment variable. This is recommended for easier access to PowerShell.

# PowerShell Version


To check version of PowerShell

```powershell
  PS C:\> $PSVersionTable.PSVersion
```


## Screenshots

!Major  Minor  Build  Revision
-----  -----  -----  --------
7      1      0      0

# Commandlets

Some of the basic cmdlets used within the Active Directory Module for PowerShell, for manipulating Users, Groups, Computers and Objects.Powershell naming system has quite strict rules of naming cmdlets (Verb-Noun template;

```powershell
  PS C:\> Get-Date
  PS C:\> Get-Service
  PS C:\> Get-Command
  PS C:\> Get-Help Get-Service 
  PS C:\> Get-Help Get-Service -Full
 
```
# Aliases
Powershell enables using shortcuts - aliases - instead of cmdlet names.
You can write ls, dir or gci instead of Get-ChildItem and get the same result. Alias is equivalent to
its cmdlet.
```bash
  PS C:\> get-alias -Definition Get-ChildItem


CommandType Name Version Source
----------- ---- ------- ------
Alias dir -> Get-ChildItem
Alias gci -> Get-ChildItem
Alias ls -> Get-ChildItem


PS C:\> Set-Alias -Name proc -Value Get-Process
PS C:\> proc

Handles NPM(K) PM(K) WS(K) VM(M) CPU(s) Id SI ProcessName
------- ------ ----- ----- ----- ------ -- -- -----------
292 17 13052 20444 ...19 7.94 620 1 ApplicationFrameHost
....
```
## Automatic Variables
Introduction
Automatic Variables are created and maintained by Windows PowerShell.  These variables, without a doubt, will be the most
repetitious objects you use in PowerShell next to functions (like $? - indicates Success/ Failure
status of the last operation)

Syntax  
• $$ - Contains the last token in the last line received by the session.    
• $^ - Contains the first token in the last line received by the session.   
• $? - Contains the execution status of the last operation.     
• $_ - Contains the current object in the pipeline

### Array

```
$myArray+="test5"
$myArray=$myArray-ne "test2"
$myArray

##########################################

$myList=New-Object -TypeName System.Collections.ArrayList

[void]$myList.Add("Test1")
[void]$myList.Add("Test2")
$myList.AddRange(@("Test3","Test4","Test5"))
$myList.Remove("Test2")
$myList

```

### Homework 1

```
function Test-MicrosoftEmail {
    #mandatory parameter
    param(
        [string]$EmailAddress
    )

    $isMicrosoftEmail = $EmailAddress -like "*@microsoft.com"

    return $isMicrosoftEmail
}


$email1 = "pratik.sapkota@gmail.com"
$email2 = "pratik.sapkota@microsoft.com"
$email3="amitkumarkushwaha445@gmail.com"

$isMicrosoft1 = Test-MicrosoftEmail -EmailAddress $email1
$isMicrosoft2 = Test-MicrosoftEmail -EmailAddress $email2
$isMicrosoft3 = Test-MicrosoftEmail -EmailAddress $email3

```


### ForEach Loop

```
foreach loop
$filePath= "C:\Scripts\Data\FolderNames.txt"
$foldersPath="C:\Scripts\Data"
$folderNames=Get-Content -Path $filePath

foreach($name in $folderNames){
    if((Test-Path -Path "$foldersPath\$name")-eq $false){
        New-Item -Path "$foldersPth" -Name $name-ItemType Directory
    }else{
        Write-Output "Folder exists"
    }
}
```
 








