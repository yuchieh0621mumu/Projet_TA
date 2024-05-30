# Evaluation du moteur de traduction neuronale OpenNMT sur un corpus parallèle anglais-français

Ce projet contient plusieurs notebooks Jupyter dédiés à diverses tâches de traitement automatique du langage naturel (TALN). Les notebooks incluent des scripts pour l'entraînement de modèles de traduction, la lemmatisation de textes et le découpage de corpus.

## Prérequis

Avant d'exécuter les scripts, assurez-vous d'avoir les dépendances suivantes installées :

- Python 3.x
- Jupyter Notebook
- Les bibliothèques Python spécifiées dans chaque notebook (par exemple, `nltk`, `french_lefff_lemmatizer`).

## Contenu

### Entraînement de Modèles de Traduction

1. `openEMT_run1_nolem.ipynb` : Entraînement de modèle de traduction sans lemmatisation pour le run 1.
2. `openNMT_lem_run1.ipynb` : Entraînement de modèle de traduction avec lemmatisation pour le run 1.
3. `openEMT_run2_nolem.ipynb` : Entraînement de modèle de traduction sans lemmatisation pour le run 2.
4. `openNMT_lem_run2.ipynb` : Entraînement de modèle de traduction avec lemmatisation pour le run 2.

### Autres Tâches

5. `split_corpus.ipynb` : Découpage de corpus en ensembles d'entraînement, de validation et de test.
6. `lemmatizer.ipynb` : Lemmatisation des corpus en anglais et en français.

### Description des Runs

#### Run 1

- **Apprentissage :** 100K phrases (Europarl)
- **Tuning :** 3,75K phrases (Europarl)

#### Run 2

- **Apprentissage :** 100K+10K phrases (Europarl+Emea)
- **Tuning :** 3,75K phrases (Europarl)

## Instructions d'Exécution

Chaque notebook contient des cellules de code qui peuvent être exécutées séquentiellement. Voici les étapes pour exécuter chaque notebook :

### Entraînement de Modèles de Traduction

#### Run 1 - Sans Lemmatisation

```bash
jupyter notebook openEMT_run1_nolem.ipynb
```

#### Run 1 - Avec Lemmatisation

```bash
jupyter notebook openNMT_lem_run1.ipynb
```

#### Run 2 - Sans Lemmatisation

```bash
jupyter notebook openEMT_run2_nolem.ipynb
```

#### Run 2 - Avec Lemmatisation

```bash
jupyter notebook openNMT_lem_run2.ipynb
```

### Autres Tâches

#### Découpage de Corpus

```bash
jupyter notebook split_corpus.ipynb
```

#### Lemmatisation des Textes

```bash
jupyter notebook lemmatizer.ipynb
```

### Options de Ligne de Commande

Pour les utilisateurs préférant les scripts en ligne de commande, les fonctions dans les notebooks peuvent être converties en scripts Python. Voici un exemple de script de lemmatisation :

```python
from french_lefff_lemmatizer.french_lefff_lemmatizer import FrenchLefffLemmatizer

lemmatizer = FrenchLefffLemmatizer()

def lemmatize_file_fr(input_file, output_file):
    with open(input_file, 'r') as infile, open(output_file, 'w') as outfile:
        for line in infile:
            lemmatized_line = ' '.join([lemmatizer.lemmatize(word) for word in line.split()])
            outfile.write(lemmatized_line + '\n')

if __name__ == "__main__":
    import argparse

    parser = argparse.ArgumentParser(description='Lemmatize French text files.')
    parser.add_argument('input_file', type=str, help='Path to the input text file')
    parser.add_argument('output_file', type=str, help='Path to the output text file')
    
    args = parser.parse_args()
    
    lemmatize_file_fr(args.input_file, args.output_file)
```

Pour exécuter ce script en ligne de commande :

```bash
python lemmatize_fr.py path/to/input_file.txt path/to/output_file.txt
```

### Exemples d'Utilisation

#### Entraînement du Modèle

1. Ouvrir et exécuter `openEMT_run1_nolem.ipynb` pour entraîner un modèle de traduction sans lemmatisation pour le run 1.
2. Ouvrir et exécuter `openNMT_lem_run1.ipynb` pour entraîner un modèle de traduction avec lemmatisation pour le run 1.
3. Ouvrir et exécuter `openEMT_run2_nolem.ipynb` pour entraîner un modèle de traduction sans lemmatisation pour le run 2.
4. Ouvrir et exécuter `openNMT_lem_run2.ipynb` pour entraîner un modèle de traduction avec lemmatisation pour le run 2.

#### Lemmatisation des Textes

1. Ouvrir et exécuter `lemmatizer.ipynb` pour lemmatiser les corpus en anglais et en français.
2. Utiliser le script en ligne de commande pour lemmatiser un fichier de texte en français.

#### Découpage du Corpus

1. Ouvrir et exécuter `split_corpus.ipynb` pour découper un corpus en ensembles d'entraînement, de validation et de test.

## Auteurs

- WEN, Yu-Chieh
