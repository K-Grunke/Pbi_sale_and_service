# 📊 Analiza sprzedaży, skuteczności i serwisu – Power BI

## 📌 Opis projektu

Projekt prezentuje **wizualizację i analizę danych sprzedażowych, usługowych oraz serwisowych** z wykorzystaniem Power BI.  

Celem raportu jest dostarczenie spójnego obrazu:

- wyników sprzedaży,
- skuteczności realizacji potencjału,
- aktywności serwisowej (sprzedaż i wizyty),

z możliwością analizy w czasie oraz według kluczowych wymiarów biznesowych.

Projekt został przygotowany z myślą o **czytelności modelu danych**, **dobrych praktykach BI** oraz **możliwości dalszej rozbudowy**.

## 👨‍🎓 Informacje o autorze

**Imię i nazwisko:** Konrad Grünke  
**Kontakt:** konrad.grunke@gmail.com  
**LinkedIn:** [linkedin.com/in/konrad-grunke/](https://www.linkedin.com/in/konrad-grunke/)


## 🎯 Zakres analizy

Raport odpowiada m.in. na pytania:

- jak kształtuje się sprzedaż i marża w czasie,
- jak wygląda skuteczność realizacji potencjału transakcyjnego,
- jaka jest aktywność serwisu (sprzedaż i wizyty),
- jak wyniki różnią się w zależności od lokalizacji, doradcy lub serwisanta.

## 🗂 Źródła danych

### 🧾 Sprzedaż

Arkusz zawiera dane transakcyjne sprzedaży:

- `Data transakcji`
- `Marża`
- `Lokalizacja`
- `Doradca`
- `Model pojazdu`

### 📈 Skuteczność

Arkusz wykorzystywany do analizy potencjału:

- `Miesiąc`
- `Data transakcji`
- `Potencjał transakcji`

### 🔧 Serwis sprzedaż

Dane dotyczące sprzedaży usług serwisowych:

- `Data transakcji`
- `Produkt`
- `Serwisant`

### 🛠 Serwis wizyty

Dane dotyczące liczby wizyt serwisowych:

- `Data`
- `Serwisant`
- `Liczba wizyt`

## 🧩 Model danych

Projekt opiera się na:

- **centralnej tabeli kalendarza**,
- rozdzieleniu danych na **tabele faktów i wymiary**,
- współdzielonych wymiarach (czas, serwisant),
- czytelnych relacjach umożliwiających analizę przekrojową.  

Model został zaprojektowany z myślą o:

- poprawnej obsłudze Time Intelligence,
- wydajności,
- łatwej rozbudowie o kolejne obszary.

## 🧠 Zastosowane rozwiązania

- Power Query – czyszczenie i normalizacja danych
- DAX – miary biznesowe i Time Intelligence
- Parametryzacja źródeł danych (sample / raw)
- Dokumentacja logiki transformacji i miar (`docs`, `dax`)

## 📁 Struktura repozytorium (skrót)

├── powerbi/ # raporty i model  
├── dax/ # miary DAX  
├── powerquery/ # transformacje M  
├── data/ # dane sample / raw  
├── docs/ # dokumentacja projektu  
└── README.md  

## 🚀 Status projektu
Projekt rozwojowy / demonstracyjny.  
Możliwa dalsza rozbudowa m.in. o:
- dodatkowe KPI,
- porównania okresów (YoY, MoM),
- automatyzację odświeżania,
- publikację do Power BI Service.

## 🤝 Kontakt i rozmowa
Projekt został udostępniony również w celu **wymiany doświadczeń, rozmowy o danych i Power BI**.

Jeśli:
- masz sugestie lub pytania,
- chcesz omówić model danych lub DAX,
- szukasz współpracy,

👉 **zapraszam do kontaktu przez GitHub lub LinkedIn**.

Chętnie porozmawiam o:
- Power BI
- modelowaniu danych
- dobrych praktykach BI
- projektach analitycznych

📬 **Dziękuję za poświęcony czas i zapraszam do rozmowy!**
