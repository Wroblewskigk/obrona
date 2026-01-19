# 12 Gromadzenie informacji medycznych – klasyfikacje, rekordy pacjenta

## Klasyfikacje

### ICD10/11 - International Classification of Diseases 

The International Classification of Diseases (ICD) (Po Polsku: **Międzynarodowa Statystyczna Klasyfikacja Chorób i Problemów Zdrowotnych lub Międzynarodowa Klasyfikacja Chorób**) is a globally used medical classification that is used in epidemiology, health management and clinical diagnosis. The ICD is maintained by the World Health Organization (WHO), which is the directing and coordinating authority for health within the United Nations System.[1] The ICD was originally designed as a health care classification system, providing a system of diagnostic codes for classifying diseases, including nuanced classifications of a wide variety of signs, symptoms, abnormal findings, complaints, social circumstances, and external causes of injury or disease. This system is designed to map health conditions to corresponding generic categories together with specific variations; for these designated codes are assigned, each up to six characters long. Thus each major category is designed to include a set of similar diseases.

### SNOMED / SNOMED CT - Systematized Nomenclature of Medicine + Clinical Terms

SNOMED to najbardziej kompleksowa, wielojęzyczna i międzynarodowa terminologia kliniczna, służąca do ustrukturyzowanego opisu danych pacjenta w elektronicznej dokumentacji medycznej

SNOMED CT or SNOMED Clinical Terms is a systematically organized computer-processable collection of medical terms providing codes, terms, synonyms and definitions used in clinical documentation and reporting. SNOMED CT is considered to be the most comprehensive, multilingual clinical healthcare terminology in the world.[1][2] The primary purpose of SNOMED CT is to encode the meanings that are used in health information and to support the effective clinical recording of data with the aim of improving patient care. SNOMED CT provides the core general terminology for electronic health records. SNOMED CT comprehensive coverage includes: clinical findings, symptoms, diagnoses, procedures, body structures, organisms and other etiologies, substances, pharmaceuticals, devices and specimens.

**W przeciwieństwie** do ICD-11, SNOMED CT nie pełni funkcji klasyfikacji dla statystyk, lecz dla precyzyjnego kodowania klinicznych obserwacji w elektronicznej dokumentacji medycznej.

### ECS?

## Standardy wymiany danych

### HL7 - Health level 7

#### **HL7 v2: Rozpowszechniony, Ale Przestarzały Standard Komunikatów**

HL7 v2 (Health Level Seven version 2), opracowany w latach 1990-tych, stanowi de facto standard wymiany komunikatów medycznych w ~90% szpitali w Stanach Zjednoczonych. Protokół bazuje na komunikatach ASCII o określonej strukturze segmentów (np. PID dla danych pacjenta, OBX dla wyników obserwacji) oddzielonych specjalnymi znaki delimitacyjnymi.Charakterystyka HL7 v2:

- Format tekstowy (ASCII), łatwy do analizy dla człowieka
- Wymierna niezawodność z potwierdzeniami dostarczenia
- Niska złożoność implementacyjna
- Brak wsparcia dla semantyki; kodowanie terminów wymaga dodatkowych słowników (SNOMED CT, LOINC)
- Trudności z integracją aplikacji mobilnych i API-based

Pomimo rozpowszechnienia, HL7 v2 wykazuje fundamentalne ograniczenia w erze cyfryzacji: elastyczność niska (niestandardowe rozszerzenia i „flavor" lokalnych), brak formalnego wsparcia dla międzysystemowych transformacji, oraz wysoki koszt operacyjny (parsing, walidacja, mapowanie kodów).
​
#### **HL7 v3/CDA: Semantyka i Strukturalność Kosztem Złożoności**

HL7 v3 (Health Level Seven version 3), wprowadzony w 2005 roku, przesunął paradygmat z komunikatów na dokumenty strukturalne, wykorzystując XML (eXtensible Markup Language) jako format bazowy. Kluczowym komponentem HL7 v3 jest **Clinical Document Architecture (CDA)**, specyfikacja dla wymiany dokumentów medycznych (wypisów, raportów, notek klinicznych). CDA definiuje sześć cech dokumentu medycznego:

- Persistence: Dokument jest trwałym rekordem zdarzenia klinicznego
- Stewardship: Odpowiedzialność za dokument jest jasno określona
- Authentication: Dokument może być podpisany cyfrowo
- Context: Informacja o pacjencie, czasie, miejscu zdarzenia
- Wholeness: Dokument stanowi samodzielną jednostkę informacyjną
- Human Readability: Obowiązkowa część tekstowa dla człowieka + opcjonalne części maszynowe

Struktura CDA kombinuje obowiązkową część tekstową (zapewniającą czytelność dla człowieka) z opcjonalnym XML-structured body dla przetwarzania maszynowego. Kodowanie terminów w CDA uwzględnia SNOMED CT i LOINC, umożliwiając semantyczną interoperacyjność.

**Polska Implementacja Krajowa (PIK) HL7 CDA**, opracowana przez Centrum e-Zdrowia, stanowi adaptację standardu do polskich wymagań i rejestrów medycznych. Transport CDA może odbywać się poprzez HL7 v2, HL7 v3, protokoły IHE (Integrating the Healthcare Enterprise), DICOM, czy tradycyjne email/HTTP.

Główną wadą HL7 v3/CDA jest wysoka złożoność implementacji – model RIM (Reference Information Model), skomplikowana semantyka i obowiązkowe XML sprawdzanie schematu utrudniają adopcję zwłaszcza dla mniejszych placówek medycznych.

#### **HL7 FHIR (Fast Healthcare Interoperability Resources)**

Wprowadzony w 2014 roku, reprezentuje paradygmatyczną zmianę w wymianie danych medycznych poprzez adheres do współczesnych standardów web API. FHIR łączy uproszczoną strukturę HL7 v2 z semantyczną mocą HL7 v3, oferując jednocześnie nowoczesną architekturę REST API.Cechy charakterystyczne FHIR:

- RESTful Architecture: Utilizacja standardowych operacji HTTP (GET, POST, PUT, DELETE) na zasobach medycznych
- JSON/XML Formats: Obsługa obu formatów serializacji, przy preferencji dla JSON (lżejszy, popularny w mobilnych aplikacjach)
- Resource-Based Design: Zasoby (Resources) reprezentujące obiekty medyczne – Patient, Condition, Encounter, MedicationStatement, Laboratory Observation
​- Modularity: Implementacja poddawanych profili FHIR – standaryzujących struktury zasobów dla konkretnych przypadków użycia
- Versioning: Wsparcie dla przechowywania wersji zasobów i dostępu do historycznych stań

Przykładowe zasoby FHIR i ich mapowanie do danych klinicznych:

- Patient: Dane demograficzne pacjenta
- Condition: Stan zdrowia, diagnoza (kodowana w SNOMED CT)
- Encounter: Wizyta kliniczna, hospitalizacja
- Observation: Wynik laboratoryjny (kodowany w LOINC)
- MedicationStatement: Historia leków
- AllergyIntolerance: Alergie i nietolerancje

Wymiana zasobów FHIR realizuje się dwoma podejściami: (1) document-based – wysyłanie kompletnych dokumentów (analogia do CDA), lub (2) REST interactions – manipulacja zasobami poprzez HTTP operacje z serwera zgodnego ze standardem FHIR. W praktyce mobilne aplikacje komunkują się z serwerem FHIR poprzez RESTful API, wysyłając żądania HTTP GET i odbierając odpowiedzi w JSON.

Mandatowe wdrożenie FHIR:
W Stanach Zjednoczonych Centers for Medicare & Medicaid Services (CMS) i Office of the National Coordinator (ONC) wymogli na dostawcach systemów EHR obowiązek udostępniania interfejsów FHIR API. Trend ten przenosi się do Europy – Europejska Przestrzeń Danych o Zdrowiu (EHDS) planuje FHIR jako standard dla europejskich systemów EHR z docelowym wdrożeniem do 2025-2026.

### DICOM - Digital Imaging and Communications in Medicine

Digital Imaging and Communications in Medicine is an international protocol for transmission and management of medical images and related meta-
data. It is mostly used to facilitate communication between software and hardware made by different manufacturers. Examples of DICOM metadata:
1. Patient Data
- Patient’s Name (DICOM Tag 0010,0010)
- Patient ID (DICOM Tag 0010,0020)
2. Study Information
- Study Instance UID (DICOM Tag 0020,000D)
- Referring Physician Name (DICOM Tag
0008,0090)
3. Technical Parameters and Device Information
- Manufacturer’s Model Name (DICOM Tag
0008,1090)
- Modality e.g., CT, MR, US (DICOM Tag
0008,0060)
4. Series and Instance Description
- Series Instance UID (DICOM Tag 0020,000E)
- Series Description (DICOM Tag 0008,103E)
5. Clinical Context and Additional Information
- Body Part Examined (DICOM Tag 0018,0015)
- Additional Patient History (DICOM Tag
0010,21B0)

As of now DICOM is contantly being worked on by American College of Radiology (ACR) and National Electrical Manufacturers Association (NEMA).[31][9]

## Systemy / rekordy pacjenta

### EDM - Elektroniczna dokumentacja medyczna - Wyłącznie Polska implementacja

Elektroniczna Dokumentacja Medyczna (EDM) to polskie designacji dla dokumentacji cyfrowej gromadzonej w ramach Systemu e-Zdrowia (e-health system P1), wdrażanego od 2012 roku. EDM łączy elementy zarówno EMR (dokumentacja placówkowa), jak i EHR (dostęp międzyplacówkowy), będąc przejściem w kierunku pełnej interoperacyjności.

- Struktura EDM w Polsce:
- Transport: Polska Implementacja Krajowa HL7 CDA (PIK HL7 CDA) – wersja CDA dostosowana do polskich wymagań
- Kodowanie: SNOMED CT dla diagnoz (wdrażane), ICD-10 dla statystyk (z przejściem na ICD-11)
- Przechowywanie: Centralne repozytorium w systemie e-Zdrowia
- Dostęp pacjenta: Portal Patient (pacjent.gov.pl) – dostęp do wyników i dokumentacji
- Integracja: API dla placówek medycznych i aplikacji trzecich

### EHR - Electronic health record

Electronic Health Record (EHR) przechodzi poza ograniczenia EMR, oferując międzyplacówkowy dostęp do kompletnej dokumentacji medycznej pacjenta. EHR zawiera nie tylko dane z jednego szpitala, ale zintegrowaną informację ze wszystkich placówek, które pacjent odwiedził – szpitale, kliniki, laboratoria, apteki, pogotowie ratunkowe, a nawet placówki zagraniczne (w ramach międzynarodowych systemów interoperacyjności).

- Zaawansowane funkcjonalności EHR:
- Dostęp pacjenta do własnej dokumentacji medycznej (patient portal)
- Możliwość pobierania raportów laboratoryjnych i wyników obrazowych
- Historia wszystkich wizyt i hospitalizacji
- Informacje o bieżącym leczeniu (leki, plany terapii)
- Wsparcie dla decyzji klinicznych opartej na pełnej historii medycznej
- Integracja z aplikacjami mobilnymi pacjenta (Patient Engagement Apps)

**Kluczowa różnica między EMR a EHR** znajduje się w domenach technicznych: EMR działa zwykle na lokalnych bazach danych placówki, zaś EHR wymaga centralnego repozytorium lub federacyjnej architektury z synchronizacją między placówkami. Semantyczna interoperacyjność wymaga użycia wspólnych standardów kodowania – SNOMED CT dla diagnoz, LOINC dla obserwacji laboratoryjnych, DICOM dla obrazów.
​

### EMR - Electronic medical record

Electronic Medical Record (EMR) reprezentuje cyfrową wersję tradycyjnej karty pacjenta prowadzonej w ramach pojedynczej placówki medycznej (szpital, klinika specjalistyczna, poradnia). EMR zawiera historię leczenia pacjenta u danego dostawcy, obejmując: notatki z wizyt, wyniki badań laboratoryjnych, diagnozy, recepty, alergię oraz kartę szczepień.

- Funkcjonalność EMR:
- Śledzenie danych pacjenta w czasie (trendowanie wartości parametrów)
- Automatyczne przypomnienia o badaniach przesiewowych i kontrolach profilaktycznych
- Wsparcie dla decyzji klinicznych (alerts o interakcjach lekowych)
- Poprawa jakości opieki poprzez redukcję błędów diagnostycznych

Jednak EMR ma fundamentalne ograniczenie: nie wychodzi poza granice organizacji. Jeżeli pacjent trafi do innego szpitala lub specjalisty poza siecią, historia medyczna nie jest dostępna, zmuszając lekarza do powtórnych badań i zwiększając ryzyko pominięcia ważnych informacji.

### Porównanie EDM, EHR, EMR

| Aspekt                    | EMR               | EHR              | EDM                       |
| ------------------------- | ----------------- | ---------------- | ------------------------- |
| Zasięg                    | Wewnątrz placówki | Międzyplacówkowy | Międzyplacówkowy (Polska) |
| Dane laboratoryjne        | ✓                 | ✓                | ✓                         |
| Wyniki obrazowe (DICOM)   | Ograniczone       | ✓                | Rosnące                   |
| Wymiana między placówkami | ✗                 | ✓                | ✓                         |
| Dostęp pacjenta           | Ograniczony       | Pełny            | Rosnący                   |
| Standard transportu       | Niestandardowy    | HL7 FHIR         | PIK HL7 CDA + FHIR        |
| Kodowanie diagnoz         | Lokalnie          | SNOMED CT        | SNOMED CT (rosnące)       |

https://www.perplexity.ai/search/opracuj-mi-nastepujace-tresci-3iIQb8bqQca_kv_QKcqYGA#0