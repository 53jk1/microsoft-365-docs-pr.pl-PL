---
title: Usuwanie domeny z innego konta
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b9707ec8-2247-4e25-9bad-f11ddbc686e4
description: Dowiedz się, jak dołączyć do niezazajemnianego konta utworzonego przez użytkownika, który tworzy samodzielne konto w usłudze Microsoft 365.
ms.openlocfilehash: 23fff52a4c42da05f787bfbe8207d3e090c0105c
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2022
ms.locfileid: "63013340"
---
# <a name="perform-an-internal-admin-takeover"></a>Przeprowadzanie przejęcia administratora wewnętrznego

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Jeśli jesteś administratorem i chcesz przejąć niezawiązane konto utworzone przez samodzielne konto użytkownika, możesz to zrobić przez przejęcie roli administratora wewnętrznego.

> [!NOTE]
> Samodzielne tworzenie konta w dowolnej usłudze w chmurze, która korzysta z usługi Azure AD, powoduje dodanie użytkownika do niezazadowonianego lub "cienia" katalogu Azure AD i utworzenie konta niezazadowońnego. Niezamanektowane konto to katalog bez administratora globalnego. Aby określić, czy konto jest zarządzane, czy nieza zarządzaniem, zobacz [Określanie typu dzierżawy](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type). 
  
## <a name="before-you-begin"></a>Przed rozpoczęciem

Czasami nie można dodać domeny do konta organizacji, ponieważ inna osoba już załozyła konto w udatku Microsoft 365 przy użyciu adresu e-mail skojarzonego z tą nazwą domeny. Możesz jednak usunąć domenę z innego konta nieza zarządzaniem i dodać ją do konta zarządzanego w Twojej organizacji.

Zanim będzie można usunąć domenę z drugiego konta i dodać ją do swojego konta, musisz dołączyć do konta niezamanektowego i zostać administratorem tego konta. Następnie usuniesz domenę z nieza zarządzania kontem, ponownie zalogujesz się do swojego konta i dodasz domenę do konta zarządzanego.

W procedurach  opisanej w tym artykule opisano tylko sposób dołączenia do drugiego konta (kroki 1 i 2) i wykonania czynności w kreatorze przejęcia administratora, aby zostać administratorem na koncie niezawiązyanych (krok 3).

Gdy zostaniesz administratorem dla konta niezawiązywana, możesz usunąć domenę z konta niezakierowane i dodać ją do swojego konta. 

## <a name="step-1-verify-your-email-address"></a>Krok 1. Weryfikowanie adresu e-mail

> [!NOTE]
> Jeśli na Twoim koncie jest włączona samoobsługa, użytkownicy mogą samodzielnie Power BI bezpłatne usługi, takie jak usługa online. Te usługi są przeznaczone specjalnie do użytku w przypadkach, gdy subskrypcja usługi samoobsługowej utworzyła konto użytkownika niezamówione, które chcesz przejąć jako administrator. W kroku 1 utworzysz konto użytkownika dla domeny, którą chcesz usunąć, za pomocą usługi Power BI w celu uruchomienia kreatora przejęcia roli administratora, który umożliwia Ci zostanie administratorem niezawiązyanego konta domeny.

1. Aby zarejestrować się w Power BI, przejdź do witryny usługi [Power BI](https://powerbi.com) i wybierz pozycję Rozpocznij bezpłatny okres próbny **FreeStart** >  (w polu Udostępnij Power BI Pro). 

2. Załóż konto użytkownika, które używa nazwy domeny Twojej organizacji (np `powerbiadmin@contoso.com`. ). Jeśli Twoje konto jest już używania, zaloguj się przy użyciu bieżącego hasła.

3. Sprawdź kod weryfikacyjny w wiadomości **e-mail** i wprowadź ten kod, aby zweryfikować swój adres e-mail.

## <a name="step-2-create-a-new-account-for-admin-access"></a>Krok 2. Tworzenie nowego konta w celu uzyskania dostępu administratora

1. Po wprowadzeniu kodu weryfikacyjnego zostaniesz przekierowyny do strony, na której możesz utworzyć nowe konto.

2. Wypełnij pola nazwy użytkownika i hasła konta, którego chcesz użyć, a następnie wybierz przycisk **Start**.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Krok 3. Zweryfikuj własność domeny i zostań administratorem

1. Po zakończeniu kroku 2 wybierz ikonę centrum administracyjnego w lewym okienku nawigacji (ewentualnie przejdź do przeglądarki i wpisz ).`https://admin.microsoft.com`

    Nastąpi przekierowanie do kreatora przejęcia roli administratora.

1. Wybierz **pozycję Dalej** i sprawdź, czy jesteś właścicielem domeny, którą chcesz przejąć, dodając rekord TXT u rejestratora domen. 

    Kreator udostępni rekord TXT do dodania, a także link do witryny internetowej twojego rejestratora oraz link do instrukcji krok po kroku.

1. Na **stronie Jesteś teraz administratorem** wybierz pozycję **Przejdź do centrum administracyjnego**.

    Teraz masz uprawnienia administratora wymagane do usunięcia domeny z drugiego konta. 
## <a name="related-content"></a>Zawartość pokrewna

YouTube: [3 kroki przejęcia](https://www.youtube.com/watch?v=xt5EsrQBZZk) roli administratora IT Power BI i Microsoft 365 (wideo)\
[Przejęcie roli administratora w usłudze Azure AD](/azure/active-directory/users-groups-roles/domains-admin-takeover) (artykuł)\
[Korzystanie z samodzielnego rejestracji w organizacji](self-service-sign-up.md) (artykuł)\
[Opis roli Power BI administratora](/power-bi/service-admin-role) usługi (artykuł)