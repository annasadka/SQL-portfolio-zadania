## 📝 script04.sql: Podstawowe zapytania SELECT z warunkami
> *Filtrowanie danych przy użyciu podstawowych operatorów*

| Operator | Opis | Przykład |
|----------|------|----------|
| `=` | Równość | `WHERE wiek = 25` |
| `>` | Większe niż | `WHERE wiek > 30` |
| `<` | Mniejsze niż | `WHERE wiek < 20` |
| `!=` | Nierówność | `WHERE wiek != 25` |

<br>

1. Wyświetlanie klientów, którzy mają wiek poniżej 30 lat
2. Wyświetlanie klientów, którzy zarejestrowali się po określonej dacie
3. Aktualizacja wieku klientów
4. Wyświetlanie klientów, których wiek jest różny od 25
<br>

``` sql
-- Wyświetlanie klientów, którzy mają wiek poniżej 30 lat
SELECT * FROM klienci
WHERE wiek < 30;

-- Wyświetlanie klientów, którzy zarejestrowali się po określonej dacie
SELECT * FROM klienci
WHERE data_rejestracji > '2023-03-01';

-- Aktualizacja wieku klientów
UPDATE klienci
SET wiek = wiek + 1
WHERE data_rejestracji < '2023-02-01';

-- Wyświetlanie klientów, których wiek jest różny od 25
SELECT * FROM klienci
WHERE wiek != 25;
```
