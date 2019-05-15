---
title: Sprawdź poprawność ustawień ochrony aplikacji na urządzeniach Android lub iOS
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: f3433b6b-02f7-447f-9d62-306bf03638b0
description: 'Learn how to validate the Microsoft 365 Business app protection settings in your Android or iOS devices.  '
ms.openlocfilehash: 5ab16d481bd11ec31a1387a7e94d8b08bb3e0abe
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "32287394"
---
# <a name="validate-app-protection-settings-on-android-or-ios-devices"></a>Sprawdź poprawność ustawień ochrony aplikacji na urządzeniach Android lub iOS

Postępuj zgodnie z instrukcjami na kartach, aby sprawdzić poprawność ustawień ochrony aplikacji na urządzeniach Android lub iOS.
  
## <a name="androidtab"></a>[Android](#tab/)
  
### <a name="check-that-the-app-protection-settings-are-working-on-user-devices"></a>Sprawdzanie, czy na urządzeniach użytkowników działają ustawienia ochrony aplikacji

Gdy [skonfigurujesz aplikacje dla urządzeń z systemem Android](app-protection-settings-for-android-and-ios.md) w celu ochrony aplikacji, możesz wykonać czynności opisane poniżej, aby sprawdzić działanie wybranych ustawień. 
  
Najpierw upewnij się, że zasady obejmują aplikację, której działanie chcesz sprawdzić.
  
1. W [centrum administracyjnym](https://portal.office.com) usługi Microsoft 365 Business wybierz pozycję **Zasady** \> **Edytuj zasady**.
    
2. Wybierz pozycję **Zasady dotyczące aplikacji dla systemu Android** obok ustawień utworzonych podczas konfiguracji lub innych utworzonych zasad i sprawdź, czy są one zastosowane na przykład do programu Outlook. 
    
    ![Shows all the apps for which this policy protects files.](media/b3be3ddd-f683-4073-8d7a-9c639a636a2c.png)
  
### <a name="validate-require-a-pin-or-a-fingerprint-to-access-office-apps"></a>Sprawdzanie działania ustawienia Wymagaj numeru PIN lub odcisku palca w celu uzyskania dostępu do aplikacji pakietu

W okienku **Edytuj zasady** wybierz pozycję **Edytuj** obok pozycji **Kontrola dostępu do dokumentów pakietu Office**, rozwiń pozycję **Zarządzaj dostępem użytkowników do plików pakietu Office na urządzeniach przenośnych** i upewnij się, że funkcja **Wymagaj numeru PIN lub odcisku palca w celu uzyskania dostępu do aplikacji pakietu Office** jest **włączona**.
  
![Make sure that the Require a PIN or fingerprint to acces Office apps is set to On.](media/f37eb5b2-7e26-49fb-9bd6-d955d196bacf.png)
  
1. Na urządzeniu użytkownika z systemem Android otwórz aplikację Outlook i zaloguj się za pomocą poświadczeń użytkownika do usług Microsoft 365 Business.
    
2. Zostanie też wyświetlony monit o wprowadzenie numeru PIN lub użycie odcisku palca.
    
    ![Enter a PIN on your Android device to access Office apps.](media/9e8ecfee-8122-4a3a-8918-eece80344310.png)
  
### <a name="validate-reset-pin-after-number-of-failed-attempts"></a>Sprawdzanie działania ustawienia Resetuj numer PIN po określonej liczbie nieudanych prób

W okienku **Edytuj zasady** wybierz pozycję **Edytuj** obok pozycji **Kontrola dostępu do dokumentów pakietu Office**, rozwiń pozycję **Zarządzaj dostępem użytkowników do plików pakietu Office na urządzeniach przenośnych** i upewnij się, że funkcja **Resetuj numer PIN po określonej liczbie nieudanych prób** jest ustawiona na dowolną wartość (domyślnie jest to 5). 
  
1. Na urządzeniu użytkownika z systemem Android otwórz aplikację Outlook i zaloguj się za pomocą poświadczeń użytkownika do usług Microsoft 365 Business.
    
2. Wprowadź nieprawidłowy numer PIN więcej razy niż zezwalają na to obowiązujące zasady. Pojawi się komunikat z informacją o **Osiągnięto limit prób wprowadzenia numeru PIN** i monit o zresetowanie tego numeru. 
    
    ![After too many incorrect PIN attempts, you need to reset your PIN.](media/fca6fcb4-bb5c-477f-af5e-5dc937e8b835.png)
  
3. Naciśnij pozycję **Resetuj numer PIN**. Zostanie wyświetlony monit o zalogowanie się przy użyciu poświadczeń użytkownika do usług Microsoft 365 Business i ustawienie nowego numeru PIN.
    
### <a name="validate-force-users-to-save-all-work-files-to-onedrive-for-business"></a>Sprawdzanie działania ustawienia Wymuszaj na użytkownikach zapisywanie wszystkich plików służbowych w usłudze OneDrive dla Firm

W okienku **Edytuj zasady** wybierz pozycję **Edytuj** obok pozycji **Ochrona w razie utraty lub kradzieży urządzenia**, rozwiń pozycję **Chroń pliki służbowe w przypadku zgubienia lub kradzieży urządzenia** i upewnij się, że funkcja **Wymuszaj na użytkownikach zapisywanie wszystkich plików służbowych w usłudze OneDrive dla Firm** jest **włączona**.
  
![Verify that Force users to save all work files to OneDrive for Business is set to On.](media/7140fa1d-966d-481c-829f-330c06abb5a5.png)
  
1. Na urządzeniu użytkownika z systemem Android otwórz aplikację Outlook, zaloguj się za pomocą poświadczeń użytkownika do usług Microsoft 365 Business i w razie potrzeby wprowadź numer PIN.
    
2. Otwórz wiadomość e-mail zawierającą załącznik, a następnie naciśnij ikonę strzałki w dół obok informacji o załączniku.
    
    ![Tap the down arrow next to an attachment to try to save it.](media/b22573bb-91ce-455f-84fa-8feb2846b117.png)
  
    U dołu ekranu zostanie wyświetlony komunikat **Nie można zapisać na urządzeniu**. 
    
    ![Warning text that indicates cannot save a file locally to an Android.](media/52ca3f3d-7ed0-4a52-9621-4872da6ea9c5.png)
  
    > [!NOTE]
    > Zapisywanie w usłudze OneDrive dla Firm nie jest obecnie włączone dla systemu Android, więc jest tylko wyświetlana informacja o zablokowanej możliwości zapisywania lokalnie. 
  
### <a name="validate-require-user-to-sign-in-again-if-office-apps-have-been-idle-for-a-specified-time"></a>Sprawdzanie działania ustawienia Wymagaj ponownego logowania użytkownika po określonym czasie bezczynności aplikacji pakietu Office

W okienku **Edytuj zasady** wybierz pozycję **Edytuj** obok pozycji **Kontrola dostępu do dokumentów pakietu Office**, rozwiń pozycję **Zarządzaj dostępem użytkowników do plików pakietu Office na urządzeniach przenośnych** i upewnij się, że funkcja **Wymagaj ponownego logowania użytkowników po czasie bezczynności aplikacji pakietu Office** ma ustawioną dowolną wartość (domyślnie jest to 30 minut). 
  
1. Na urządzeniu użytkownika z systemem Android otwórz aplikację Outlook, zaloguj się za pomocą poświadczeń użytkownika do usług Microsoft 365 Business i w razie potrzeby wprowadź numer PIN.
    
2. Powinna zostać wyświetlona skrzynka odbiorcza aplikacji Outlook. Nie dotykaj urządzenia z systemem Android przez co najmniej 30 minut (lub inny czas dłuższy niż wartość określona w zasadach). Ekran urządzenia prawdopodobnie zostanie wygaszony.
    
3. Ponownie otwórz aplikację Outlook na urządzeniu z systemem Android.
    
4. Przed ponownym uzyskaniem dostępu do aplikacji Outlook pojawi się monit o wprowadzenie numeru PIN.
    
### <a name="validate-protect-work-files-with-encryption"></a>Sprawdzanie działania ustawienia Chroń pliki służbowe przy użyciu szyfrowania

W okienku **Edytuj zasady** wybierz pozycję **Edytuj** obok pozycji **Ochrona w razie utraty lub kradzieży urządzenia**, rozwiń pozycję **Chroń pliki służbowe w przypadku zgubienia lub kradzieży urządzenia** i upewnij się, że funkcja **Chroń pliki służbowe przy użyciu szyfrowania** jest **włączona**, a funkcja **Wymuszaj na użytkownikach zapisywanie wszystkich plików służbowych w usłudze OneDrive dla Firm** jest **wyłączona**.
  
1. Na urządzeniu użytkownika z systemem Android otwórz aplikację Outlook, zaloguj się za pomocą poświadczeń użytkownika do usług Microsoft 365 Business i w razie potrzeby wprowadź numer PIN.
    
2. Otwórz wiadomość e-mail z załączonymi kilkoma plikami obrazu.
    
3. Naciśnij ikonę strzałki w dół obok informacji o załączniku, aby go zapisać.
    
    ![Tap the down arrow to save the figure file to the Android device.](media/08a9e21e-4022-45d5-acff-59cface651e7.png)
  
4. Może pojawić się monit o zezwolenie programowi Outlook na dostęp do zdjęć, multimediów i plików na urządzeniu. Naciśnij pozycję **Zezwalaj**.
    
5. U dołu ekranu wybierz pozycję **Zapisz na urządzeniu**, a następnie otwórz aplikację **Galeria**. 
    
6. Na liście powinno zostać wyświetlone zaszyfrowane zdjęcie (lub kilka zdjęć, jeśli zapisano ich więcej). Może ono być wyświetlane na liście obrazów w postaci szarego kwadratu z białym wykrzyknikiem w białym okręgu w środku szarego kwadratu.
    
    ![An encrypted image file in the Gallery app.](media/25936414-bd7e-421d-824e-6e59b877722d.png)
  
## <a name="iostab"></a>[iOS](#tab/)
  
### <a name="check-that-the-app-protection-settings-are-working-on-user-devices"></a>Sprawdzanie, czy na urządzeniach użytkowników działają ustawienia ochrony aplikacji

Gdy [skonfigurujesz aplikacje dla urządzeń z systemem iOS](app-protection-settings-for-android-and-ios.md) w celu ochrony aplikacji, możesz wykonać czynności opisane poniżej, aby sprawdzić działanie wybranych ustawień. 
  
Najpierw upewnij się, że zasady obejmują aplikację, której działanie chcesz sprawdzić.
  
1. W [centrum administracyjnym](https://portal.office.com) usługi Microsoft 365 Business wybierz pozycję **Zasady** \> **Edytuj zasady**.
    
2. Wybierz pozycję **Zasady aplikacji dla systemu iOS** obok ustawień utworzonych podczas konfiguracji lub innych utworzonych zasad i sprawdź, czy są one wymuszane na przykład w programie Outlook. 
    
    ![Shows all the apps for which this policy protects files.](media/842441b8-e7b1-4b86-9edd-d94d1f77b6f4.png)
  
### <a name="validate-require-a-pin-to-access-office-apps"></a>Sprawdzanie działania ustawienia Wymagaj numeru PIN w celu uzyskania dostępu do aplikacji pakietu Office

W okienku **Edytuj zasady** wybierz pozycję **Edytuj** obok pozycji **Kontrola dostępu do dokumentów pakietu Office**, rozwiń pozycję **Zarządzaj dostępem użytkowników do plików pakietu Office na urządzeniach przenośnych** i upewnij się, że funkcja **Wymagaj numeru PIN lub odcisku palca w celu uzyskania dostępu do aplikacji pakietu Office** jest **włączona**.
  
![Make sure that the Require a PIN or fingerprint to acces Office apps is set to On.](media/f37eb5b2-7e26-49fb-9bd6-d955d196bacf.png)
  
1. Na urządzeniu użytkownika z systemem iOS otwórz aplikację Outlook i zaloguj się za pomocą poświadczeń użytkownika do usługi Microsoft 365 Business.
    
2. Zostanie też wyświetlony monit o wprowadzenie numeru PIN lub użycie odcisku palca.
    
    ![Enter a PIN on your IOS device to access Office apps.](media/06fc5cf3-9f19-4090-b23c-14bb59805b7a.png)
  
### <a name="validate-reset-pin-after-number-of-failed-attempts"></a>Sprawdzanie działania ustawienia Resetuj numer PIN po określonej liczbie nieudanych prób

W okienku **Edytuj zasady** wybierz pozycję **Edytuj** obok pozycji **Kontrola dostępu do dokumentów pakietu Office**, rozwiń pozycję **Zarządzaj dostępem użytkowników do plików pakietu Office na urządzeniach przenośnych** i upewnij się, że funkcja **Resetuj numer PIN po określonej liczbie nieudanych prób** jest ustawiona na dowolną wartość (domyślnie jest to 5). 
  
1. Na urządzeniu użytkownika z systemem iOS otwórz aplikację Outlook i zaloguj się za pomocą poświadczeń użytkownika do usługi Microsoft 365 Business.
    
2. Wprowadź nieprawidłowy numer PIN więcej razy niż zezwalają na to obowiązujące zasady. Pojawi się komunikat z informacją o **Osiągnięto limit prób wprowadzenia numeru PIN** i monit o zresetowanie tego numeru. 
    
    ![After too many incorrect PIN attempts, you need to reset your PIN.](media/fab5c089-a4a5-4e8d-8c95-b8eed1dfa262.png)
  
3. Naciśnij przycisk **OK**. Zostanie wyświetlony monit o zalogowanie się przy użyciu poświadczeń użytkownika do usług Microsoft 365 Business i ustawienie nowego numeru PIN.
    
### <a name="validate-force-users-to-save-all-work-files-to-onedrive-for-business"></a>Sprawdzanie działania ustawienia Wymuszaj na użytkownikach zapisywanie wszystkich plików służbowych w usłudze OneDrive dla Firm

W okienku **Edytuj zasady** wybierz pozycję **Edytuj** obok pozycji **Ochrona w razie utraty lub kradzieży urządzenia**, rozwiń pozycję **Chroń pliki służbowe w przypadku zgubienia lub kradzieży urządzenia** i upewnij się, że funkcja **Wymuszaj na użytkownikach zapisywanie wszystkich plików służbowych w usłudze OneDrive dla Firm** jest **włączona**.
  
![Verify that Force users to save all work files to OneDrive for Business is set to On.](media/7140fa1d-966d-481c-829f-330c06abb5a5.png)
  
1. Na urządzeniu użytkownika z systemem iOS otwórz aplikację Outlook i zaloguj się za pomocą poświadczeń użytkownika do usługi Microsoft 365 Business. W razie potrzeby wprowadź kod PIN.
    
2. Otwórz wiadomość e-mail z załącznikiem, otwórz ten załącznik i wybierz pozycję **Zapisz** u dołu ekranu. 
    
    ![Tap the Save option after you open an attachment to try to save it.](media/b419b070-1530-4f14-86a8-8d89933a2b25.png)
  
3. Powinna być widoczna tylko jedna opcja umożliwiająca zapisanie pliku w usłudze OneDrive dla Firm. Jeśli jej nie ma, naciśnij opcję **Dodaj konto** i wybierz pozycję **OneDrive dla Firm** na ekranie **Dodawanie konta magazynu**. Zaloguj się do usługi Microsoft 365 Business przez wprowadzenie poświadczeń użytkownika. 
    
    Naciśnij przycisk **Zapisz** i wybierz opcję **OneDrive dla Firm**.
    
### <a name="validate-require-user-to-sign-in-again-if-office-apps-have-been-idle-for-a-specified-time"></a>Sprawdzanie działania ustawienia Wymagaj ponownego logowania użytkownika po określonym czasie bezczynności aplikacji pakietu Office

W okienku **Edytuj zasady** wybierz pozycję **Edytuj** obok pozycji **Kontrola dostępu do dokumentów pakietu Office**, rozwiń pozycję **Zarządzaj dostępem użytkowników do plików pakietu Office na urządzeniach przenośnych** i upewnij się, że funkcja **Wymagaj ponownego logowania użytkowników po czasie bezczynności aplikacji pakietu Office** ma ustawioną dowolną wartość (domyślnie jest to 30 minut). 
  
1. Na urządzeniu użytkownika z systemem iOS otwórz aplikację Outlook i zaloguj się za pomocą poświadczeń użytkownika do usługi Microsoft 365 Business. W razie potrzeby wprowadź kod PIN.
    
2. Powinna zostać wyświetlona skrzynka odbiorcza aplikacji Outlook. Nie dotykaj urządzenia z systemem iOS przez co najmniej 30 minut (lub inny czas, który jest dłuższy od wartości określonej w zasadach). Ekran urządzenia prawdopodobnie zostanie wygaszony.
    
3. Ponownie otwórz aplikację Outlook na urządzeniu z systemem iOS.
    
4. Przed ponownym uzyskaniem dostępu do aplikacji Outlook pojawi się monit o wprowadzenie numeru PIN.
    
### <a name="validate-protect-work-files-with-encryption"></a>Sprawdzanie działania ustawienia Chroń pliki służbowe przy użyciu szyfrowania

W okienku **Edytuj zasady** wybierz pozycję **Edytuj** obok pozycji **Ochrona w razie utraty lub kradzieży urządzenia**, rozwiń pozycję **Chroń pliki służbowe w przypadku zgubienia lub kradzieży urządzenia** i upewnij się, że funkcja **Chroń pliki służbowe przy użyciu szyfrowania** jest **włączona**, a funkcja **Wymuszaj na użytkownikach zapisywanie wszystkich plików służbowych w usłudze OneDrive dla Firm** jest **wyłączona**.
  
1. Na urządzeniu użytkownika z systemem iOS otwórz aplikację Outlook i zaloguj się za pomocą poświadczeń użytkownika do usługi Microsoft 365 Business. W razie potrzeby wprowadź kod PIN.
    
2. Otwórz wiadomość e-mail z załączonymi kilkoma plikami obrazu.
    
3. Naciśnij załącznik i wybierz pod nim opcję **Zapisz**. 
    
4. Otwórz aplikację **Zdjęcia** na ekranie głównym. Zobaczysz zapisane zdjęcie (lub kilka, jeśli zapiszesz ich więcej) w zaszyfrowanej postaci. 
    
---
