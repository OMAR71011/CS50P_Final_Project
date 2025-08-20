# Password Strength Checker (CS50P – Projet final)

#### Video Demo: <URL ICI>

## Description

Ce projet est un **analyseur de force de mots de passe** écrit en Python. Il évalue un mot de passe et retourne un **score sur 100**, un **verdict** (Faible, Moyen, Fort, Très fort), ainsi que des **conseils d’amélioration**.

Il permet de pratiquer :

* Les bases de Python (fonctions, structures de contrôle, E/S, parsing d’arguments)
* Les tests unitaires via **pytest**
* La logique de sécurité (longueur, diversité de caractères, entropie, détection de mots de passe communs)

## Fichiers

* **`project.py`** : Logique principale et fonctions d’évaluation (`check_length`, `has_upper`, `has_lower`, `has_digit`, `has_symbol`, `estimate_entropy`, `score_password`, `load_common_passwords`, `is_common_password`) + `main()` pour la ligne de commande.
* **`test_project.py`** : Tests unitaires pour vérifier les fonctions clés et les plages de score.
* **`requirements.txt`** : Dépendances (vide ici).
* **`common_passwords.txt`** *(optionnel)* : Échantillon de mots de passe communs.

## Utilisation

Mode interactif :

```bash
python project.py
```

Avec mot de passe fourni :

```bash
python project.py -p "MonPassw0rd!"
```

Avec fichier de mots de passe communs (optionnel) :

```bash
python project.py -p "MonPassw0rd!" -c common_passwords.txt
```

## Interprétation du score

* **0–39** : Faible — augmentez la longueur, ajoutez diversité et symboles.
* **40–59** : Moyen — améliorez la longueur et/ou la diversité.
* **60–79** : Fort — bon niveau, encore améliorable.
* **80–100** : Très fort — excellent.

## Exemples

| Mot de passe  | Score | Verdict   | Conseils                                            |
| ------------- | ----- | --------- | --------------------------------------------------- |
| `password`    | 20    | Faible    | Ajouter majuscules, chiffres, symboles              |
| `P@ssw0rd123` | 90    | Très fort | Ajouter caractères spéciaux supplémentaires         |
| `12345678`    | 15    | Faible    | Diversifier caractères, ajouter lettres et symboles |

## Tests

Installer `pytest` :

```bash
pip install pytest
```

Lancer les tests :

```bash
pytest -q
```

## Choix techniques

* **Entropie estimée** : `estimate_entropy` calcule L \* log2(N) pour mesurer la résistance d’un mot de passe.
* **Score pondéré** : longueur (+30), diversité (+40), entropie (+30), malus (-40) si mot de passe commun.
* **Extensibilité** : seuils et symboles modifiables, possibilité d’ajouter interface graphique ou vérificateur en ligne.
* **Tests** : couvrent la composition, la progression de l’entropie et les plages de score.

## Soumission (CS50P)

Depuis le dossier contenant `project.py`, `test_project.py`, `README.md` (et `requirements.txt` si besoin) :

```bash
submit50 cs50/problems/2022/python/project
```

Vérifiez ensuite votre carnet de notes sur `cs50.me/cs50p` pour déclencher la génération du certificat.
