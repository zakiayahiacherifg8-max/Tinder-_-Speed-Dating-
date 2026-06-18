# 💘 TINDER _ Speed Dating Analysis — Décoder l'attraction

> Analyse exploratoire des mécanismes réels de l'attraction lors d'événements de speed dating —
> entre ce que les gens déclarent vouloir et ce qui gouverne réellement leurs choix.

![Python](https://img.shields.io/badge/Python-3.11-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![Pandas](https://img.shields.io/badge/Pandas-NumPy-purple)
![Stats](https://img.shields.io/badge/Statistiques-inférentielles-green)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📌 Contexte

Réalisé dans le cadre d'un cas pratique pour **Tinder**, confronté à une baisse des matchs sur sa plateforme. Pour comprendre ce qui suscite l'intérêt entre les personnes, Tinder a mis à disposition les données d'expériences de **speed dating** organisées par la Columbia Business School (2002–2004).

Chaque rendez-vous durait **4 minutes**. Après chaque rencontre, les participants décidaient s'ils souhaitaient revoir la personne et l'évaluaient sur 6 critères. Ils remplissaient également des questionnaires détaillés sur leurs préférences, leur perception d'eux-mêmes et leurs valeurs.

Il en résulte un dataset qui capture à la fois **ce que les gens disent** et **ce qu'ils font réellement**.

---

## 📊 Chiffres clés

| Métrique | Valeur |
|---|---|
| Rendez-vous analysés | 8 378 |
| Participants uniques | 551 |
| Vagues d'expérimentation | 21 |
| Variables disponibles | 195 |
| Taux de match global | 16,5% |
| AUC du modèle prédictif | 0,80 |

---

## 🔍 Résultats clés

### 1. Le grand écart déclaré / réel
Les hommes prétendent chercher un équilibre entre les attributs. Dans les faits, **l'attractivité physique domine massivement leurs décisions**. Les corrélations point-bisériales révèlent un écart systématique entre les préférences avouées et les comportements effectifs — chez les deux genres.

> Corrélation attractivité physique × décision : **r = +0,43** chez les hommes

### 2. Différences Hommes / Femmes significatives
Les femmes valorisent davantage la **sincérité**, l'**intelligence** et l'**ambition**. Les hommes, l'**attractivité physique**. Ces écarts sont confirmés par des tests de Mann-Whitney sur l'ensemble des 6 attributs.

> 6/6 attributs présentent des différences statistiquement significatives (p < 0,001)

### 3. Biais d'auto-perception universel
Hommes comme femmes **surestiment leur propre attractivité physique** par rapport aux notes réellement reçues de leurs partenaires. Le biais est plus marqué chez les hommes.

> Surestimation moyenne : **+0,9 pt** (hommes) · **+0,5 pt** (femmes)

### 4. Intérêts communs > Origines communes
Les intérêts partagés ont un effet mesurable et significatif sur le match (r = 0,031, p < 0,01). La même origine ethnique n'est pas statistiquement significative une fois les autres variables contrôlées.

> Intérêts élevés + origines différentes : **18,6% de match**
> Intérêts faibles + même origine : **16,1% de match**

### 5. Fatigue décisionnelle en fin de soirée
Tendance à dire "oui" moins souvent à mesure que la soirée avance. Corrélation de Spearman négative entre l'ordre du rendez-vous et le taux de décision favorable.

> Effet modéré, non dominant (r ≈ −0,25)

### 6. Modèle prédictif : les 4 minutes suffisent
Une régression logistique sur les attributs évalués lors du rendez-vous atteint une **AUC de 0,80**, confirmant que les signaux émis en 4 minutes sont suffisants pour prédire un match dans 8 cas sur 10.

---

## 💡 Recommandations produit pour Tinder

**01 · Algorithme de matching**
Pondérer davantage l'attractivité perçue dans le scoring de compatibilité — c'est le signal le plus prédictif, quelle que soit la rhétorique des utilisateurs.

**02 · Profils enrichis**
Encourager les photos de qualité (facteur #1 réel). Les sections "intérêts" ont un impact secondaire mais fidélisent — les garder pour réduire le churn.

**03 · Calibration des attentes**
Les utilisateurs surestiment leur attractivité → recommander des profils légèrement au-dessus de leur tier réel pour maximiser les matchs effectifs.

**04 · Limiter le volume par session**
Réduire la fatigue décisionnelle, observée dès le milieu des soirées speed dating. Moins de profils par session = meilleures décisions.

**05 · Matching différencié par genre**
Les critères de compatibilité ne devraient pas être symétriques H/F — les priorités sont statistiquement distinctes sur l'ensemble des attributs.

---

## 🗂️ Structure du notebook

```
01 · Chargement & nettoyage          → 195 variables, gestion des valeurs manquantes
02 · Statistiques descriptives        → Distributions, taux de match, profils démographiques
03 · Différences Hommes / Femmes      → Préférences déclarées + tests Mann-Whitney
04 · Déclaré vs. réel                 → Corrélations point-bisériales, visualisation de l'écart
05 · Perception de soi                → Auto-évaluation vs. notes reçues, biais quantifié
06 · Effet d'ordre                    → Position dans la soirée et fatigue décisionnelle
07 · Intérêts communs & origine       → Tests χ², impact comparé sur les matchs
08 · Matrice de corrélation           → Vue d'ensemble des relations entre variables
09 · Modèle prédictif                 → Régression logistique — AUC 0.80, coefficients standardisés
10 · Recommandations produit          → 5 leviers actionnables pour Tinder
```

---

## 🛠️ Stack technique

| Outil | Usage |
|---|---|
| **Python 3.11** | Langage principal |
| **Pandas / NumPy** | Manipulation et nettoyage des données |
| **Matplotlib / Seaborn** | Visualisations |
| **SciPy** | Tests statistiques (Mann-Whitney, chi², point-bisériale, Spearman) |
| **Scikit-learn** | Régression logistique, StandardScaler, ROC-AUC |
| **Jupyter Notebook** | Environnement d'analyse et de restitution |

---

## 📁 Données

- **Source** : Columbia Business School Speed Dating Experiment
- **Période** : 2002–2004
- **Format** : CSV (8 378 lignes × 195 colonnes)
- **Documentation** : Data key fournie par les auteurs de l'étude

---

> *"We say we want a soulmate, but we swipe on a face."*
> Ce dataset le prouve empiriquement.
