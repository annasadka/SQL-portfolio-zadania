``` sql
-- Liczenie klientów (COUNT)
SELECT COUNT(*) AS liczba_klientow
FROM klienci;

-- Znajdowanie średniego wieku klientów (AVG)
SELECT AVG(wiek) AS sredni_wiek
FROM klienci;

-- Znajdowanie najwyższej i najniższej ceny produktów (MAX, MIN)
SELECT MAX(cena) AS najwyzsza_cena, MIN(cena) AS najnizsza_cena
FROM produkty;

-- Sumowanie dostępnych ilości produktów (SUM)
SELECT SUM(dostepna_ilosc) AS laczna_ilosc
FROM produkty;

-- Grupowanie według kategorii (GROUP BY)
SELECT id_kategorii, COUNT(*) AS liczba_produktow, 
       AVG(cena) AS srednia_cena,
       SUM(dostepna_ilosc) AS laczna_ilosc
FROM produkty
GROUP BY id_kategorii;

-- Filtrowanie grup (HAVING)
SELECT id_kategorii, COUNT(*) AS liczba_produktow
FROM produkty
GROUP BY id_kategorii
HAVING COUNT(*) > 1;

-- Grupowanie z dołączeniem nazw kategorii
SELECT k.nazwa AS kategoria, COUNT(p.id) AS liczba_produktow, 
       AVG(p.cena) AS srednia_cena
FROM produkty p
JOIN kategorie k ON p.id_kategorii = k.id
GROUP BY k.id, k.nazwa;
```
