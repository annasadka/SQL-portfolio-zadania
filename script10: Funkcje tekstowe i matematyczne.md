## 📝 script10.sql: Funkcje tekstowe i matematyczne

> *Manipulowanie i formatowanie danych*

1. Użycie funkcji CONCAT do łączenia imienia i nazwiska
2. Użycie funkcji UPPER i LOWER do zmiany wielkości liter
3. Użycie funkcji matematycznych (ROUND, ABS)
4. Użycie funkcji do formatowania dat
<br>

``` sql
-- Użycie funkcji CONCAT do łączenia imienia i nazwiska
SELECT id, CONCAT(imie, ' ', nazwisko) AS pelne_imie
FROM klienci;

-- Użycie funkcji UPPER i LOWER do zmiany wielkości liter
SELECT UPPER(imie) AS imie_duze, LOWER(nazwisko) AS nazwisko_male
FROM klienci;

-- Użycie funkcji matematycznych (ROUND, ABS)
SELECT nazwa, cena, 
       ROUND(cena * 0.23, 2) AS podatek_vat,
       ROUND(cena * 1.23, 2) AS cena_brutto
FROM produkty;

-- Użycie funkcji do formatowania dat
SELECT id, imie, nazwisko, 
       DATE_FORMAT(data_rejestracji, '%d-%m-%Y') AS data_formatowana,
       DATEDIFF(CURRENT_DATE, data_rejestracji) AS dni_od_rejestracji
FROM klienci;

-- Przykład z funkcją SUBSTRING
SELECT id, email, 
       SUBSTRING(email, 1, POSITION('@' IN email) - 1) AS nazwa_uzytkownika,
       SUBSTRING(email, POSITION('@' IN email) + 1) AS domena
FROM klienci;
```
