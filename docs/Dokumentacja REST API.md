# Dokumentacja REST API

## RUP Hotel

### Autor: Konrad Pierzyński

### Wersja: 001

### Data: 10.12.2018

### Kierownik Projektu: Michał Starski

* * *

## Spis treści:

1.  Endpoint'y API
    
2.  Komunikacja z zewnętrznym systemem płatności
    

* * *

## Endpoint'y API

**POST /rooms**

Zwraca listę wolnych pokoi w oparciu o podane kryteria.

```
{
    from: Date,
    to: Date,
    personCount: int
}
```
_from_ - Data przyjazdu,<br>
_to_ - Data wyjazdu,<br>
_personCount_ - Liczba osób, dla których użytkownik chce zarezerwować pokój<br>

Odpowiedź

```
{
    rooms: [
        {
            roomID: int,
            type: int,
            price: float
        }
        {
            ...
        }
    ]
}
```

Dany endpoint służy do odpytania serwera przez klienta o wolne pokoje w oparciu o datę rezerwacji wraz z ilością osób do zakwaterowania. Serwer powinien odpowiedzieć tablicą wolnych pokoi, przez co dane te mogą zostać zwizualizowane na frontendzie.

* * *

**POST /generate-token**

Zwraca JSON web token w opaciu o dane użytkownika.

```json
{
    name: String,
    surname: String,
    identity: String,
    rooms: Array
}
```

_name_ - Imię użytkownika,<br>
_surname_ - Nazwisko użytkownika,<br>
_identity_ - Numer dowodu osobistego,<br>

Odpowiedź:

```
{
    token: String,
    id: int
}
```

/generate-token to endpoint służący do wygenerowania kodu płatności przez serwer w oparciu o informacje o użytkowniku tj. imię, nazwisko i numer dowodu wraz z wybranymi przez użytkownika pokojami tworzony jest token (JWT)[https://jwt.io/]. Utworzony token zostanie przedstawiony użytkownikowi po stronie klienta, skąd będzie można wykorzystać go do płatności w zewnętrznym serwisie.

* * *

## Komunikacja z zewnętrznym systemem płatności

**POST /pay**

Wysyła informację o nadchodzącej płatności.

```json
{
    id: int,
    name: String,
    surname: String,
    identityID: String,
    price: float
}
```

_id_ - Id płatności,<br>
_name_ - Imię użytkownika,<br>
_surname_ - Nazwisko użytkownika,<br>
_identityID_ - Nr. dowodu osobistego,<br>
_price_ - Cena<br>

Serwer wysyła dane o użytkowniku do serwisu płatności, który próbuje zarezerwować pokoje. Dane te służą do zweryfikowania poprawności kodu po stronie usługi obsługującą płatność.
