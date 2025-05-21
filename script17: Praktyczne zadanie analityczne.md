``` sql
-- Stworzenie pełnej analizy sprzedaży
-- 1. Sprzedaż według kategorii
SELECT kat.nazwa AS kategoria,
       COUNT(DISTINCT zs.id) AS liczba_sprzedanych_pozycji,
       SUM(zs.ilosc) AS laczna_sprzedana_ilosc,
       SUM(zs.ilosc * zs.cena_jednostkowa) AS wartosc_sprzedazy,
       ROUND(SUM(zs.ilosc * zs.cena_jednostkowa) / 
             (SELECT SUM(ilosc * cena_jednostkowa) FROM zamowienia_szczegoly) * 100, 2) AS procent_calkowitej_sprzedazy
FROM kategorie kat
JOIN produkty p ON kat.id = p.id_kategorii
JOIN zamowienia_szczegoly zs ON p.id = zs.id_produktu
GROUP BY kat.id, kat.nazwa
ORDER BY wartosc_sprzedazy DESC;

-- 2. Znajdowanie najlepszych klientów
SELECT k.id, k.imie, k.nazwisko, k.email,
       COUNT(DISTINCT z.id) AS liczba_zamowien,
       SUM(zs.ilosc) AS liczba_kupionych_produktow,
       ROUND(SUM(zs.ilosc * zs.cena_jednostkowa), 2) AS wartosc_zakupow,
       MAX(z.data_zamowienia) AS ostatni_zakup
FROM klienci k
JOIN zamowienia z ON k.id = z.id_klienta
JOIN zamowienia_szczegoly zs ON z.id = zs.id_zamowienia
GROUP BY k.id, k.imie, k.nazwisko, k.email
ORDER BY wartosc_zakupow DESC
LIMIT 10;

-- 3. Znajdowanie najpopularniejszych produktów
SELECT p.id, p.nazwa, kat.nazwa AS kategoria,
       SUM(zs.ilosc) AS ilosc_sprzedana,
       COUNT(DISTINCT z.id_klienta) AS liczba_kupujacych,
       ROUND(AVG(zs.ilosc), 2) AS srednia_ilosc_w_zamowieniu,
       ROUND(SUM(zs.ilosc * zs.cena_jednostkowa), 2) AS wartosc_sprzedazy
FROM produkty p
JOIN kategorie kat ON p.id_kategorii = kat.id
JOIN zamowienia_szczegoly zs ON p.id = zs.id_produktu
JOIN zamowienia z ON zs.id_zamowienia = z.id
GROUP BY p.id, p.nazwa, kat.nazwa
ORDER BY ilosc_sprzedana DESC
LIMIT 10;

-- 4. Analiza sprzedaży w czasie (po miesiącach)
SELECT 
    DATE_FORMAT(z.data_zamowienia, '%Y-%m') AS miesiac,
    COUNT(DISTINCT z.id) AS liczba_zamowien,
    COUNT(DISTINCT z.id_klienta) AS liczba_klientow,
    SUM(zs.ilosc) AS liczba_sprzedanych_produktow,
    ROUND(SUM(zs.ilosc * zs.cena_jednostkowa), 2) AS przychod
FROM zamowienia z
JOIN zamowienia_szczegoly zs ON z.id = zs.id_zamowienia
GROUP BY miesiac
ORDER BY miesiac;
```
