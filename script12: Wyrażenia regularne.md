## script12.sql: Wyrażenia regularne

| Zaawansowane wzorce wyszukiwania

1. Wyszukiwanie klientów według wzorców w emailach
2. Wyszukiwanie produktów według wzorców w nazwach
<br>

``` sql
-- Wyszukiwanie klientów według wzorców w emailach
SELECT * FROM klienci
WHERE email REGEXP '^[a-z]+\.[a-z]+@example\.com$';

-- Klienci, których email zaczyna się od imienia
SELECT * FROM klienci
WHERE email REGEXP CONCAT('^', LOWER(imie), '\\.');

-- Wyszukiwanie produktów według wzorców w nazwach
SELECT * FROM produkty
WHERE nazwa REGEXP '^[A-Z]';  -- Nazwy zaczynające się wielką literą

SELECT * FROM produkty
WHERE nazwa REGEXP '[0-9]';   -- Nazwy zawierające cyfry

-- Wyszukiwanie określonych kategorii produktów
SELECT * FROM produkty
WHERE nazwa REGEXP '(Laptop|Smartfon)';
```
