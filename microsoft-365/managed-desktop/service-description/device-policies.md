---
title: Konfiguracja urządzenia
description: Dowiedz się więcej o domyślnych zasadach stosowanych do Microsoft Managed Desktop urządzeniach.
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 9b770fd7abb8c569d115891824c264f4d32dd20e
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2022
ms.locfileid: "63026819"
---
# <a name="device-configuration"></a>Konfiguracja urządzenia


<!--This topic is the target for a "Learn more" link in the Enterprise Agreement (aka.ms/dev-config); do not delete.-->

<!-- Device configuration and Security Addendum-->

Gdy jest konfigurowane Microsoft Managed Desktop nowe urządzenie, zapewniamy, że ma ono odpowiednią konfigurację zoptymalizowaną pod kątem Microsoft Managed Desktop. Ta konfiguracja zawiera zestaw domyślnych zasad ustawionych w ramach procesu dołączania. Te zasady są dostarczane przy użyciu funkcji Zarządzanie urządzeniami przenośnymi,gdy tylko jest to możliwe. Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi](/windows/client-management/mdm/). 

>[!NOTE]
>Aby uniknąć konfliktów, nie zmieniaj tych zasad.

Urządzenia będą przychodzić z obrazem podpisu, a następnie dołączać Azure Active Directory domeny po pierwszym użytkowniku. Urządzenie automatycznie zainstaluje wymagane zasady i aplikacje bez interwencji pracowników IT.

## <a name="default-policies"></a>Zasady domyślne

W poniższej tabeli wyróżniliśmy domyślne zasady, które są stosowane do wszystkich Microsoft Managed Desktop podczas inicjowania obsługi administracyjnej urządzeń. Wszystkie wykryte zmiany, które nie zostały Microsoft Managed Desktop przez zespół operacyjny, do obiektów zarządzanych przez Microsoft Managed Desktop zostaną przywrócone.

Zasady | Opis
--- | ---
Plan bazowy zabezpieczeń | [Plan bazowy zabezpieczeń firmy Microsoft](/windows/device-security/windows-security-baselines) dla usługi MDM jest skonfigurowany dla wszystkich Microsoft Managed Desktop urządzeniach. Ten plan bazowy jest konfiguracją standardową w branży. Jest ona publicznie opublikowana, dobrze przetestowana i została przejmowana przez ekspertów do spraw zabezpieczeń firmy Microsoft w celu zabezpieczenia Microsoft Managed Desktop urządzeniach i aplikacjach w nowoczesnym miejscu pracy. <br><br>Aby zminimalizować zagrożenia w stale rozwijającym się środowisku zagrożeń bezpieczeństwa, plan bazowy zabezpieczeń firmy Microsoft zostanie zaktualizowany i wdrożony na wszystkich Microsoft Managed Desktop w poszczególnych aktualizacjach funkcji Windows 10 zabezpieczeń.<br><br>Aby uzyskać więcej informacji, [zobacz Windows planu bazowego zabezpieczeń](/windows/security/threat-protection/windows-security-baselines).
Microsoft Managed Desktop zalecany szablon zabezpieczeń | Zestaw zalecanych zmian w planie bazowym zabezpieczeń, które optymalizują środowisko użytkownika.  Te zmiany są udokumentowane w [addendum zabezpieczeń](#security-addendum). Aktualizacje dodatku zasad są dostępne w zależności od potrzeb.  
Aktualizowanie wdrożenia | Użyj Windows Update dla firm, aby przeprowadzić stopniowe wdrażanie aktualizacji oprogramowania. Administratorzy IT nie mogą modyfikować ustawień zasad grupy wdrażania. Aby uzyskać więcej informacji na temat wdrażania opartego na grupach, zobacz [Jak są obsługiwane aktualizacje w programie Microsoft Managed Desktop](updates.md).
Połączenia taryfowe | Domyślnie aktualizacje za pośrednictwem połączeń taryfowej (takich jak sieci LTE) są wyłączone, ale każdy użytkownik może niezależnie włączyć tę funkcję w opcjach Ustawienia > **Aktualizacje > zaawansowane**. Jeśli chcesz zezwolić wszystkim użytkownikom na włączanie aktualizacji za pośrednictwem połączeń taryfowej [, prześlij](../working-with-managed-desktop/admin-support.md) żądanie zmiany, co spowoduje włączenie tego ustawienia dla wszystkich urządzeń.
| Zgodność urządzenia | Te zasady są skonfigurowane dla wszystkich Microsoft Managed Desktop urządzeniach. Urządzenie jest zgłaszane jako niezgodne, gdy pochodzi z wymaganej przez nas konfiguracji zabezpieczeń.

## <a name="windows-diagnostic-data"></a>Windows danych diagnostycznych

 Urządzenia będą ustawione w celu zapewnienia firmie Microsoft rozszerzonych danych diagnostycznych pod znanym identyfikatorem komercyjnym. W ramach Microsoft Managed Desktop administratorzy IT nie mogą zmieniać tych ustawień. Dla klientów w regionach ogólnego rozporządzenia o ochronie danych (RODO) użytkownicy mogą zmniejszyć poziom dostarczonych danych diagnostycznych, ale spowoduje to zmniejszenie ilości usług. Na przykład Microsoft Managed Desktop zbieranie danych niezbędnych do iteratu w ustawieniach i zasadach w celu jak najlepszego przetwarzania potrzeb w zakresie wydajności i zabezpieczeń. Aby uzyskać więcej informacji, [zobacz Windows danych diagnostycznych w organizacji.](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enhanced-level)

## <a name="security-addendum"></a>Dodatek zabezpieczeń

 W tej sekcji przedstawiono zasady, które zostaną wdrożone oprócz standardowych Microsoft Managed Desktop wymienionych w [sekcji Zasady domyślne](#default-policies). Ta konfiguracja została zaprojektowana z myślą o usługach finansowych i najlepiej uregulowanych branżach, które optymalizują się pod kątem najwyższych zabezpieczeń przy zachowaniu produktywności użytkowników.

 ### <a name="additional-security-policies"></a>Dodatkowe zasady zabezpieczeń

 Te zasady zostały dodane w celu zwiększenia zabezpieczeń dla branż ściśle uregulowanych. 
 - **Monitorowanie zabezpieczeń**: Firma Microsoft będzie monitorować urządzenia za pomocą [programu Microsoft Defender for Endpoint](/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection). W przypadku wykrycia zagrożenia firma Microsoft powiadomi klienta, wyizoluje urządzenie i zdalnie naprawi problem. 
 - **Wyłączanie programu PowerShell W2**. Firma Microsoft usunęła program PowerShell V2 w sierpniu 2017 r. Ta funkcja została wyłączona na wszystkich Microsoft Managed Desktop urządzeniach. Aby uzyskać więcej informacji na temat tej zmiany, [zobacz Windows PowerShell 2.0 Cofanie.](https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/)