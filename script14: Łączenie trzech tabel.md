## script14.sql: Łączenie trzech tabel

| Zaawansowane łączenie wielu tabel

1. Łączenie tabel zamowienia, klienci i produkty
2. Wyświetlanie pełnych danych zamówienia

<br>

``` sql
-- Łączenie tabel zamowienia, klienci i produkty
SELECT z.id AS zamowienie_id, 
       z.data_zamowienia, 
       k.imie, 
       k.nazwisko, 
       p.nazwa AS produkt, 
       zs.ilosc, 
       zs.cena_jednostkowa, 
       (zs.ilosc * zs.cena_jednostkowa) AS wartosc
FROM zamowienia z
JOIN klienci k ON z.id_klienta = k.id
JOIN zamowienia_szczegoly zs ON z.id = zs.id_zamowienia
JOIN produkty p ON zs.id_produktu = p.id
ORDER BY z.data_zamowienia DESC;

-- Wyświetlanie pełnych danych zamówienia z kategorią produktu
SELECT z.id AS zamowienie_id, 
       z.data_zamowienia, 
       k.imie, 
       k.nazwisko, 
       p.nazwa AS produkt, 
       kat.nazwa AS kategoria,
       zs.ilosc, 
       zs.cena_jednostkowa, 
       (zs.ilosc * zs.cena_jednostkowa) AS wartosc
FROM zamowienia z
JOIN klienci k ON z.id_klienta = k.id
JOIN zamowienia_szczegoly zs ON z.id = zs.id_zamowienia
JOIN produkty p ON zs.id_produktu = p.id
JOIN kategorie kat ON p.id_kategorii = kat.id
ORDER BY z.id, p.nazwa;

-- Podsumowanie zamówień dla każdego klienta
SELECT k.id, 
       k.imie, 
       k.nazwisko, 
       COUNT(DISTINCT z.id) AS liczba_zamowien,
       SUM(zs.ilosc * zs.cena_jednostkowa) AS laczna_wartosc
FROM klienci k
LEFT JOIN zamowienia z ON k.id = z.id_klienta
LEFT JOIN zamowienia_szczegoly zs ON z.id = zs.id_zamowienia
GROUP BY k.id, k.imie, k.nazwisko
ORDER BY laczna_wartosc DESC NULLS LAST;
```
