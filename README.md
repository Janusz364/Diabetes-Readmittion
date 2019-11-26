# Machine Learning for Diabetes Readmittion

Wykorzystanie modeli uczenia maszynowego do przewidywania, czy pacjenci z cukrzycą zostaną ponownie przyjęci do szpitala w ciągu 30 dni<br>

## Kontekst biznesowy
Chcemy zminimalizować refundację dla szpitali o ponadprzeciętnej readmisji. <br>
Dla tych szpitali, które są obecnie karane w ramach tego programu, jednym z rozwiązań jest stworzenie interwencji w celu zapewnienia dodatkowej pomocy pacjentom o zwiększonym ryzyku readmisji. <br>
Pytanie jednak jest takie: <b>jak rozpoznać takich pacjentów?</b> 

## Cel dla ML
Chcemy przewidzieć, czy pacjent z cukrzycą zostanie odesłany do szpitala w ciągu 30 dni.<br>
Target w zbiorze danych treningowych i testowych zawarto w kolumnie readmitted. <br>
Wartość readmitted=100 - pacjent wróci w ciagu 30 dni do szpitala <br>
Wartość readmitted=0 pacjent nie wróci wciągu 30 dni di szpitala<br>


## Miara
Miarą sukcesu (ang. *success metric*) jest współczynik RMSLE: <br>
$RMSLE=\sqrt{\frac{1}{n}\sum_{i=1}^{n} (log(p_i+1)-log(a_i+1))^2}= \sqrt{\frac{1}{n}\sum_{i=1}^{n} \Big(\log{\frac{p_i+1}{a_i+1}}\Big)^2}$

$a_i$ -wartości rzeczywiste <br>
$p_i$ - wartość predykcji <br>


## Kaggle
Konkurs dostępny na Kaggle - link do [konkursu](https://www.kaggle.com/t/5f586fe8eb894a01bdbd4332bbc10d67).

## Dane treningowe i testowe
W danych jest **66 221** wierszy, które zostały podzielone prawie na równe cześci:
- train (33 051 wierszy)
- test (33 170 wierszy) - to trochę większy zbiór niż testowy, więec trzeba będzie spojrzeć na krzywą uczenia

## Zmienne
encounter_id - Unikalny identyfikator spotkania<br>
patient_nbr - Unikalny identyfikator pacjenta<br>
race - Rasa<br>
gender - Płeć<br>
age - Wiek pogrupowany w 10-letnich interwałach<br>
weight - Waga w funtach<br>
admission_type_id - Cyfrowy identyfikator rodzaju przyjęcia do szpitala (np. "awaryjny", "nowo narodzony" itp.)<br>
discharge_disposition_id - Cyfrowy identyfikator rodzaju wypisania ze szpitala (np. "przeterminowane", "zwolniony do domu" itp.)<br>
admission_source_id - Cyfrowy identyfikator źródła wizyty (np. "transfer z innego szpitala", "skierowanie od lekarza" itp.)<br>
time_in_hospital - Czas w szpitalu w dniach<br>
payer_code - Identyfikator rodzaju płatności (np. czy pacjent sam płacił albo czy miał ubezpieczenie w Blue Cross/Blue Shield itp.)<br>
medical_specialty - Specjalizacja lekarza, który przyjął pacjenta<br>
num_lab_procedures - Ilość testów laboratoryjnych przeprowadzonych w trakcie spotkania<br>
num_procedures - Ilość procedur (innych, niż testy laboratoryjne) przeprowadzonych w trakcie spotkania<br>
num_medications - Ilość unikalnych lekarstw podanych w trakcie spotkania<br>
number_outpatient - Ilość wizyt ambulatorium przez pacjenta w ciągu roku poprzedzającego spotkanie<br>
number_emergency - Ilość awaryjnych (ang. emergency) wizyt pacjenta w ciągu roku poprzedzającego spotkanie<br>
number_inpatient - Ilość hospitalizowanych wizyt pacjenta w ciągu roku poprzedzającego spotkanie<br>
diag_1 - Pierwotna diagnoza (oznaczona jako 3 pierwsze cyfry wg standardu ICD9)<br>
diag_2 - Wtórna diagnoza (oznaczona jako 3 pierwsze cyfry wg standardu ICD9)<br>
diag_3 - Dodatkowa wtórna diagnoza (oznaczona jako 3 pierwsze cyfry wg standardu ICD9)<br>
number_diagnoses - Ilość diagnoz wprowadzona do systemu<br>
max_glu_serum - Wynik badań na glukozę.<br>
A1Cresult - Wynik badania A1c. ">8" jeśli wynik był większy, niż 8%, ">7" jeśli wynik był większy, niż 7%, ale mniejszy, niż 8%. <br>"normal" jeśli wynik jest mniejszy, niż 7%<br>
change - Informacja, czy była zmiana w lekarstwach (zarówno dawka, jak i rodzaj leku)<br>
diabetesMed - Informacja, czy była recepta na dowolne lekarstwa na cukrzycę<br>
24 kolumny z nazwami lekarstw (metformin, repaglinide, nateglinide, chlorpropamide, glimepiride, acetohexamide, glipizide, glyburide, tolbutamide, pioglitazone, rosiglitazone, acarbose, miglitol, troglitazone, tolazamide, examide, sitagliptin, insulin, glyburide-metformin, glipizide-metformin, glimepiride-pioglitazone, metformin-rosiglitazone, metformin-pioglitazone) - Mówi o tym czy dawka na dane lekarstwo została zwiększona, zmniejszona, czy pozostała bez zmian, lub czy w ogóle nie było recepty na to lekarstwo<br>
readmitted - Czy w ciągu 30 dni pacjent był ponownie skierowany do hospitalizacji<br>
id - Unikalne id obserwacji (potrzebne do Kaggle)<br>
