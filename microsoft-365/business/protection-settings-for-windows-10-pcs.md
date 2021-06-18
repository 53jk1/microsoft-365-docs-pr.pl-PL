---
title: Edytowanie lub tworzenie ustawień ochrony urządzeń dla Windows 10 PC
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: bd66c26c-73a4-45a8-8642-3ea4ee7cd89d
description: Dowiedz się więcej o ustawieniach dostępnych Microsoft 365 dla firm na potrzeby zabezpieczania Windows 10 urządzeniach.
ms.openlocfilehash: 4859681d5e71a61b8a5dd58114bce899f485967a
ms.sourcegitcommit: be929f79751c0c52dfa6bd98a854432a0c63faf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/14/2021
ms.locfileid: "52925324"
---
# <a name="edit-or-create-device-protection-settings-for-windows-10-pcs"></a>Edytowanie lub tworzenie ustawień ochrony urządzeń dla Windows 10 PC

Ten artykuł dotyczy Microsoft 365 Business Premium.

Po skonfigurowaniu domyślnych ustawień Windows ochrony na stronie Konfiguracja możesz dodać nowe ustawienia dotyczące wszystkich użytkowników lub zestawu użytkowników. Możesz również edytować dowolne z utworzonych przez Ciebie plików.

## <a name="create-protection-settings-for-windows-10-devices"></a>Tworzenie ustawień ochrony dla Windows 10 urządzeniach

Wyświetl klip wideo na temat zabezpieczania Windows 10 za pomocą Microsoft 365 Business Premium:
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/a5734146-620a-4cec-8618-536b3ca37972?autoplay=false]
  
1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a> . 
2. W lewym okienku narracji wybierz pozycję **Urządzenia Zasady** \>  \> **Dodaj**.
3. W okienku **Dodawanie zasad** wprowadź unikatową nazwę dla zasad. 
4. W sekcji **Typ zasad** wybierz opcję **Konfiguracja urządzeń z systemem Windows 10**.
5. Expand **Secure Windows 10 Devices** \> configure the settings how you would like. Aby uzyskać więcej informacji, zobacz [Dostępne ustawienia.](#available-settings) 
    
    Aby zresetować ustawienia do wartości domyślnych, w dowolnej chwili możesz użyć linku **Resetuj ustawienia domyślne**. 
    
    ![Add policy pane with Windows 10 Device configuration selected](../media/fa9e2dc2-7eae-4c96-af34-765a1f641ecf.png)
  
6. Next decide **Who will get these settings?** If you don't want to use the default **All users** security group, Choose **Change**, search for the security group who will get these settings \> **Select**.
7. Na koniec wybierz przycisk **Gotowe**, aby zapisać zasady i zastosować je na urządzeniach. 

## <a name="edit-windows-10-protection-settings"></a>Edytowanie Windows 10 ochrony
 
1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a> .     
2. W lewym okienku narracji wybierz pozycję **Zasady** \> **dotyczące urządzeń.**
1. Wybierz istniejącą politykę Windows urządzenia, a następnie wybierz **pozycję Edytuj**.
1. Wybierz **pozycję Edytuj** obok ustawienia, które chcesz zmienić, a następnie wybierz pozycję **Zapisz**.

## <a name="available-settings"></a>Dostępne ustawienia

Domyślnie wszystkie ustawienia są **Włączone**. Dostępne są następujące ustawienia.
  
Aby uzyskać więcej informacji, zobacz Jak działa funkcja ochrony [w usłudze Microsoft 365 Premium mapowanie do ustawień usługi Intune.](map-protection-features-to-intune-settings.md) 


|Ustawienie  <br/> |Opis  <br/> |
|:-----|:-----|
|Chroń komputery przed wirusami i innymi zagrożeniami za pomocą ochrony antywirusowej programu Windows Defender  <br/> |Wymaga włączenia programu antywirusowego Windows Defender w celu ochrony komputerów przed zagrożeniami związanymi z połączeniem z Internetem.  <br/> |
|Chroń komputery przed zagrożeniami internetowymi w programie Microsoft Edge  <br/> |Włącza w programie Microsoft Edge ustawienia ułatwiające ochronę użytkowników przed złośliwymi witrynami i złośliwą zawartością do pobrania.  <br/> |
|Użyj reguł, które zmniejszają obszar ataków na urządzenia  <br/> |Gdy zmniejszanie obszaru ataków jest włączone, pomaga blokować akcje i aplikacje zwykle używane przez złośliwe oprogramowanie do infekowania urządzeń. To ustawienie jest dostępne tylko wtedy, gdy jest włączona ochrona antywirusowa programu Windows Defender. Zobacz [Zmniejszanie obszarów ataków](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection), aby dowiedzieć się więcej.  <br/> |
|Chroń foldery przed zagrożeniami, takimi jak oprogramowanie wymuszające okup  <br/> |To ustawienie używa kontrolowanego dostępu do folderów w celu ochrony danych firmy przed modyfikacją przez podejrzane lub złośliwe aplikacje, takie jak oprogramowanie wymuszające okup. Tego typu aplikacje mają zablokowaną możliwość wprowadzania zmian w chronionych folderach. To ustawienie jest dostępne tylko wtedy, gdy jest włączona ochrona antywirusowa programu Windows Defender. Aby [dowiedzieć się więcej, zobacz Chronię foldery za pomocą](/mem/configmgr/protect/deploy-use/create-deploy-exploit-guard-policy#bkmk_CFA) kontrolowanego dostępu do folderu.  <br/> |
|Blokuj dostęp sieciowy do potencjalnie złośliwej zawartości w Internecie  <br/> |Użyj tego ustawienia, aby blokować połączenia wychodzące użytkownika do lokalizacji internetowych o niskiej reputacji, które mogą hostować wyłudzanie informacji, oszustwa lub inną złośliwą zawartość. To ustawienie jest dostępne tylko, Program antywirusowy Windows Defender ma ustawioną wartość **Wł.** Aby uzyskać więcej informacji, zobacz [Ochrona sieci.](/windows/security/threat-protection/windows-defender-antivirus/configure-real-time-protection-windows-defender-antivirus)  <br/> |
|Pomóż chronić pliki i foldery na komputerach przed nieautoryzowanym dostępem za pomocą funkcji BitLocker  <br/> |Funkcja BitLocker chroni dane przez zaszyfrowanie dysków twardych komputera i zapewnianie ochrony przed ujawnieniem danych w razie zagubienia lub kradzieży komputera. Aby uzyskać więcej informacji, zobacz [Często zadawane pytania dotyczące funkcji BitLocker.](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)  <br/> |
|Zezwalaj użytkownikom na pobieranie aplikacji z witryny Microsoft Store  <br/> |Pozwala użytkownikom pobierać i instalować aplikacje z witryny Microsoft Store. Do aplikacji tych należą zarówno gry, jak i narzędzia biurowe, więc zostawiamy to ustawienie **włączone**, ale możesz je wyłączyć w celu dodatkowego zwiększenia bezpieczeństwa.  <br/> |
|Zezwalaj użytkownikom na korzystanie z Cortany  <br/> |Cortana może być bardzo pomocna. Cortana włączyć lub wyłączyć ustawienia, udzielać wskazówek dojazdu i mieć pewność, że terminy są terminowe, więc domyślnie to ustawienie **jest** włączone.  <br/> |
|Zezwalaj użytkownikom na otrzymywanie porad i reklam dotyczących systemu Windows od firmy Microsoft  <br/> |Porady dotyczące systemu Windows mogą być przydatne i ułatwiać użytkownikom zapoznawanie się nowymi funkcjami.  <br/> |
|Automatycznie aktualizuj urządzenia z systemem Windows 10  <br/> |Zapewnia, że urządzenia z systemem Windows 10 automatycznie otrzymują najnowsze aktualizacje.  <br/> |
|Wyłącz ekran urządzenia po takim czasie bezczynności  <br/> |Zapewnia bezpieczeństwo danych firmowych podczas bezczynności użytkownika. Jeśli użytkownik pracuje w miejscu publicznym, na przykład kawiarni, i odejdzie na chwilę od urządzenia lub skupi uwagę na czymś innym, przypadkowe osoby mogą obejrzeć zawartość ekranu. To ustawienie pozwala kontrolować czas bezczynności użytkownika, po którym ekran zostanie wyłączony.  <br/> |