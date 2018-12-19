# Plan testów

## RUP-Hotel

### Autor: Mateusz Lesiecki

### Korekta: Katarzyna Makohon

### Wersja: 002

### Data: 10.12.2018

### Kierownik Projektu: Michał Starski

---

## Spis treści:

1. **Wstęp**

2. **Testowane obiekty**

3. **Funkcjonalność do przetestowania**

4. **Funkcjonalność nietestowana**

5. **Zespół**

6. **Strategia testowania**

7. **Testy automatyczne**

8. **Środowisko testowe**

9. **Standardy**

10. **Odnośniki**

---

## Wstęp:

#### Wprowadzenie

„System rezerwacji pokoi hotelowych dla RUP Hotel” jest to aplikacja internetowa pozwalajaca zarezerwować pokoje w "RUP Hotel" na określony czas pobytu oraz dokonać natychmiastowej zapłaty za pobyt w hotelu w niezależnym systemie płatnosci "RUPłatności" znajdujący się pod adresem [46.187.239.247:1897](http://46.187.239.247:1897/). W Systemie będą dostępne 1, 2 i 3 osobowe pokoje z różną konfiguracją łóżek. Projekt jest tworzony w metodyce RUP.

#### Cel

Faza testowania w projekcie „System rezerwacji pokoi hotelowych dla RUP Hotel”, ma na celu znalezienie oraz usunięcie błędów powstałych podczas tworzenie Systemu, ma on rownież za zadanie zapewnienie jak najwyższej jakości produktu. Testy powinny zostać wykonywane od początku tworzenia Systemu w celu wczesnego wykrycia nieporządanych zachowań, ma to znaczenie na końcowy efekt całego projektu. Celem tego dokumentu jest ułatwienie pracy ludziom odpowiedzialnym za przeprowadzenie testów oraz całego procesu testowania.

---

## Opis testów

#### Obiekt: Aplikacja internetowa - Wyszukiwarka

Jest to pierwsza część aplikacji internetowej znajdującej się pod adresem [pacific-tor-53766.herokuapp.com](http://pacific-tor-53766.herokuapp.com/), składa sie ona z dwóch głównych sekcji, pierwsza z nich to sekcja wyboru daty pobytu w hotelu a druga to sekcja umożliwiająca nam wybór liczby przyjezdnych gości oraz wybrać pokoje z listy dostępnych pokoi. W skład tej części wchodzą:

**Data pobytu:**

- Data przyjazdu - pole typu kalendarz

- Data wyjazdu - pole typu kalendarz

**Wybór pokoi:**

- Łączna kwota - pole typu Label

- Przejdź dalej - przycisk

- Liczba gości - lista rozwijana

- Lista składająca się z dostępnych pokoi - tabela

#### Obiekt: Aplikacja internetowa - Formularz osobowy

Jest to drugi widok aplikacji internetowej znajdujący się pod adresem [pacific-tor-53766.herokuapp.com/client-data](http://pacific-tor-53766.herokuapp.com/client-data),  (niezbędne jest przejście przez pierwszy widok), jej celem jest umożliwienie klientowi "RUP Hotel" wprowadzenia danych niezbędnych do ukończenia rezerwacji pokoju hotelowego oraz generuje kod niezbędny do potwierdzenia płatności tym samym całego procesu rezerwacji. W skład tej części wchodzi jedna głowna sekcja, której elementami są:

- Formularz składający się z 3 pól tekstowych (Imie, Nazwisko, Numer dowodu)

- Generuj kod płatności – przycisk

- Twoje dane zostały/niezostały zaakceptowane – pole typu Label

- Przejdź do płatności – przycisk

Po naciśnięciu przycisku przejdź do płatności, zostajemy przekierowni do niezależnego systemu płatności "RUPłatności", gdzie finalizujemy naszą rezerwację wpisując wygenerowany na stronie kod. Po zatwierdzeniu serwis "RUPłatności" przekierowuje nas na stronę początkową wraz z komunikatem o rezultacie rezerwacji.

---

## Funkcjonalność do przetestowania

System rezerwacji pokoi hotelowych dla "RUP Hotel" ma umożliwić użytkownikowi zarezerwowanie w wybranym przez niego terminie dowolnej ilośći pokoi w każdym z możliwych typów. Na bieżąco aktualizowana jest kwota należna do zapłaty, a na koniec generowany jest unikalny kod niezbędny do potwierdzenia płatności.

#### Pierwsza część aplikacji

- Funkcjonalność wyszukiwarki

#### Druga część aplikacji

- Pola tekstowe z formularza

- Poprawność wyświetlania statusu wypełnionych danych

- Poprawność generowania kodu do płatności 

- Funkcjonalność przycisku przejdz do płatności

#### Dodatkowo

- Poprawne załadowanie strony w przeglądarce

- Poprawność dodania rezerwacji do bazy danych

- Niedodanie rezerwacji do bazy w przypadku niepowodzenia płatności

- Generowanie poprawnego kodu płatności (zgodnego z wymaganiami)

- Przekierowanie na stronę systemu płatności

- Sprawdzenie czy wejście na "[pacific-tor-53766.herokuapp.com/result?success=true](http://pacific-tor-53766.herokuapp.com/result?success=true)" doda do bazy rezerwacje

- Przekierowanie na stornę poczatkową po udanej rezerwacji

- Przekierowanie na stronę początkową po nieudanej rezerwacji wraz z odpowiednim komunikatem

- Zgodność wyglądu strony razem z projektem GUI

---

## Funkcjonalność nietestowana

- Wszystkie napisy tekstowe

---

## Zespół

#### Podział obowiązków

| Osoba                 | Rola                            |
|:---------------------:|:-------------------------------:|
| Michał Starski        | Kierownik projektu, Programista |
| Maciej Więcek         | Programista                     |
| Katarzyna Makohon     | Analityk Systemowy              |
| Mateusz Lesiecki      | Menadżer testów                 |
| Bartłomiej Włodarczyk | Przegląd projektu               |
| Jędrzej Nowak         | Analityk Systemowy              |
| Krystian Kabat        | Integrator                      |
| Dominika Augustyniak  | Inżynier procesu                |
| Ada Andrzejczak       | Projektant GUI                  |
| Adam Ćwikliński       | Administrator Systemu           |
| Patrycja Łaźna        | Architekt Systemu               |
| Konrad Pierzyński     | Programista                     |

#### Harmonogram

| Nazwa testów | Data rozpoczęcia | Data zakończenia | Wykonał |
| ------------ | ---------------- | ---------------- | ------- |
| Jednostkowe  |                  |                  |         |
| Integracyjne |                  |                  |         |

---

## Strategia testowania

#### Testy jednostkowe

Projekt zakłada pokrycie testami jednostkowymi ~90% kodu. Testy jedndostkowe pisane są przez zespół programistów.

#### Testy funkcjonalne

**Nazwa przypadku testowego:** Załadowanie strony zgodnej z projetkem GUI.

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) .

**Wymagania:** Wyświetlenie systemu rezerwacji pod adresem [pacific-tor-53766.herokuapp.com](http://pacific-tor-53766.herokuapp.com/) .

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                             | Oczekiwany rezultat                                                                   |
|:-------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------------------:|
| 1. Wpisz w polu adresu [pacific-tor-53766.herokuapp.com](https://pacific-tor-53766.herokuapp.com) | Zostanie załadowana strona systemu rezerwacji pokoi hotelowych, zgoda z projektem GUI |

**Nazwa przypadku testowego:** Poprawne wybranie terminów przyjazdu i wyjazdu z hotelu.

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com](https://pacific-tor-53766.herokuapp.com), formularz został załadowany poprawnie oraz wszyskie pola są widoczne i dostępne do edycji.    

**Wymagania:** Prawidłowe wybranie terminu przyjazdu i wyjazdu.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                              | Oczekiwany rezultat                                         |
|:------------------------------------------------------------------------------------------------------------------:|:-----------------------------------------------------------:|
| 1. Wybierz strzałkę w polu kalendarzowym "przyjazd" i ustaw datę poźniejszą od dzisiejszej o 2 dni                 | Wartość pola kalendarzowego wskazuje wybraną przez nas datę |
| 2. Wybierz strzałkę w polu kalendarzowym "wyjazd" i ustaw datę poźniejszą od dzisiejszej o 5 dni od daty przyjazdu | Wartość pola kalendarzowego wskazuje wybrną przez nas datę  |

**Nazwa przypadku testowego:** Wybranie daty przyjazdu która minęła

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com](https://pacific-tor-53766.herokuapp.com), formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji.    

**Wymagania:** Prawidłowe wybranie terminu przyjazdu i wyjazdu.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                              | Oczekiwany rezultat                                         |
|:------------------------------------------------------------------------------------------------------------------:|:-----------------------------------------------------------:|
| 1. Wybierz strzałkę w polu kalendarzowym "przyjazd" i ustaw datę wcześniejszą od dzisiejszej o 3 dni               | Wartość pola kalendarzowego wskazuje wybraną przez nas datę |
| 2. Wybierz strzałkę w polu kalendarzowym "wyjazd" i ustaw datę poźniejszą od dzisiejszej o 5 dni od daty przyjazdu | Wartość pola kalendarzowego wskazuje wybrną przez nas datę  |
| 3. Z listy rozwijanej wybierz wartość z przedziału [1- 10] gości                                                   | Ustawienie w polu listy rozwijanej wybranej wartości        |
| 4. Naciśnij przycisk "Szukaj"                                                                                      | Komunikat "Data: Data przyjazdu już minęła"                 |

**Nazwa przypadku testowego:** Wybranie daty przyjazdu poźniejszej niz wyjazdu

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com](https://pacific-tor-53766.herokuapp.com) formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji.

**Wymagania:** Prawidłowe wybranie terminu przyjazdu i wyjazdu.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                              | Oczekiwany rezultat                                               |
|:--------------------------------------------------------------------------------------------------:|:-----------------------------------------------------------------:|
| 1. Wybierz strzałkę w polu kalendarzowym "przyjazd" i ustaw date poźniejszą o 7 dni od dzisiejszej | Wartość pola kalendarzowego wskazuje wybraną przez nas datę       |
| 2. Wybierz strzałkęw polu kalendarzowym "wyjazd" i ustaw datę poźniejszą o 3 dni od dzisiejszej    | Wartość pola kalendarzowego wskazuje wybrną przez nas datę        |
| 3. Z listy rozwijanej wybierz wartość z przedziału [1- 10] gości                                   | Ustawienie w polu listy rozwijanej wybranej wartości              |
| 4. Naciśnij przycisk "Szukaj"                                                                      | Komunikat "Data: Data wyjazdu musi być większa od daty przyjazdu" |

**Nazwa przypadku testowego:** Poprawne wyświetlenie opcji pokojowych dla określonej liczby gośći (Istnieje możliwość pomieszczenia wszystkich gości)

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com](https://pacific-tor-53766.herokuapp.com), formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji.

**Wymagania:** Prawidłowe wyświetlenie dostępnych pokoi.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                          | Oczekiwany rezultat                                               |
|:------------------------------------------------------------------------------:|:-----------------------------------------------------------------:|
| 1. Wybierz w polu kalendarzowym "przyjazd" z dowolną poprawną wartość          | Wartość pola kalendarzowego wskazuje wybraną przez nas datę       |
| 2. Wybierz w polu "wyjazd" dowolną poprawną datę późniejszą od tej z punktu 1. | Wartość pola kalendarzowego wskazuje wybraną przez nas datę       |
| 3. Z listy rozwijanej wybierz wartość z przedziału [1- 10] gości               | Ustawienie w polu listy rozwijanej wybranej wartości              |
| 4. Naciśnij przycisk "Szukaj"                                                  | Wyświetlenie wszystkich możliwych dostępnych w tym terminie pokoi |

**Nazwa przypadku testowego:** Poprawne wyświetlenie komunikatu o braku miejsc w wybranym terminie (Nie istnieje możliwość pomieszczenia wszystkich gości)

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com](https://pacific-tor-53766.herokuapp.com), formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji.

**Wymagania:** Prawidłowe wyświetlenie dostępnych pokoi.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                 | Oczekiwany rezlutat                                                                                     |
|:-----------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------------------------------------:|
| 1. Wybierz w polu kalendarzowym "przyjazd" dowolną poprawną wartość starszą lub równą dziejszej dacie | Wartość pola kalendarzowego wskazuje wybraną przez nas datę                                             |
| 2. Wybierz w polu "wyjazd" dowolną poprawną datę późniejszą od tej z punktu 1.                        | Wartość pola kalendarzowego wskazuje wybraną przez nas datę                                             |
| 3. Z listy rozwijanej wybierz wartość z przedzialu [1- 10] gości                                      | Ustawienie w polu listy rozwijanej wybranej wartości                                                    |
| 4. Naciśnij przycisk "Szukaj"                                                                         | Wyświetlenie komunikatu informującego ze w danym okresie hotel nie może pomieścić wybranej liczby gości |

**Nazwa przypadku testowego:** Poprawne wyświetlenie informacji o braku połączenia z bazą danych

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com](https://pacific-tor-53766.herokuapp.com), formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji, brak połączenia z bazą danych.

**Wymagania:** Prawidłowe wyświetlenie dostępnych pokoi.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                | Oczekiwany rezultat                                                                          |
|:----------------------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------:|
| 1. Wybierz w polu kalendarzowym "przyjazd"dowolną poprawną wartość starszą lub równą dziejszej dacie | Wartość pola kalendarzowego wskazuje wybraną przez nas datę                                  |
| 2. Wybierz w polu "wyjazd" dowolną poprawną datę późniejszą od tej z punktu 1.                       | Wartość pola kalendarzowego wskazuje wybraną przez nas datę                                  |
| 3. Z listy rozwijanej wybierz wartość z przedzialu [1- 10] gości                                     | Ustawienie w polu listy rozwijanej wybranej wartości                                         |
| 4. Naciśnij przycisk "Szukaj"                                                                        | Wyświetlenie komunikatu informującego o niemożliwości w danej chwilii załadowaniu propozycji |

**Nazwa przypadku testowego:** Poprawne wyświetlenie kwoty należnej do zapłaty

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com](https://pacific-tor-53766.herokuapp.com),  formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji.

**Wymagania:** Prawidłowe wyświetlenie kwoty należnej do zapłaty.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                                            | Oczekiwany rezultat                                                                                                      |
|:--------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------:|
| 1. Wybierz w polu kalendarzowym "przyjazd" dowolną poprawną wartość                                                              | Wartość pola kalendarzowego wskazuje wybraną przez nas datę                                                              |
| 2. Wybierz w polu "wyjazd" dowolną poprawną datę późniejszą od tej z punktu 1.                                                   | Wartość pola kalendarzowego wskazuje wybraną przez nas datę                                                              |
| 3. Z listy rozwijanej wybierz ilość gości z przedziału [1-10]                                                                    | Ustawienie w polu listy rozwijanej wybranej wartości                                                                     |
| 4. Naciśnij przycisk "Szukaj"                                                                                                    | Wyświetlenie wszystkich możliwych dostępnych w tym terminie pokoi                                                        |
| 5. Z listy dostępnych pokoi wybierz pokoje tak żeby ilość gości wybrana w kroku 3 była rowna liczbie miejsc w wybranych pokojach | Podświetlenie wybranych pokoi oraz ustawienie wartosci Labela "Łączna kwota: " na "Łączna kwota: (suma wybranych pokoi)" |

**Nazwa przypadku testowego:** Poprawne wypełnienie formularza wyszukiwarki

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com](https://pacific-tor-53766.herokuapp.com), formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji.

**Wymagania:** Prawidłowe wypełnienie danych związanych z formularzem wyszukiwarki.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                                               | Oczekiwany rezultat                                                                                                                                                                                 |
|:-----------------------------------------------------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| 1. Wybierz w polu kalendarzowym "przyjazd" dowolną poprawną wartość                                                                 | Wartość pola kalendarzowego wskazuje wybraną przez nas datę                                                                                                                                         |
| 2. Wybierz w polu ""wyjazd" dowolną poprawną datę późniejszą od tej z punktu 1.                                                     | Wartość pola kalendarzowego wskazuje wybraną przez nas datę                                                                                                                                         |
| 3. Z listy rozwijanej wybierz dowolną liczbe gości z przedziału [1-10]                                                              | Ustawienie w polu listy rozwijanej wybranej wartości                                                                                                                                                |
| 4. Naciśnij przycisk "Szukaj"                                                                                                       | Wyświetlenie wszystkich możliwych dostępnych w tym terminie pokoi                                                                                                                                   |
| 5. Z listy dostępnych pokoi wybierz pozycje tak żeby liczba miejsc w wybranych pokojach byla równa liczbie osob wybranych w kroku 3 | Zaktualizowanie Labelu "Łączna kowata: (suma wybranych pokoi)"                                                                                                                                      |
| 6. Naciśnij przycisk "Przejdź dalej"                                                                                                | Przekierowanie na [pacific-tor-53766.herokuapp.com/client-data](https://pacific-tor-53766.herokuapp.com/client-data) oraz zostaje załadowana strona zgodna z projektem GUI dla dla drugiego widoku. |

**Nazwa przypadku testowego:** Poprawne wypełnienie formularza osobowego

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com/client-data](https://pacific-tor-53766.herokuapp.com/client-data), formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji, zostały wybrane prawidłowe daty oraz pokoje.

**Wymagania:** Prawidłowe wypełnienie formularza osobowego.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                                                                 | Oczekiwany rezultat                                                                                                            |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------------:|
| 1.  Wpisz w polu tekstowym "Imię" dowolony ciąg składający sie z liter o długości minimum 2                                                           | W polu tekstowym "Imię" pojawi sie wpisany tekst                                                                               |
| 2.  Wpisz w polu tekstowym "Nazwisko" dowolony ciąg składający sie z liter o długości minimum 2                                                       | W polu tekstowym "Nazwisko" pojawi sie wpisany tekst                                                                           |
| 3. Wpisz w polu tekstowym "Numer dowodu osobistego" dowolony poprawny (poprawność sumy kontrolnej) ciąg składający sie z 3 liter alfabetu oraz 6 cyfr | W polu tekstowym "Numer dowodu osobistego" pojawi sie wpisany tekst                                                            |
| 4. Naciśnij przycisk "Generuj kod płatności"                                                                                                          | Zostaje wygenerowany zgodnie z przyjętymi założeniami i wyswietlony w szarym prostokącie unikatowy kod potwierdzający płatność |

**Nazwa przypadku testowego:** Błędne wypełnienie pola tekstowego "Imię" (Podanie niedozwolonych znaków)

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com/client-data](https://pacific-tor-53766.herokuapp.com/client-data), formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji, zostały wybrane prawidłowe daty oraz pokoje.

**Wymagania:** Prawidłowe wypełnienie formularza osobowego.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                                                                 | Oczekiwany rezultat                                                 |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------:|
| 1.  Wpisz w polu tekstowym "Imię" dowolony ciąg zawierający znak lub cyfrę o długości minimum 2                                                       | W polu tekstowym "Imię" pojawi sie wpisany tekst                    |
| 2. Wpisz w polu tekstowym "Nazwisko" dowolony ciąg składający sie z liter o długości minimum 2                                                        | W polu tekstowym "Nazwisko" pojawi sie wpisany tekst                |
| 3. Wpisz w polu tekstowym "Numer dowodu osobistego" dowolony poprawny (poprawność sumy kontrolnej) ciąg składający sie z 3 liter alfabetu oraz 6 cyfr | W polu tekstowym "Numer dowodu osobistego" pojawi sie wpisany tekst |
| 4. Naciśnij przycisk "Generuj kod płatności"                                                                                                          | Komunikat "Formularz: Proszę wypełnić wszystkie pola poprawnie"     |

**Nazwa przypadku testowego:** Błędne wypełnienie pola tekstowego "Imię" (Podanie za krótkiego ciągu)

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com/client-data](https://pacific-tor-53766.herokuapp.com/client-data), formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji, zostały wybrane prawidłowe daty oraz pokoje.

**Wymagania:** Prawidłowe wypełnienie formularza osobowego.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                                                                 | Oczekiwany rezultat                                                 |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------:|
| 1.  Wpisz w polu tekstowym "Imię" dowolony ciąg składający sie z samych liter o długości krótszej niz 2 znaki                                         | W polu tekstowym "Imię" pojawi sie wpisany tekst                    |
| 2. Wpisz w polu tekstowym "Nazwisko" dowolony ciąg składający sie z liter o długości minimum 2                                                        | W polu tekstowym "Nazwisko" pojawi sie wpisany tekst                |
| 3. Wpisz w polu tekstowym "Numer dowodu osobistego" dowolony poprawny (poprawność sumy kontrolnej) ciąg składający sie z 3 liter alfabetu oraz 6 cyfr | W polu tekstowym "Numer dowodu osobistego" pojawi sie wpisany tekst |
| 4. Naciśnij przycisk "Generuj kod płatności"                                                                                                          | Komunikat "Formularz: Proszę wypełnić wszystkie pola poprawnie"     |

**Nazwa przypadku testowego:** Błędne wypełnienie pola tekstowego "Nazwisko" (Podanie niedozwolonych znaków)

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com/client-data](https://pacific-tor-53766.herokuapp.com/client-data), formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji, zostały wybrane prawidłowe daty oraz pokoje.

**Wymagania:** Prawidłowe wypełnienie formularza osobowego.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                                                                 | Oczekiwany rezultat                                                 |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------:|
| 1. Wpisz w polu tekstowym "Imię" dowolony ciąg zawierający znak lub cyfrę o długości minimum 2                                                        | W polu tekstowym "Imię" pojawi sie wpisany tekst                    |
| 2. Wpisz w polu tekstowym "Nazwisko" dowolony ciąg zawierający znak lub cyfre o długości minimum 2                                                    | W polu tekstowym "Nazwisko" pojawi sie wpisany tekst                |
| 3. Wpisz w polu tekstowym "Numer dowodu osobistego" dowolony poprawny (poprawność sumy kontrolnej) ciąg składający sie z 3 liter alfabetu oraz 6 cyfr | W polu tekstowym "Numer dowodu osobistego" pojawi sie wpisany tekst |
| 4. Naciśnij przycisk "Generuj kod płatności"                                                                                                          | Komunikat "Formularz: Proszę wypełnić wszystkie pola poprawnie"     |

**Nazwa przypadku testowego:** Błędne wypełnienie pola tekstowego "Nazwisko" (Podanie za krótkiego ciągu)

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com/client-data](https://pacific-tor-53766.herokuapp.com/client-data), formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji, zostały wybrane prawidłowe daty oraz pokoje.

**Wymagania:** Prawidłowe wypełnienie formularza osobowego.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                                                                 | Oczekiwany rezultat                                                 |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------:|
| 1. Wpisz w polu tekstowym "Imię" dowolony ciąg zawierający znak lub cyfrę o długości minimum 2                                                        | W polu tekstowym "Imię" pojawi sie wpisany tekst                    |
| 2. Wpisz w polu tekstowym "Nazwisko" dowolony ciąg składający sie z samych liter o długości krótszej niz 2 znaki                                      | W polu tekstowym "Nazwisko" pojawi sie wpisany tekst                |
| 3. Wpisz w polu tekstowym "Numer dowodu osobistego" dowolony poprawny (poprawność sumy kontrolnej) ciąg składający sie z 3 liter alfabetu oraz 6 cyfr | W polu tekstowym "Numer dowodu osobistego" pojawi sie wpisany tekst |
| 4. Naciśnij przycisk "Generuj kod płatności"                                                                                                          | Komunikat "Formularz: Proszę wypełnić wszystkie pola poprawnie"     |

**Nazwa przypadku testowego:** Błędne wypełnienie pola tekstowego "Numer dowodu osobistego" (Podanie za krótkiego ciągu)

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com/client-data](https://pacific-tor-53766.herokuapp.com/client-data), formularz został załadowany poprawnie oraz wszystkei pola są widoczne i dostępne do edycji, zostały wybrane prawidłowe daty oraz pokoje.

**Wymagania:** Prawidłowe wypełnienie formularza osobowego.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                          | Oczekiwany rezultat                                                 |
|:----------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------:|
| 1. Wpisz w polu tekstowym "Imię" dowolony ciąg zawierający znak lub cyfrę o długości minimum 2 | W polu tekstowym "Imię" pojawi sie wpisany tekst                    |
| 2. Wpisz w polu tekstowym "Nazwisko" dowolony ciąg składający sie z liter o długości minimum 2 | W polu tekstowym "Nazwisko" pojawi sie wpisany tekst                |
| 3. Wpisz w polu tekstowym "Numer dowodu osobistego" dowolony ciąg znaków krótszy niż 9 znaków  | W polu tekstowym "Numer dowodu osobistego" pojawi sie wpisany tekst |
| 4. Naciśnij przycisk "Generuj kod płatności"                                                   | Komunikat "Formularz: Proszę wypełnić wszystkie pola poprawnie"     |

**Nazwa przypadku testowego:** Błędne wypełnienie pola tekstowego "Numer dowodu osobistego" (Podanie ciągu którego suma kontrola sie nie zgadza)

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com/client-data](https://pacific-tor-53766.herokuapp.com/client-data), formularz został załadowany poprawnie oraz wszystkei pola są widoczne i dostępne do edycji, zostały wybrane prawidłowe daty oraz pokoje.

**Wymagania:** Prawidłowe wypełnienie formularza osobowego.

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                                                                    | Oczekiwany rezultat                                                 |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------:|
| 1. Wpisz w polu tekstowym "Imię" dowolony ciąg zawierający znak lub cyfrę o długości minimum 2                                                           | W polu tekstowym "Imię" pojawi sie wpisany tekst                    |
| 2. Wpisz w polu tekstowym "Nazwisko" dowolony ciąg składający sie z liter o długości minimum 2                                                           | W polu tekstowym "Nazwisko" pojawi sie wpisany tekst                |
| 3. Wpisz w polu tekstowym "Numer dowodu osobistego" dowolony ciąg znaków składający się z 3 liter i 6 znaków, których suma kontrolna nie będzie poprawna | W polu tekstowym "Numer dowodu osobistego" pojawi sie wpisany tekst |
| 4. Naciśnij przycisk "Generuj kod płatności"                                                                                                             | Komunikat "Formularz: Proszę wypełnić wszystkie pola poprawnie"     |

**Nazwa przypadku testowego:** Przejście do niezależnego systemu płatności

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [pacific-tor-53766.herokuapp.com/client-data](https://pacific-tor-53766.herokuapp.com/client-data), formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji, zostały wybrane prawidłowe daty, pokoje oraz formularz osobowy został wypełniony i zaakceptowany, wygenerowano kod potwierdzająćy płatność.

**Wymagania:** Płatności

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

|                                                                   | Oczekiwany rezultat                                                  |
|:-----------------------------------------------------------------:|:--------------------------------------------------------------------:|
| 1. Naciśnij przycisk "Przejdź dalej" w częsci "Formularz osobowy" | Przekierowanie na [46.187.239.247:1897](http://46.187.239.247:1897/) |

**Nazwa przypadku testowego:** Udało się zapłacić

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [46.187.239.247:1897](http://46.187.239.247:1897/), formularz został załadowany poprawnie oraz wszystkie pola są widoczne i dostępne do edycji, zostały wybrane prawidłowe daty, pokoje oraz formularz osobowy został wypełniony zaakceptowany, wygenerowano kod potwierdzający płatność.

**Wymagania:** Płatność

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                | Oczekiwany rezulat                                                                                                                                                                                                                             |
|:--------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| 1. Wpisz wygenerowany kod płatności w polu tekstowym "Kod płatności" | Przekierowanie na [pacific-tor-53766.herokuapp.com/result?success=true](https://pacific-tor-53766.herokuapp.com/result?success=true) oraz wyświetlenie komunikatu potwierdzającego rezerwację, zostaje dodany wpis o rezerwacji do bazy danych |

**Nazwa przypadku testowego:** Nie udało sie zapłacić

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) pod adresem [46.187.239.247:1897](http://46.187.239.247:1897/), formularz został załadowany poprawnie oraz wszystkei pola są widoczne i dostępne do edycji, zostały wybrane prawidłowe daty, pokoje oraz formularz osobowy został wypełniony i zaakceptowany, wygenerowano kod potwierdzający płatność.

**Wymagania:** Płatność

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                               | Oczekiwany rezultat                                                                                                                                                                                                                             |
|:-------------------------------------------------------------------------------------------------------------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| 1. Wpisz kod płatności różny od wygenerowanego ale zgodny z przyjętymi założeniami w polu tekstowym "Kod płatności" | Przekierowanie na [pacific-tor-53766.herokuapp.com/result?success=false](https://pacific-tor-53766.herokuapp.com/result?success=false) oraz wyswietlenie komunikatu informującego o niepowodzeniu rezerwacji, brak dodania wpisu do bazy danych |

**Nazwa przypadku testowego:** Ominięcie wprowadzenia danych, wejście bezpośrednio na adres wygenerowany po  zatwierdzonej płatności

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) na pustej karcie.

**Wymagania:** Bezpieczeństwo

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                                                            | Oczekiwany rezultat       |
|:------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------:|
| 1. W polu adresu wpisać adres [pacific-tor-53766.herokuapp.com/result?success=true](https://pacific-tor-53766.herokuapp.com/result?success=true) | Nie dodanie wpisu w bazie |

**Nazwa przypadku testowego:** Ominięcie wprowadzenia danych, wejście bezpośrednio na adres wygenerowany po niezatwierdzonej płatności

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) na pustej karcie.

**Wymagania:** Bezpieczeństwo

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                                                       | Oczekiwany rezultat       |
|:-------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------:|
| 1. W polu adresu wpisać [s434786.students.wmi.amu.edu.pl/result?success=true](https://s434786.students.wmi.amu.edu.pl/result?success=false) | Nie dodanie wpisu w bazie |

**Nazwa przypadku testowego:** Ominięcie wprowadzenia danych, wejście bezpośrednio na adres drugiego widoku

**Warunki wstępne:** Użytkownik ma otwarta przeglądarke (Chrome wersja >= 70.0.3538.110 albo Mozilla Firefox wersja >= 62.0.3) na pustej karcie.

**Wymagania:** Bezpieczeństwo

**Autor:** Mateusz Lesiecki

**Data aktualizacji:** 10.12.2018

| Kroki                                                                                                                            | Oczekiwany rezultat                                                                          |
|:--------------------------------------------------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------:|
| 1. W polu adresu wpisać adres [pacific-tor-53766.herokuapp.com/client-data](https://pacific-tor-53766.herokuapp.com/client-data) | Przekierowanie na [pacific-tor-53766.herokuapp.com](https://pacific-tor-53766.herokuapp.com) |

---

## Testy automatyczne

- Poprawne wypełnienie formularza osobowego (Imie : "Jan", Nazwisko: "Nowak", Numer dowodu osobistego : "ABA300000")

---

## Środowisko testowe

- Łącze min. 1 MBit/s

- Przeglądarka Firefox wersja 62.0.3 lub Chrome 70.0.3538.110 (lub wyższe)

- System operacyjny - Windows 10 

- Włączona obsługa Javy

- Język polski

- Rozdzielczość min. 1280 x 720

---

## Standardy

- IEEE Standard for Software Test Documentation (ANSI/IEEE std 829)

---

## Odnośniki

- [Dokumentacja REST API](https://github.com/michalStarski/RUP-hotel/blob/master/docs/Dokumentacja%20REST%20API.md)

- [Model bazy danych](https://github.com/michalStarski/RUP-hotel/blob/master/docs/Model_Bazy_Danych.md)

- [Ogólny model informacyjny](https://github.com/michalStarski/RUP-hotel/blob/master/docs/Model_Bazy_Danych.md)

- [Specyfikacja architektury systemu](https://github.com/michalStarski/RUP-hotel/blob/master/docs/Specyfikacja%20architektury%20systemu.md)

- [Specyfikacja wykorzystywanych procesów](https://github.com/michalStarski/RUP-hotel/blob/master/docs/Specyfikacja%20wykorzystywanych%20proces%C3%B3w.md)

- [Specyfikacja wymagań systemowych](https://github.com/michalStarski/RUP-hotel/blob/master/docs/Specyfikacja%20wymaga%C5%84%20systemowych.md)

- [Diagram przypadków użycia](https://github.com/michalStarski/RUP-hotel/blob/master/docs/Diagram%20przypadk%C3%B3w%20u%C5%BCycia.pdf)

- [Diagram przypadków użycia 2](https://github.com/michalStarski/RUP-hotel/blob/master/docs/Diagram%20przypadk%C3%B3w%20u%C5%BCycia-2.png)

- [Diagram przypadków użycia 3](https://github.com/michalStarski/RUP-hotel/blob/master/docs/Diagram%20przypadk%C3%B3w%20u%C5%BCycia-3.png)
