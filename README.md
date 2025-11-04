# 💣 Minesweeper — Knowledge-Based AI Solver

> Build an AI agent that plays **Minesweeper** using logical inference and a knowledge base.

Ce projet implémente une version intelligente du célèbre jeu **Minesweeper** :  
l'agent explore la grille, apprend des informations sur les cellules voisines, et déduit où se trouvent les mines — sans triche, uniquement grâce à la logique.

---

## 🎯 Objectif du projet

- Comprendre la représentation des connaissances (Knowledge Representation)
- Implémenter un **agent logique** basé sur des règles
- Construire une base de connaissances dynamique
- Faire des inférences :  
    ✅ cellules sûres → jouer automatiquement  
    ✅ mines → marquer automatiquement  
    ❓ sinon → choisir un coup aléatoire

---

## 📚 Contexte

Minesweeper est un jeu où chaque case révèle un chiffre indiquant combien de mines voisines elle touche.  
L'IA utilise des **phrases logiques** de la forme :

`{(cell1), (cell2), …} = count`

Exemples d'inférences :

- `{D, E, G} = 0` ⟹ D, E, G sont sûres ✅
- `{E, F, H} = 3` ⟹ E, F, H sont toutes des mines 💣
- Subset rule :  
    `{A, B, C} = 1` et `{A, B, C, D, E} = 2` → `{D, E} = 1`

---

## 🧠 Concept clés

|Concept|Description|
|---|---|
|Knowledge base|Ensemble de contraintes `{cells} = count`|
|Inference rules|Déduit mines/safe cells automatiquement|
|Subset resolution|Combine contraintes pour découvrir info|
|Safe-move strategy|Joue une case sûre|
|Random-move fallback|Si le raisonnement ne suffit pas|

---

## 📁 Structure du projet

```bash
minesweeper/ 
│── minesweeper.py   # logiques du jeu + IA (à compléter) 
│── runner.py        # UI graphique (fournie) 
│── README.md
```

---

## 🚀 Exécution du jeu

### Lancer le jeu (joueur humain + IA possible)

`python runner.py`

### Dépendances

`pip3 install -r requirements.txt`

---

## 🧠 Fonctions à implémenter

|Classe|Méthodes|
|---|---|
|`Sentence`|`known_mines`, `known_safes`, `mark_mine`, `mark_safe`|
|`MinesweeperAI`|`add_knowledge`, `make_safe_move`, `make_random_move`|

---

## ✅ Tests officiels

### Vérification du code

`check50 ai50/projects/2024/x/minesweeper`

### Style

`style50 minesweeper.py`

---

## 🧪 Stratégie de l'IA

1. Clique sur une cellule sûre
2. Observe le nombre de mines voisines
3. Ajoute une nouvelle **phrase** dans sa base de connaissances
4. Réduit / combine les phrases existantes
5. Marque mines / cases sûres
6. Joue encore si possible, sinon choisit une case aléatoire

> 💡 L’IA ne gagne pas à tous les coups — parfois, il faut deviner !

---

## 🔍 Conseils de développement

- Implémente progressivement
- Attention à la mutation d'ensembles en boucle
- Chaque modification de la base peut entraîner de nouvelles inférences
- Prioriser :
    - ✅ marquer safe
    - ✅ marquer mines
    - ➕ générer nouvelles phrases par subset rule

---

## 🎓 À propos

Projet issu du cours  
**CS50’s Introduction to Artificial Intelligence with Python**

---

## 🙌 Remerciements

- Harvard CS50 team
- Communauté Ed / Discord / Reddit