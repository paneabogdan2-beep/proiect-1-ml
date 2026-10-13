# proiect-1-ml

E clasificare sau regresie? Ce greșeală a modelului ar costa mai mult în realitate?
Este o clasificare binară (prezicem o categorie discretă: clientul pleacă sau nu). Cel mai mult costă un False Negative (modelul prezice că clientul rămâne, dar el pleacă), deoarece compania pierde clientul definitiv, în timp ce un False Positive aduce doar un cost operațional minor (o promoție oferită unui client loial).

De ce împărțim datele înainte de scalare?
Împărțirea datelor înainte de scalare este obligatorie pentru a preveni scurgerea de informații (data leakage). Parametrii de scalare (media și deviația standard) trebuie calculați doar pe setul de antrenament și aplicați ulterior pe setul de test, simulând scenariul real în care datele viitoare sunt complet necunoscute modelului.

Ce scor are un model care nu știe nimic?
Un model care nu știe nimic (DummyClassifier setat pe clasa majoritară) obține o acuratețe de ~73.4% (ghicind mereu că clientul rămâne), dar are un F1-score de 0 pe clasa minoritară (churn), demonstrând că acuratețea generală este înșelătoare pe date dezechilibrate.

Care a ieșit mai bine și de ce credeți că s-a întâmplat asta?
Random Forest optimizat a ieșit cel mai bine (obținând un F1-score de 0.5595, la limită peste XGBoost). Acest lucru s-a întâmplat deoarece Random Forest gestionează excelent relațiile non-lineare din datele tabulare și reduce riscul de supraîncregere (overfitting) prin combinarea mai multor arbori de decizie antrenați pe subseturi diferite, stabilindu-se eficient după optimizarea hiperparametrilor.

De ce ați ales metrica principală pe care ați ales-o?
Am ales F1-score ca metrică principală de optimizare (în loc de acuratețe) deoarece setul de date este puternic dezechilibrat (~26% clienți care pleacă). F1-score oferă o medie armonică între Precision (câte alarme de plecare au fost reale) și Recall (câți dintre clienții care au plecat au fost depistați efectiv), penalizând modelele care ignoră clasa minoritară în favoarea clasei majoritare.

Am cerut agentului textul cerintei usor modificat:

1. Explorați datele: dimensiune, valori lipsă, distribuția coloanei de prezis, 3 grafice cu câte o propoziție despre ce se vede.
2. Pregătiți datele: împărțire train/test, valori lipsă, coloane text transformate în numere, scalare dacă e nevoie.
3. Baseline: DummyClassifier sau DummyRegressor .
4. Antrenați 3 modele regresie  logistică, Random Forest, XGBoost.
5. Evaluați pe setul de test: la clasificare matrice de confuzie, precision, recall, F1. De ce ați ales metrica principală pe care ați ales-o?
6. Concluzie: ce model recomandați, cât de mult bate baseline-ul și o limitare a analizei.

