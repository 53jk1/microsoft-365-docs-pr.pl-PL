---
title: Punkty końcowe usługi Office 365 U.S. Government GCC High
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/31/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: W tym artykule znajdziesz punkty końcowe osiągalne dla klientów korzystających z Office 365 Government GCC High.
hideEdit: true
ms.openlocfilehash: d22d292cd8914dd336d410dcbcb82e1ffb0d5362
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2022
ms.locfileid: "63009756"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Punkty końcowe usługi Office 365 U.S. Government GCC High

*Dotyczy: Office 365 Admin*

Usługa Office 365 wymaga połączenia z Internetem. Poniższe punkty końcowe powinny być osiągalne tylko dla klientów korzystających z Office 365 Government GCC High.
  
 **Office 365** punkty końcowe: Na całym świecie (w tym GCC [)](urls-and-ip-address-ranges.md) \| Office 365 obsługiwane przez firmę [21 Vianet](urls-and-ip-address-ranges-21vianet.md) \| [Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) \| *Office 365 U.S. Government GCC High*

<br>

****

|Uwagi|Pobierz|
|---|---|
|**Ostatnia aktualizacja:** 2021-10-29 — ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Subskrypcja dziennika zmian](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Pobierz:** pełna lista w formacie [JSON](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|
|

 Zacznij od [tematu Office 365 punktów końcowych,](managing-office-365-endpoints.md) aby zrozumieć nasze zalecenia dotyczące zarządzania łącznością sieciową przy użyciu tych danych. Na początku każdego miesiąca dane dotyczące punktów końcowych są aktualizowane przy użyciu nowych adresów IP i adresów URL opublikowanych 30 dni przed ich aktywnością. Dzięki temu klienci, którzy nie mają jeszcze automatycznych aktualizacji, mogą dokończyć swoje procesy, zanim będzie wymagana nowa łączność. W razie potrzeby punkty końcowe mogą być także aktualizowane w ciągu miesiąca, aby rozwiązać potrzeby dotyczące eskalacji pomocy technicznej, zdarzeń dotyczących zabezpieczeń lub innych natychmiastowych wymagań operacyjnych. Wszystkie dane pokazane na poniższej stronie są generowane z usług sieci Web opartych na u dołu. Jeśli uzyskujesz dostęp do tych danych za pomocą skryptu lub urządzenia sieciowego, przejdź [bezpośrednio do usługi](microsoft-365-ip-web-service.md) sieci Web.

Poniżej przedstawiono dane punktu końcowego z listą wymagań dotyczących łączności między komputerami Office 365. Nie obejmuje ona połączeń sieciowych firmy Microsoft do sieci klienta, czasami nazywanych hybrydowymi lub przychodzącymi połączeniami sieciowymi.

Punkty końcowe są pogrupowane w cztery obszary usługi. Pierwsze trzy obszary usługi można niezależnie wybrać dla łączności. Czwarty obszar usługi jest wspólną zależnością (o nazwie Microsoft 365 Common i Office) i musi zawsze mieć łączność sieciową.

Pokazane są kolumny danych:

- **Identyfikator**: Numer identyfikacyjny wiersza, nazywany również zestawem punktów końcowych. Ten identyfikator jest taki sam, jak jest zwracany przez usługę sieci Web dla zestawu punktów końcowych.

- **Kategoria**: Pokazuje, czy zestaw punktów końcowych jest kategoryzowany jako "Optymalizuj", "Zezwalaj" lub "Domyślny". Informacje na temat tych kategorii i wskazówek dotyczących zarządzania nimi można znaleźć na stronie [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). W tej kolumnie wymieniono również zestawy punktów końcowych, które są wymagane do łączności sieciowej. W przypadku zestawów punktów końcowych, które nie są wymagane do łączności sieciowej, w tym polu są dostępne uwagi wskazujące, jakie funkcje byłyby brakujące w przypadku zablokowania zestawu punktów końcowych. Jeśli wykluczasz cały obszar usługi, zestawy punktów końcowych wymienione jako wymagane nie wymagają łączności.

- **ER**: Jest tak **, jeśli** zestaw punktów końcowych jest obsługiwany przez usługę Azure ExpressRoute Office 365 prefiksami tras. Społeczność BGP, która zawiera przedstawione prefiksy tras, jest wyrównana z wymienionym obszarem usługi. Gdy ER ma **wartość Nie**, oznacza to, że w tym zestawie punktów końcowych usługi ExpressRoute nie jest obsługiwana. Nie należy jednak zakładać, że żadne trasy nie są ogłaszane dla zestawu punktów końcowych, w którym ER ma wartość **Nie**. Jeśli planujesz korzystać z usługi Azure AD Połączenie, przeczytaj sekcję ze [](/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) specjalnymi zagadnieniami, aby upewnić się, że masz odpowiednią konfigurację usługi Azure AD Połączenie konfiguracji.

- **Adresy**: Zawiera listę nazw FQDN lub nazw domen z symbolami wieloznacznych i zakresów adresów IP dla zestawu punktów końcowych. Zakres adresów IP jest w formacie CIDR i może zawierać wiele pojedynczych adresów IP w określonej sieci.

- **Porty**. Zawiera listę portów TCP lub UDP, które są połączone z adresami, aby stanowią punkt końcowy sieci. W zakresach adresów IP, w których znajdują się różne porty, możesz zauważyć pewne duplikaty.

[!INCLUDE [Office 365 U.S. Government GCC High endpoints](../includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Uwagi dotyczące tej tabeli:

- Centrum zabezpieczeń i zgodności (SCC) zapewnia obsługę usługi Azure ExpressRoute dla sieci Office 365. To samo dotyczy wielu funkcji ujawnionych za pośrednictwem centrum SCC, takich jak raportowanie, inspekcja, Advanced eDiscovery, ujednolicone zasady ochrony przed dostępem do danych i zarządzanie danymi. Dwie określone funkcje, Importowanie pliku PST i eksport zbierania elektronicznych materiałów dowodowych, obecnie nie obsługują usługi Azure ExpressRoute z tylko filtrami tras usługi Office 365 ze względu na ich zależność od usługi Azure Blob Storage. Aby korzystać z tych funkcji, potrzebujesz oddzielnej łączności z usługą Azure Blob Storage przy użyciu dowolnych opcji łączności z platformą Azure, które obejmują łączność internetową lub usługę Azure ExpressRoute z filtrami tras publicznych Azure. Należy ocenić ustanowienie takiej łączności dla obu tych funkcji. Zespół usługi Office 365 Information Protection wie o tym ograniczeniu i aktywnie pracuje nad zapewnianie obsługi usługi Azure ExpressRoute dla usługi Office 365 jako ograniczone Office 365 filtrów tras dla obu tych funkcji.

- Istnieją dodatkowe opcjonalne punkty końcowe dla Aplikacje Microsoft 365 dla przedsiębiorstw, których nie wymieniono i które nie są wymagane do uruchamiania aplikacji Aplikacje Microsoft 365 dla przedsiębiorstw i edytowania dokumentów. Opcjonalne punkty końcowe są hostowane w centrach danych firmy Microsoft i nie przetwarzają, nie przesyłają ani nie przechowują danych klientów. Zalecamy, aby połączenia użytkowników z tymi punktami końcowymi były kierowane do domyślnej sieci obwodowej internetowego punktu wychodzącego.