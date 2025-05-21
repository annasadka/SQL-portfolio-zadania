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
