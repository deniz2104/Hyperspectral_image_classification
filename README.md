# Hyperspectral image classificator using supervised learning

## Descrierea setului de date:

Setul de date indian pines contine informatii despre mai multe tipuri de elemente prezente in respectivul teren.Contine 17 elemente in teren,200 de benzi spectrale,145x145 de pixeli.

## Motivatia:

Scopul proiectului de a folosi metode supervizate in vederea clasificarii imaginii,observand la final capacitatea metodelor de a prezice diverse elemente din teren comparativ cu imaginea din teren reala,ground truth-ul.

## Implementarea:

Avand in vedere ca ma folosesc de `classification_report(...,...)` am definit la inceput un map unde fiecare cifra mapeaza catre o caracteristica a terenului pentru o deducere mai rapida a eficientei algoritmilor.

### Prepocesarea datelor si aplicarea PCA:

-Avand in vedere ca este vorba de o imagine cu 3 dimensiuni,a trebuit sa dau resize la fiecare dintre cele doua componente.
-Am aplicat PCA asupra imaginii pentru a vedea cate elemente retin cea mai multa informatie fara a deveni prea noisy
-Apoi am folosit functia `split_data(...)` pentru a imparti fiecare parte a imaginii in parte
-Aplicarea efectiva a PCA-ului asupra matricii `apply_pca(...)`

### Metoda SVM:vezi descrierea proiectului

- Definita prin functia `train_and_evaluate_svm(...)`

### Metoda RF:vezi descrierea proiectului

- Definita prin functia `train_and_evaluate_rf(...)`

### Functiile pentru SVM si RF:

- idem in ceea ce priveste structura si implemenarea
- Abordarea de clasificarea a imaginii a fost luand fiecare 20% din imagine,iterand de 5 ori prin ea si obtinand informatii de interes.
- Am intializat o lista pentru accurateti si pentru imaginile prezise,am apelat functia `split_data(...)`
- Am impartit in matrici de atrenare si testare,apoi am aplicat PCA
- Am apelat functia `train_and_evaluate_svm/rf(...)` pentru a extrage acuratetea si rezulatul prezis
- Le am adauga in lista,apoi la final am plotat imaginile,am printat performantele fiecarei caracteristici si matricea de confuzie printr-un heatmap

### Plotarea si compararea rezultatelor:

Am adus imaginea prezisa la forma standard pentru a o compara cu ground truth-ul si am afisat langa ground truth-ul.

### Main-ul:

Apeleaza cele doua functii `svm_with_pca()` si `random_forest_with_pca()`.

## Performante:

- SVM: 83% acuratete medie
- RF: 76% acuratete medie

## Concluzii si mai multe detalii:

Vezi descrierea proiectului din Jupyter Notebook
