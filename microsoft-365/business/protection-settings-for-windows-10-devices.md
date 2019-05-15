---
title: Konfigurowanie ustawień ochrony aplikacji dla urządzeń z systemem Windows 10
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
f1_keywords:
- Win10AppPolicy
- O365E_Win10AppPolicy
- BCS365_Win10AppPolicy
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 02e74022-44af-414b-9d74-0ebf5c2197f0
description: Dowiedz się, jak utworzyć zasady aplikacji zarządzania i ochrony plików praca na urządzeniach Windows 10.
ms.openlocfilehash: f649454417dceae05255df6b37760af99c0b8d4f
ms.sourcegitcommit: db1dfb2df2c2f7beced3b57bc772d106c189e88a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "33660406"
---
# <a name="set-application-protection-settings-for-windows-10-devices"></a>Konfigurowanie ustawień ochrony aplikacji dla urządzeń z systemem Windows 10

## <a name="create-an-app-management-policy-for-windows-10"></a>Tworzenie zasad zarządzania aplikacjami dla systemu Windows 10

Jeśli użytkownicy mają urządzenia osobiste z systemem Windows 10, na których wykonują zadania służbowe, możesz również chronić dane na tych urządzeniach.
  
1. Przejdź do Centrum administracyjnego o <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
    
2. Na nawigacji z lewej strony wybierz **urządzenia** \> **zasady** \> **Dodaj**.

3. W okienku **Dodawanie zasad** wprowadź unikatową nazwę dla zasad. 
    
4. W sekcji **Typ zasad** wybierz pozycję **Zarządzanie aplikacjami dla systemu Windows 10**.
    
5. W obszarze **Typ urządzenia**wybierz **osobiste** lub **Właścicielem firmy**.
    
6. Opcja **Szyfruj pliki służbowe** zostanie włączona automatycznie. 
    
7. Jeśli nie chcesz, aby użytkownicy mogli zapisywać pliki służbowe na swoich komputerach, **włącz** ustawienie **Uniemożliw użytkownikom kopiowanie danych firmy do plików osobistych i wymuś na nich zapisywanie plików służbowych w usłudze OneDrive dla Firm**. 
    
9. Rozwiń sekcję **Odzyskiwanie danych na urządzeniach z systemem Windows** i **włącz** tę opcję (jest to zalecane).
    
    Aby móc przejść do lokalizacji certyfikatu agenta odzyskiwania danych, musisz najpierw go utworzyć. Odpowiednie instrukcje znajdziesz w artykule na temat [tworzenia i weryfikowania certyfikatu agenta odzyskiwania danych systemu szyfrowania plików](https://go.microsoft.com/fwlink/p/?linkid=853700).
    
    Domyślnie pliki robocze są szyfrowane przy użyciu klucza tajnego, który jest przechowywany na urządzeniu i skojarzony z profilem użytkownika. Tylko użytkownik może otwierać i odszyfrowywać plik. Jednak w razie utraty urządzenia lub usunięcia użytkownika plik może utknąć w stanie zaszyfrowania. Administrator może użyć certyfikatu agenta odzyskiwania danych (DRA) do odszyfrowania pliku.
    
    ![Browse to Data Recovery Agent certificate.](media/7d7d664f-b72f-4293-a3e7-d0fa7371366c.png)
  
10. Rozwiń sekcję **Chroń dodatkowe lokalizacje sieciowe i w chmurze**, jeśli chcesz dodać więcej domen lub lokalizacji usługi SharePoint Online. W ten sposób możesz się upewnić, że pliki we wszystkich wymienionych aplikacjach będą chronione. Poszczególne pozycje wprowadzane w polach oddzielaj średnikami.
    
    ![Expand Protect additional network and cloud locations, and enter domains or SharePoint Online sites you own.](media/7afaa0c7-ba53-456d-8c61-312c45e09625.png)
  
11. Next decide **Who will get these settings?** If you don't want to use the default **All Users** security group, choose **Change**, choose the security groups who will get these settings \> **Select**.
    
12. Na koniec wybierz przycisk **Dodaj**, aby zapisać zasady i zastosować je na urządzeniach. 