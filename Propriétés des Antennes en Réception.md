# Propriétés des Antennes en Réception

## Introduction

Les antennes constituent des éléments fondamentaux des systèmes de communication. Alors que les propriétés de transmission (rayonnement) sont souvent présentées en premier, les caractéristiques de réception méritent une analyse détaillée, car elles introduisent des concepts clés comme l'aire effective, le gain et la directivité. Ce document aborde les propriétés essentielles des antennes en réception et établit les relations fondamentales qui gouvernent la transmission électromagnétique entre deux antennes.

## 1. Aire Effective

### 1.1 Définition et Signification Physique

L'aire effective (ou surface effective, notée $A_e$ ou $A_{eff}$) d'une antenne réceptrice représente la surface équivalente qui capture l'énergie de l'onde électromagnétique incidente. Contrairement à la surface physique de l'antenne, l'aire effective tient compte de l'efficacité avec laquelle l'antenne collecte l'énergie.

Mathématiquement, l'aire effective est définie par la relation :

$$
A_e = \frac{P_r}{S}
$$

où :
- $P_r$ est la puissance reçue par l'antenne (en watts)
- $S$ est la densité de flux de puissance (en W/m²) ou intensité énergétique de l'onde incidente

### 1.2 Interprétation Physique

Cette définition révèle que l'aire effective n'est pas une propriété géométrique pure, mais une grandeur électromagnétique. Une antenne donnée capte une fraction seulement de la puissance contenue dans l'onde incidente. Par exemple :

- Une antenne physiquement petite peut posséder une aire effective appréciable à certaines fréquences (par exemple, une antenne résonante)
- À l'inverse, une antenne mal adaptée ou désaccordée possède une aire effective réduite

L'aire effective dépend fortement de :
- La fréquence de fonctionnement (pour une géométrie donnée)
- L'adaptation d'impédance (coefficient de réflexion)
- L'orientation relative entre l'antenne et l'onde incidente

## 2. Relation entre Aire Effective, Gain et Directivité

### 2.1 Gain Directif

Le gain directif $D(\theta, \phi)$ (ou directivité directionnelle) représente le rapport entre l'intensité de rayonnement (puissance par unité d'angle solide) dans une direction donnée et l'intensité moyenne si le rayonnement était isotrope :

$$
D(\theta, \phi) = \frac{U(\theta, \phi)}{U_{moy}} = \frac{4\pi \, U(\theta, \phi)}{P_{rayonnée}}
$$

où $U(\theta, \phi)$ est l'intensité de rayonnement dans la direction $(\theta, \phi)$.

La directivité maximale (ou simplement "directivité" $D_0$) est le gain directif maximal :

$$
D_0 = \max_{\theta,\phi} \, D(\theta, \phi)
$$

### 2.2 Gain Réalisé (ou Gain Absolu)

Le gain réalisé $G$ (gain absolu ou simplement "gain") tient compte des pertes ohmiques de l'antenne et de l'adaptation d'impédance :

$$
G = \eta \cdot D
$$

où $\eta$ (avec $0 \leq \eta \leq 1$) est le rendement de l'antenne.

Pour une antenne sans pertes totalement adaptée ($\eta = 1$), on a $G = D$.

### 2.3 Relation Fondamentale : Aire Effective et Gain

La relation clé reliant l'aire effective, le gain et la longueur d'onde est :

$$
A_e = \frac{\lambda^2}{4\pi} \, G
$$

où :
- $\lambda$ est la longueur d'onde (en mètres)
- $G$ est le gain réalisé (grandeur sans dimension, ou en dB : $G_{dB} = 10 \log_{10} G$)

**Démonstration esquissée :**

À partir des équations de Maxwell et en analysant le rayonnement d'une antenne comme source locale sur une sphère lointaine, on montre que :

$$
A_e = \frac{\lambda^2}{4\pi} \, D
$$

pour une antenne idéale sans pertes. En présence de pertes et de désadaptation, on introduit le rendement $\eta$, d'où :

$$
A_e = \frac{\lambda^2}{4\pi} \, \eta \, D = \frac{\lambda^2}{4\pi} \, G
$$

### 2.4 Implications et Interprétations

Cette relation fondamentale enseigne que :

- L'aire effective augmente avec $\lambda^2$ (aux basses fréquences, l'aire effective est grande relative à la longueur d'onde)
- L'aire effective est proportionnelle au gain : un gain élevé implique une aire effective grande
- Pour une antenne physique donnée, le produit $A_e \cdot G$ est optimal à une fréquence de résonance ; hors de cette fréquence, $A_e$ diminue
- Cette relation unifies les propriétés de transmission et de réception (réciprocité)

**Exemple numérique :**
- Antenne dipôle demi-onde : $G \approx 1.64$ (soit environ 2.15 dB), avec $D_0 = 1.5$
- À 1 GHz ($\lambda = 0.3$ m) : $A_e \approx \frac{(0.3)^2}{4\pi} \times 1.64 \approx 0.0117$ m² = 117 cm²

## 3. Transmission entre Deux Antennes : Formule de Friis

### 3.1 Contexte et Hypothèses

Considérons un système de communication composé de deux antennes :
- Antenne 1 (émettrice) : gain $G_1$, à distance $d$ de l'antenne 2
- Antenne 2 (réceptrice) : gain $G_2$, aire effective $A_{e2}$

Les hypothèses fondamentales sont :
1. Zone lointaine (champ lointain) : $d \gg \lambda$ et $d \gg D_{max}$ (où $D_{max}$ est la plus grande dimension de l'antenne)
2. Conditions de propagation en espace libre (absence d'obstacles et de trajets multiples)
3. Polarisation alignée entre émetteur et récepteur
4. Antennes adaptées à la source et la charge

### 3.2 Dérivation de la Formule

La puissance rayonnée par l'antenne émettrice dans une direction est modulée par son gain $G_1$. La puissance isotrope équivalente rayonnée (PIRE) est :

$$
P_{PIRE} = P_1 \cdot G_1
$$

où $P_1$ est la puissance d'entrée de l'antenne émettrice.

À la distance $d$, la densité de flux de puissance (intensité énergétique) reçue est donnée par la loi de conservation de l'énergie :

$$
S(d) = \frac{P_{PIRE}}{4\pi d^2} = \frac{P_1 \cdot G_1}{4\pi d^2}
$$

La puissance captée par l'antenne réceptrice est :

$$
P_r = S(d) \cdot A_{e2} = \frac{P_1 \cdot G_1}{4\pi d^2} \cdot A_{e2}
$$

En substituant la relation $A_{e2} = \frac{\lambda^2}{4\pi} G_2$ :

$$
P_r = \frac{P_1 \cdot G_1}{4\pi d^2} \cdot \frac{\lambda^2}{4\pi} G_2
$$

$$
P_r = P_1 \cdot G_1 \cdot G_2 \cdot \left(\frac{\lambda}{4\pi d}\right)^2
$$

Cela conduit à la **formule de Friis** :

$$
\boxed{\frac{P_r}{P_1} = G_1 \cdot G_2 \cdot \left(\frac{\lambda}{4\pi d}\right)^2}
$$

ou de manière équivalente :

$$
\boxed{P_r = P_1 \cdot G_1 \cdot G_2 \cdot \frac{\lambda^2}{(4\pi d)^2}}
$$

### 3.3 Terme d'Atténuation de Propagation

La quantité $\left(\frac{\lambda}{4\pi d}\right)^2$ est appelée coefficient d'atténuation en espace libre (ou loss factor). Elle peut également s'écrire :

$$
L = \left(\frac{\lambda}{4\pi d}\right)^2 = \left(\frac{c}{4\pi d f}\right)^2
$$

où $f$ est la fréquence et $c$ la vitesse de la lumière.

En décibels, l'atténuation de propagation en espace libre est :

$$
L_{dB} = 20 \log_{10} \left(\frac{\lambda}{4\pi d}\right) = 20 \log_{10} \left(\frac{c}{4\pi d f}\right)
$$

$$
L_{dB} = -20 \log_{10}(4\pi d f / c)
$$

Remarque : Cette atténuation s'accroît avec la distance et la fréquence (propagation en $1/d^2$ ou $-20$ dB/décade en distance).

### 3.4 Formule de Friis en Décibels

Pour faciliter les calculs en télécommunications, la formule de Friis s'exprime souvent en décibels :

$$
P_{r,dB} = P_{1,dB} + G_{1,dB} + G_{2,dB} + L_{dB}
$$

où :
- $P_{r,dB} = 10 \log_{10}(P_r / 1\text{ W})$ (puissance reçue en dBW)
- $P_{1,dB} = 10 \log_{10}(P_1 / 1\text{ W})$ (puissance transmise)
- $G_{1,dB}, G_{2,dB}$ : gains en dB
- $L_{dB} = -20 \log_{10}(4\pi d f / c)$ : atténuation (grandeur négative)

### 3.5 Interprétation Physique

La formule de Friis révèle plusieurs principes fondamentaux :

1. **Dépendance en fréquence :** L'atténuation s'accroît avec la fréquence ($\propto f^2$), ce qui explique pourquoi les communications aux hautes fréquences (mm-wave, THz) nécessitent des antennes très directionnelles ou une proximité accrue.

2. **Dépendance en distance :** L'atténuation décroît en $1/d^2$ (régime de champ lointain). Ce régime contraste avec les régimes de champ proche où la dépendance en distance est plus complexe.

3. **Importance du gain :** Des gains élevés compensent l'atténuation de propagation. Une augmentation de gain de +3 dB compense une augmentation de distance d'environ 41 %.

4. **Réciprocité :** La formule de Friis est symétrique en $G_1$ et $G_2$, reflétant le principe de réciprocité des antennes : il est équivalent d'émettre par l'antenne 1 et de recevoir par l'antenne 2, ou vice-versa.

## 4. Cas Particuliers et Extensions

### 4.1 Antennes Isotropes Fictives

Une antenne isotrope idéale possède un gain unitaire ($G = 1$, soit 0 dB) dans toutes les directions. La formule de Friis pour deux antennes isotropes donne :

$$
P_r = P_1 \cdot \left(\frac{\lambda}{4\pi d}\right)^2
$$

Cette limite sert de référence pour évaluer l'efficacité des antennes réelles.

### 4.2 Coefficient de Désadaptation de Polarisation

Si les polarisations de l'antenne émettrice et réceptrice ne sont pas parfaitement alignées, on introduit un coefficient de perte de polarisation $\rho$ (avec $0 \leq \rho \leq 1$) :

$$
P_r = P_1 \cdot G_1 \cdot G_2 \cdot \left(\frac{\lambda}{4\pi d}\right)^2 \cdot \rho
$$

### 4.3 Bilan de Liaison (Link Budget)

Dans les télécommunications, le bilan de liaison est l'application systématique de la formule de Friis. En décibels :

$$
\text{Marge} = P_{1,dB} + G_{1,dB} + G_{2,dB} - L_{dB} - P_{seuil,dB}
$$

où $P_{seuil}$ est la puissance minimale nécessaire au récepteur pour atteindre un taux d'erreur acceptable.

## 5. Réciprocité et Dualité Émission-Réception

### 5.1 Théorème de Réciprocité

L'une des propriétés les plus profondes des antennes est leur **réciprocité**. Le théorème de réciprocité énonce que les propriétés directionnelles d'une antenne en émission et en réception sont identiques (en supposant une géométrie et une nature linéaire).

Mathématiquement, si une antenne possède un diagramme de rayonnement $D(\theta, \phi)$ en émission, alors en réception, elle possède exactement le même diagramme directif $D(\theta, \phi)$.

### 5.2 Conséquences

Cette réciprocité implique que :

- La relation $A_e = \frac{\lambda^2}{4\pi} G$ est valide indifféremment pour l'émission ou la réception
- Les paramètres $G$ et $D$ d'une antenne sont identiques, qu'elle soit utilisée en émission ou en réception
- La formule de Friis est symétrique : $P_r = P_1 G_1 G_2 (\lambda / 4\pi d)^2$, indépendamment de laquelle des deux antennes émet

Cette dualité simplifie considérablement l'analyse des systèmes de communication bidirectionnels.

## 6. Exemple Numérique d'Application

Considérons un système de liaison par satellite :

**Paramètres :**
- Fréquence : $f = 10$ GHz ($\lambda = 0.03$ m)
- Distance : $d = 40\,000$ km
- Gain antenne émettrice (station au sol) : $G_1 = 40$ dB = 10\,000
- Gain antenne réceptrice (satellite) : $G_2 = 15$ dB ≈ 31.6
- Puissance d'entrée : $P_1 = 1$ W (0 dBW)

**Calcul de l'atténuation :**

$$
L = 10 \log_{10}\left(\frac{\lambda}{4\pi d}\right)^2 = 20 \log_{10}\left(\frac{0.03}{4\pi \times 4 \times 10^7}\right)
$$

$$
L \approx 20 \log_{10}(5.97 \times 10^{-10}) \approx -204.5 \text{ dB}
$$

**Puissance reçue (en dB) :**

$$
P_{r,dB} = 0 + 40 + 15 - 204.5 = -149.5 \text{ dBW} \approx 3.16 \times 10^{-15} \text{ W}
$$

Cet exemple illustre pourquoi les liaisons satellites et spatiales nécessitent des antennes hautement directionnelles et des amplificateurs de bas bruit très sensibles en réception.

## 7. Limitations et Extensions du Modèle

### 7.1 Hypothèses du Modèle de Friis

Le modèle classique de Friis repose sur plusieurs hypothèses restrictives :

1. **Espace libre** : Absence d'obstacles et de trajets multiples (propagation non-specculaire)
2. **Champ lointain** : Les antennes sont distantes de plusieurs longueurs d'onde
3. **Polarisation alignée** : Les polarisations émettrice et réceptrice coïncident
4. **Adaptation d'impédance** : Les antennes sont adaptées aux sources/charges

### 7.2 Environnements Réalistes

En pratique, les environnements de propagation sont complexes :

- **Trajets multiples** : Réflexions, diffractions, scattering introduisent une atténuation supplémentaire (fading)
- **Pertes atmosphériques** : Absorption par l'oxygène, l'eau, la pluie (importants aux hautes fréquences)
- **Interférences** : Autres sources électromagnétiques réduisent le rapport signal-à-bruit
- **Directivité imparfaite** : Les lobes latéraux des antennes capturent du bruit hors-axe

Ces effets sont modélisés par des facteurs correctifs (coefficient de fading, facteur de bruit additif, etc.) appliqués à la formule de base.

## Conclusion

Les propriétés des antennes en réception—aire effective, gain, directivité—constituent le socle théorique de toute liaison radiofréquence. La relation $A_e = \frac{\lambda^2}{4\pi} G$ établit l'équivalence entre les caractéristiques directionnelles et la capacité physique de capture d'énergie. La formule de Friis unifie ces concepts en fournissant une prédiction quantitative de la puissance reçue en fonction des paramètres d'émission, de propagation et de réception.

Bien que le modèle d'espace libre représente une idéalisation, ses principes restent fondamentaux et permettent d'évaluer rapidement les performances d'une liaison radiofréquence. Les extensions à des environnements réalistes conservent cette structure conceptuelle et introduisent des termes correctifs adapés au contexte physique.

La compréhension approfondie de ces mécanismes est essentielle pour la conception de systèmes de communication, de radar, et de capteurs électromagnétiques modernes.

## Références

[1] Balanis, C. A. (2016). *Antenna Theory: Analysis and Design* (4th ed.). John Wiley & Sons.

[2] Jackson, J. D. (1999). *Classical Electrodynamics* (3rd ed.). John Wiley & Sons.

[3] Griffiths, D. J. (2013). *Introduction to Electrodynamics* (4th ed.). Pearson.

[4] IEEE. (2022). IEEE Standard for Definitions of Terms for Antennas. IEEE Std 149.

[5] Friis, H. T. (1946). A note on a simple transmission formula. *Proceedings of the IRE*, 34(5), 254–256.

[6] Collin, R. E., & Zucker, F. J. (1969). *Antenna Theory* (Parts 1 & 2). McGraw-Hill.

[7] Pozar, D. M. (2012). *Microwave Engineering* (4th ed.). John Wiley & Sons.
