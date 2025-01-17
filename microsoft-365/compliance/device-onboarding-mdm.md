---
title: Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu narzędzi do zarządzania urządzeniami przenośnymi
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Użyj narzędzi Zarządzanie urządzeniami mobilnych, aby wdrożyć pakiet konfiguracji na urządzeniach, aby zostały one wdrożone w usłudze.
ms.openlocfilehash: 9b329ccf86a2364c13ac72bd4348711d72c17ff5
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634498"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-mobile-device-management-tools"></a>Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu narzędzi do zarządzania urządzeniami przenośnymi

**Dotyczy:**

- [Microsoft 365 punktu końcowego ochrony przed utratą danych (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

Urządzenia można konfigurować za pomocą rozwiązań zarządzania urządzeniami przenośnymi (MDM). Microsoft 365 informacji obsługuje usługi MDM, udostępniając OMA-URIs tworzenia zasad do zarządzania urządzeniami.


## <a name="before-you-begin"></a>Przed rozpoczęciem
Jeśli korzystasz z usługi Microsoft Intune, musisz mieć zarejestrowane mdm urządzenia. W przeciwnym razie ustawienia nie zostaną zastosowane pomyślnie. 

Aby uzyskać więcej informacji na temat włączania usługi MDM Microsoft Intune, zobacz [Rejestracja urządzenia (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Urządzenia w urządzeniach w urządzeniu Microsoft Intune

Postępuj zgodnie z instrukcjami [podanymi Intune](/mem/intune/protect/advanced-threat-protection-configure).
 
> [!NOTE]
> - W **zasadach Stan kondycji urządzeń wewnenych** używane są właściwości tylko do odczytu, których nie można rozwiązać.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Urządzenia wyełowywne i monitorują je przy Zarządzanie urządzeniami urządzeniach przenośnych

Ze względów bezpieczeństwa pakiet używany na urządzeniach offboardowych wygaśnie po 30 dniach od daty jego pobrania. Pakiety wynoszące wygasłe wysłane na urządzenie zostaną odrzucone. Podczas pobierania pakietu wynegocjowego zostaniesz o nim powiadomiony(-a) o dacie wygaśnięcia pakietów, a także w nazwie pakietu.

> [!NOTE]
> Zasad wnoszeń i wynoszeń nie można wdrażać jednocześnie na tym samym urządzeniu, w przeciwnym razie spowoduje to nieprzewidywalne błędy.

1. Pobierz pakiet wywęszania z <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a>.

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Device onboardingOffboarding** > .

3. W polu **Metoda wdrażania** wybierz pozycję **Zarządzanie urządzeniami / Microsoft Intune**.

4. Kliknij **pozycję Pobierz** pakiet i zapisz .zip pliku.

5. Wyodrębnianie zawartości pliku .zip do udostępnionej lokalizacji tylko do odczytu, do której dostęp mogą uzyskać administratorzy sieci, którzy wdrożyą pakiet. Plik powinien mieć nazwę *: DeviceCompliance_valid_until_YYYY-MM-DD.offboarding*.

6. Skorzystaj z Microsoft Intune konfiguracji niestandardowej, aby wdrożyć następujące obsługiwane ustawienia OMA-URI.

    ```text
    OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
    Date type: String
    Value: [Copy and paste the value from the content of the DeviceCompliance_valid_until_YYYY-MM-DD.offboarding file]
    ```
> [!NOTE]
> Jeśli Ochrona punktu końcowego w usłudze Microsoft Defender jest już skonfigurowany, możesz włączyć dołączanie urządzenia  i krok 6 nie jest już wymagany.

> [!NOTE]
> W **zasadach Stan kondycji urządzeń wynoszonych** używane są właściwości tylko do odczytu, których nie można rozwiązać.

> [!IMPORTANT]
> Wynoszenie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołania do wszelkich posiadanych alertów, będą przechowywane przez maksymalnie 6 miesięcy.

## <a name="related-topics"></a>Tematy pokrewne
- [Na urządzeniach Windows 10 przy użyciu aplikacji zasady grupy](device-onboarding-gp.md)
- [Urządzenia Windows 10 przy użyciu Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Dołączanie Windows 10 przy użyciu skryptu lokalnego](device-onboarding-script.md)
- [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)](device-onboarding-vdi.md)
- [Rozwiązywanie problemów z dołączaniem do zaawansowanej ochrony przed zagrożeniami w u programie Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
