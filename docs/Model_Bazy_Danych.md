# Model Bazy Danych
## RUP Hotel
### Autor: Patrycja Łaźna
### Korekta: 
### Wersja: 001
### Data: 24.11.2018
### Kierownik Projektu: Michał Starski
---
## Spis treści:
1. Diagram Bazy Danych
2. Model Danych
---
## Diagram Bazy Danych
![](diagramdb.png)
## Model Danych
Aplikacja przechowuje kilka typów danych, które można podzielić na 4 grupy.
- Dane użytkownika skojarzone z tabelą __„Client”__ w bazie danych.
Są to: imię (name), nazwisko (surname), numer dowodu osobistego (id_number) oraz wewnętrzne id (client_id) nadawane automatycznie, dane są niezbędne przy składaniu rezerwacji oraz przy sprawdzeniu historii danego klienta
- Dane rezerwacji, skojarzone z tabelą __„Reservation”__. 
Przechowywane dane to: wewnętrzne id (reservationID) nadawane automatycznie, identyfikator klienta rezerwującego pokój (client_id), numer pokoju, który zarezerwował (room_number), data zameldowania (arrival) oraz data wymeldowania (departure).
- Dane pokoju, skojarzone z tabelą __„Room”__.
Są to: wewnętrzny numer identyfikujący pokój (room_number), skrócona informacja o typie pokoju (room_type) oraz cena danego pokoju (price).
- Dane typów pokoi, skojarzone z tabelą __„Room Type”__. 
Przyporządkowujące skróconym informacjom o typach pokoju (roomtypeID) opisy wyjaśniające (room_type).


Dodatkowo:
- Jeden pokój może być wynajmowany w danym czasie tylko przez jednego klienta.
- Pojemność pokoju jest określona przez typ pokoju.
- Wszystkie pola identyfikujące klienta muszą zostać wypełnione.
- Nie może istnieć pokój bez typu.
- Data zameldowania musi być wcześniejsza niż data wymeldowania.
- Typ pokoju musi posiadać opis.
- Dane historycznych rezerwacji powinny być zachowywane w bazie danych.
- Numer dowodu ma określoną formę – 9 znaków.
