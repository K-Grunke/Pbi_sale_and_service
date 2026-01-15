# DAX – Miary i tabele obliczeniowe

## 📦 Kalendarz

### Kalendarz

**Typ:** Tabela obliczeniowa  

**Cel:** Centralna tabela dat wykorzystywana do filtrowania wszystkich tabel faktów oraz obsługi Time Intelligence.

Tabela generowana automatycznie na podstawie zakresu dat występujących w modelu danych.

**Kolumny:**

- `Date` – pełna data
- `Miesiąc skrót` – skrócona nazwa miesiąca (np. sty, lut)
- `Miesiąc numer` – numer miesiąca (1–12)

**Logika:**
```
Kalendarz =

ADDCOLUMNS(

   CALENDARAUTO(),

   "Miesiąc skrót", FORMAT ( [Date], "mmm" ),

   "Miesiąc numer", MONTH ( [Date] )

)
```

## 📦 Skuteczność - Realizacja potencjału

**Opis:** Wskaźnik realizacji potencjału transakcyjnego w danym okresie.

Miara pokazuje, jaka część dostępnego potencjału została faktycznie wykorzystana.

**Użycie:** KPI, wykres liniowy, analiza miesięczna

**Logika:**
```
Realizacja potencjału :=

DIVIDE(

   COUNTA ( 'Sprzedaż'[Lokalizacja] ),

   SUM ( 'Skuteczność'[Potencjał Transakcji] )

)
```
**Interpretacja:**

- licznik: liczba zrealizowanych transakcji (na podstawie lokalizacji)
- mianownik: sumaryczny potencjał transakcyjny

**Uwagi:**

- DIVIDE zabezpiecza przed dzieleniem przez zero
- miara wrażliwa na kontekst czasu (Kalendarz)
- poprawność zależy od relacji między Sprzedaż a Skuteczność