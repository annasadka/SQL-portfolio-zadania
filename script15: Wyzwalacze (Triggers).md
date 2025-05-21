## script15.sql: Wyzwalacze (Triggers)

| Automatyczne reakcje na zmiany w danych

1. Tworzenie triggerów do automatycznej aktualizacji stanu magazynowego
2. Przykład: zmniejszanie stanu magazynowego po dodaniu nowego zamówienia

<br>

``` sql
-- Tworzenie triggera do automatycznej aktualizacji stanu magazynowego po dodaniu zamówienia
DELIMITER //
CREATE TRIGGER zmniejsz_stan_magazynowy
AFTER INSERT ON zamowienia_szczegoly
FOR EACH ROW
BEGIN
    UPDATE produkty
    SET dostepna_ilosc = dostepna_ilosc - NEW.ilosc
    WHERE id = NEW.id_produktu;
END //
DELIMITER ;

-- Trigger do zwiększania stanu magazynowego przy usunięciu pozycji zamówienia
DELIMITER //
CREATE TRIGGER zwieksz_stan_magazynowy
AFTER DELETE ON zamowienia_szczegoly
FOR EACH ROW
BEGIN
    UPDATE produkty
    SET dostepna_ilosc = dostepna_ilosc + OLD.ilosc
    WHERE id = OLD.id_produktu;
END //
DELIMITER ;

-- Trigger do aktualizacji stanu magazynowego przy zmianie ilości w zamówieniu
DELIMITER //
CREATE TRIGGER aktualizuj_stan_magazynowy
AFTER UPDATE ON zamowienia_szczegoly
FOR EACH ROW
BEGIN
    UPDATE produkty
    SET dostepna_ilosc = dostepna_ilosc + OLD.ilosc - NEW.ilosc
    WHERE id = NEW.id_produktu;
END //
DELIMITER ;

-- Przykładowy test triggerów
INSERT INTO zamowienia (id_klienta, status)
VALUES (1, 'Nowe');

INSERT INTO zamowienia_szczegoly (id_zamowienia, id_produktu, ilosc, cena_jednostkowa)
VALUES (5, 3, 5, 89.99);

-- Sprawdzenie aktualnego stanu magazynowego
SELECT id, nazwa, dostepna_ilosc FROM produkty WHERE id = 3;
```
