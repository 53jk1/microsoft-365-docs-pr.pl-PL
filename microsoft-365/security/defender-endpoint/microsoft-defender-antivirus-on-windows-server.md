---
title: Program antywirusowy Microsoft Defender na Windows Server
description: Dowiedz się, jak włączyć i skonfigurować Program antywirusowy Microsoft Defender w Windows Server 2016, Windows Server 2019 i Windows Server 2022.
keywords: windows defender, server, scep, ochrona punktu końcowego centrum systemu, serwer 2016, bieżąca gałąź, serwer 2012
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr, shwjha
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 01/26/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 0ea2184720467b3756b5cde8c8973e8952d5b50c
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009567"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Program antywirusowy Microsoft Defender na Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Program antywirusowy Microsoft Defender jest dostępna w następujących wersjach/wersjach programu Windows Server:

- Windows Server 2022
- Windows Server 2019
- Windows Server w wersji 1803 lub nowszej
- System Windows Server 2016
- Windows Server 2012 R2 (wymaga programu Microsoft Defender dla punktu końcowego)

W niektórych przypadkach Program antywirusowy Microsoft Defender jest nazywane *Endpoint Protection*, jednak aparat ochrony jest taki sam. Chociaż funkcje, konfiguracja i zarządzanie są w dużym stopniu takie same w przypadku Program antywirusowy Microsoft Defender w systemach [Windows 10](microsoft-defender-antivirus-windows.md) i Windows 11, istnieje kilka istotnych różnic w Windows Server:

- Na Windows serwera automatyczne [wykluczenia](configure-server-exclusions-microsoft-defender-antivirus.md) są stosowane na podstawie zdefiniowanej roli serwera.

- W Windows Server, jeśli używasz rozwiązania antywirusowego lub ochrony przed złośliwym oprogramowaniem innego niż firmy Microsoft, Program antywirusowy Microsoft Defender nie włącza się automatycznie ani do trybu pasywnego, ani wyłączonego. Można jednak ustawić tryb Program antywirusowy Microsoft Defender lub wyłączony ręcznie.

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Konfigurowanie Program antywirusowy Microsoft Defender na Windows Server

Proces konfigurowania i uruchamiania programu Program antywirusowy Microsoft Defender na platformie serwera składa się z kilku kroków:

1. [Włącz interfejs](#enable-the-user-interface-on-windows-server).
2. [Instalowanie Program antywirusowy Microsoft Defender](#install-microsoft-defender-antivirus-on-windows-server).
3. [Sprawdź Program antywirusowy Microsoft Defender czy jest uruchomiony](#verify-microsoft-defender-antivirus-is-running).
4. [Zaktualizuj zabezpieczenia przed złośliwym kodem](#update-antimalware-security-intelligence).
5. (W razie potrzeby) [Prześlij próbki](#submit-samples).
6. (W razie potrzeby) [Konfigurowanie wykluczeń automatycznych](#configure-automatic-exclusions).
7. (Tylko w razie potrzeby) Ustaw [Windows serwer na tryb pasywny](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>Włączanie interfejsu użytkownika na Windows Server

Domyślnie na Program antywirusowy Microsoft Defender i działa on na Windows Server. Czasami interfejs użytkownika jest domyślnie instalowany, ale interfejs użytkownika nie jest wymagany. Do zarządzania plikami możesz używać zasady grupy PowerShell, programu PowerShell Program antywirusowy Microsoft Defender.

Jeśli na serwerze nie zainstalowano graficznego interfejsu użytkownika i chcesz go zainstalować, należy użyć kreatora Dodawania ról i funkcji lub poleceń cmdlet programu PowerShell.

> [!NOTE]
> Ta opcja nie jest dostępna w przypadku Windows Server 2012 R2. Aby uzyskać więcej informacji, [zobacz Opcje instalowania programu Microsoft Defender dla punktu końcowego](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

### <a name="turn-on-the-gui-using-the-add-roles-and-features-wizard"></a>Włączanie graficznego interfejsu użytkownika przy użyciu Kreatora dodawania ról i funkcji

1. Zobacz [Instalowanie ról, usług ról i funkcji przy użyciu Kreatora](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) dodawania ról i funkcji, a następnie korzystanie z Kreatora dodawania **ról i funkcji**.

2. Po otworzyeniu kroku **Funkcje** kreatora w **obszarze** Funkcje Windows Defender wybierz graficznego interfejsu użytkownika, aby **Windows Defender** opcje.

   W Windows Server 2016 dodawania **ról i funkcji Kreator** dodawania funkcji wygląda następująco:

   ![Dodaj role i kreatora funkcji z wyświetloną graficznego interfejsu użytkownika Windows Defender opcji.](images/server-add-gui.png)

   W Windows Server 2019 i Windows Server 2022 Kreator dodawania **ról** i funkcji jest podobny.

### <a name="turn-on-the-gui-using-powershell"></a>Włączanie graficznego interfejsu użytkownika przy użyciu programu PowerShell

Następujące polecenie cmdlet programu PowerShell włączy interfejs:

```powershell
Install-WindowsFeature -Name Windows-Defender-GUI
```

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Instalowanie Program antywirusowy Microsoft Defender na Windows Server

Jeśli chcesz zainstalować lub ponownie zainstalować pakiet Program antywirusowy Microsoft Defender w programie Windows Server, możesz to zrobić za pomocą Kreatora dodawania ról i **funkcji lub programu** PowerShell.

### <a name="use-the-add-roles-and-features-wizard-to-install-microsoft-defender-antivirus"></a>Instalowanie nowych użytkowników za pomocą Kreatora dodawania ról i funkcji Program antywirusowy Microsoft Defender

1. Zapoznaj się [z tym artykułem](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) i użyj **Kreatora dodawania ról i funkcji**.

2. Po **dojechu** do kroku Funkcje kreatora wybierz Program antywirusowy Microsoft Defender kreatora. Wybierz też opcję **graficznego interfejsu użytkownika Windows Defender** interfejsu użytkownika.

### <a name="use-powershell-to-install-microsoft-defender-antivirus"></a>Instalowanie programu PowerShell Program antywirusowy Microsoft Defender

Aby zainstalować Program antywirusowy Microsoft Defender programu PowerShell, uruchom następujące polecenie cmdlet:

```powershell
Install-WindowsFeature -Name Windows-Defender
```

Komunikaty o zdarzeniach aparatu ochrony przed złośliwym oprogramowaniem dołączonego Program antywirusowy Microsoft Defender można znaleźć w Program antywirusowy Microsoft Defender [Zdarzenia](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Sprawdzanie Program antywirusowy Microsoft Defender czy jest uruchomiony

Po Program antywirusowy Microsoft Defender instalacji następnym krokiem jest sprawdzenie, czy jest uruchomiony. Na punkcie Windows serwera uruchom następujące polecenie cmdlet programu PowerShell:

```powershell
Get-Service -Name windefend
```

Aby sprawdzić, czy ochrona zapory jest włączona, uruchom następujące polecenie cmdlet programu PowerShell:

```powershell
Get-Service -Name mpssvc
```

Jako alternatywy dla programu PowerShell możesz użyć wiersza polecenia, aby sprawdzić, Program antywirusowy Microsoft Defender działa. W tym celu uruchom następujące polecenie z wiersza polecenia:

```console
sc query Windefend
```

Polecenie `sc query` zwraca informacje o Program antywirusowy Microsoft Defender sieci. Gdy Program antywirusowy Microsoft Defender uruchomiony, jest wyświetlana `STATE` wartość `RUNNING`.

Aby wyświetlić wszystkie usługi, które nie są uruchomione, uruchom następujące polecenie cmdlet programu PowerShell:

```console
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>Aktualizacja analizy zabezpieczeń przed złośliwym kodem

Aby uzyskać zaktualizowaną analizę zabezpieczeń przed złośliwym kodem, musisz mieć Windows uruchomiona usługa aktualizacji oprogramowania. Jeśli korzystasz z usługi zarządzania aktualizacjami, na przykład programu Windows Server Update Services (WSUS), upewnij się, że aktualizacje dla programu Program antywirusowy Microsoft Defender Funkcje analizy zabezpieczeń są zatwierdzone dla komputerów, których zarządzasz.

Domyślnie aktualizacja Windows nie pobiera i nie instaluje aktualizacji automatycznie na serwerze Windows Server 2019 lub Windows Server 2022 lub Windows Server 2016. Tę konfigurację można zmienić przy użyciu jednej z następujących metod:

<br/><br/>

| Metoda | Opis |
|---|---|
| **Windows w** Panelu sterowania | **Zainstalowanie aktualizacji powoduje automatyczne** zainstalowanie wszystkich aktualizacji, w tym aktualizacji analizy Windows Defender zabezpieczeń. <br/><br/> **Pobieraj aktualizacje, ale zdecyduję**, czy je zainstalować, Windows Defender automatyczne pobieranie i instalowanie aktualizacji analizy zabezpieczeń, ale inne aktualizacje nie są instalowane automatycznie. |
| **zasady grupy** | Aktualizację usługi Windows i zarządzanie nimi można skonfigurować przy użyciu ustawień dostępnych w programie zasady grupy w następującej ścieżce: Szablony administracyjne **\Windows Składniki\Windows Update\Konfigurowanie** aktualizacji automatycznych |
| Klucz rejestru **AUOptions** | Dwie poniższe wartości umożliwiają automatyczne Windows aktualizacji zabezpieczeń w celu automatycznego pobierania i instalowania aktualizacji analizy zabezpieczeń: <br/><br/> **4** -  **Automatyczne instalowanie aktualizacji**. Ta wartość powoduje, że wszystkie aktualizacje są instalowane automatycznie, w tym aktualizacje Windows Defender aktualizacje analizy zabezpieczeń. <br/><br/> **3** -  **Pobieraj aktualizacje, ale pozwól mi wybrać, czy chcesz je zainstalować**. Ta wartość umożliwia Windows Defender automatyczne pobieranie i instalowanie aktualizacji analizy zabezpieczeń, ale inne aktualizacje nie są instalowane automatycznie. |

Aby zapewnić ochronę przed złośliwym oprogramowaniem, zalecamy włączenie następujących usług:

- Raportowanie błędów systemu Windows usługi
- Windows usługi aktualizacji

W poniższej tabeli wymieniono usługi dla Program antywirusowy Microsoft Defender i usługi zależne.

<br/><br/>


| Nazwa usługi | Lokalizacja pliku | Opis |
|---|---|---|
| Windows Defender (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Jest to główna Program antywirusowy Microsoft Defender, która musi być uruchomiona przez cały czas.|
| Raportowanie błędów systemu Windows (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Ta usługa wysyła raporty o błędach z powrotem do firmy Microsoft. |
| Windows Defender MpsSvc | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Zalecamy pozostawienie włączonej Windows Defender Zapory sieciowej. |
| Windows (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows aktualizacja jest potrzebna do uzyskania aktualizacji analizy zabezpieczeń i aktualizacji aparatu ochrony przed złośliwym kodem |

## <a name="submit-samples"></a>Prześlij próbki

Przykładowe przesyłanie umożliwia firmie Microsoft zbieranie próbek potencjalnie złośliwego oprogramowania. Aby zapewnić trwałą i na bieżąco ochronę, firma Microsoft używa tych próbek do analizowania podejrzanych działań i tworzenia zaktualizowanych analizy zabezpieczeń przed złośliwym kodem. Gromadzimy pliki wykonywalne programu, takie jak pliki .exe i .dll pliki. Nie gromadzimy plików zawierających dane osobowe, takich jak pliki Microsoft Word pdf.

### <a name="submit-a-file"></a>Przesyłanie pliku

1. Przejrzyj przewodnik [przesyłania](/windows/security/threat-protection/intelligence/submission-guide).
2. Odwiedź [przykładowy portal przesyłania](https://www.microsoft.com/wdsi/filesubmission) i prześlij plik.

### <a name="enable-automatic-sample-submission"></a>Włączanie automatycznego przesyłania próbek

Aby włączyć automatyczne przesyłanie próbek, uruchom konsolę Windows PowerShell jako administrator i ustaw dane wartości **SubmitSamplesConsent** zgodnie z jednym z następujących ustawień:

<br/><br/>

|Ustawienie|Opis|
|---|---|
| **0** -  **Zawsze monituj** | Usługa Program antywirusowy Microsoft Defender wyświetli monit o potwierdzenie przesłania wszystkich wymaganych plików. Jest to domyślne ustawienie dla programu Program antywirusowy Microsoft Defender, ale nie jest zalecane w przypadku instalacji w programie Windows Server 2016, 2019 lub Windows Server 2022 bez graficznego interfejsu użytkownika. |
| **1**  -  **Automatyczne wysyłanie bezpiecznych próbek** | Usługa Program antywirusowy Microsoft Defender wysyła wszystkie pliki oznaczone jako "bezpieczne" i wyświetla monit o pozostałe pliki. |
| **2** -  **Nigdy nie wysyłaj** | Usługa Program antywirusowy Microsoft Defender nie wyświetla monitu i nie wysyła żadnych plików. |
| **3** -  **Automatyczne wysyłanie wszystkich próbek** | Usługa Program antywirusowy Microsoft Defender wysyła wszystkie pliki bez monitu o potwierdzenie. |

> [!NOTE]
> Ta opcja nie jest dostępna w przypadku Windows Server 2012 R2. 


## <a name="configure-automatic-exclusions"></a>Konfigurowanie wykluczeń automatycznych

W celu zapewnienia bezpieczeństwa i wydajności niektóre wykluczenia są dodawane automatycznie na podstawie ról i funkcji instalowanych podczas korzystania z programu Program antywirusowy Microsoft Defender w systemie Windows Server 2016 lub 2019 albo Windows Server 2022.

Zobacz [Konfigurowanie wykluczeń w Program antywirusowy Microsoft Defender na Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md).

## <a name="passive-mode-and-windows-server"></a>Tryb pasywny i Windows serwera

Jeśli używasz produktu antywirusowego innego niż firmy Microsoft jako podstawowego rozwiązania antywirusowego w programie Windows Server, musisz ustawić tryb Program antywirusowy Microsoft Defender pasywny lub wyłączony.

Aby uzyskać więcej informacji, zobacz [Instalowanie Program antywirusowy Microsoft Defender na Windows Server](microsoft-defender-antivirus-on-windows-server.md#install-microsoft-defender-antivirus-on-windows-server).


### <a name="set-microsoft-defender-antivirus-to-passive-mode-using-a-registry-key"></a>Ustawianie Program antywirusowy Microsoft Defender do trybu pasywnego przy użyciu klucza rejestru

Można ustawić tryb Program antywirusowy Microsoft Defender pasywnego, ustawiając następujący klucz rejestru:
- Ścieżka: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Nazwa: `ForceDefenderPassiveMode`
- Typ: `REG_DWORD`
- Wartość: `1`

### <a name="disable-microsoft-defender-antivirus-using-the-remove-roles-and-features-wizard"></a>Wyłączanie Program antywirusowy Microsoft Defender przy użyciu kreatora Usuwanie ról i funkcji

1. Zobacz [Instalowanie lub odinstalowywanie ról, usług ról lub funkcji](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard) i korzystanie z Kreatora **usuwania ról i funkcji**.

2. Po **dojechu** do kroku Funkcje kreatora wyczyść opcję Windows Defender **Funkcje**.

    Jeśli wyczyścisz **Windows Defender** w sekcji Funkcje Windows Defender, zostanie wyświetlony  monit o usunięcie graficznego interfejsu użytkownika dla **Windows Defender**.

    Program antywirusowy Microsoft Defender działać normalnie bez interfejsu użytkownika, ale nie można włączyć interfejsu użytkownika, jeśli wyłączysz podstawową **Windows Defender** interfejsu.

### <a name="turn-off-the-microsoft-defender-antivirus-user-interface-using-powershell"></a>Wyłączanie interfejsu Program antywirusowy Microsoft Defender przy użyciu programu PowerShell

Aby wyłączyć graficzne Program antywirusowy Microsoft Defender użytkownika, użyj następującego polecenia cmdlet programu PowerShell:

```powershell
Uninstall-WindowsFeature -Name Windows-Defender-GUI
```

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Używasz programu Windows Server 2012 R2 lub Windows Server 2016?

Teraz można uruchamiać Program antywirusowy Microsoft Defender w trybie pasywnym na Windows Server 2012 R2 i Windows Server 2016. Aby uzyskać więcej informacji, [zobacz Opcje instalowania programu Microsoft Defender dla punktu końcowego](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

<br/><br/>

| Procedura | Opis |
|---|---|
| Wyłączanie Program antywirusowy Microsoft Defender przy użyciu zasady grupy | W Edytorze zasady grupy lokalnym  >  przejdź do szablonu administracyjnego **Windows składnik** >  **Endpoint Protection** >  **Wyzysłane Endpoint Protection**, a następnie wybierz **pozycję EnabledOK** > . |
| Wyłączanie Program antywirusowy Microsoft Defender przy użyciu klucza rejestru | Aby użyć klucza rejestru [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) , `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`przejdź do pozycji , a następnie ustaw lub utwórz wpis DWORD o nazwie `DisableAntiSpyware`. Ustaw wartość tego `1` klucza na (co oznacza wartość klucza *rejestru na prawda*). |
| Wyłączanie Program antywirusowy Microsoft Defender przy użyciu programu PowerShell | Użyj następującego polecenia cmdlet programu PowerShell: `Set-MpPreference -DisableRealtimeMonitoring $true` |
| Odinstalowywanie Program antywirusowy Microsoft Defender przy użyciu programu PowerShell | Użyj następującego polecenia cmdlet programu PowerShell: `Uninstall-WindowsFeature -Name Windows-Defender` |


## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender w programie Windows](microsoft-defender-antivirus-windows.md)
- [Program antywirusowy Microsoft Defender zgodności](microsoft-defender-antivirus-compatibility.md)