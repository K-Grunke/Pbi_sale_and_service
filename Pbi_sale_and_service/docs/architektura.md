# 🧱 Architektura rozwiązania

## 🎯 Cel dokumentu

Celem dokumentu jest opisanie architektury rozwiązania analitycznego Power BI, obejmującego:

- sposób pozyskania i przetwarzania danych,
- strukturę modelu danych,
- warstwy logiki analitycznej,
- kluczowe decyzje projektowe.

Dokument ma umożliwić **szybkie zrozumienie projektu** osobom technicznym i biznesowym, bez konieczności otwierania raportu Power BI.

---

## 🏗 Architektura wysokiego poziomu

Rozwiązanie zostało zaprojektowane w oparciu o klasyczną architekturę warstwową BI:

Źródła danych

↓

Power Query (ETL)

↓

Model danych (fakty + wymiary)

↓

DAX (logika analityczna)

↓

Raport Power BI

Każda warstwa ma jasno określoną odpowiedzialność, co ułatwia utrzymanie i dalszy rozwój projektu.

---

## 📥 Warstwa źródeł danych

Źródła danych obejmują arkusze kalkulacyjne zawierające dane:

- sprzedażowe
- skutecznościowe
- serwisowe

Dane są przechowywane w repozytorium w dwóch wariantach:

- `raw` – struktura zbliżona do danych produkcyjnych,
- `sample` – minimalne dane demonstracyjne umożliwiające uruchomienie projektu bez dostępu do produkcji.

---

## 🔄 Warstwa przetwarzania danych (Power Query)

Power Query odpowiada za:

- normalizację struktury danych,
- przygotowanie tabel faktów i wymiarów,
- ujednolicenie typów danych.

Transformacje zostały podzielone logicznie na:

- zapytania źródłowe (staging),
- zapytania końcowe wykorzystywane w modelu.


Szczegółowy opis transformacji znajduje się w pliku:

- `powerquery/transformacje.md`

---

## 🧩 Model danych

Model danych opiera się na:

- centralnej tabeli kalendarza
- wielu tabelach faktów
- współdzielonych wymiarach

### Tabele faktów

- `Sprzedaż` – dane transakcyjne sprzedaży i marży
- `Skuteczność` – potencjał transakcyjny
- `Serwis sprzedaż` – sprzedaż usług serwisowych
- `Serwis wizyty` – liczba wizyt serwisowych

### Tabele wymiarów

- `Kalendarz` – wspólny wymiar czasu dla wszystkich faktów
- `Serwisant` – wymiar obsługujący dane serwisowe

Model został zaprojektowany w sposób umożliwiający:

- analizę przekrojową danych,
- poprawne działanie Time Intelligence,
- dalszą rozbudowę o kolejne obszary biznesowe.

---

## 🧠 Warstwa logiki analitycznej (DAX)

Logika analityczna została zaimplementowana w DAX i obejmuje:

- miary bazowe (sumy, liczniki)
- miary pochodne (wskaźniki, średnie)
- miary skuteczności
- Time Intelligence (analiza w czasie)

Miary zostały zaprojektowane w sposób:

- czytelny biznesowo
- odporny na błędy
- zgodny z kontekstem filtrowania modelu

Dokumentacja miar znajduje się w:
- `dax/miary.md`

---

## 📊 Warstwa raportowa

Warstwa raportowa Power BI odpowiada za:

- prezentację danych w formie wizualizacji
- interakcję użytkownika z danymi
- filtrowanie i eksplorację wyników

Raport wykorzystuje:

- filtry czasu
- podziały na lokalizacje, doradców i serwisantów
- wskaźniki KPI oraz wykresy trendów

---

## ⚙️ Decyzje architektoniczne

W projekcie przyjęto następujące założenia:

- jeden wspólny kalendarz dla całego modelu
- rozdzielenie faktów i wymiarów
- brak logiki biznesowej w wizualizacjach
- pełna dokumentacja transformacji i miar poza raportem

Decyzje te zwiększają:

- czytelność rozwiązania
- możliwość pracy zespołowej
- łatwość utrzymania projektu

---

## 🔮 Możliwości rozwoju

Architektura umożliwia w przyszłości:

- dodanie nowych źródeł danych
- rozbudowę modelu o kolejne wymiary
- automatyzację odświeżania danych
- publikację i zarządzanie raportem w Power BI Service

---

📌 *Dokument stanowi punkt odniesienia dla dalszego rozwoju projektu oraz rozmów technicznych i biznesowych.*