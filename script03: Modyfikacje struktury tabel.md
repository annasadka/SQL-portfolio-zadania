## 

``` sql
-- Dodanie nowej kolumny telefon do tabeli klienci
ALTER TABLE klienci
ADD COLUMN telefon VARCHAR(15);

-- Zmiana typu danych kolumny
ALTER TABLE klienci
MODIFY COLUMN telefon VARCHAR(20);

-- Dodanie kolumny z domyślną wartością
ALTER TABLE klienci
ADD COLUMN aktywny BOOLEAN DEFAULT TRUE;

-- Usunięcie kolumny
ALTER TABLE klienci
DROP COLUMN aktywny;

-- Przywrócenie kolumny (dla celów edukacyjnych)
ALTER TABLE klienci
ADD COLUMN aktywny BOOLEAN DEFAULT TRUE;

```
