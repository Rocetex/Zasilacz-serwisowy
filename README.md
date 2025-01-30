# Zasilacz-serwisowy
Zasilacz laboratoryjny z zastosowaniem do serwisu urządzeń elektronicznych będący moją pracą inżynierską.
## Wstęp:
Projekt polegał na opracowaniu i wykonaniu zasilacza laboratoryjnego z zastosowaniem do serwisu urządzeń elektronicznych. Zasilacz zaprojektowany został jako urządzenie o wysokiej sprawności i niskich wartościach tętnień wyjściowych. Ważnym aspektem urządzenia jest możliwość komunikacji z wykorzystaniem magistrali UART. Zasilacz został zbudowany jako dwie przetwornice DC-DC zsynchronizowane z sobą. Wykorzystany model przetwornicy to LM5145.

## Założenia projektu:
W ramach projektu przyjęto następujące założenia, które określają wymagania funkcjonalne oraz techniczne projektowanego zasilacza laboratoryjnego:
* maksymalne napięcie wyjściowe równe 25 V,
* maksymalny prąd wyjściowy 10 A,
* sprawność przetwornicy co najmniej 80% przy obciążeniu 1 A,
* komunikacja i sterowanie z wykorzystaniem zewnętrznego urządzenia,
* sterowanie napięciem wyjściowym w zakresie od 0.5 do 25 V,
* zabezpieczenie w postaci ograniczenia prądowego
* możliwość pomiaru napięcia wyjściowego:
  + w zakresie napięcia do 5 V błąd względny poniżej 4% wartości mierzonej,
  + w zakresie napięcia od 5 do 25 V błąd względny poniżej 2% wartości mierzonej,
* możliwość pomiaru prądu z błędem do 3% wartości mierzonej,
* tętnienia napięcia wyjściowego poniżej 100 mV.
  
## Schemat blokowy i projekt układu
Jako zasilacz zdecydowano się na przetwornicę impulsową. W celu jej zasilania zastosowano zasilacz impulsowy, zmieniający napięcie wejściowe 230 V AC na bezpiecznie 29 V DC. W schemacie zastosowano dwa układu przetwornic połączone równolegle o maksymalnym napięciu wyjściowym 25 V i maksymalnym prądzie wyjściowym 5 A co w rezultacie daje wartość 10 A. Napięcie z przekształtników następnie podawane jest na układ do kompensacji zer i biegunów w celu stabilizacji ich charakterystyki amplitudowej. Jako filtr napięcia wyjściowego zastosowano parę Sziklaiego, z którego napięcie podawane jest na wyjście urządzenia jak również na układ dopasowujący wartość napięcia do pomiaru. Pomiędzy wyjściem masy zasilacza, a rzeczywistą masą urządzenia dodano układ konwersji prądu na napięcie. W urządzeniu zastosowano mikrokontroler, pełniący funkcję pomiarową, jak również odpowiedzialną za komunikację z użytkownikiem oraz zarządzanie pracą urządzenia, umożliwiając zmianę parametrów napięcia i prądu wyjściowego. Sterowanie umożliwiają dwa układy odpowiedzialne za sterowanie poprzez porównanie napięć z mikrokontrolera z napięciami odniesienia przetwornicy. Jako interfejs użytkownika zastosowano wyświetlacz alfanumeryczny pokazujący wartości napięcia i prądu wyjściowego. Urządzenie również umożliwia sterowanie parametrami poprzez podłączenie go do zewnętrznego komputera z wykorzystaniem przewodu USB i wirtualnego portu COM.

![image](https://github.com/user-attachments/assets/cce6aa5b-7759-4b47-b326-5169f5f1a568)

## Schematy poszczególnych bloków funkcjonalnych:
### Układ przetwornicy:
![image](https://github.com/user-attachments/assets/e02f8832-dded-444e-83c9-854f93c814df)
### Blok sprzężenia zwrotnego oraz kompensatora 3 typu:
![image](https://github.com/user-attachments/assets/66211fc0-6dc3-4049-ad74-e2f8dcb2d991)
### Filtracja napięcia wyjściowego z wykorzystaniem pary Sziklaia:
![image](https://github.com/user-attachments/assets/d9ada3ab-ea25-4972-96f7-424ab7ca9310)
### Pomiar prądu wyjściowego:
![image](https://github.com/user-attachments/assets/d43cef15-db57-4aa8-84bb-317e603736a4)
### Układ sterowania napięciem i prądem wyjściowym:
![image](https://github.com/user-attachments/assets/38afad43-1507-49fb-aff9-dd97fcbc424b)
![image](https://github.com/user-attachments/assets/80393d93-d8b2-41a0-82c2-b9f91cdc1722)

## Prezentacja płytki PCB oraz gotowego urządzenia:
![image](https://github.com/user-attachments/assets/00de83dc-907a-4b40-9ccb-063cf437151e)
![image](https://github.com/user-attachments/assets/0443ab24-bb8c-4500-b53a-08e7defc5b48)

## Podsumowanie:

Poniżej zamieszczono krótkie podsumowanie zrealizowanego projektu wraz z napotkanymi problemami. Dokładny opis urządzenia, uruchomienia oraz przetestowania urządzenia znajduje się w dołączonym pliku PDF.
Pomiary wykazały, iż urządzenie spełnia zdecydowaną większość założeń projektowych. Zasilacz osiąga maksymalne napięcie wyjściowe równe 25 V, jak również umożliwia komunikację z urządzeniem zewnętrznym w celu pomiaru oraz nastawienia parametrów urządzenia. Urządzenie prawidłowo ogranicza wartość prądu wyjściowego. Warto podkreślić wysoką sprawność układu przetwornic, która dla napięcia 25 V i prądu wyjściowego 1 A wynosi powyżej 92%. Maksymalna zmierzona wartość sprawności urządzenia wyniosła aż 98%. Również dużym atutem są niskie tętnienia na wyjściu przetwornic, wynoszące niecałe 30 mV. Analiza tętnień dla układu z jedną przetwornicą oraz konfiguracji z dwiema przetwornicami wykazała znaczną redukcję tętnień w przypadku drugiego układu. Przedstawiona analiza potwierdza główną część tezy pracy, iż zastosowanie kaskadowego układu kondycjonującego poziom napięcia i prądu wyjściowego zasilacza impulsowego ograniczy wpływ zastosowanych układów konwersji energii. Istotnym aspektem jest również dokładność pomiaru napięcia i prądu mieszcząca się z założonych wartościach oraz poprawne działanie ograniczenia prądowego.

### Napotkane błędy:
Jednym z nich jest sterowanie napięciem wyjściowym przetwornicy. Ze względu ograniczonego czasu nie wykonano niezbędnych zmian w układzie regulacji napięcia. Zastosowanie układu użytego w celu regulacji prądu wyjściowego umożliwiłoby poprawne sterowanie napięciem wyjściowym. W pracy nie przeprowadzono pomiaru dla zakładanej maksymalnej wartości prądu wyjściowego równego 10 A, z uwagi na nieprawidłowość pracy układu dla prądów powyżej 6 A. Problem wynika z rozbieżności w pracy przetwornic, co może być spowodowane faktem, iż jeden układ załączał się wcześniej w porównaniu drugiego układu przetwornicy. Rozwiązaniem może okazać się zwiększenie czasu uruchomienia przetwornic oraz odseparowanie układów sprzężenia zwrotnego dla każdej z przetwornic. Przeprowadzone pomiary prądu wyjściowego o wartości około 4 A dla pojedynczego układu przetwornicy wykazały, że zastosowane układy w odpowiedniej konfiguracji umożliwiają osiągnięcie założonej wartości 10 A.
