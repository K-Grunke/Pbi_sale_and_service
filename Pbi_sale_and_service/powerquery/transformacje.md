# Power Query – Transformacje danych

## Opis transformacji - normalizacja danych wizyt

**Źródło:** `Serwis_wizyty.xlsx`  

**Cel:** `Normalizacja danych wizyt`

Tabela źródłowa zawierała serwisantów jako osobne kolumny.

Dane zostały przekształcone do postaci:

- Data

- Serwisant

- Liczba wizyt


**Zastosowane operacje:**

- jawne typowanie kolumn 🔧

- unpivot kolumn serwisantów 🔄

- sortowanie po liczbie wizyt 📊


**Kluczowa logika:**

```
let

   Source = #"Nagłówki o podwyższonym poziomie",



   ChangedTypes = Table.TransformColumnTypes(

       Source,

       {

           {"Data", type date},

           {"Sandra", Int64.Type},

           {"Kamila", Int64.Type},

           {"Stefan", Int64.Type},

           {"Michał", Int64.Type}

       }

   ),



   Unpivoted = Table.UnpivotOtherColumns(

       ChangedTypes,

       {"Data"},

       "Serwisant",

       "Liczba wizyt"

   ),



   RenamedColumns = Table.RenameColumns(

       Unpivoted,

       {

           {"Serwisant", "Serwisant"},

           {"Liczba wizyt", "Liczba wizyt"}

       }

   ),



   SortedRows = Table.Sort(

       RenamedColumns,

       {{"Liczba wizyt", Order.Ascending}}

   )



in

   SortedRows
```

---

## Opis transformacji - Utworzenie tabeli wymiaru Serwisant

**Źródło:** `Serwis_wizyty.xlsx`

**Cel:** `Stworzenie nowej tabeli`

Na podstawie tabeli źródłowej przygotowano unikalną listę serwisantów wykorzystywaną w modelu danych (relacje, filtrowanie, slicery).

**Zastosowane operacje:**

Tabela źródłowa została zduplikowana, a następnie:

- jawnie określono typy danych kolumn 📝

- wyodrębniono kolumnę identyfikującą serwisanta 👤

- usunięto duplikaty, tworząc listę unikalnych wartości ✅

Transformacja ma charakter pomocniczy i służy normalizacji modelu (oddzielenie wymiaru od faktu).


**Kluczowa logika:**

```let

   Source = #"Nagłówki o podwyższonym poziomie",



   ChangedTypes = Table.TransformColumnTypes(

       Source,

       {

           {"Data", type date},

           {"Sandra", Int64.Type},

           {"Kamila", Int64.Type},

           {"Stefan", Int64.Type},

           {"Michał", Int64.Type}

       }

   ),



   SerwisantOnly = Table.SelectColumns(

       ChangedTypes,

       {"Serwisant"}

   ),



   DistinctSerwisant = Table.Distinct(

       SerwisantOnly

   )



in

   DistinctSerwisant
```