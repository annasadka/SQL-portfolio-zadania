## 📝 script11.sql: Podzapytania i widoki

> *Zaawansowane techniki zapytań i wirtualne tabele*

1. Tworzenie podzapytań
2. Tworzenie widoku dla najnowszych klientów
3. Tworzenie widoku dla najdroższych produktów
4. Wyświetlanie danych z widoków

<br>

``` sql
-- Tworzenie podzapytań
SELECT * FROM produkty
WHERE cena > (SELECT AVG(cena) FROM produkty);

-- Podzapytanie w SELECT
SELECT p.nazwa, p.cena,
       (SELECT nazwa FROM kategorie WHERE id = p.id_kategorii) AS kategoria
FROM produkty p;

-- Tworzenie widoku dla najnowszych klientów
CREATE VIEW najnowsi_klienci AS
SELECT * FROM klienci
ORDER BY data_rejestracji DESC
LIMIT 3;

-- Tworzenie widoku dla najdroższych produktów
CREATE VIEW najdrozsze_produkty AS
SELECT * FROM produkty
WHERE cena > (SELECT AVG(cena) * 1.5 FROM produkty);

-- Wyświetlanie danych z widoków
SELECT * FROM najnowsi_klienci;
SELECT * FROM najdrozsze_produkty;

-- Przykład bardziej złożonego podzapytania
SELECT k.nazwa AS kategoria, 
       (SELECT COUNT(*) FROM produkty WHERE id_kategorii = k.id) AS liczba_produktow,
       (SELECT AVG(cena) FROM produkty WHERE id_kategorii = k.id) AS srednia_cena
FROM kategorie k;
```
