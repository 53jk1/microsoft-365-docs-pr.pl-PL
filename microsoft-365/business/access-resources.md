---
title: Dostęp do zasobów lokalnych z Azure urządzenia przyłączonych do AD w Microsoft 365 Business
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
ms.collection: M365-subscription-management
localization_priority: Normal
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: b0f4d010-9fd1-44d0-9d20-fabad2cdbab5
description: Dowiedz się, jak uzyskać dostęp do zasobów lokalnych, jak linia biznesowych aplikacji, udziałów plików i drukarek z usługi Active Directory Azure dołączył do urządzenia systemu Windows 10.
ms.openlocfilehash: 2be8eb16b9d17547d3bc4c3e4fe499b4c14117a4
ms.sourcegitcommit: db1dfb2df2c2f7beced3b57bc772d106c189e88a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "33660274"
---
# <a name="access-on-premises-resources-from-an-azure-ad-joined-device-in-microsoft-365-business"></a>Dostęp do zasobów lokalnych z Azure urządzenia przyłączonych do AD w Microsoft 365 Business

Dowolnych urządzeń 10 systemu Windows Azure Active Directory połączonych będą mieli dostęp do wszystkich zasobów w chmurze takie jak aplikacje pakietu Office 365 i mogą być chronione przez Microsoft 365 Business. Aby również zezwolić na dostęp do zasobów lokalnych, takich jak aplikacje linii biznesowych (LOB), udziałów plików i drukarek, należy zsynchronizować usługi Active Directory na lokalnym z usługą Active Directory za pomocą [Azure AD Connect](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect). Zobacz [Wprowadzenie do zarządzania urządzeniami w usłudze Active Directory Azure](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction) , aby dowiedzieć się więcej. 
  
## <a name="run-azure-ad-connect"></a>Uruchom Azure AD Connect

Wykonaj następujące kroki, aby włączyć w urządzeniach Azure AD dołączył do organizacji dostęp do zasobów lokalnych.
  
1. Aby zsynchronizować użytkowników, grup i kontakty z lokalną usługę Active Directory z usługą Active Directory Azure, uruchom Kreatora synchronizacji katalogu i Azure Połącz AD jako opisane w [Konfigurowanie synchronizacji katalogów usługi Office 365](https://support.office.com/article/1b3b5318-6977-42ed-b5c7-96fa74b08846).
    
2. Po zakończeniu synchronizacji katalogów, upewnij się, że urządzenia Windows 10 organizacji są Azure AD przyłączony. Ten krok jest wykonywana indywidualnie na każde urządzenie Windows 10. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie urządzeń systemu Windows dla użytkowników biznesowych 365 Microsoft](set-up-windows-devices.md) . 
    
3. Po zainstalowaniu urządzeń 10 systemu Windows Azure AD przyłączony, każdy użytkownik należy ponownie uruchomić komputer ich urządzenia i zaloguj się przy użyciu poświadczeń Microsoft 365 Business. Wszystkie urządzenia mają teraz dostęp do zasobów lokalnych, jak również.
    
Żadne dodatkowe kroki są wymagane do uzyskania dostępu do lokalnego czy zasobów dla Azure AD dołączył do urządzenia. Jest to wbudowane funkcje dostępne w systemie Windows 10. 
  
Jeśli w organizacji nie jest gotowa do wdrożenia w Azure AD dołączył do konfiguracji urządzenia opisane powyżej, warto rozważyć skonfigurowanie [połączonych AD Azure hybrydowe konfiguracji urządzenia](manage-windows-devices.md).
  
### <a name="considerations-when-joining-your-windows-devices-to-azure-ad"></a>Zagadnienia dotyczące przyłączania urządzenia z systemem Windows do Azure AD

Azure AD przyłączania urządzeń systemu Windows, który wcześniej został przyłączony do domeny czy do grupy roboczej, należy wziąć pod uwagę następujące ograniczenia:
  
- Gdy urządzenie Azure AD dołącza, tworzy nowego użytkownika bez odwoływania się do istniejącego profilu. Aby rozwiązać ten problem, trzeba ręcznie można migrować profile. Profil użytkownika zawiera informacje, takie jak Ulubione, pliki lokalne, ustawienia przeglądarki, ustawienia menu Start, itp. Najlepszym rozwiązaniem jest znaleźć narzędzia innej firmy do mapowania istniejące pliki i ustawienia na nowy profil

- Jeśli urządzenie używa obiektów zasady grupy (GPO), niektóre obiekty zasad grupy może nie mieć porównywalne [Konfiguracji usługodawcy](https://docs.microsoft.com/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers) (CSP) w usłudze Intune. Uruchom [Narzędzie MMAT](https://www.microsoft.com/download/details.aspx?id=45520) odnaleźć dostawców CSP porównywalnych dla istniejących obiektów zasad grupy.

- Użytkownicy nie będą w stanie uwierzytelnić do aplikacji, które zależą od uwierzytelniania usługi Active Directory. Radzić sobie z oceny, za pomocą starszej wersji aplikacji i rozważyć aktualizację do aplikacji, która wykorzystuje nowoczesny Auth, jeśli jest to możliwe.

- Odnajdywanie drukarki w usłudze Active Directory nie będzie działać. Aby rozwiązać ten problem, zapewnić bezpośrednie drukarki ścieżki dla wszystkich użytkowników lub wykorzystać [Hybrid Cloud Print](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy).