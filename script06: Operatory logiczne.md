## 📝 script06.sql: Operatory logiczne

| Łączenie warunków przy użyciu operatorów logicznych

1. Użycie AND do filtrowania wyników
2. Użycie OR do łączenia warunków
3. Użycie NOT dla negacji warunków
<br>

``` sql
-- Użycie AND do filtrowania wyników
SELECT * FROM klienci
WHERE wiek > 30 AND data_rejestracji > '2023-02-01';

-- Użycie OR do łączenia warunków
SELECT * FROM klienci
WHERE imie = 'Jan' OR imie = 'Anna';

-- Użycie NOT dla negacji warunków
SELECT * FROM klienci
WHERE NOT wiek < 30;

-- Złożone warunki
SELECT * FROM klienci
WHERE (wiek > 30 OR data_rejestracji < '2023-03-01') 
  AND nazwisko NOT LIKE 'K%';
```
