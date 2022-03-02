---
title: Zarządzanie urządzeniami za pomocą usługi Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- enroll devices into Intune
- manage device endpoints
- zero trust deployment stack
- device management with zero trust
manager: dougeby
audience: ITPro
ms.topic: article
description: Zarejestruj urządzenia punktu końcowego w Microsoft Intune jako część architektury zabezpieczeń Zerowe zaufanie, chroniąc przed oprogramowaniem wymuszającym okup podczas tworzenia ochrony dla pracowników zdalnych.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-overview
ms.custom: ''
keywords: ''
ms.openlocfilehash: 9b1f3fbf48b58c477c1ae4c49870af6d58341bc4
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014767"
---
# <a name="manage-devices-with-intune-overview"></a>Zarządzanie urządzeniami za pomocą usługi Intune — omówienie

Podstawowym elementem zabezpieczeń na poziomie przedsiębiorstwa jest zarządzanie urządzeniami i ich ochrona. W ramach strategii należy się budować architekturę zabezpieczeń Zero Trust, chronić środowisko przed oprogramowaniem wymuszającym okup lub chronić pracowników zdalnych, zarządzając urządzeniami. Chociaż Microsoft 365 narzędzia i metodyka do zarządzania urządzeniami i ochrony ich, w ramach tych wskazówek osądzie się zalecenia firmy Microsoft z zastosowaniem metodyki Microsoft Intune. To jest odpowiednie wskazówki dla Ciebie, jeśli:

- Zaplanuj zarejestrowanie urządzeń w usłudze Intune za pośrednictwem programu Azure AD Join (w tym hybrydowego dołączania do usługi Azure AD).
- Zaplanuj ręczne zarejestrowanie urządzeń w usłudze Intune.
- Zezwalaj na urządzenia BYOD z planami zaimplementowania ochrony aplikacji i danych i/lub zarejestruj te urządzenia do zarządzania.

Z drugiej strony, jeśli Twoje środowisko zawiera plany współzawłasniania, w tym Microsoft Endpoint Configuration Manager[](/mem/configmgr/comanage/), zobacz Dokumentacja dotycząca współzawłasniania, aby opracować najlepszą ścieżkę dla organizacji. Jeśli Twoje środowisko zawiera plany usługi Windows 365 Cloud PC, zobacz dokumentację usługi [Windows 365 Enterprise](/windows-365/enterprise/), aby opracować najlepszą ścieżkę dla organizacji. 

## <a name="why-manage-endpoints"></a>Dlaczego warto zarządzać punktami końcowymi?
Nowoczesne przedsiębiorstwo ma wiele różnych punktów końcowych, które mają dostęp do swoich danych. Ta konfiguracja tworzy olbrzymią powierzchnię ataków, w wyniku czego punkty końcowe mogą łatwo stać się najbłędszym linkiem w strategii zabezpieczeń Zerowe zaufanie. 

Głównie kierowani koniecznością, gdy świat został przenoszony na model pracy zdalnej lub hybrydowej, użytkownicy pracują z dowolnego miejsca, z dowolnego urządzenia, więcej niż kiedykolwiek w historii. Atakujący szybko dopasowywują swoje taktyki, aby skorzystać z tej zmiany. Wiele organizacji ma ograniczone zasoby, gdy nawigują po tych nowych wyzwaniach biznesowych. Niemal w nocy firmy przyspieszyły transformację cyfrową. Mówiąc po prostu, zmienił się sposób pracy osób — nie oczekujemy już dostępu do wielu zasobów firmy tylko z biura i na urządzeniach należących do firmy.

Uzyskiwanie dostępu do punktów końcowych w celu uzyskiwania dostępu do zasobów firmy to pierwszy krok w strategii dotyczącej urządzeń bez zaufania. Zazwyczaj firmy aktywnie chronią komputery przed luki w zabezpieczeniach i atakami, podczas gdy urządzenia przenośne często są niemonitorowane i nie są zabezpieczane. Aby mieć pewność, że nie ujawniasz ryzyka związanego z danymi, musimy monitorować każdy punkt końcowy pod względami ryzyka i stosować szczegółową kontrolę dostępu w celu dostarczania odpowiedniego poziomu dostępu w oparciu o zasady organizacji. Jeśli na przykład urządzenie osobiste jest zablokowane, możesz zablokować dostęp, aby zapewnić, że aplikacje dla przedsiębiorstw nie będą narażone na znane luki w zabezpieczeniach.

W tej serii artykułów osą znajdziesz informacje o zalecanym procesie zarządzania urządzeniami, które mają dostęp do zasobów. Jeśli posuniesz zalecane czynności, Twoja organizacja osiągnie bardzo zaawansowaną ochronę Twoich urządzeń i dostępnych zasobów.


## <a name="implementing-the-layers-of-protection-on-and-for-devices"></a>Implementowanie warstw ochrony na urządzeniach i dla nich

Ochrona danych i aplikacji na urządzeniach i samych urządzeniach jest procesem wieloetapowym. Istnieją pewne zabezpieczenia, które można uzyskać na urządzeniach niezamanektowych. Po zarejestrowaniu urządzeń w zarządzaniu można zaimplementować bardziej zaawansowane kontrolki. Gdy ochrona przed zagrożeniami jest wdrażana w punktach końcowych, zyskasz jeszcze więcej informacji i możliwość automatycznego korygowania niektórych ataków. Ponadto, jeśli Twoja organizacja włożyła pracę w identyfikowanie poufnych danych, stosowanie klasyfikacji i etykiet oraz konfigurowanie zasad ochrony przed utratą danych, możesz uzyskać jeszcze bardziej szczegółową ochronę danych na swoich punktach końcowych.

Na poniższym diagramie pokazano bloki konstrukcyjne w celu osiągnięcia zerowego zaufania dla zabezpieczeń Microsoft 365 innych aplikacji SaaS wprowadzanych do tego środowiska. Elementy związane z urządzeniami są numerowane od 1 do 7. To są warstwy zabezpieczeń, które administratorzy urządzeń ochrony będą koordynować z innymi administratorami w celu wykonania tych zadań. 

![Microsoft 365 stosu wdrażania Bez zaufania](../media/devices/m365-zero-trust-deployment-stack-devices.png#lightbox)

Na poniższej ilustracji: 


|&nbsp;|Krok |Opis  |Wymagania dotyczące licencjonowania  |
|---------|---------|---------|---------|
|1     | Konfigurowanie zasad dostępu do urządzeń i tożsamości zerowego zaufania od początku       | We współpracy z administratorem tożsamości przejmij ochronę danych w zasadach ochrony aplikacji [(APP) poziomu 2](manage-devices-with-intune-app-protection.md). Te zasady nie wymagają, aby zarządzać urządzeniami. Zasady aplikacji konfigurujesz w usłudze Intune. Administrator tożsamości konfiguruje zasady dostępu warunkowego tak, aby wymagały zatwierdzonych aplikacji.          |E3, E5, F1, F3, F5    |
|2     | Rejestrowanie urządzeń do zarządzania       | To zadanie wymaga więcej planowania i czasu wdrożenia. Firma Microsoft zaleca zarejestrowanie urządzeń za pomocą usługi Intune, ponieważ to narzędzie zapewnia optymalną integrację. Istnieje kilka opcji rejestracji urządzeń w zależności od platformy. Na przykład za Windows usługi Azure AD można przystąpić do pracy lub za pomocą rozwiązania Autopilot. Musisz przejrzeć opcje dla każdej platformy i zdecydować, która opcja rejestracji jest najlepsza dla Twojego środowiska. Zobacz [Krok 3. Rejestrowanie urządzeń do zarządzania,](manage-devices-with-intune-enroll.md) aby uzyskać więcej informacji.      | E3, E5, F1, F3, F5        |
|3     | Konfigurowanie zasad zgodności        |  Chcesz się upewnić, że urządzenia, które mają dostęp do aplikacji i danych, spełniają minimalne wymagania, na przykład urządzenia są chronione hasłem lub przypinaniem, a system operacyjny jest aktualny. Zasady zgodności są sposobem definiowania wymagań, które muszą spełnić urządzenia. [Krok 3. Konfigurowanie zasad zgodności ułatwia](manage-devices-with-intune-compliance-policies.md) ich konfigurowanie.        |   E3, E5, F3, F5      |
|4     | Konfigurowanie Enterprise (zalecane) Zasady dostępu do urządzeń i tożsamości zerowego zaufania        |Po zarejestrowaniu urządzeń możesz we współpracy z administratorem tożsamości dostosować zasady dostępu warunkowego, aby wymagały urządzeń o dobrej kondycji [i zgodności](manage-devices-with-intune-require-compliance.md).          | E3, E5, F3, F5        |
|5     |Wdrażanie profilów konfiguracji      | W odróżnieniu od zasad zgodności urządzeń, które po prostu oznaczają urządzenie jako zgodne lub nie na podstawie skonfigurowanych kryteriów, profile konfiguracji w rzeczywistości zmieniają konfigurację ustawień na urządzeniu. Przy użyciu zasad konfiguracji można chronić urządzenia przed cyberatakami. Zobacz [Krok 5. Wdrażanie profilów konfiguracji](manage-devices-with-intune-configuration-profiles.md).        | E3, E5, F3, F5        |
|6     |Monitorowanie ryzyka urządzenia i zgodności z planami bazowymi zabezpieczeń         | W tym kroku połącz usługę Intune z usługą Microsoft Defender for Endpoint. Dzięki tej integracji można monitorować ryzyko związane z urządzeniem jako warunek dostępu. Urządzenia, których stan jest ryzykowny, zostaną zablokowane. Możesz również monitorować zgodność z planami bazowymi zabezpieczeń. Zobacz [Krok 6. Monitorowanie ryzyka urządzenia i zgodności z planami bazowymi zabezpieczeń](manage-devices-with-intune-monitor-risk.md).       | E5, F5        |
|7     |Wdrażanie funkcji ochrony przed utratą danych (DLP, data loss prevention) za pomocą funkcji ochrony informacji   | Jeśli Twoja organizacja włożyła pracę w identyfikowanie poufnych danych i oznaczanie dokumentów etykietami, możesz współpracować z administratorem ochrony informacji w celu ochrony poufnych informacji i dokumentów [na Twoich urządzeniach](manage-devices-with-intune-dlp-mip.md).         | Dodatek zgodności E5, F5        |
| | | | |

## <a name="coordinating-endpoint-management-with-zero-trust-identity-and-device-access-policies"></a>Koordynowanie zarządzania punktami końcowymi przy użyciu zasad dostępu do urządzeń i tożsamości bez zaufania

Te wskazówki są ściśle skoordynowane z zalecanymi zasadami [dostępu do tożsamości i](../security/office-365-security/microsoft-365-policies-configurations.md) urządzeń bez zaufania. Będziesz pracować ze swoim zespołem tożsamości, aby chronić konfigurować usługę Intune do zasad dostępu warunkowego w usłudze Azure AD. 

Poniżej przedstawiono ilustrację zalecanego zestawu zasad z objaśnieniami kroku dotyczącymi pracy, która będzie robisz w usłudze Intune/MEM, i powiązanych zasad dostępu warunkowego, które pomogą skoordynować w usłudze Azure AD. 

[![Zasady zerowego zaufania w zakresie tożsamości i dostępu do urządzeń](../media/devices/identity-device-overview-steps.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-overview-steps.png)


Na poniższej ilustracji:
- W kroku 1, [Implementowanie zasad ochrony aplikacji (APP) poziomu 2](manage-devices-with-intune-app-protection.md) konfigurujesz zalecany poziom ochrony danych za pomocą zasad aplikacji. Następnie we współpracy ze swoim zespołem tożsamości skonfigurujesz powiązaną regułę dostępu warunkowego, aby wymagać korzystania z tej ochrony.
- W krokach 2, 3 i 4 rejestrujesz urządzenia do zarządzania za pomocą intune/MEM, definiujesz zasady zgodności urządzeń, a następnie koordynujesz je ze swoim zespołem tożsamości, aby skonfigurować powiązaną regułę dostępu warunkowego w celu umożliwienia dostępu tylko do zgodnych urządzeń. 

<!---
## Managing change with users
--->

## <a name="enrolling-devices-vs-onboarding-devices"></a>Urządzenia rejestrujące a urządzenia dołączające
Jeśli będziesz postępować zgodnie z tymi wskazówkami, zarejestrujesz urządzenia do zarządzania za pomocą usługi Intune (lub innego narzędzia), a do urządzenia zostaną nało że do korzystania z dwóch usług:
- Defender for Endpoint
- DLP punktu końcowego


Na poniższej ilustracji przedstawiono sposób działania tej funkcji przy użyciu usługi Intune.
<br>

![Proces rejestracji i dołączania urządzeń](../media/devices/devices-enroll-onboard-process.png#lightbox)

Na ilustracji:
1. Zarejestruj urządzenia do zarządzania za pomocą usługi Intune.
2. Usługa Intune umożliwia dołączanie urządzeń do usługi Defender for Endpoint.
3. Urządzenia, które są podłączone do usługi Defender for Endpoint, są również wnoszone na Microsoft 365 funkcji zgodności, w tym funkcji DLP punktu końcowego.
 
Pamiętaj, że tylko usługa Intune zarządza urządzeniami. Dołączanie oznacza możliwość udostępniania informacji przez urządzenie w określonej usłudze. W poniższej tabeli podsumowano różnice między zarejestrowaniem urządzeń do zarządzania i wnoszeń do określonej usługi.


|         |Zarejestruj     |Onboard  |
|---------|---------|---------|
|Opis     |  Rejestracja dotyczy zarządzania urządzeniami. Urządzenia są zarejestrowane do zarządzania za pomocą usługi Intune lub Menedżer konfiguracji.        | Wewnecie konfiguruje urządzenie do pracy z określonym zestawem funkcji w programie Microsoft 365. Obecnie dołączanie dotyczy programu Microsoft Defender w zakresie funkcji zgodności i punktu końcowego firmy Microsoft. <br><br>Na Windows urządzeniach dołączanie obejmuje przełączanie ustawienia w programie Windows Defender, które pozwala usłudze Defender na łączenie się z usługą online i akceptowanie zasad, które mają zastosowanie do urządzenia.        |
|Zakres     | Za pomocą tych narzędzi do zarządzania urządzeniami można zarządzać całym urządzeniem, łącznie z konfigurowaniem urządzenia w celu spełnienia określonych celów, takich jak zabezpieczenia.        |Dołączanie dotyczy tylko tych usług, które mają zastosowanie.     |
|Zalecana metoda     | Azure Active Directory automatycznie rejestruje urządzenia w usłudze Intune.        | Usługa Intune jest preferowaną metodą dołączania urządzeń do Windows Defender punktu końcowego, a w rezultacie Microsoft 365 funkcji zgodności.<br><br>Pamiętaj, że urządzenia, które zostały Microsoft 365 w celu zapewnienia zgodności za pomocą innych metod, nie są automatycznie zarejestrowane dla usługi Defender for Endpoint.        |
|Inne metody     |   Inne metody rejestracji zależą od platformy urządzenia i od tego, czy jest to byod, czy zarządzane przez Twoją organizację.      | Inne metody dołączania urządzeń są następujące:<br><li>Menedżer konfiguracji<li>Inne narzędzie do zarządzania urządzeniami przenośnymi (jeśli urządzenie jest zarządzane przez jedno narzędzie)<li>Skrypt lokalny<li>Pakiet konfiguracji VDI dla urządzeń VDI (onboarding non-persistent virtual desktop infrastructure)<li>zasady grupy|
| | |     |



## <a name="learning-for-administrators"></a>Edukacja dla administratorów
Poniższe zasoby ułatwiają administratorom poznanie pojęć dotyczących korzystania z MEM i Intune.

[Uprość zarządzanie urządzeniami](/learn/modules/simplify-device-management-with-microsoft-endpoint-manager/) dzięki opisowi Microsoft Endpoint Manager: poznaj nowoczesne zarządzanie i Microsoft Endpoint Manager oraz dowiedz się, jak narzędzia do zarządzania biznesowego w programie Microsoft 365 upraszczają zarządzanie wszystkimi Twoimi urządzeniami.

[Konfigurowanie Microsoft Intune](/learn/modules/set-up-microsoft-intune/) Opis: program Microsoft Intune, który jest częścią usługi Microsoft Endpoint Manager, pomaga chronić urządzenia, aplikacje i dane, z których korzystają osoby w Twojej organizacji, aby zwiększyć produktywność. Po zakończeniu pracy nad tym modułem skonfigurujemy Microsoft Intune. Konfiguracja obejmuje przeglądanie obsługiwanych konfiguracji, tworzenie konta w usłudze Intune, dodawanie użytkowników i grup, przypisywanie licencji do użytkowników, udzielanie uprawnień administratora i ustawianie urzędu zarządzania usługą MDM.