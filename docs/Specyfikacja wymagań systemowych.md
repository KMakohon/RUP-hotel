# Specyfikacja wymagań systemowych

## RUP-Hotel

### Autor: Katarzyna Makohon

### Korekta: Konrad Pierzyński

### Wersja: 003

### Data: 10.12.2018

### Kierownik projektu: Michał Starski

---

## Spis treści

1. **Źródła wymagań**

2. **Cele systemu**

3. **Otoczenie systemu**

4. **Przewidywane komponenty systemu**

5. **Wymagania funkcjonalne**

6. **Wymagania na dane**

7. **Sytuacje wyjątkowe**

8. **Kryteria akceptacyjne**

---

## Źródła wymagań

| INTP 001 | Zleceniodawca                                                        |
| -------- | -------------------------------------------------------------------- |
| Opis     | RUP-Hotel                                                            |
| Typ      | instytucjonalny                                                      |
| Adres    | RUP-Hotel<br/>Ulica Umultowska 86<br/>61-614 Poznań<br/>Wielkopolska |

| INTP 002 | Przedstawiciel zleceniodawcy                                               |
| -------- | -------------------------------------------------------------------------- |
| Opis     | Osoba oddelegowana przez zleceniodawcę do kontaktów z zespołem projektowym |
| Typ      | osobowy                                                                    |
| Kontakt  | Rafał Witkowski<br/>email: rmiw@amu.edu.pl                                 |

## Cele systemu

**Cele biznesowe**

| BSCE 001  | Otwarcie nowego kanału sprzedaży                                              |
| --------- | ----------------------------------------------------------------------------- |
| Opis      | Ułatwienie dostępu do oferty hotelu. Otwarcie się hotelu na nowe technologie. |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                         |
| Priorytet | wysoki                                                                        |

| BSCE 002  | Umożliwienie jak najlepszego dostosowania zasobów hotelu do wymagań klienta                                                                            |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Opis      | W momencie, w którym możliwości hotelu nie są identyczne z wymaganiami klienta system proponuje rozwiązanie, które może usatysfakcjonować obie strony. |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                                                                                                  |
| Priorytet | normalny                                                                                                                                               |

**Cele funkcjonalne**

| BSCE 003  | Umożliwienie rezerwacji pokoi przez Internet                                         |
| --------- | ------------------------------------------------------------------------------------ |
| Opis      | Umożliwienie rezerwacji pokoju o każdej porze. Ułatwienie procesu rezerwacji pokoju. |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                                |
| Priorytet | normalny                                                                             |

| BSCE 004  | Umożliwienie płatności za pokój przez Internet         |
| --------- | ------------------------------------------------------ |
| Opis      | Bezpieczny sposób realizowanie płatności internetowych |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                  |
| Priorytet | normalny                                               |

| BSCE 005  | Umożliwienie sprawdzenia dostępności pokoju przez Internet                           |
| --------- | ------------------------------------------------------------------------------------ |
| Opis      | Umożliwienie sprawdzenia dostępności, ilości oraz typu pokoi oferowanych przez hotel |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                                |
| Priorytet | normalny                                                                             |

## Otoczenie systemu

**Użytkownicy**

| USER 001  | Klient                                                                                                                                                              |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Opis      | Użytkownikiem systemu jest każda osoba chcąc zarezerwować pokój, bądź sprawdzić dostępność pokoju o danym typie                                                     |
| Potrzeby  | Rezerwacja jednego lub więcej pokoi jednego lub więcej typów.<br/>Możliwość zapłaty przez Internet.<br/>Możliwość sprawdzenia dostępności pokoi w zadanym terminie. |
| Zadania   | Stworzyć prosty interfejs umożliwiający sprawdzenie dostępności pokoju, zarezerwowanie i zapłatę za niego przez Internet                                            |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                                                                                                               |
| Priorytet | normalny                                                                                                                                                            |

**Systemy wewnętrzne**

| ISYS 001  | Baza danych                                                                                               |
| --------- | --------------------------------------------------------------------------------------------------------- |
| Opis      | Baza danych przechowująca informacje o pokojach, ich typie, cenie oraz dostępności w konkretnym terminie. |
| Potrzeby  | Struktura umożliwiająca sprawdzanie, czy w danym terminie jest dostępny pokój danego typu.                |
| Zadania   | Znajdowanie wolnych pokoi zadanego typu w zadanym terminie.                                               |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                                                     |
| Priorytet | normalny                                                                                                  |

| ISYS 002  | API                                                                                                           |
| --------- | ------------------------------------------------------------------------------------------------------------- |
| Opis      | API komunikuje się z bazą danych i systemem płatności w celu umożliwienia użytkownikowi dokonania rezerwacji. |
| Potrzeby  | Przekazywania danych klienta pomiędzy stronami rejestracji i płatności                                        |
| Zadania   | Wyswietlić użytkownikowi listę dostępnych pokoi w wybranym terminie. <br/>Dostarczyć kod płatności<br/>       |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                                                         |
| Priorytet | normalny                                                                                                      |

Pełna dokumentacja: [Dokumentacja REST API](https://github.com/michalStarski/RUP-hotel/blob/master/docs/Dokumentacja%20REST%20API.md)

## Przewidywane komponenty systemu

- Strona internetowa oferująca możliwość rezerwacji pokoju;

- Strona internetowa umożliwiająca dokonanie płatności za rezerwacje;

- Serwer hostujący stronę rezerwacji oraz stronę płatności;

- API komunikujące się między stroną rezerwacji pokoju, a stroną płatności;

- Relacyjna baza danych.

## Wymagania funkcjonalne

| FUNC 001   | **Rezerwacja pokoi**                                                                                  |
| ---------- | ----------------------------------------------------------------------------------------------------- |
| Opis       | Możliwość zarezerwowania jednego lub kilku pokoi jednego lub kilku typów dostępnych w ofercie hotelu. |
| Dotyczy    | USER 001 Klient                                                                                       |
| Powiązania |                                                                                                       |
| Źródło     | INTP 002 Przedstawiciel zleceniodawcy                                                                 |
| Priorytet  | normalny                                                                                              |

| FUNC 002   | **Płatność internetowa**                                                                  |
| ---------- | ----------------------------------------------------------------------------------------- |
| Opis       | Bezpieczne przekierowanie oraz obsłużenie płatności internetowej za zarezerwowane pokoje. |
| Dotyczy    | USER 001 Klient                                                                           |
| Powiązania | FUNC 001 Rezerwacja pokoi                                                                 |
| Źródło     | INTP 002 Przedstawiciel zleceniodawcy                                                     |
| Priorytet  | normalny                                                                                  |

| FUNC 003   | **Sprawdzenie dostępności danego pokoju w zadanym terminie.**                                         |
| ---------- | ----------------------------------------------------------------------------------------------------- |
| Opis       | Możliwość sprawdzenia czy w danym terminie hotel oferuje możliwość zarezerwowania pokoju danego typu. |
| Dotyczy    | USER 001 Klient                                                                                       |
| Powiązania | FUNC 001 Rezerwacja pokoi                                                                             |
| Źródło     | INTP 002 Przedstawiciel zleceniodawcy                                                                 |
| Priorytet  | normalny                                                                                              |

## Wymagania na dane

| TABLE 001 | **Client**                                                  |
| --------- | ----------------------------------------------------------- |
| Opis      | Klient posiada imię, nazwisko oraz numer dowodu osobistego. |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                       |
| Priorytet | normalny                                                    |

| TABLE 002 | **Room**                                                                                                                                                   |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Opis      | Istnieją pokoje jedno- dwu- oraz trzyosobowe w z góry zadanej ilości. Pokoje mają różne ceny, w zależności od tego dla jakiej ilości osób są przeznaczone. |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                                                                                                      |
| Priorytet | normalny                                                                                                                                                   |

| TABLE 003 | **Room Type**                                                                                                                                                                                                                                                         |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Opis      | Istnieją pokoje jednoosobowe. Pokoje dwuosobowe posiadające jedno podwójne łóżko. Pokoje dwuosobowe posiadające dwa oddzielne łóżka. Pokoje trzyosobowe posiadające jedno podwójne i jedno pojedyncze łóżko oraz pokoje trzyosobowe posiadające trzy oddzielne łóżka. |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                                                                                                                                                                                                                 |
| Priorytet | normalny                                                                                                                                                                                                                                                              |

| TABLE 004 | **Reservation**                                                                                                                                   |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Opis      | Rezerwacje posiadają identyfikator pokoju, identyfikator klienta oraz w jednoznaczny sposób określają okres czasu na jaki pokój jest wynajmowany. |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                                                                                             |
| Priorytet | normalny                                                                                                                                          |

Szczegółowe wymagania dotyczące danych przetwarzanych w systemie znajdują się w dokumencie [Ogólny model informacyjny](https://github.com/michalStarski/RUP-hotel/blob/master/docs/Og%C3%B3lny%20model%20informacyjny.md)

## Wymagania jakościowe

- Niezawodny, stabilny i niezakłócony kontakt.

- Bezbłędny zapis informacji do bazy danych oraz ich odczyt i wyświetlenie przez aplikację.

## Wymagania niefunkcjonalne

- Dostosowana, prosta intuicyjna strona internetowa.

- System powinień być dostępny na różnych urządzeniach np. Smartphone.

- System powinien być łatwy w opanowaniu dla ludzi z każdego przedziału wiekowego.

## Sytuacje wyjątkowe

- Brak połączenia z bazą danych w momencie połączenia strony internetowej;

  - Należy odświeżyc stronę.

- Niepodanie terminu rezerwacji;

  - Należy podać termin wyjazdu oraz przyjazdu.

- Nie podanie wszystkich danych osobowych niezbędnych do przejścia przez proces rezerwacji;

  - Należy podać poprawne brakujące dane.

## Kryteria akceptacyjne

| ACPT 001  | **Testy akceptacyjne u klienta – Poprawność przekierowań.** |
| --------- | ----------------------------------------------------------- |
| Opis      | Sprawdzenie poprawności przekierowań adresów.               |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                       |
| Priorytet | normalny                                                    |

| ACPT 002  | **Testy akceptacyjne u klienta – Poprawność działania formularza wyszukiwarki.** |
| --------- | -------------------------------------------------------------------------------- |
| Opis      | Sprawdzenie czy akcje każdego elementu formularza wyszukiwarki działa poprawnie. |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                            |
| Priorytet | normalny                                                                         |

| ACPT 003  | **Testy akceptacyjne u klienta – Poprawne wyświetlenie propozycji pokoi.** |
| --------- | -------------------------------------------------------------------------- |
| Opis      | Wyświetlenie wszystkich wolnych pokoi w danym terminie.                    |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                      |
| Priorytet | normalny                                                                   |

| ACPT 004  | **Testy akceptacyjne u klienta – Wyświetlenie komunikatu o braku pokoi.** |
| --------- | ------------------------------------------------------------------------- |
| Opis      | Wyświetlenie komunikatu o braku miejsc w wybranym terminie.               |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                     |
| Priorytet | normalny                                                                  |

| ACPT 005  | **Testy akceptacyjne u klienta – Poprawność działania formularza osobowego.** |
| --------- | ----------------------------------------------------------------------------- |
| Opis      | Sprawdzenie czy akcje każdego elementu formularza osobowego działa poprawnie. |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                         |
| Priorytet | normalny                                                                      |

| ACPT 006  | Testy akceptacyjne u klienta – Poprawność generowania kodu płatności. |
| --------- | --------------------------------------------------------------------- |
| Opis      | Sprawdzenie czy generowany kod jest zgodny z ustalonymi wymaganiami.  |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                 |
| Priorytet | normalny                                                              |

| ACPT 007  | Testy akceptacyjne u klienta – Transakcja zaakceptowana.                                                |
| --------- | ------------------------------------------------------------------------------------------------------- |
| Opis      | Przekierowanie na strone z formularzem wyszukiwarki wraz z odpowiednim komunikatem po udanej płatności. |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                                                   |
| Priorytet | normalny                                                                                                |

| ACPT 008  | Testy akceptacyjne u klienta – Transakcja odrzucona.                                                       |
| --------- | ---------------------------------------------------------------------------------------------------------- |
| Opis      | Przekierowanie na strone z formularzem wyszukiwarki wraz z odpowiednim komunikatem po nieudanej płatności. |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                                                      |
| Priorytet | normalny                                                                                                   |

| ACPT 009  | Testy akceptacyjne u klienta – Poprawne przejście do zewnętrznego systemu płatności.                                                   |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Opis      | Sprawdzenie czy po naciśnięciu przycisku "Przejdź dalej" w formularzu osobowym zostaniemy przekierowani na strone systemu RUPłatności. |
| Źródło    | INTP 002 Przedstawiciel zleceniodawcy                                                                                                  |
| Priorytet | normalny                                                                                                                               |
