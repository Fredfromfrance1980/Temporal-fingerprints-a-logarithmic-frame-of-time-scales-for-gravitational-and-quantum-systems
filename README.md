# Temporal fingerprints · Empreintes temporelles

**A logarithmic reference frame of time scales for gravitational and quantum systems**
**Un référentiel logarithmique des échelles de temps pour les systèmes gravitationnels et quantiques**

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23106130.svg)](https://doi.org/10.5281/zenodo.23106130)

**Frédérick Vronsky** — Independent researcher in theoretical cosmology / Chercheur indépendant en cosmologie théorique, Toulouse
ORCID: [0009-0003-5719-9604](https://orcid.org/0009-0003-5719-9604) · Version 1.1 · October / octobre 2026 · CC BY-NC-SA 4.0

[English](#english) · [Français](#français)

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

**This is a methods paper.** It proposes no new dynamics and modifies neither general relativity nor quantum mechanics. It builds a coordinate system in which known laws become linear, so that very different systems can be classified, compared and audited in a common language.

### Contents

| Path | Contents |
|---|---|
| `Temporal_fingerprints_EN.pdf`, `Empreintes_temporelles_FR.pdf` | the paper in English and French (16 pages each) |
| `papier/*.tex` | XeLaTeX sources |
| `code/empreintes.py` | Python module: fingerprint, relative state, log matrix, hyperplanes and residuals, kernel elimination, uncertainty propagation, quantum extension, Hubble sphere |
| `code/test_empreintes.py` | numerical tests of the paper's identities (10 tests) |
| `code/verifier_equations.py` | symbolic check (sympy) of every equation (36 checks) |
| `code/reproduire_papier.py` | recomputes every number, the atlas and the figures |
| `atlas_temporel.csv`, `code/atlas.py` | temporal atlas of 33 systems, with sources (regenerated in `code/`) |
| `code/figures.py` | figures in French and English |
| `banc_empreintes.html` | interactive bench |

**The atlas (`atlas_temporel.csv`)** covers 33 systems, from the proton to the Hubble sphere: Earth, Solar System, pulsars, black holes, quantum experiments and cosmos. Each row gives:
- M, R and T<sub>obs</sub> (when one exists), with the nature of T<sub>obs</sub> and the definition and status of R;
- T<sub>P</sub>, T<sub>G</sub>, T<sub>C</sub> and T<sub>Q</sub>, in seconds;
- log₁₀X, log₁₀Y, log₁₀O and log₁₀(g/a<sub>P</sub>);
- the Kepler residual, the conventional regime and the source.

**The interactive bench (`banc_empreintes.html`)** needs only to be downloaded and opened in any web browser. It needs no installation and no internet connection, and it collects no data.
- Pick a system from the atlas, or set M, R and T<sub>obs</sub> with sliders.
- Read the time scales, the relative state, the proper-time factors and the deviation from Kepler's law (K<sub>T</sub>, A<sub>T</sub>, r<sub>T</sub>).
- Add a quantum particle to get its Compton time, the self-gravity and internal-clock phases, and the minimum duration to reach quadrant Q4.
- See the result on the paper's three maps: the clock plane (X, O), the (X, Y) plane and the quantum quadrants.

The bench interface is in French.

### Usage

```bash
pip install -r code/requirements.txt      # numpy, scipy, matplotlib, sympy
cd code
python test_empreintes.py                 # numerical tests
python verifier_equations.py              # symbolic verification
python reproduire_papier.py               # all numbers, atlas and figures
```

```python
from empreintes import Fingerprint, M_sun, AU, yr
earth = Fingerprint(M=M_sun, R=AU, T_obs=yr, clock="orbit", name="Earth around the Sun")
print(earth.X, earth.Y, earth.O)
print(earth.kepler_residual())     # ≈ -1.9e-5: on Kepler's law
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

**C'est un article de méthode.** Il ne propose aucune dynamique nouvelle et ne modifie ni la relativité générale ni la mécanique quantique. Il construit un système de coordonnées dans lequel les lois connues deviennent linéaires, pour classer, comparer et auditer des systèmes très différents dans une langue commune.

### Contenu

| Chemin | Contenu |
|---|---|
| `Empreintes_temporelles_FR.pdf`, `Temporal_fingerprints_EN.pdf` | l'article en français et en anglais (16 pages chacun) |
| `papier/*.tex` | sources XeLaTeX |
| `code/empreintes.py` | module Python : empreinte, état relatif, matrice logarithmique, hyperplans et résidus, élimination par noyau, propagation des incertitudes, extension quantique, sphère de Hubble |
| `code/test_empreintes.py` | tests numériques des identités du papier (10 tests) |
| `code/verifier_equations.py` | vérification symbolique (sympy) de chaque équation (36 vérifications) |
| `code/reproduire_papier.py` | recalcule tous les nombres, l'atlas et les figures |
| `atlas_temporel.csv`, `code/atlas.py` | atlas temporel de 33 systèmes, avec sources (régénéré dans `code/`) |
| `code/figures.py` | figures en français et en anglais |
| `banc_empreintes.html` | banc interactif |

**L'atlas (`atlas_temporel.csv`)** couvre 33 systèmes, du proton à la sphère de Hubble : Terre, Système solaire, pulsars, trous noirs, expériences quantiques et cosmos. Chaque ligne donne :
- M, R et T<sub>obs</sub> (quand il en existe une), avec la nature de T<sub>obs</sub>, la définition et le statut de R ;
- T<sub>P</sub>, T<sub>G</sub>, T<sub>C</sub> et T<sub>Q</sub>, en secondes ;
- log₁₀X, log₁₀Y, log₁₀O et log₁₀(g/a<sub>P</sub>) ;
- le résidu à la loi de Kepler, le régime conventionnel et la source.

Les noms de colonnes et la colonne « regime » sont en anglais.

**Le banc interactif (`banc_empreintes.html`)** se télécharge et s'ouvre dans n'importe quel navigateur. Il ne demande ni installation ni connexion internet, et ne collecte aucune donnée.
- Choisissez un système de l'atlas, ou réglez M, R et T<sub>obs</sub> avec des curseurs.
- Lisez les échelles de temps, l'état relatif, les facteurs de temps propre et l'écart à la loi de Kepler (K<sub>T</sub>, A<sub>T</sub>, r<sub>T</sub>).
- Ajoutez une particule quantique pour obtenir son temps de Compton, les phases d'auto-gravité et d'horloge interne, et la durée minimale pour atteindre le quadrant Q4.
- Le résultat s'affiche sur les trois cartes du papier : le plan des horloges (X, O), le plan (X, Y) et les quadrants quantiques.

### Utilisation

```bash
pip install -r code/requirements.txt      # numpy, scipy, matplotlib, sympy
cd code
python test_empreintes.py                 # tests numériques
python verifier_equations.py              # vérification symbolique
python reproduire_papier.py               # tous les nombres, l'atlas et les figures
```

```python
from empreintes import Fingerprint, M_sun, AU, yr
terre = Fingerprint(M=M_sun, R=AU, T_obs=yr, clock="orbit", name="Terre autour du Soleil")
print(terre.X, terre.Y, terre.O)
print(terre.kepler_residual())     # ≈ -1,9e-5 : sur la loi de Kepler
```

Pour compiler l'article, lancez `cd papier && xelatex empreintes_fr.tex` deux fois.

---

## Citation

> Vronsky, F. (2026). *Temporal fingerprints: a logarithmic reference frame of time scales for gravitational and quantum systems* (v1.0). Zenodo. https://doi.org/10.5281/zenodo.23106130

See also / voir aussi `CITATION.cff`.

## Licence

Creative Commons Attribution–NonCommercial–ShareAlike 4.0 International (CC BY-NC-SA 4.0). See / voir `LICENCE`.

## Statement of assistance · Déclaration d'assistance

Analysis, code and writing were carried out with the assistance of an AI model (Claude, Anthropic). The author directed the work, checked the results and remains solely responsible for the content.

L'analyse, le code et la rédaction ont été réalisés avec l'assistance d'un modèle d'IA (Claude, Anthropic). L'auteur a dirigé le travail, vérifié les résultats et reste seul responsable du contenu.
