---
title: Optymalizowanie wdrażania reguł asr i wykrywanie
description: Zoptymalistruj reguły ograniczania powierzchni ataków, aby zidentyfikować typowe luki w złośliwym oprogramowaniu i zapobiegać ich wykorzystywaniu.
keywords: onboard, zarządzanie usługą Intune, program Microsoft Defender dla punktu końcowego, program Microsoft Defender, Windows Defender, zmniejszenie obszarów ataków, asr, plan bazowy zabezpieczeń
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: bd5b88c5d43f2ec20c200ee55458e2ef204775ae
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997796"
---
# <a name="optimize-asr-rule-deployment-and-detections"></a>Optymalizowanie wdrażania reguł asr i wykrywanie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

[Reguły zmniejszania powierzchni ataków (ASR, Attack Surface Reduction)](./attack-surface-reduction.md) identyfikują typowe luki w złośliwym oprogramowaniu i zapobiegają im. Kontrolują one czas i sposób uruchamiania potencjalnie złośliwego kodu. Mogą one na przykład zapobiegać uruchamianiu pobranego pliku wykonywalnego przez język JavaScript lub VBScript, blokować połączenia interfejsu API Win32 z makr programu Office oraz blokować procesy uruchamiane z dysków USB.


:::image type="content" source="../../media/attack-surface-mgmt.png" alt-text="Karta zarządzania powierzchnią ataków.":::
<br>
*Karta zarządzania powierzchnią ataków*

Karta *Zarządzanie powierzchnią ataków* to punkt wejścia do narzędzi w Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">narzędzi</a>, których można używać do:

* Zrozumienie sposobu wdrażania reguł asr w organizacji.
* Przejrzyj wykrywanie asr i zidentyfikuj możliwe niepoprawne wykrywanie.
* Analizowanie wpływu wykluczeń i generowanie listy ścieżek plików do wykluczenia.

Wybierz **pozycję Przejdź do zarządzania powierzchnią ataków** **Raporty** \> \> **Reguły ograniczania powierzchni ataków** \> **Dodaj wykluczenia**. W tym miejscu możesz przejść do innych sekcji Microsoft 365 Defender portalu.

![Dodaj kartę wykluczeń na stronie Reguły ograniczania powierzchni ataków w Microsoft 365 Defender sieci Web.](images/secconmgmt_asr_m365exlusions.png)<br>
Karta ***Dodawanie wykluczeń** na stronie Zasad ograniczania powierzchni ataków w Microsoft 365 Defender sieci Web*

> [!NOTE]
> Aby uzyskać Microsoft 365 Defender portalu, potrzebujesz licencji Microsoft 365 E3 lub E5 oraz konta, które ma pewne role na Azure Active Directory. [Przeczytaj o wymaganych licencjach i uprawnieniach](/office365/securitycompliance/microsoft-security-and-compliance#required-licenses-and-permissions).

Aby uzyskać więcej informacji na temat wdrażania reguł ASR <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalu</a>, zobacz Monitorowanie wdrażania reguł [ASR](/office365/securitycompliance/monitor-devices#monitor-and-manage-asr-rule-deployment-and-detections) i wykrywanie oraz zarządzanie nimi.

**Tematy pokrewne**

* [Upewnij się, że urządzenia są poprawnie skonfigurowane](configure-machines.md)
* [Uzyskiwanie urządzeń podłączonych do programu Microsoft Defender dla punktu końcowego](configure-machines-onboarding.md)
* [Monitorowanie zgodności z planem bazowym zabezpieczeń programu Microsoft Defender for Endpoint](configure-machines-security-baseline.md)