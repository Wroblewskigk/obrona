# 12 Gromadzenie informacji medycznych – klasyfikacje, rekordy pacjenta

## Klasyfikacje

### ICD10/11 - International Classification of Diseases 

The International Classification of Diseases (ICD) (Po Polsku: **Międzynarodowa Statystyczna Klasyfikacja Chorób i Problemów Zdrowotnych lub Międzynarodowa Klasyfikacja Chorób**) is a globally used medical classification that is used in epidemiology, health management and clinical diagnosis. The ICD is maintained by the World Health Organization (WHO), which is the directing and coordinating authority for health within the United Nations System.[1] The ICD was originally designed as a health care classification system, providing a system of diagnostic codes for classifying diseases, including nuanced classifications of a wide variety of signs, symptoms, abnormal findings, complaints, social circumstances, and external causes of injury or disease. This system is designed to map health conditions to corresponding generic categories together with specific variations; for these designated codes are assigned, each up to six characters long. Thus each major category is designed to include a set of similar diseases.

### SNOMED / SNOMED CT - Systematized Nomenclature of Medicine + Clinical Terms

SNOMED to najbardziej kompleksowa, wielojęzyczna i międzynarodowa terminologia kliniczna, służąca do ustrukturyzowanego opisu danych pacjenta w elektronicznej dokumentacji medycznej

SNOMED CT or SNOMED Clinical Terms is a systematically organized computer-processable collection of medical terms providing codes, terms, synonyms and definitions used in clinical documentation and reporting. SNOMED CT is considered to be the most comprehensive, multilingual clinical healthcare terminology in the world.[1][2] The primary purpose of SNOMED CT is to encode the meanings that are used in health information and to support the effective clinical recording of data with the aim of improving patient care. SNOMED CT provides the core general terminology for electronic health records. SNOMED CT comprehensive coverage includes: clinical findings, symptoms, diagnoses, procedures, body structures, organisms and other etiologies, substances, pharmaceuticals, devices and specimens.

**W przeciwieństwie** do ICD-11, SNOMED CT nie pełni funkcji klasyfikacji dla statystyk, lecz dla precyzyjnego kodowania klinicznych obserwacji w elektronicznej dokumentacji medycznej.

### ECS?

## Standaryzacja gromadzenia danych

## Standardy wymiany danych

### HL7 - Health level 7

### DICOM

## Systemy 

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