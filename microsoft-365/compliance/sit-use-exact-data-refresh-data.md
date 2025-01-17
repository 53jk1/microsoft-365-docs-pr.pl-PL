---
title: Odśwież dokładny plik tabeli źródła informacji zgodnych z danymi
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Odśwież plik tabeli źródła informacji poufnych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fe72fac43d3cc9a568d8aa1c5d985d34f8477a4d
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760850"
---
# <a name="refresh-your-exact-data-match-sensitive-information-source-table-file"></a>Odświeżanie dokładnego pliku tabeli źródła informacji poufnych zgodnych z danymi poufnymi 

Bazę danych informacji poufnych można odświeżać maksymalnie 5 razy co 24 godziny. Musisz ponownie przekazać i przekazać tabelę źródła informacji poufnych.

1. Ponownie wyeksportuj poufne dane do aplikacji, takie jak Microsoft Excel, i zapisz plik w formacie .csv, tsv lub rozdzielanym potokiem (|). Zachowaj tę samą nazwę pliku i lokalizację, której użyto podczas poprzedniego skrótu i przekazanego pliku. Zobacz [Eksportowanie danych źródłowych w celu dokładnego dopasowania danych do typu informacji poufnych opartych](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type) na danych, aby uzyskać szczegółowe informacje na temat eksportowania poufnych danych i uzyskiwania ich w prawidłowym formacie.

      > [!NOTE]
      > Jeśli nie ma żadnych zmian w strukturze (nazwach pól) pliku tabeli źródła informacji poufnych, podczas odświeżania danych nie trzeba wprowadzać żadnych zmian w pliku schematu bazy danych. Jeśli jednak musisz wprowadzić zmiany, pamiętaj, aby odpowiednio edytować schemat bazy danych i pakiet reguł. Zobacz [Zarządzanie dokładnym schematem dopasowania danych](sit-use-exact-data-manage-schema.md#manage-your-exact-data-match-schema) , aby uzyskać instrukcje edytowania lub usuwania schematu. Zobacz Create exact data match sensitive information type/rule package for the steps to edit or remove your EDM SIT/rule package ( [Tworzenie dokładnego dopasowania danych do poufnych informacji typu/pakietu reguł](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) ), aby zapoznać się z krokami edytowania lub usuwania pakietu EDM SIT/rule.

2. Użyj procedur w obszarze [Skrót i przekaż tabelę źródła informacji poufnych, aby dokładnie dopasować dane do typów informacji poufnych](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) , aby przekazać plik źródłowy tabeli informacji poufnych.

3. Za pomocą [harmonogramu zadań](/windows/desktop/TaskSchd/task-scheduler-start-page) można zautomatyzować skrót [i przekazać tabelę źródła informacji poufnych, aby uzyskać dokładne dane zgodne z procedurą typów informacji poufnych](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) . Zadania można zaplanować przy użyciu kilku metod:

   |Metoda|Co robić|
   |---|---|
   |Windows PowerShell|Zobacz dokumentację [scheduledtasks](/powershell/module/scheduledtasks/) i [przykładowy skrypt programu PowerShell](#example-powershell-script-for-task-scheduler) w tym artykule|
   |Interfejs API harmonogramu zadań|Zobacz dokumentację [harmonogramu zadań](/windows/desktop/TaskSchd/using-the-task-scheduler)|
   |interfejs użytkownika Windows|W Windows kliknij przycisk **Start** i wpisz Harmonogram zadań. Następnie na liście wyników kliknij prawym przyciskiem myszy harmonogram **zadań** i wybierz pozycję **Uruchom jako administrator**.|

### <a name="example-powershell-script-for-task-scheduler"></a>Przykładowy skrypt programu PowerShell dla harmonogramu zadań 

Ta sekcja zawiera przykładowy skrypt programu PowerShell, za pomocą którego można zaplanować zadania tworzenia skrótów danych i przekazywania danych skrótu:

#### <a name="schedule-hashing-and-upload-in-a-combined-step"></a>Planowanie tworzenia skrótów i przekazywania w połączonym kroku

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext"
$uploadDataArgs = '/UploadData /DataStoreName ' + $dataStoreName + ' /DataFile ' + $dataFile + ' /HashLocation' + $hashLocation + ' /Schema ' + $schemaFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadDataArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```

#### <a name="schedule-hashing-and-upload-as-separate-steps"></a>Planowanie tworzenia skrótów i przekazywania jako oddzielnych kroków

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$edmext = '.EdmHash'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
$hashFile = "$fileLocation\\$dataStoreName$edmext"
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext "

\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
$createHashArgs = '/CreateHash' + ' /DataFile ' + $dataFile + ' /HashLocation ' + $hashLocation + ' /Schema ' + $schemaFile
$uploadHashArgs = '/UploadHash /DataStoreName ' + $dataStoreName + ' /HashFile ' + $hashFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $createHashArgs -WorkingDirectory $edminstallpath
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadHashArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```
