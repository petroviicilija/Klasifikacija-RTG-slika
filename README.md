**Klasiﬁkacija anatomskih X-ray struktura pomoću DenseNet121**
Ovaj projekat predstavlja kompletan pipeline za treniranje, evaluaciju i analizu modela za klasifikaciju anatomskih regiona na X-ray slikama. Implementacija uključuje:

automatsko učitavanje i strukturiranje medicinskog dataset-a

prilagođeni PyTorch Dataset i DataLoader

napredne augmentacije za povećanje robustnosti

fine-tuning DenseNet121 na grayscale X-ray slikama

trening sa Cosine Annealing Warm Restarts, Early Stopping, AdamW

detaljnu evaluaciju: konfuziona matrica, izveštaji, analiza grešaka

vizuelizaciju predikcija, metrika i učinka po klasama

**Licence**
Kod i model su otvoreni za istraživačke i edukativne svrhe. Dataset je vlasništvo originalnih autora.
https://cloud.visaris.com/index.php/s/tT2qKG4YLHmf4Wo

**Sadržaj projekta**

Data Loading – Učitavanje slika, ekstrakcija labela, proveravanje dataset-a

Transforms – Augmentacije specifične za medicinske slike

Dataset & DataLoader – Prilagođena klasa za X-ray dataset

Model – Modifikovani DenseNet121 za 1-kanalne slike

Training – kompletna petlja obuke i validacije

Early Stopping i najbolji model checkpoint

Evaluation – accuracy, precision, recall, F1-score

Confusion Matrices – detaljne heatmap vizualizacije

Per-Class Analysis – statistike i najčešće greške

Visualization – prikaz predikcija sa sigurnošću modela

**Model**

Koristi se DenseNet121 pretreniran na ImageNet-u, prilagođen za grayscale slike:

conv0 modifikovan da prima 1 kanal

izlazna classifier linijska mreža podešena prema broju klasa

Optimizator i scheduler:

AdamW (lr=1e-4, weight_decay=5e-3)

CosineAnnealingWarmRestarts – stabilnije učenje

Early Stopping – zaustavlja trening kada se validacioni gubitak ne popravlja

**Augmentacije**

Na trening delu koristi se set augmentacija optimizovan za medicinske slike:

RandomAffine (rotacija, translacija, skaliranje)

Horizontal & Vertical flip

ColorJitter (brightness/contrast)

Normalize(mean=0.5, std=0.5)

Val/Test transformacije su konzervativne:

Resize → Normalize

**Trening i Validacija**

Pipeline obuhvata:

praćenje trening/validacionog gubitka

praćenje preciznosti

LR schedulering po epoch-ama

čuvanje najboljih težina modela

Na kraju se vizuelno prikazuju:

Loss per epoch

Accuracy per epoch

**Evaluacija**

Na test skupu se računaju:

Accuracy

Macro Precision

Macro Recall

Macro F1-score

**Vizuelizacija predikcija**

Primer prikaza jedne figure:

originalna grayscale slika

predikcija modela

confidence

označen okvir (zelen ako je tačno, crven ako je pogrešno)

**Rezultati**

Zavise od dataset-a, ali tipično uključuju:

80–95% ukupne tačnosti

macro F1-score

plotovi za treniranje

matrice konfuzije

analizu najtežih anatomskih struktura
