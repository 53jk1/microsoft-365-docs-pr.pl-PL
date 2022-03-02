---
title: Włączanie i wyłączanie aplikacji Microsoft Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.custom: admindeeplinkMAC
ms.localizationpriority: medium
ms.assetid: 5382dc07-aaa5-45c9-8767-502333b214ce
description: Dowiedz się, jak uzyskać dostęp do usługi Microsoft Bookings w Microsoft 365.
ms.openlocfilehash: 8a92f156406a7c3aa4539036ae31d883a6db766f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984555"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Włączanie i wyłączanie aplikacji Microsoft Bookings

Usługę Bookings można włączać i wyłączać dla całej organizacji lub konkretnych użytkowników. Po włączeniu aplikacji Bookings dla użytkowników mogą oni utworzyć stronę aplikacji Bookings, utworzyć kalendarz i zezwolić innym osobom na zarezerwowanie czasu przy ich użyciu.

> [!NOTE]
> Kontrolki administratora opisane w tych sekcjach nie są dostępne dla klientów usługi Office 365 obsługiwanej przez firmę 21Vianet (Chiny).

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>Włączanie lub wyłączanie aplikacji Bookings dla organizacji przy użyciu aplikacji centrum administracyjne platformy Microsoft 365

1. Zaloguj się do centrum centrum administracyjne platformy Microsoft 365 jako administrator globalny.

2. W centrum administracyjnym przejdź do pozycji  **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**ustawienia organizacji**</a>.

3. Zaznacz pole wyboru **Zezwalaj organizacji na używanie aplikacji Bookings** do włączania lub wyłączania aplikacji Bookings w Twojej organizacji.

   > [!NOTE]
   > Wyłączenie aplikacji Bookings spowoduje wyłączenie całego dostępu do usługi, łącznie z tworzeniem stron aplikacji Bookings i zarządzaniem nimi.

4. Wybierz opcję **Zapisz zmiany**.

## <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>Włączanie lub wyłączanie aplikacji Bookings dla organizacji za pomocą programu PowerShell

Aby włączyć lub wyłączyć usługę Bookings dla organizacji przy użyciu polecenia cmdlet [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) programu PowerShell, Połączenie w celu Exchange Online [programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i uruchom następujące polecenie:

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Włączanie lub wyłączanie aplikacji Bookings dla poszczególnych użytkowników

Możesz wyłączyć usługę Bookings dla poszczególnych użytkowników.

1. Przejdź do centrum administracyjne platformy Microsoft 365, a następnie wybierz **pozycję Aktywni** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**użytkownicy**</a> użytkownicy.

1. Wybierz odpowiedniego użytkownika, a następnie wybierz **pozycję Licencje i aplikacje**.

1. **Rozwiń kartę** Aplikacje i wyczyść pole wyboru aplikacji Microsoft Bookings.

## <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Wymaganie zatwierdzenia personelu przed udostępnieniem informacji o wolnym/zajętym

Administratorzy mogą wymagać od pracowników w organizacji zgody na zapisanie się na to, zanim ich informacje o dostępności zostaną udostępnione za pośrednictwem usługi Bookings i zanim będzie można ich zarezerwować za pośrednictwem strony rezerwacji. To ustawienie jest dostępne na stronie **centrum administracyjne platformy Microsoft 365 w Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Ustawienia organizacji Bookings**</a>\>.

Gdy to ustawienie jest włączone, pracownicy dodani jako pracownicy w kalendarzach rezerwacji znajdą link Zatwierdź/Odrzuć w obierania wiadomości e-mail.

## <a name="block-social-sharing-options"></a>Blokowanie opcji udostępniania sieci społecznościowych

Administratorzy mogą kontrolować sposób współużytkowania stron rezerwacji w sieciach społecznościowych. To ustawienie jest dostępne na stronie **centrum administracyjne platformy Microsoft 365 w Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Ustawienia organizacji Bookings**</a>\>.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Zezwalaj tylko wybranym użytkownikom na tworzenie kalendarzy aplikacji Bookings

Stosując ograniczenia zasad, można uniemożliwić licencjonowanym użytkownikom tworzenie kalendarzy aplikacji Bookings. Najpierw musisz włączyć usługę Bookings dla całej organizacji. Wszyscy użytkownicy w Twojej organizacji będą mieli licencje aplikacji Bookings, ale tylko użytkownicy uwzględnioni w zasadach mogą tworzyć kalendarze aplikacji Bookings i mieć pełną kontrolę nad tym, kto ma dostęp do tworzyć kalendarze.

Użytkownicy uwzględnieni w tych zasadach mogą tworzyć nowe kalendarze aplikacji Bookings i dodawać je jako pracowników z dowolnej wydajności (łącznie z rolą administratora) do istniejących kalendarzy aplikacji Bookings. Użytkownicy, którzy nie są uwzględnioni w tych zasadach, nie będą mogli tworzyć nowych kalendarzy aplikacji Bookings i w razie próby ich utworzenia otrzymają komunikat o błędzie.

Poniższe polecenia należy uruchomić przy użyciu programu Exchange Online PowerShell. Aby uzyskać więcej informacji na temat Exchange Online poleceń cmdlet, zobacz Połączenie [aby Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> W poniższej czynności założono, że Outlook Web App nie zostały utworzone żadne inne zasady skrzynek pocztowych aplikacji (OWA).

1. Utwórz nowe zasady skrzynki pocztowej dla użytkowników, którzy powinni mieć możliwość tworzenia kalendarzy aplikacji Bookings. (Tworzenie kalendarza aplikacji Bookings jest domyślnie dozwolone przez nowe zasady skrzynki pocztowej).

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   Aby uzyskać więcej informacji, [zobacz New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy).

2. Przypisz te zasady do odpowiednich użytkowników, uruchamiając to polecenie dla każdego użytkownika, którego chcesz udzielić uprawnień do tworzenia kalendarzy aplikacji Bookings.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   Aby uzyskać więcej informacji, [zobacz Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

3. Opcjonalnie: Uruchom to polecenie, jeśli chcesz wyłączyć usługę Bookings dla wszystkich innych użytkowników w organizacji.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   Aby uzyskać więcej informacji, [zobacz Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

Aby uzyskać więcej informacji na temat zasad skrzynek pocztowych aplikacji OWA, zobacz następujące tematy:

- [Tworzenie zasad skrzynki Outlook w sieci Web pocztowej w aplikacji Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [Stosowanie lub usuwanie zasad skrzynki Outlook w sieci Web do skrzynki pocztowej w programie Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)