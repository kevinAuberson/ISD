# ISD - SA2022 - TP1 

Fichier de réponses

Professeur: Carlos Peña
Assistant: Thibault Schowing

Étudiant: Kevin - Auberson

-----------------------

#  Partie 1

-----------------------

## Exercice 1

(5 points)

1) Ecrivez un script qui génère une liste contenant un million de valeurs entières aléatoires entre 1 et 10 (y compris) et qui calcule le pourcentage de valeurs paires dans cette liste.

```
# Importation du module random. 
from random import randrange

# Générer une liste de valeurs aléatoire
evenNumber = 0
oddNumber = 0
listRandomNumber=[]

for x in range(1000000):
    listRandomNumber.append(random.randrange(1,11))
    if listRandomNumber[x]%2 == 0:
        evenNumber+=1
    else:
        oddNumber+=1
        
# Générer une liste / compter les valeurs paires et calculer le pourcentage de ces valeurs. 
percentageEven = float(evenNumber/1000000*100)
percentageOdd = float(oddNumber/1000000*100)

# Afficher le résultat
print("Nombre de nombres paires : "+ str(evenNumber))   
print("Pourcentage de nombres paires : "+str(percentageEven)+"%")
print("Nombre de nombres impaires : "+str(oddNumber)) 
print("Pourcentage de nombres impaires : "+str(percentageOdd)+"%")

```


**Points obtenus: /5**
**Remarques:**


## Exercice 2

(10 points)

2.1) Décrivez avec vos mots et l'aide de la documentation les trois methodes décrites ci-dessus, leur différences et les fonctions utilisées. 

Réponse: 

La méthode 1: compte dans une liste concaténée ([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]+[12, 13, 14, 15, 16, 17, 18, 19, 20] dans la première, elle compte les valeurs impaires alors que dans la 2ème les valeurs paires) puis élève la valeur au carré et l'ajoute dans la liste.

La méthode 2: compte dans une séquence de nombre allant de 1 à 20 puis vérifie la condition que lorsque la valeur est plus petite ou égale à 10 et que son modulo par 2 n'est pas égale à 0 (donc nombre impair) ou que la valeur est plus grande que 10 et que son modulo par 2 est égale à 0 (donc nombre pair). Puis toutes les valeurs qui satisfissent cette condition sont élevés au carré et ajouter à la liste.

La méthode 3: compte dans une séquence de nombre allant de 1 à 10 les nombres impairs puis les élèvent au carré et les ajoutent à une première liste. Puis une seconde liste est crée et compte dans une séquence de nombre allant de 12 à 20, les nombres pairs puis les élèvent au carré et les ajoutent à la liste. Pour finir, les deux listes sont concaténés.


2.2) A partir de la liste "objets" données ci-dessous, créez une liste contenant uniquement les mots de la première liste qui contiennent la lettre "z" ou "Z".

```
objets = ["Canicule", "Zoo", "Prix béton 1981", "Pancréas", "Zebre", "Jazz", "Yverdon-les-Bains"]
newList = []

for x in objets:
    if "z" in x:
        newList.append(x)
    elif "Z" in x:
        newList.append(x)
        
print(newList)

```

**Points obtenus: /5**
**Remarques:**

-----------------------

#  Partie 2

-----------------------

(5 points)


1) Pourquoi utiliser NumPy ?

Réponse: NumPy est une library Python pour travailler avec des tableaux qui sont jusqu'à 50 fois plus rapides que les listes Python. C'est très utile en science des données où la vitesse et les ressources sont importantes.


2) Comment s'appelle (n.b. "de quel type est") l'objet "array" dans NumPy et que signifie son nom ?

Réponse:  ndarray est cela signifie tableau à N dimensions


3) Pourquoi utiliser NumPy est-il plus rapide qu'utiliser les listes ?

Réponse: Numpy est plus rapide que les listes car il stocke ses données dans un endroit continu de la mémoire. Ce qui facilite l'accès au processus.


4) A quelle question le code "# Question 4" ci-dessous répond-il ?

Réponse: la question 2 de quel type est l'objet array: <class 'numpy.ndarray'>


5) Affichez la somme des deux derniers éléments du tableau

```
import numpy as np

arr = np.array([1, 2, 3, 4, 5])

print(arr[3]+arr[4])

```


**Points obtenus: /5**
**Remarques:**


-----------------------

#  Partie 3

-----------------------

(5 points)

1) Pourquoi utiliser Pandas ?

Réponse: Pandas nous permet d'analyser les Big Data et nettoyer des données désordonnées pour les rendre lisibles et pertinentes. 

2) Que peut faire pandas (d'après le tuto w3schools) ?

Réponse: Pandas nous permet de trouver les valeurs maximum, minimum, moyen et aussi s'il existe des corrélations entre des colonnes de données.

3) Que fait l'exemple "Question 3" ci-dessous ?

Réponse: Il affiche un tableau 2 dimensions avec les 2 series entrés dans mydataset qui sont ensuite convertis en DataFrame.

4) Compléter la cellule "Question 4" pour afficher les lignes demandées. Utiliser l'attribut *loc* comme décrit dans le tutoriel. Que remarquez vous concernant l'utilisation de simples crochets ([...]) ou doubles crochets ([[x,y]]) pour extraire _une_ colonne du dataframe ? En utilisant la fonction type(), donnez le type de données retournées avec les simples crochets ([...]) ou doubles crochets ([[x,y]]).

Réponse:Le simple crochet nous donne le dtype en plus qu'avec le double crochet. L'affichage est aussi différent dans le premier cas, les valeurs sont listées alors que dans le 2ème cas, le tableau est affiché mais, seulement avec l'index choisi.

Le type du simple crochet est une série : <class 'pandas.core.series.Series'>
Le type du double crochet est un dataframe : <class 'pandas.core.frame.DataFrame'>

5) Complétez le code comme demandé dans la cellule "Question 5 - exercice". Extrait du tutoriel Pandas de w3school.

```
import pandas as pd

df = pd.read_csv("https://www.w3schools.com/python/pandas/dirtydata.csv.txt")

# 1) Enlevez les données manquantes (NaN = Not a Number) et créez un nouveau dataframe appelé df_clean 
#    (n.b ne changez pas le dataframe original, n'utilisez pas *inplace=True*)
#    n'hésitez pas à utiliser "print(df_clean)" pour voir les changements, mais déplacez-le / commentez-le pour ne pas encombrer l'affichage de votre cellule !

df_clean = df.dropna()


# 2) La ligne 26 contient une date au mauvais format. Pour cela nous allons convertir la colonne "Date".
#    Attention a bien faire cette opération sur df_clean et non sur df (modifiez par rapport au tutoriel). 
#    En cas de Warnings, vous pouvez l'ignorer.

df_clean['Date'] = pd.to_datetime(df_clean['Date'])

# 3) La valeur à la ligne 7 vous semble suspecte. Vous pouvez choisir de la remplacer par une valeur qui a plus de sense (45) 
#    ou vous pouvez simplement supprimer la ligne. Basez-vous toujours sur le tutoriel pour réaliser cette tâche. 

df_clean.loc[7, 'Duration'] = 45

# Enfin on affiche notre dataframe propre et ses infos. Décommentez les "print" pour afficher le dataframe df_clean et ses infos

print("\n\n===================== Dataframe ====================\n\n")
print(df_clean)
print("\n\n===================== Infos ====================\n\n")
print(df_clean.info()) 
```

**Points obtenus: /5**
**Remarques:**

-------------
  Partie 4
-------------

(2 points)

1) Pourquoi utiliser Matplotlib ?

Réponse: Afin de visualiser des données sous forme de graphique, la librairie Matplotlib nous le permet sous python.


2) Allez regarder la gallerie des exemples de Matplotlib et regardez rapidement les 5 premières sections (jusqu'à la section "Pie and polar charts compris"). Choisissez 2 types de graphiques (Ou prenez les plus importants: Barchart, Boxplot et Scatterplot) et écrivez une courte description pour chaqu'un d'eux.

Réponse: Boxplot : montre une distribution de données et nous aide à voir le centre de celle-ci. Cependant, il permet aussi d'identifier des valeurs aberrantes.
         Histogramme : montre la forme des valeurs et nous aide à voir la dispersion des donnés.

3)Donnez rapidement une description contenu du dataset avec vos mots

Réponse: Le dataset nous permet de créer un jeu de donnée.


**Points obtenus: /5**
**Remarques:**







