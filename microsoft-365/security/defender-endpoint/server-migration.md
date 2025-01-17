---
title: Scenariusze migracji serwera dla nowej wersji Ochrona punktu końcowego w usłudze Microsoft Defender
description: Przeczytaj ten artykuł, aby zapoznać się z omówieniem sposobu migracji serwerów z poprzedniego rozwiązania mma do bieżącego pakietu rozwiązania ujednoliconego usługi Defender for Endpoint.
keywords: migrowanie serwera, serwera, 2012r2, 2016, migracja serwera, zarządzanie urządzeniami, konfigurowanie serwerów Ochrona punktu końcowego w usłudze Microsoft Defender, dołączanie serwerów Ochrona punktu końcowego w usłudze Microsoft Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: ed31a629f6cde18af03c3c6102b821cb6a04dd96
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782682"
---
# <a name="server-migration-scenarios-from-the-previous-mma-based-microsoft-defender-for-endpoint-solution"></a>Scenariusze migracji serwera z poprzedniego rozwiązania Ochrona punktu końcowego w usłudze Microsoft Defender opartego na programie MMA

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- Windows Server 2012 R2
- System Windows Server 2016
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 

[!include[Prerelease information](../../includes/prerelease.md)]

> [!NOTE]
> Przed kontynuowaniem instalacji lub uaktualnienia zawsze upewnij się, że system operacyjny i Program antywirusowy Microsoft Defender na Windows Server 2016 są w pełni zaktualizowane. Aby otrzymywać regularne ulepszenia i poprawki produktu dla składnika czujnika EDR, upewnij się, Windows Update [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) zostanie zastosowana lub zatwierdzona po instalacji. Ponadto, aby aktualizować składniki ochrony, zapoznaj się z [tematem Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie punktów odniesienia](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

Te instrukcje dotyczą nowego pakietu ujednoliconego rozwiązania i instalatora (MSI) Ochrona punktu końcowego w usłudze Microsoft Defender dla Windows Server 2012 R2 i Windows Server 2016. Ten artykuł zawiera ogólne instrukcje dotyczące różnych możliwych scenariuszy migracji z poprzedniego do bieżącego rozwiązania. Te kroki wysokiego poziomu są przeznaczone jako wytyczne, które mają zostać dostosowane do narzędzi wdrażania i konfiguracji dostępnych w danym środowisku.

> [!NOTE]
> Uaktualnienia systemu operacyjnego z zainstalowanymi Ochrona punktu końcowego w usłudze Microsoft Defender nie są obsługiwane. Odinstaluj go przed kontynuowaniem uaktualnienia.

> [!NOTE]
> Pełna automatyzacja Microsoft Endpoint Configuration Manager i integracja w celu przeprowadzenia automatycznego uaktualnienia będą dostępne w nowszej wersji programu MECM. W wersji 2107 z najnowszym pakietem zbiorczym poprawek możesz użyć węzła Endpoint Protection na potrzeby konfiguracji, a także zasady grupy, programu PowerShell, Microsoft Endpoint Manager dołączania dzierżawy lub konfiguracji lokalnej. Ponadto możesz skorzystać z istniejących funkcji w Microsoft Endpoint Configuration Manager, aby zautomatyzować kroki uaktualniania ręcznego— metody opisane poniżej.


## <a name="installer-script"></a>Skrypt instalatora

Aby ułatwić uaktualnianie, gdy Microsoft Endpoint Configuration Manager lub Microsoft Defender dla Chmury nie są używane lub nie są jeszcze dostępne do przeprowadzenia uaktualnienia, możesz użyć tego [skryptu uaktualnienia](https://github.com/microsoft/mdefordownlevelserver). Może pomóc w zautomatyzowaniu następujących wymaganych kroków:

1. Usuń obszar roboczy pakietu OMS dla Ochrona punktu końcowego w usłudze Microsoft Defender (OPCJONALNIE).
2. Usuń klienta System Center Endpoint Protection (SCEP), jeśli jest zainstalowany.
3. W razie potrzeby pobierz i zainstaluj wymagania [wstępne](configure-server-endpoints.md#prerequisites) (Windows Server 2012 R2).
4. Zainstaluj Ochrona punktu końcowego w usłudze Microsoft Defender.
5. Zastosuj skrypt dołączania **do użycia z zasady grupy** pobranym z [Microsoft 365 Defender](https://security.microsoft.com).

Aby użyć skryptu, pobierz go do katalogu instalacyjnego, w którym również umieszczono pakiety instalacyjne i dołączane (zobacz [Konfigurowanie punktów końcowych serwera](configure-server-endpoints.md).

PRZYKŁAD: .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd"

## <a name="microsoft-endpoint-configuration-manager-migration-scenarios"></a>scenariusze migracji Microsoft Endpoint Configuration Manager 

>[!NOTE]
>Musisz Microsoft Endpoint Configuration Manager w wersji 2107 lub nowszej.

Kroki migracji: 

1. W pełni zaktualizuj maszynę, w tym Program antywirusowy Microsoft Defender (Windows Server 2016).
2. Utwórz nową kolekcję z regułami członkostwa, aby uwzględnić maszyny do migracji.
3. [Utwórz aplikację do](/mem/configmgr/apps/deploy-use/create-applications) wykonywania następujących zadań: 
   1. Odinstaluj protokół SCEP.
   2. W razie potrzeby zainstaluj [wymagania wstępne](configure-server-endpoints.md#prerequisites) .
   3. Zainstaluj Ochrona punktu końcowego w usłudze Microsoft Defender (zobacz [Konfigurowanie punktów końcowych serwera](configure-server-endpoints.md).
   4. Zastosuj skrypt dołączania **do użycia z zasady grupy** pobranym z [Microsoft 365 Defender](https://security.microsoft.com). 
   > [!TIP]
   > Aby zautomatyzować powyższe kroki, możesz użyć [skryptu instalatora](server-migration.md#installer-script) w ramach aplikacji.
4. Wdróż aplikację w nowej kolekcji.
5. Utwórz i/lub przypisz (istniejące) zasady Endpoint Protection do kolekcji.
6. Zastosuj aktualizacje.

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-are-running-a-non-microsoft-antivirus-solution-and-the-mma-based-sensor-you-want-to-upgrade-to-the-new-microsoft-defender-for-endpoint"></a>Obecnie używasz Microsoft Endpoint Configuration Manager do zarządzania serwerami, korzystasz z rozwiązania antywirusowego innego niż Microsoft i czujnika mma. Chcesz przeprowadzić uaktualnienie do nowej Ochrona punktu końcowego w usłudze Microsoft Defender.

Kroki migracji:

1. W pełni zaktualizuj maszynę, w tym Program antywirusowy Microsoft Defender (Windows Server 2016).
2. Utwórz nową kolekcję z regułami członkostwa, aby uwzględnić maszyny do migracji. 
3. Upewnij się, że zarządzanie programami antywirusowymi innych firm nie wypycha już oprogramowania antywirusowego do tych maszyn.*
4. Tworzyć zasady w węźle Endpoint Protection mecm i kierować je do nowo utworzonej kolekcji.*
5. Utwórz aplikację do wykonywania następujących zadań:
   1. Usuń konfigurację obszaru roboczego programu MMA dla Ochrona punktu końcowego w usłudze Microsoft Defender. Zobacz [Usuwanie obszaru roboczego przy użyciu programu PowerShell](/azure/azure-monitor/agents/agent-manage). Ten krok jest opcjonalny; poprzedni czujnik EDR przestanie działać po uaktywnieniu nowszego.
   2. W razie potrzeby zainstaluj [wymagania wstępne](configure-server-endpoints.md#prerequisites) .
   3. Zainstaluj Ochrona punktu końcowego w usłudze Microsoft Defender dla pakietu Windows Server 2012 R2 i 2016 i **włącz tryb pasywny**. Zobacz [Instalowanie Program antywirusowy Microsoft Defender przy użyciu wiersza polecenia](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
   4. Zastosuj skrypt dołączania **do użycia z zasady grupy** pobranym z [Microsoft 365 Defender](https://security.microsoft.com).
6. Zastosuj aktualizacje.
7. Usuń oprogramowanie antywirusowe spoza firmy Microsoft przy użyciu konsoli antywirusowej innej niż Microsoft lub odpowiednio Microsoft Endpoint Configuration Manager. Pamiętaj, aby usunąć konfigurację trybu pasywnego.*

> [!TIP]
> Aby zautomatyzować powyższe kroki, możesz użyć [skryptu instalatora](server-migration.md#installer script) jako części aplikacji. Aby włączyć tryb pasywny, zastosuj flagę -Passive. Na przykład .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive

*Te kroki mają zastosowanie tylko wtedy, gdy zamierzasz zastąpić rozwiązanie antywirusowe inne niż Microsoft. Zobacz [Razem Lepiej: Program antywirusowy Microsoft Defender i Ochrona punktu końcowego w usłudze Microsoft Defender](why-use-microsoft-defender-antivirus.md).

Aby przenieść maszynę z trybu pasywnego, ustaw następujący klucz na 0:

Ścieżka: HKLM\SOFTWARE\Policies\Microsoft\Windows Nazwa zaawansowanej ochrony przed zagrożeniami: ForceDefenderPassiveMode Typ: REG_DWORD wartość: 0


## <a name="other-migration-scenarios"></a>Inne scenariusze migracji

### <a name="you-have-a-server-that-has-been-onboarded-using-the-mma-based-microsoft-defender-for-endpoint-it-has-scep-installed-windows-server-2012-r2-or-microsoft-defender-antivirus-windows-server-2016-this-machine-is-not-managed-through-microsoft-defender-for-cloud-microsoft-endpoint-manager-or-microsoft-endpoint-configuration-manager"></a>Masz serwer, który został dołączony przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender mma. Zainstalowano protokół SCEP (Windows Server 2012 R2) lub Program antywirusowy Microsoft Defender (Windows Server 2016). Ta maszyna **nie** jest zarządzana za pośrednictwem Microsoft Defender dla Chmury, Microsoft Endpoint Manager lub Microsoft Endpoint Configuration Manager.

1. W pełni zaktualizuj maszynę, w tym Program antywirusowy Microsoft Defender (Windows Server 2016).
2. Usuń konfigurację obszaru roboczego programu MMA dla Ochrona punktu końcowego w usłudze Microsoft Defender. Zobacz [Usuwanie obszaru roboczego przy użyciu programu PowerShell](/azure/azure-monitor/agents/agent-manage).
3. Odinstaluj System Center Endpoint Protection (Windows Server 2012 R2).
4. W razie potrzeby zainstaluj [wymagania wstępne](configure-server-endpoints.md#prerequisites) . 
5. Zainstaluj Ochrona punktu końcowego w usłudze Microsoft Defender (zobacz [Konfigurowanie punktów końcowych serwera](configure-server-endpoints.md)).
6. Zastosuj skrypt dołączania **do użycia z zasady grupy** pobranym z [Microsoft 365 Defender](https://security.microsoft.com). 
7. Zastosuj aktualizacje.
8. Tworzenie i stosowanie zasad przy użyciu zasady grupy, programu PowerShell lub rozwiązania do zarządzania innej firmy.

> [!TIP]
> Aby zautomatyzować powyższe kroki, możesz użyć skryptu instalatora.

### <a name="you-have-a-server-on-which-you-want-to-install-microsoft-defender-for-endpoint-it-has-a-non-microsoft-endpoint-protection-or-endpoint-detection-and-response-solution-installed-you-do-not-intend-to-use-microsoft-endpoint-configuration-manager-or-microsoft-defender-for-cloud-you-use-your-own-deployment-mechanism"></a>Masz serwer, na którym chcesz zainstalować Ochrona punktu końcowego w usłudze Microsoft Defender. Ma zainstalowaną ochronę punktu końcowego lub rozwiązanie wykrywanie i reagowanie w punktach końcowych firmy Microsoft. Nie zamierzasz używać Microsoft Endpoint Configuration Manager ani Microsoft Defender dla Chmury. Używasz własnego mechanizmu wdrażania. 

1. W pełni zaktualizuj maszynę, w tym Program antywirusowy Microsoft Defender (Windows Server 2016).
2. Zainstaluj Ochrona punktu końcowego w usłudze Microsoft Defender dla pakietu Windows Server 2012 R2 & 2016 i **włącz tryb pasywny**. Zobacz [Instalowanie Program antywirusowy Microsoft Defender przy użyciu wiersza polecenia](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
3. Zastosuj skrypt dołączania, odpowiedni dla środowiska, pobrany z [Microsoft 365 Defender](https://security.microsoft.com). 
4. Usuń rozwiązanie wykrywanie i reagowanie w punktach końcowych lub ochrony punktów końcowych innych niż Microsoft i usuń tryb pasywny.*
5. Zastosuj aktualizacje.
6. Tworzenie i stosowanie zasad przy użyciu zasady grupy, programu PowerShell lub rozwiązania do zarządzania innej firmy.

> [!TIP]
> Skrypt [instalatora](server-migration.md#installer-script) ułatwia automatyzację kroków od 1 do 4. Aby włączyć tryb pasywny, zastosuj flagę -Passive, która gwarantuje, że program antywirusowy Defender przejdzie w tryb pasywny przed dołączeniem i nie zakłóca działania rozwiązania chroniącego przed złośliwym kodem innych firm. Następnie, aby upewnić się, że program antywirusowy Defender pozostaje w trybie pasywnym po dołączeniu do obsługi funkcji EDR, takich jak EDR Block, upewnij się, że ustawiono klucz rejestru "ForceDefenderPassiveMode". PRZYKŁAD: `.\install.ps1 -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive`


*Ten krok ma zastosowanie tylko wtedy, gdy zamierzasz zastąpić rozwiązanie antywirusowe inne niż Microsoft. Zalecamy używanie Program antywirusowy Microsoft Defender, dołączonego do Ochrona punktu końcowego w usłudze Microsoft Defender, w celu zapewnienia pełnego zestawu możliwości. Zobacz [Razem Lepiej: Program antywirusowy Microsoft Defender i Ochrona punktu końcowego w usłudze Microsoft Defender](why-use-microsoft-defender-antivirus.md).

Aby przenieść maszynę z trybu pasywnego, ustaw następujący klucz na 0:

Ścieżka: HKLM\SOFTWARE\Policies\Microsoft\Windows Nazwa zaawansowanej ochrony przed zagrożeniami: ForceDefenderPassiveMode Typ: REG_DWORD wartość: 0


## <a name="microsoft-defender-for-cloud-scenarios"></a>scenariusze Microsoft Defender dla Chmury

### <a name="youre-using-microsoft-defender-for-cloud-the-microsoft-monitoring-agent-mma-andor-microsoft-antimalware-for-azure-scep-are-installed-and-you-want-to-upgrade"></a>Używasz Microsoft Defender dla Chmury. Zainstalowano Microsoft Monitoring Agent (MMA) i/lub Microsoft Antimalware dla platformy Azure (SCEP) i chcesz przeprowadzić uaktualnienie.
Jeśli używasz Microsoft Defender dla Chmury, możesz skorzystać z zautomatyzowanego procesu uaktualniania. Zobacz [Ochrona punktów końcowych za pomocą zintegrowanego rozwiązania EDR Defender dla Chmury: Ochrona punktu końcowego w usłudze Microsoft Defender](/azure/security-center/security-center-wdatp#enable-the-microsoft-defender-for-endpoint-integration).

## <a name="group-policy-configuration"></a>konfiguracja zasady grupy
W przypadku konfiguracji przy użyciu zasady grupy upewnij się, że używasz najnowszych plików ADMX w magazynie centralnym, aby uzyskać dostęp do prawidłowych opcji zasad usługi Defender for Endpoint. Zapoznaj się z artykułem [How to create the Central Store for zasady grupy Administrative Templates in Windows and download the latest files for use with Windows 10 (Jak utworzyć magazyn centralny dla szablonów administracyjnych zasady grupy i zarządzać nimi w Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) i pobrać najnowsze pliki **do użycia z Windows 10**.
