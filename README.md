# Diabetes-Readmittion

Hospital Readmission of Patients with Diabetes.<br>

# 1. Cel, pomiar celu, dane
Chcemy przewidzieć, czy pacjent z cukrzycą zostanie odesłany do szpitala w ciągu 30 dni. Target zawarto w kolumnie readmitted (wartość readmitted=100 - pacjent wróci w ciagu 30 dni do szpitala,readmitted=0 pacjent nie wróci wciągu 30 dni di szpitala)

## 1.1 Miara
Miarą sukcesu (ang. success metric) jest współczynik RMSLE:

## 1.2. Kaggle
Konkurs dostępny na Kaggle - link do konkursu: https://www.kaggle.com/c/diabetes-readmission/

## 1.3 Dane treningowe i testowe
W danych jest 66 221 wierszy, które zostały podzielone prawie na równe cześci:

train (33 051 wierszy)
test (33 170 wierszy) - to trochę większy zbiór niż testowy, więec trzeba będzie spojrzeć na krzywą uczenia
## 1.4 Zmienne
encounter_id - Unikalny identyfikator spotkania
patient_nbr - Unikalny identyfikator pacjenta
race - Rasa
gender - Płeć
age - Wiek pogrupowany w 10-letnich interwałach
weight - Waga w funtach
admission_type_id - Cyfrowy identyfikator rodzaju przyjęcia do szpitala (np. "awaryjny", "nowo narodzony" itp.)
discharge_disposition_id - Cyfrowy identyfikator rodzaju wypisania ze szpitala (np. "przeterminowane", "zwolniony do domu" itp.)
admission_source_id - Cyfrowy identyfikator źródła wizyty (np. "transfer z innego szpitala", "skierowanie od lekarza" itp.)
time_in_hospital - Czas w szpitalu w dniach
payer_code - Identyfikator rodzaju płatności (np. czy pacjent sam płacił albo czy miał ubezpieczenie w Blue Cross/Blue Shield itp.)
medical_specialty - Specjalizacja lekarza, który przyjął pacjenta
num_lab_procedures - Ilość testów laboratoryjnych przeprowadzonych w trakcie spotkania
num_procedures - Ilość procedur (innych, niż testy laboratoryjne) przeprowadzonych w trakcie spotkania
num_medications - Ilość unikalnych lekarstw podanych w trakcie spotkania
number_outpatient - Ilość wizyt ambulatorium przez pacjenta w ciągu roku poprzedzającego spotkanie
number_emergency - Ilość awaryjnych (ang. emergency) wizyt pacjenta w ciągu roku poprzedzającego spotkanie
number_inpatient - Ilość hospitalizowanych wizyt pacjenta w ciągu roku poprzedzającego spotkanie
diag_1 - Pierwotna diagnoza (oznaczona jako 3 pierwsze cyfry wg standardu ICD9)
diag_2 - Wtórna diagnoza (oznaczona jako 3 pierwsze cyfry wg standardu ICD9)
diag_3 - Dodatkowa wtórna diagnoza (oznaczona jako 3 pierwsze cyfry wg standardu ICD9)
number_diagnoses - Ilość diagnoz wprowadzona do systemu
max_glu_serum - Wynik badań na glukozę.
A1Cresult - Wynik badania A1c. ">8" jeśli wynik był większy, niż 8%, ">7" jeśli wynik był większy, niż 7%, ale mniejszy, niż 8%. "normal" jeśli wynik jest mniejszy, niż 7%
change - Informacja, czy była zmiana w lekarstwach (zarówno dawka, jak i rodzaj leku)
diabetesMed - Informacja, czy była recepta na dowolne lekarstwa na cukrzycę
24 kolumny z nazwami lekarstw (metformin, repaglinide, nateglinide, chlorpropamide, glimepiride, acetohexamide, glipizide, glyburide, tolbutamide, pioglitazone, rosiglitazone, acarbose, miglitol, troglitazone, tolazamide, examide, sitagliptin, insulin, glyburide-metformin, glipizide-metformin, glimepiride-pioglitazone, metformin-rosiglitazone, metformin-pioglitazone) - Mówi o tym czy dawka na dane lekarstwo została zwiększona, zmniejszona, czy pozostała bez zmian, lub czy w ogóle nie było recepty na to lekarstwo
readmitted - Czy w ciągu 30 dni pacjent był ponownie skierowany do hospitalizacji
id - Unikalne id obserwacji (potrzebne do Kaggle)
