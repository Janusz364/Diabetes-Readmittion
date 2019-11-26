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
Wartość readmitted=0 pacjent nie wróci wciągu 30 dni do szpitala<br>


## Miara
Miarą sukcesu (ang. *success metric*) jest współczynik RMSLE: <br>
$RMSLE=\sqrt{\frac{1}{n}\sum_{i=1}^{n} (log(p_i+1)-log(a_i+1))^2}= \sqrt{\frac{1}{n}\sum_{i=1}^{n} \Big(\log{\frac{p_i+1}{a_i+1}}\Big)^2}$

$a_i$ -wartości rzeczywiste <br>
$p_i$ - wartość predykcji <br>


## Kaggle
Konkurs dostępny na Kaggle - link do konkursu: https://www.kaggle.com/c/diabetes-readmission/).

## Dane treningowe i testowe
W danych jest **66 221** wierszy, które zostały podzielone prawie na równe cześci: <br>
- train (33 051 wierszy) <br>
- test (33 170 wierszy) - to trochę większy zbiór niż testowy, więec trzeba będzie spojrzeć na krzywą uczenia

## Zmienne
<b>encounter_id</b> - Unikalny identyfikator spotkania<br>
<b>patient_nbr</b> - Unikalny identyfikator pacjenta<br>
<b>race</b> - Rasa<br>
<b>gender</b> - Płeć<br>
<b>age</b> - Wiek pogrupowany w 10-letnich interwałach<br>
<b>weight</b> - Waga w funtach<br>
<b>admission_type_id </b>- Cyfrowy identyfikator rodzaju przyjęcia do szpitala (np. "awaryjny", "nowo narodzony" itp.)<br>
<b>discharge_disposition_id</b> - Cyfrowy identyfikator rodzaju wypisania ze szpitala (np. "przeterminowane", "zwolniony do domu" itp.)<br>
<b>admission_source_id</b> - Cyfrowy identyfikator źródła wizyty (np. "transfer z innego szpitala", "skierowanie od lekarza" itp.)<br>
<b>time_in_hospital</b> - Czas w szpitalu w dniach<br>
<b>payer_code</b> - Identyfikator rodzaju płatności (np. czy pacjent sam płacił albo czy miał ubezpieczenie w Blue Cross/Blue Shield itp.)<br>
<b>medical_specialty</b> - Specjalizacja lekarza, który przyjął pacjenta<br>
<b>num_lab_procedures</b> - Ilość testów laboratoryjnych przeprowadzonych w trakcie spotkania<br>
<b>num_procedures </b>- Ilość procedur (innych, niż testy laboratoryjne) przeprowadzonych w trakcie spotkania<br>
<b>num_medications</b> - Ilość unikalnych lekarstw podanych w trakcie spotkania<br>
<b>number_outpatient</b> - Ilość wizyt ambulatorium przez pacjenta w ciągu roku poprzedzającego spotkanie<br>
<b>number_emergency</b> - Ilość awaryjnych (ang. emergency) wizyt pacjenta w ciągu roku poprzedzającego spotkanie<br>
<b>number_inpatient</b> - Ilość hospitalizowanych wizyt pacjenta w ciągu roku poprzedzającego spotkanie<br>
<b>diag_1 </b>- Pierwotna diagnoza (oznaczona jako 3 pierwsze cyfry wg standardu ICD9)<br>
<b>diag_2 </b>- Wtórna diagnoza (oznaczona jako 3 pierwsze cyfry wg standardu ICD9)<br>
<b>diag_3 </b>- Dodatkowa wtórna diagnoza (oznaczona jako 3 pierwsze cyfry wg standardu ICD9)<br>
<b>number_diagnoses </b></b>- Ilość diagnoz wprowadzona do systemu<br>
<b>max_glu_serum </b>- Wynik badań na glukozę.<br>
<b>A1Cresult </b>- Wynik badania A1c. ">8" jeśli wynik był większy, niż 8%, ">7" jeśli wynik był większy, niż 7%, ale mniejszy, niż 8%. "normal" jeśli wynik jest mniejszy, niż 7%<br>
<b>change </b>- Informacja, czy była zmiana w lekarstwach (zarówno dawka, jak i rodzaj leku)<br>
<b>diabetesMed</b> - Informacja, czy była recepta na dowolne lekarstwa na cukrzycę<br>
<b>24 kolumny z nazwami lekarstw</b> (metformin, repaglinide, nateglinide, chlorpropamide, glimepiride, acetohexamide, glipizide, glyburide, tolbutamide, pioglitazone, rosiglitazone, acarbose, miglitol, troglitazone, tolazamide, examide, sitagliptin, insulin, glyburide-metformin, glipizide-metformin, glimepiride-pioglitazone, metformin-rosiglitazone, metformin-pioglitazone) - Mówi o tym czy dawka na dane lekarstwo została zwiększona, zmniejszona, czy pozostała bez zmian, lub czy w ogóle nie było recepty na to lekarstwo<br>
<b>readmitted </b>- Czy w ciągu 30 dni pacjent był ponownie skierowany do hospitalizacji<br>
<b>id </b>- Unikalne id obserwacji (potrzebne do Kaggle)<br>
