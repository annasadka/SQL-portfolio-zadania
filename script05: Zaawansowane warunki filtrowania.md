``` sql
-- Użycie operatora BETWEEN dla wieku
SELECT * FROM klienci
WHERE wiek BETWEEN 25 AND 35;

-- Użycie operatora IN dla imion klientów
SELECT * FROM klienci
WHERE imie IN ('Jan', 'Anna', 'Katarzyna');

-- Użycie operatora LIKE do wyszukiwania wzorców w nazwiskach
SELECT * FROM klienci
WHERE nazwisko LIKE 'K%';  -- Nazwiska zaczynające się na K

SELECT * FROM klienci
WHERE nazwisko LIKE '%ski';  -- Nazwiska kończące się na 'ski'

SELECT * FROM klienci
WHERE nazwisko LIKE '%ow%';  -- Nazwiska zawierające 'ow'

-- Użycie operatorów IS NULL i IS NOT NULL
SELECT * FROM klienci
WHERE telefon IS NULL;

SELECT * FROM klienci
WHERE telefon IS NOT NULL;
```
