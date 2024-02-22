# Python

| Type          | Description |
| ------------- | ----------- |
| Durée         | 2x45 minutes |
| Rendu         | Pas de rendu |
| Format | Travail individuel |
| Évaluation | Pas de note |

## Objectifs

- Première mise en pratique de Python
- Utiisation de l'interface iPython
- Écrire son premier script Python
- Configuration de l'IDE Visual Studio Code
- Utiliser pip pour installer des packages

## Marche à suivre

En cas de problème, n'hésitez pas à demander de l'aide, nous sommes à votre disposition pour vous aider.

### Installation de Python, quelle distribution ?

Il existe plusieurs distributions de Python, la plus connue est [Anaconda](https://www.anaconda.com/products/distribution). Elle est très complète et contient de nombreux packages. Néanmoins elle est aussi très lourde et contient des packages qui ne sont pas forcément utiles tous les jours.

Il existe des alternatives très intéressantes comme [Miniconda](https://docs.conda.io/en/latest/miniconda.html) qui est une version allégée d'Anaconda.

Sans devoir installer une distribution, vous pouvez aussi installer Python directement depuis le site officiel [Python.org](https://www.python.org/downloads/). Ou mieux encore utiliser le *store* Windows si vous êtes sous Windows.

Python étant essentiellement un programme écrit prioritairement pour un système POSIX (Linux, MacOS, Unix, Android...) il est souvent plus simple de l'installer sur ces systèmes et fort heureuseemnt sous Windows vous pouvez utiliser WSL2 (Windows Subsystem for Linux) pour installer Python.

Vous êtes libre d'installer la distribution que vous voulez, mais pour ce cours nous aurons besoin des éléments suivants :

1. Python 3.10 ou plus récent
2. `pip` (le gestionnaire de paquets de Python)
3. `ipython` (un shell interactif pour Python)
4. Être capable d'afficher des fenêtres graphiques

### Installation et configuration de Git

Si vous ne l'avez pas déjà fait, ayez une version récente de [Git](https://git-scm.com/) installée sur votre machine. Sous WSL2, Git est déjà installé par défaut. Sous Windows vous pouvez installer Git depuis [Winget](https://winget.run/pkg/Git/Git).

Pour ce cours nous utiliserons GitHub pour rendre les travaux pratiques. Nous utiliserons des dépôts privés pour cela. Si vous n'avez pas de compte GitHub, créez-en un et configurez votre clé SSH pour pouvoir cloner et pousser des dépôts plus facilement.

### Installation de Visual Studio Code

Si vous ne l'avez pas fait déjà, installez [Visual Studio Code](https://code.visualstudio.com/). C'est un éditeur de texte très complet et très populaire. Il est très bien intégré avec Python et possède de nombreuses extensions pour faciliter le développement.

### Configuration de Visual Studio Code

1. Ouvrez Visual Studio Code
2. Installez l'extension Python depuis la fenêtre d'extensions
3. Installez l'extension Python Debugger (optionnel)

### Premiers pas avec Ipython

#### Votre calculatrice préférée

Commencez par ouvrir un terminal PowerShell sous Windows ou Ubuntu pour Linux.

Lancez `ipython` pour ouvrir le shell interactif, vous aurez quelque chose commec ceci:

```python
Python 3.10.12 (main, Nov 20 2023, 15:14:05) [GCC 11.4.0]
Type 'copyright', 'credits' or 'license' for more information
IPython 7.31.1 -- An enhanced Interactive Python. Type '?' for help.

In [1]:
```

Le *prompt* `In [1]:` vous indique que vous êtes dans le shell interactif. Vous pouvez taper des commandes Python directement dans ce shell. Commencez par essayez quelques fonctions mathématiques. Vous verrez, iPython deviendra bien vite votre calculatrice préférée.

Essyez les opérateurs suivants :

```python
+ - * / // % ** ^
```

Parvenez-vous à comprendre ce que fait chacun de ces opérateurs ?

Essayez un calcul plus compliqué avec des parenthèses, des opérateurs et même des variables ? Par exemple:

```python
a = 5
b = 3
c = a + b
c
```

Bien vite vous aurez-besoin de fonctionnalités mathématique avec votre calculatrice préférée. Pour ce faire nous aurons besoin d'importer des modules. Essayez d'importer le module `math` et de calculer la racine carrée de 2.

```python
import math
math.sqrt(2)
```

Pouvez-vous également calculer le sinus de 45 degrés ?

Remarquez que vous devez impérativement préfixer les fonctions du module `math` avec `math.` pour les utiliser. C'est parce que la fonction `sqrt` est définie dans le module `math` et non pas dans le module principal de Python. La philosophie de Python est de ne pas surcharger l'espace de nom avec des fonctions inutiles pour ne pas rentrer en conflit avec d'autres fonctions.

Cependant, il est possible d'importer certaines fonctions dans l'espace de nom principal. Par exemple, vous pouvez importer la fonction `sqrt` directement dans l'espace de nom principal avec la commande suivante :

```python
from math import sqrt
sqrt(2)
```

Parfois, il est plus simple d'importer toutes les fonctions d'un module directement dans l'espace de nom principal. Cela peut être fait avec la commande suivante :

```python
pi = 42
from math import *
sqrt(2)
u = sin(2*pi/4)
```

Remarquez que nous avons défini une variable `pi` avant d'importer toutes les fonctions du module `math`. Cela a pour effet de masquer la variable `pi` de votre propre variable `pi`. Cela peut être dangereux et il est préférable de ne pas importer toutes les fonctions d'un module directement dans l'espace de nom principal sauf si vous savez ce que vous faites.

Il existe en Python une variable particulière `_` qui contient le résultat de la dernière expression évaluée. Cela peut être très pratique pour éviter de stocker des résultats intermédiaires dans des variables. Par exemple :

```python
In [1]: 42 + 23
Out[1]: 65
In [2]: _ * 2
Out[2]: 130
```

Sous iPython, chaque expression est numérotée. Vous pouvez vous référer à une expression précédente avec la syntaxe `In[1]` ou `Out[1]`. Cela peut être très pratique pour retrouver un résultat précédent. On peut se référer à l'entrée précédente avec `_i` et à la sortie précédente avec `_`.

Par exemple essayez de récupérer l'entrée ou la sortie d'une cellule, par exemple la cellule 42 si vous l'avez déjà évaluée.

```python
In [84]: _42
In [85]: print(_i42)
```

#### Typage dynamique

Python est un langage à typage dynamique. Cela signifie que vous n'avez pas besoin de spécifier le type des variables que vous utilisez.

Essayez également d'utiliser la fonction `factorial` défini dans le module `math`. Pouvez-vous calculer $425!$ ? Quel est le résultat ?

Vous souvenez-vous qu'en C/C++ les entiers sont stockés sur 32 ou 64 bits ? En Python, les entiers sont stockés sur 64 bits par défaut. Cela signifie que vous pouvez stocker des entiers très grands sans problème. Néanmoins, un entier 64 bits peut stocker la valeur maximum de $2**64-1$ ce qui est bien plus petit que $425!$. Python utilise des entiers arbitrairement grands pour stocker des entiers très grands. Cela peut être très pratique pour faire des calculs mathématiques.

En Python vous n'avez pas à vous souciez du type des variables. Vous pouvez additionner un entier avec un flottant sans problème. Par exemple :

```python
a = 5
b = 3.14
type(a)
type(b)
a = a + b
type(a)
```

Vous noterez que la variable `a` est devenue un flottant après l'addition. Python ajuste automatiquement le type à l'exécution. C'est très pratique.

#### Formattage de chaînes de caractères

À l'instar d'autres langage de programmation, Python dispose d'une fonction `print` qui permet d'afficher des chaînes de caractères. Par exemple :

```python
print("Hello, World!")
```

Il est possible d'insérer des variables dans une chaîne de caractères avec la syntaxe suivante :

```python
name = "John"
print(f"Hello, {name}!")
```

La lettre `f` devant la chaîne de caractères indique que c'est une chaîne de caractères formatée. Vous pouvez insérer des variables entre `{}` dans la chaîne de caractères. Cela peut être très pratique pour afficher des résultats intermédiaires.

Vous pouvez également configurer l'affichage des variables avec des formats spécifiques. Par exemple :

```python
pi = 3.141592653589793
print(f"La valeur de pi est {pi:.2f}")
```

La fonction `print` peut prendre des arguments optionnels par exemple pour spécifier le retour à la ligne ou le fichier de sortie. Par exemple :

```python
print("Hello, World!", end=" ")
print("Hello, World!", file=open("output.txt", "w"))
```

Notez que dans le second cas, vous avez spécifié un fichier de sortie pour la fonction `print`. Cela peut être très pratique pour écrire des logs dans un fichier. Allez-vous dans le fichier `output.txt` pour voir ce qui a été écrit.

Accessoirement vous pouvez spécifier un fichier déjà ouvert comme la sortie d'erreur standard avec `sys.stderr` ou la sortie standard avec `sys.stdout`.

### Fonctions

Créez une fonction qui prend un argument `x` et qui retourne `x^2 + 2x + 1`.

Une fonction en Python s'écrit de la manière suivante :

```python
def f(x):
    return x**2 + 2*x + 1
```

Notez qu'il est important de respecter l'indentation de 4 espaces. Python utilise l'indentation pour définir les blocs de code et non les points virgules ou les accolades comme dans d'autres langages. Notez également la présence d'un `:` à la fin de la ligne de la fonction. C'est une syntaxe propre à Python qui permet de définir un bloc de code.

Appelez votre fonction avec un argument `x` égal à 3 et vérifiez que votre fonction retourne bien 16.

Essayez d'écrire la fonction `fibonacci` qui retourne le n-ième terme de la suite de Fibonacci. La suite de Fibonacci est définie de la manière suivante :

```python
def fibonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fibonacci(n-1) + fibonacci(n-2)
```

Cette fonction est récursive. Cela signifie qu'elle s'appelle elle-même. Cela peut être très pratique pour résoudre des problèmes mathématiques. Néanmoins, il faut faire attention à ne pas créer des boucles infinies. Par exemple, si vous appelez `fibonacci(100)` vous risquez de bloquer votre ordinateur pendant un certain temps. Essayez d'appeler `fibonacci(10)` pour voir le résultat. Puis d'augmenter progressivement la valeur du paramètre pour voir les délais.

Si votre exécution est bloquée, vous pouvez interrompre l'exécution avec `Ctrl+C` sous Linux ou `Ctrl+Break` sous Windows.

### Scripts Python

Depuis Visual Studio Code, créez un nouveau fichier `main.py` et tentez d'implémenter la résolution de l'équation du second degré. L'équation du second degré est définie de la manière suivante :

$$x_{1,2} = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$$

Pour ce faire vous pouvez créer deux fonctions :

1. Une fonction `delta` qui prend trois arguments `a`, `b` et `c` et qui retourne le discriminant de l'équation du second degré.
2. Une fonction `solve` qui prend trois arguments `a`, `b` et `c` et qui retourne les deux solutions de l'équation du second degré.

Pour la valeur de retour, vous pouvez retourner un `tuple` avec les deux solutions. Par exemple :

```python
def foo():
    return 1, 2
```

Essayez d'appeler cette fonction, vous obtiendrez un `tuple` avec deux éléments `(1, 2)`. Vous pouvez accéder aux éléments du `tuple` avec la syntaxe suivante :

```python
a, b = foo()
```

Vous pouvez également accéder à un élément spécifique du `tuple` avec la syntaxe suivante :

```python
a = foo()[0]
```

Pour appeler votre script Python vous avez plusieurs possibilités. Vous pouvez utiliser le shell interactif iPython ou vous pouvez exécuter votre script directement depuis le terminal. Par exemple :

Depuis le shell interactif vous utilisez la commande `%run` pour exécuter un script Python. Par exemple :

```python
%run main.py
```

Depuis le terminal vous utilisez la commande `python` pour exécuter un script Python. Par exemple :

```bash
python main.py
```

### Listes

En Python les tableaux sont appelés des listes. Elles sont par défaut dynamiques et hétérogènes. Cela signifie que vous pouvez stocker des éléments de différents types dans une liste. Par exemple :

```python
a = [1, 2, 3, 4, 5]
b = [1, 2, "Hello", 3.14, True]
```

Pour accéder à un élément spécifique d'une liste vous utilisez la syntaxe suivante :

```python
a[0]
```

Notez que les indices commencent à 0. Vous pouvez également accéder à un élément spécifique en partant de la fin avec des indices négatifs. Par exemple :

```python
a[-1]
```

Vous pouvez également accéder à une tranche de la liste avec la syntaxe suivante :

```python
a[1:3]
```

Cela retourne une nouvelle liste avec les éléments de `a` entre les indices 1 et 3. Notez que l'indice de fin est exclusif. Vous pouvez également omettre l'indice de début ou de fin pour spécifier le début ou la fin de la liste. Par exemple :

```python
a[:3]
```

Essayons de créer une liste de 100 entiers consécutifs. Vous pouvez utiliser la fonction `range` pour cela. Par exemple :

```python
a = list(range(100))
```

Pour récupérer que les valeurs paires de cette liste vous pouvez utiliser la syntaxe suivante :

```python
a[::2]
```

Essayez d'expérimenter avec les opérateurs `+` et `*` sur une liste pour voir ce que cela fait : `[1,2,3,4] + [5,6,7,8]` ou `[1,2,3,4] * 3`.

### Installation de packages

La force de Python réside dans sa communauté et dans les nombreux packages disponibles. Vous pouvez installer des packages avec le gestionnaire de paquets `pip`. Par exemple, pour installer le package `numpy` vous pouvez utiliser la commande suivante depuis votre terminal :

```bash
pip install numpy
```

Le package `numpy` est un package très populaire pour faire des calculs mathématiques. Il est très utilisé dans le domaine de l'analyse de données et du machine learning. Explorons un peu ce package.

`numpy` va rajouter une surchage des opérateurs pour les listes, il permet de changer le comportement par défaut de Python pour les listes. Par exemple :

```python
import numpy as np
a = [1,2,3,4,5]
b = np.array(a)
a * 2
b * 2
```

Vous comprenez la différence ?

### Conclusion

Vous avez maintenant une bonne base pour commencer à écrire des scripts Python. Vous avez appris à utiliser iPython, à écrire des fonctions, des scripts, des listes et à installer des packages. Vous êtes prêt pour la suite du cours.
