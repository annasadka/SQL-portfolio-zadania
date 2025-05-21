📝 script07.sql: Sortowanie wyników

| Organizowanie wyników zapytań

1. Sortowanie klientów według wieku rosnąco (ASC)
2. Sortowanie klientów według daty rejestracji malejąco (DESC)
3. Sortowanie z wieloma kolumnami
4. Filtrowanie i sortowanie w jednym zapytaniu
 <br>
 
``` sql
-- Sortowanie klientów według wieku rosnąco (ASC)
SELECT * FROM klienci
ORDER BY wiek ASC;

-- Sortowanie klientów według daty rejestracji malejąco (DESC)
SELECT * FROM klienci
ORDER BY data_rejestracji DESC;

-- Sortowanie z wieloma kolumnami
SELECT * FROM klienci
ORDER BY nazwisko ASC, imie ASC;

-- Filtrowanie i sortowanie w jednym zapytaniu
SELECT * FROM klienci
WHERE wiek > 25
ORDER BY data_rejestracji DESC, nazwisko ASC;

```
