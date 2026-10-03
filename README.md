# Temporal fingerprints · Empreintes temporelles

**A logarithmic reference frame of time scales for gravitational and quantum systems**
**Un référentiel logarithmique des échelles de temps pour les systèmes gravitationnels et quantiques**

[![DOI v2.0](https://zenodo.org/badge/DOI/10.5281/zenodo.23116283.svg)](https://doi.org/10.5281/zenodo.23116283)

**Frédérick Vronsky**, independent researcher in theoretical cosmology / chercheur indépendant en cosmologie théorique, Toulouse
ORCID: [0009-0003-5719-9604](https://orcid.org/0009-0003-5719-9604) · October / octobre 2026 · CC BY-NC-SA 4.0

[English](#english) · [Français](#français)

| Archive | Version | Zenodo DOI | Status |
|---|---|---|---|
| `Empreintes temporelles complet  V.2.zip` | **2.0** | [10.5281/zenodo.23116283](https://doi.org/10.5281/zenodo.23116283) | **current / actuelle** |
| `Empreintes temporelles complet V1.1.zip` | 1.1 | [10.5281/zenodo.23107603](https://doi.org/10.5281/zenodo.23107603) | archived / archivée |

---

## English

### What it is

Any physical system with a mass *M*, a length *R* and an observed clock *T*<sub>obs</sub> defines four time scales:

| Symbol | Definition | Meaning |
|---|---|---|
| T<sub>P</sub> | √(ħG/c⁵) | Planck time |
| T<sub>G</sub> | GM/c³ | gravitational time |
| T<sub>C</sub> | R/c | light-crossing time |
| T<sub>obs</sub> | measured | observed clock (period, duration, …) |
| T<sub>Q</sub> | ħ/(mc²) | reduced Compton time (quantum particle) |

This set, together with its dimensionless **relative state**
X = T<sub>G</sub>/T<sub>C</sub> = GM/(Rc²), Y = T<sub>P</sub>/T<sub>G</sub> = M<sub>P</sub>/M, O = T<sub>obs</sub>/T<sub>C</sub> = cT<sub>obs</sub>/R,
is called a **temporal fingerprint**.

### What it does

In the space of the logarithms of these times:

- a change of unit is a translation that leaves (X, Y, O) invariant;
- there are exactly three independent coordinates (Buckingham's theorem as rank–nullity);
- every power law becomes a hyperplane (Kepler's third law: O√X = 2π);
- physical thresholds (Schwarzschild radius X = 1/2, innermost stable orbit X = 1/6, Planck mass Y = 1, Planck length XY = 1, Compton length XY² = 1) cut the space into cells;
- eliminating a variable reduces to computing a kernel;
- the deviation of a system from a law becomes a signed distance, and logarithmic covariances propagate exactly for power laws.

**New in version 2.0:**

- each observed clock has a class (period or duration, signal front, group transit, conditional time, difference of times) that fixes the admissible domain of O;
- signal fronts obey the causal half-space O ≥ 1, and circular orbital clocks obey O > 2π√3 ≈ 10.9, which gives an audit test;
- intrinsically signed quantities get an encoding rule: log of a ratio to a positive reference, arsinh for a sign change through zero, and the inverse for a sign change through a pole;
- applied to recent "negative time" results (cold-atom cloud, artificial atom in front of a mirror, Shapiro delay, time-reversed and time-superposed quantum evolutions), the tool shows which quantity is negative, without making any fundamental time scale negative;
- corrections to version 1.1, listed in the paper and on the Zenodo page.

**This is a methods paper.** It proposes no new dynamics and modifies neither general relativity nor quantum mechanics. It builds a coordinate system in which known laws become linear, so that very different systems can be classified, compared and audited in a common language.

### Contents of each archive

Both archives have the same structure.

| File | Contents |
|---|---|
| `Temporal_fingerprints_EN.pdf`, `Empreintes_temporelles_FR.pdf` | the paper in English and French (v2.0: 21 pages each; v1.1: 16 pages) |
| `code_python.zip` | Python code and XeLaTeX sources: unzip it to get the `code/` and `papier/` folders |
| `atlas_temporel.csv` | temporal atlas of 33 systems, with sources |
| `banc_empreintes.html` | interactive bench |
| `README.md`, `CITATION.cff` | inside the v2.0 archive only |

Inside `code_python.zip`:

| Path | Contents | v1.1 | v2.0 |
|---|---|---|---|
| `code/empreintes.py` | Python module: fingerprint, relative state, hyperplanes and residuals, kernel elimination, uncertainty propagation, quantum extension, Hubble sphere; in v2.0 also clock classes and signed encodings | ✓ | ✓ |
| `code/test_empreintes.py` | numerical tests | 10 | 15 |
| `code/verifier_equations.py` | symbolic check (sympy) of every equation | 36 | 56 |
| `code/reproduire_papier.py` | recomputes every number, the atlas and the figures | ✓ | ✓ |
| `code/atlas.py`, `code/figures.py` | atlas and figures (French and English) | ✓ | ✓ |
| `papier/*.tex` | XeLaTeX sources of the paper | ✓ | ✓ |

**The atlas (v2.0)** covers 33 systems, from the proton to the Hubble sphere. Each row gives:
- M, R and T<sub>obs</sub> (when one exists), the nature and class of T<sub>obs</sub>, and the definition and status of R;
- T<sub>P</sub>, T<sub>G</sub>, T<sub>C</sub> and T<sub>Q</sub> in seconds;
- log₁₀X, log₁₀Y, log₁₀O and log₁₀(g/a<sub>P</sub>);
- the Kepler residual, the conventional regime (in French and English) and the source.

**The interactive bench** is a single HTML file to open in any web browser. It needs no installation and no internet connection, and it collects no data. The interface is in French.
- Pick a system from the atlas, or set M, R and T<sub>obs</sub> with sliders.
- Choose the clock class; the bench flags inconsistent values (O ≤ 2π√3 for a circular orbit, O < 1 for a signal front).
- Add a quantum particle to get its Compton time, the self-gravity and internal-clock phases, and the minimum duration to reach quadrant Q4.
- See the result on the paper's three maps: the clock plane (X, O), the (X, Y) plane and the quantum quadrants.

### Usage

```bash
unzip "Empreintes temporelles complet  V.2.zip"
cd github_v2
unzip code_python.zip                     # creates code/ and papier/
pip install -r code/requirements.txt      # numpy, scipy, matplotlib, sympy
cd code
python test_empreintes.py                 # numerical tests
python verifier_equations.py              # symbolic verification
python reproduire_papier.py               # all numbers, atlas and figures
```

```python
from empreintes import Fingerprint, M_sun, AU, yr, admissible_O, asinh_coord
earth = Fingerprint(M=M_sun, R=AU, T_obs=yr, clock="orbit", name="Earth around the Sun")
print(earth.X, earth.Y, earth.O)
print(earth.kepler_residual())     # ≈ -1.9e-5: on Kepler's law
print(admissible_O(0.95, "P"), admissible_O(0.95, "F"))   # True False
print(asinh_coord(-3.0, 1.0))      # signed encoding of a negative delay
```

To compile the paper, run `cd papier && xelatex empreintes_en.tex` twice.

---

## Français

### De quoi s'agit-il

Tout système physique doté d'une masse *M*, d'une longueur *R* et d'une horloge observée *T*<sub>obs</sub> définit quatre échelles de temps :

| Symbole | Définition | Signification |
|---|---|---|
| T<sub>P</sub> | √(ħG/c⁵) | temps de Planck |
| T<sub>G</sub> | GM/c³ | temps gravitationnel |
| T<sub>C</sub> | R/c | temps de traversée lumineuse |
| T<sub>obs</sub> | mesuré | horloge observée (période, durée…) |
| T<sub>Q</sub> | ħ/(mc²) | temps de Compton réduit (particule quantique) |

Cet ensemble, accompagné de son **état relatif** sans dimension
X = T<sub>G</sub>/T<sub>C</sub> = GM/(Rc²), Y = T<sub>P</sub>/T<sub>G</sub> = M<sub>P</sub>/M, O = T<sub>obs</sub>/T<sub>C</sub> = cT<sub>obs</sub>/R,
est appelé **empreinte temporelle**.

### Ce que l'outil permet

Dans l'espace des logarithmes de ces temps :

- un changement d'unité est une translation qui laisse (X, Y, O) invariant ;
- il y a exactement trois coordonnées indépendantes (le théorème de Buckingham vu comme théorème du rang) ;
- toute loi en loi de puissance devient un hyperplan (troisième loi de Kepler : O√X = 2π) ;
- les seuils physiques (rayon de Schwarzschild X = 1/2, dernière orbite stable X = 1/6, masse de Planck Y = 1, longueur de Planck XY = 1, longueur de Compton XY² = 1) découpent l'espace en cellules ;
- éliminer une variable revient à calculer un noyau ;
- l'écart d'un système à une loi devient une distance signée, et les covariances logarithmiques s'y propagent exactement pour les lois en loi de puissance.

**Nouveau en version 2.0 :**

- chaque horloge observée a une classe (période ou durée, front de signal, transit de groupe, temps conditionnel, différence de temps) qui fixe le domaine admissible de O ;
- un front de signal obéit au demi-espace causal O ≥ 1, et une horloge d'orbite circulaire à O > 2π√3 ≈ 10,9, ce qui fournit un test d'audit ;
- les grandeurs intrinsèquement signées reçoivent une règle de codage : logarithme d'un rapport à une référence positive, arsinh pour un changement de signe par zéro, inverse pour un changement de signe par un pôle ;
- appliqué aux résultats récents de « temps négatif » (nuage d'atomes froids, atome artificiel devant un miroir, délai de Shapiro, évolutions quantiques inversées ou superposées dans le temps), l'outil montre quelle grandeur est négative, sans rendre négative aucune échelle de temps fondamentale ;
- des corrections par rapport à la version 1.1, détaillées dans l'article et sur la page Zenodo.

**C'est un article de méthode.** Il ne propose aucune dynamique nouvelle et ne modifie ni la relativité générale ni la mécanique quantique. Il construit un système de coordonnées dans lequel les lois connues deviennent linéaires, pour classer, comparer et auditer des systèmes très différents dans une langue commune.

### Contenu de chaque archive

Les deux archives ont la même structure.

| Fichier | Contenu |
|---|---|
| `Empreintes_temporelles_FR.pdf`, `Temporal_fingerprints_EN.pdf` | l'article en français et en anglais (v2.0 : 21 pages chacun ; v1.1 : 16 pages) |
| `code_python.zip` | code Python et sources XeLaTeX : à décompresser pour obtenir les dossiers `code/` et `papier/` |
| `atlas_temporel.csv` | atlas temporel de 33 systèmes, avec sources |
| `banc_empreintes.html` | banc interactif |
| `README.md`, `CITATION.cff` | uniquement dans l'archive v2.0 |

Dans `code_python.zip` :

| Chemin | Contenu | v1.1 | v2.0 |
|---|---|---|---|
| `code/empreintes.py` | module Python : empreinte, état relatif, hyperplans et résidus, élimination par noyau, propagation des incertitudes, extension quantique, sphère de Hubble ; en v2.0, aussi les classes d'horloges et les codages signés | ✓ | ✓ |
| `code/test_empreintes.py` | tests numériques | 10 | 15 |
| `code/verifier_equations.py` | vérification symbolique (sympy) de chaque équation | 36 | 56 |
| `code/reproduire_papier.py` | recalcule tous les nombres, l'atlas et les figures | ✓ | ✓ |
| `code/atlas.py`, `code/figures.py` | atlas et figures (français et anglais) | ✓ | ✓ |
| `papier/*.tex` | sources XeLaTeX de l'article | ✓ | ✓ |

**L'atlas (v2.0)** couvre 33 systèmes, du proton à la sphère de Hubble. Chaque ligne donne :
- M, R et T<sub>obs</sub> (quand il en existe une), la nature et la classe de T<sub>obs</sub>, la définition et le statut de R ;
- T<sub>P</sub>, T<sub>G</sub>, T<sub>C</sub> et T<sub>Q</sub> en secondes ;
- log₁₀X, log₁₀Y, log₁₀O et log₁₀(g/a<sub>P</sub>) ;
- le résidu à la loi de Kepler, le régime conventionnel (en français et en anglais) et la source.

**Le banc interactif** est un fichier HTML unique, à ouvrir dans n'importe quel navigateur. Il ne demande ni installation ni connexion internet, et ne collecte aucune donnée.
- Choisissez un système de l'atlas, ou réglez M, R et T<sub>obs</sub> avec des curseurs.
- Choisissez la classe de l'horloge ; le banc signale les valeurs incohérentes (O ≤ 2π√3 pour une orbite circulaire, O < 1 pour un front de signal).
- Ajoutez une particule quantique pour obtenir son temps de Compton, les phases d'auto-gravité et d'horloge interne, et la durée minimale pour atteindre le quadrant Q4.
- Le résultat s'affiche sur les trois cartes de l'article : le plan des horloges (X, O), le plan (X, Y) et les quadrants quantiques.

### Utilisation

```bash
unzip "Empreintes temporelles complet  V.2.zip"
cd github_v2
unzip code_python.zip                     # crée code/ et papier/
pip install -r code/requirements.txt      # numpy, scipy, matplotlib, sympy
cd code
python test_empreintes.py                 # tests numériques
python verifier_equations.py              # vérification symbolique
python reproduire_papier.py               # tous les nombres, l'atlas et les figures
```

```python
from empreintes import Fingerprint, M_sun, AU, yr, admissible_O, asinh_coord
terre = Fingerprint(M=M_sun, R=AU, T_obs=yr, clock="orbit", name="Terre autour du Soleil")
print(terre.X, terre.Y, terre.O)
print(terre.kepler_residual())     # ≈ -1,9e-5 : sur la loi de Kepler
print(admissible_O(0.95, "P"), admissible_O(0.95, "F"))   # True False
print(asinh_coord(-3.0, 1.0))      # codage signé d'un délai négatif
```

Pour compiler l'article, lancez `cd papier && xelatex empreintes_fr.tex` deux fois.

---

## Citation

> Vronsky, F. (2026). *Temporal fingerprints: a logarithmic reference frame of time scales for gravitational and quantum systems* (v2.0). Zenodo. https://doi.org/10.5281/zenodo.23116283

Version 1.1 / version 1.1 : https://doi.org/10.5281/zenodo.23107603. See also / voir aussi `CITATION.cff`.

## Licence

Creative Commons Attribution–NonCommercial–ShareAlike 4.0 International (CC BY-NC-SA 4.0). See / voir `LICENCE`.

## Statement of assistance · Déclaration d'assistance

Analysis, code and writing were carried out with the assistance of an AI model (Claude, Anthropic). The author directed the work, checked the results and remains solely responsible for the content.

L'analyse, le code et la rédaction ont été réalisés avec l'assistance d'un modèle d'IA (Claude, Anthropic). L'auteur a dirigé le travail, vérifié les résultats et reste seul responsable du contenu.
