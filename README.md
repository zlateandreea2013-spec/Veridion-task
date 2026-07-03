Rezolvare task

Cum am rezolvat potrivirile

592 de companii verificate una cate una manual ar fi durat foarte mult, asa ca am scris un mic
script in Python care compara numele companiei din input cu numele celor 5 candidati (si cu
denumirile lor legale) si le da un scor de similaritate. Cea mai buna potrivire castiga.

Am observat repede ca scorul simplu se pacaleste usor - de exemplu "Apple South Asia Thailand"
s-a potrivit cu o firma numita "Asia Biogas" doar pentru ca ambele au cuvantul "Asia" in nume.
Am adaugat o regula in plus: potrivirea trebuie sa aiba in comun un cuvant care chiar inseamna
ceva (nu cuvinte generice gen "group", "network", "asia", "international").

Asta a scos la iveala vreo 20 de cazuri care nu erau in regula. Le-am verificat manual, uitandu-ma
direct la toti cei 5 candidati. Cateva exemple din ce am gasit:

- Pentru branduri mari (HP, SAP, Dell, LinkedIn) niciunul din cei 5 candidati nu era compania
  reala, ci firme mici fara nicio legatura care aveau intamplator un cuvant comun in nume. Le-am
  lasat nerezolvate.
- Pentru "Job-Index A/S" (o firma daneza), Veridion avea 3 inregistrari aproape identice pentru
  aceeasi companie reala, dintre care una avea un link stricat. Am ales-o pe cea corecta, dupa ce
  am verificat pe google ca site-ul e real.
- Pentru "A.T. Kearney" (o firma de consultanta), algoritmul alesese o subsidiara mai putin
  cunoscuta a lor in loc de compania principala. Am corectat.

La final: din 592, am rezolvat 575 (97%). Restul de 17 le-am lasat nerezolvate, cu motivul notat
pentru fiecare, in loc sa aleg ceva random doar ca sa "bifez" toate randurile.

Ce probleme am gasit in date

- Duplicate ascunse: 14 grupuri de companii diferite din lista clientului (ex. filiale din
  tari diferite ale aceleasi firme) au fost potrivite cu aceeasi inregistrare din Veridion. Practic
  Veridion le vede ca pe o singura companie mare, desi clientul le are ca entitati separate. E util
  de stiut daca clientul vrea cheltuieli calculate pe tara.
- Date lipsa: la aproape jumatate din companii lipseste venitul, numarul de angajati sau anul
  infiintarii. Nu e o greseala, dar trebuie stiut dinainte, nu descoperit dupa ce clientul isi
  construieste un raport pe aceste date.
- Linkuri stricate: vreo 11 companii au in loc de site web un link de redirectionare de la
  Google, nu adresa reala.
- Sustenabilitate: clientul a zis ca ii intereseaza si partea de sustenabilitate. Nu exista un
  camp special pentru asta in date, dar am cautat cuvinte relevante (carbon, reciclare, verde etc.)
  in descrierile companiilor si am gasit ca aproape 1 din 10 companii au deja ceva relevant scris
  acolo. Deci se poate porni de aici, fara sa promitem date care nu exista.
