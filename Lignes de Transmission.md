# Lignes de Transmission
## Théorie et Applications

---

## 1. Introduction

Les **lignes de transmission** constituent le fondement de la propagation des signaux haute fréquence et de la distribution d'énergie. Contrairement aux circuits localisés où les retards de propagation sont négligeables, les lignes de transmission traitent des phénomènes de propagation ondulatoire sur des distances significatives.

Cette théorie s'applique lorsque :
- La longueur de la ligne est comparable ou supérieure à la longueur d'onde $\lambda$
- Les fréquences de fonctionnement sont suffisamment élevées pour que les effets distribués dominent
- Des réflexions d'ondes apparaissent aux discontinuités d'impédance

---

## 2. Lignes de Transmission Idéales

### 2.1 Modèle distribué

Une ligne de transmission est caractérisée par quatre paramètres primaires par unité de longueur :

- **$R$** : Résistance par unité de longueur (Ω/m)
- **$L$** : Inductance par unité de longueur (H/m)
- **$G$** : Conductance par unité de longueur (S/m) — dissipation du diélectrique
- **$C$** : Capacité par unité de longueur (F/m)

**Cas idéal (lossless)** : $R = 0$ et $G = 0$

Le modèle distribué repose sur le circuit équivalent d'une section infinitésimale $dz$ :
- L'inductance série $L \, dz$ modélise le champ magnétique autour des conducteurs
- La capacité shunt $C \, dz$ modélise le champ électrique entre les conducteurs
- La résistance $R \, dz$ et la conductance $G \, dz$ représentent les pertes

### 2.2 Équations des télégraphistes

En appliquant les lois de Kirchhoff à une section élémentaire, on obtient les **équations des télégraphistes** :

$$
\frac{\partial V}{\partial z} = -(R + j\omega L)I = -Z \cdot I
$$

$$
\frac{\partial I}{\partial z} = -(G + j\omega C)V = -Y \cdot V
$$

où :
- $Z = R + j\omega L$ : impédance série par unité de longueur
- $Y = G + j\omega C$ : admittance parallèle par unité de longueur
- $\omega = 2\pi f$ : pulsation angulaire
- $j$ : unité imaginaire

**Interprétation physique** :
- La première équation décrit comment la chute de tension provient de l'inductance (réactance) et de la résistance du conducteur
- La deuxième équation montre comment le courant se divise entre la capacité (courant de déplacement) et la conductance (pertes)

---

## 3. Équations des Ondes de Courant et de Tension

### 3.1 Dérivation

En dérivant les équations des télégraphistes et en les combinant, on obtient deux **équations d'onde** découplées :

$$
\frac{\partial^2 V}{\partial z^2} = \gamma^2 V
$$

$$
\frac{\partial^2 I}{\partial z^2} = \gamma^2 I
$$

où $\gamma$ est la **constante de propagation complexe** :

$$
\gamma = \sqrt{(R + j\omega L)(G + j\omega C)} = \sqrt{Z \cdot Y}
$$

### 3.2 Solutions générales

Les solutions de ces équations d'onde sont des combinaisons linéaires d'ondes se propageant dans les deux directions :

$$
V(z) = V_+ e^{-\gamma z} + V_- e^{+\gamma z}
$$

$$
I(z) = I_+ e^{-\gamma z} + I_- e^{+\gamma z}
$$

où :
- $V_+, I_+$ : amplitude et courant de l'onde incidente (direction $+z$)
- $V_-, I_-$ : amplitude et courant de l'onde réfléchie (direction $-z$)
- Les constantes $V_+, V_-$ sont déterminées par les conditions aux limites

**Interprétation physique** : Toute onde électromagnétique sur une ligne peut être décomposée en deux ondes planes se propageant en directions opposées, une transmise et une réfléchie.

---

## 4. Vitesse de Propagation

### 4.1 Définition et calcul

La **vitesse de propagation** (ou **vitesse de phase**) est définie par :

$$
v_p = \frac{\omega}{\beta}
$$

où $\beta$ est la **constante de phase** (partie réelle de $\gamma$ pour une ligne sans pertes).

### 4.2 Cas lossless ($R \approx 0, G \approx 0$)

Pour une ligne idéale (lossless), la constante de propagation se réduit à :

$$
\gamma = j\omega\sqrt{LC} = j\beta
$$

d'où :

$$
\beta = \omega\sqrt{LC}
$$

$$
v_p = \frac{\omega}{\omega\sqrt{LC}} = \frac{1}{\sqrt{LC}}
$$

**Exemple** : Pour un câble coaxial standard avec $\varepsilon_r = 2.02$ (PTFE) :
$$
v_p = \frac{c}{\sqrt{\varepsilon_r}} \approx 0.66 \, c
$$
où $c = 3 \times 10^8$ m/s.

### 4.3 Longueur d'onde sur la ligne

$$
\lambda = \frac{v_p}{f} = \frac{2\pi}{\beta}
$$

La longueur d'onde sur une ligne **avec diélectrique** est inférieure à la longueur d'onde en espace libre, ce qui affecte les dimensions physiques des circuits d'adaptation.

---

## 5. Impédance Caractéristique

### 5.1 Définition

L'**impédance caractéristique** $Z_0$ d'une ligne est l'impédance présente le long de la ligne en l'absence de réflexions (ligne infinie ou terminée par $Z_0$) :

$$
Z_0 = \frac{V_+}{I_+} = -\frac{V_-}{I_-}
$$

Générale expression :

$$
Z_0 = \sqrt{\frac{R + j\omega L}{G + j\omega C}} = \sqrt{\frac{Z}{Y}}
$$

### 5.2 Cas lossless

Pour une ligne idéale ($R = 0, G = 0$) :

$$
Z_0 = \sqrt{\frac{L}{C}}
$$

Cette formule montre que l'impédance caractéristique dépend uniquement de la **géométrie et des matériaux** de la ligne, et **non de la fréquence** (pour une ligne idéale).

**Interprétation physique** : $Z_0$ représente le rapport entre le champ électrique et le champ magnétique transportés par l'onde propagative. Elle détermine l'efficacité du transfert de puissance.

### 5.3 Cas low-loss ($R \ll \omega L, G \ll \omega C$)

$$
Z_0 \approx \sqrt{\frac{L}{C}} \left(1 + j\frac{R}{2\omega L} - j\frac{G}{2\omega C}\right)
$$

---

## 6. Coefficient de Réflexion

### 6.1 Définition

Le **coefficient de réflexion** $\Gamma$ quantifie l'amplitude de l'onde réfléchie par rapport à l'onde incidente. À une position $z$ quelconque :

$$
\Gamma(z) = \frac{V_-}{V_+} e^{2\gamma z}
$$

Au niveau de la charge ($z = z_L$) :

$$
\Gamma_L = \frac{V_-}{V_+} e^{2\gamma z_L}
$$

### 6.2 Relation avec l'impédance

Le coefficient de réflexion est relié à l'impédance terminale par la **transformation de Möbius** :

$$
\Gamma_L = \frac{Z_L - Z_0}{Z_L + Z_0}
$$

Inversement :

$$
Z_L = Z_0 \frac{1 + \Gamma_L}{1 - \Gamma_L}
$$

**Cas particuliers** :
- Si $Z_L = Z_0$ (adaptation) : $\Gamma_L = 0$ (pas de réflexion)
- Si $Z_L = 0$ (court-circuit) : $\Gamma_L = -1$ (réflexion totale, opposition de phase)
- Si $Z_L = \infty$ (circuit ouvert) : $\Gamma_L = +1$ (réflexion totale, même phase)

### 6.3 Coefficient de réflexion de tension normalisé

$$
\Gamma(z) = \frac{V_-(z)}{V_+(z)} = \Gamma_L e^{-2(R+j\omega L)z}
$$

Pour une ligne lossless, en remontant vers la source ($z$ décroissant) :

$$
\Gamma(z) = \Gamma_L e^{j2\beta(z_L - z)}
$$

L'argument du coefficient de réflexion tourne de $2\beta$ par mètre en remontant vers la source.

---

## 7. Ligne Quelconque en Régime Sinusoïdal

### 7.1 Formulation phasori

En régime sinusoïdal établi, les tensions et courants sont représentés par leurs **phaseurs** (amplitudes complexes) :

$$
V(z) = V_+ e^{-\gamma z} + V_- e^{+\gamma z}
$$

$$
I(z) = \frac{V_+ e^{-\gamma z} - V_- e^{+\gamma z}}{Z_0}
$$

### 7.2 Constante de propagation complexe

$$
\gamma = \alpha + j\beta
$$

où :
- **$\alpha$** : **constante d'atténuation** (Np/m) — décroissance exponentielle
- **$\beta$** : **constante de phase** (rad/m) — oscillation spatiale

Pour une ligne avec pertes :

$$
\alpha = \frac{1}{2}\sqrt{\text{Re}[ZY]} = \frac{1}{2v_p}\sqrt{R^2 + \omega^2 L^2} \cdot \sqrt{G^2 + \omega^2 C^2} / \sqrt{ZY}
$$

**Approximation low-loss** :

$$
\alpha \approx \frac{1}{2Z_0}\left(R + \frac{G Z_0^2}{2}\right)
$$

$$
\beta \approx \omega\sqrt{LC}
$$

### 7.3 Qualités de la ligne

- **Ligne de transmission basse fréquence** : $\beta L \ll 1$ (retard negligible)
- **Ligne de transmission RF/Micro-ondes** : $\beta L > 1$ (effets distribués importants)

---

## 8. Exposant de Propagation

### 8.1 Définition et décomposition

L'**exposant de propagation** est la constante complexe $\gamma$ définie précédemment :

$$
\gamma = \sqrt{ZY} = \sqrt{(R + j\omega L)(G + j\omega C)}
$$

### 8.2 Décomposition en atténuation et phase

$$
e^{-\gamma z} = e^{-\alpha z} e^{-j\beta z}
$$

- **Terme exponentiel réel** $e^{-\alpha z}$ : représente l'**amortissement** dû aux pertes
- **Terme exponentiel imaginaire** $e^{-j\beta z}$ : représente la **propagation ondulatoire**

### 8.3 Distance caractéristique

La **longueur caractéristique d'atténuation** (distance où l'amplitude est réduite de $e^{-1}$) :

$$
L_\alpha = \frac{1}{\alpha}
$$

Pour une ligne très basse perte :

$$
L_\alpha = \frac{2Z_0}{R + \frac{G Z_0^2}{2}}
$$

---

## 9. Impédance d'une Ligne Terminée

### 9.1 Formule générale

L'**impédance d'entrée** (ou impédance vue en un point $z$ de la ligne) est donnée par :

$$
Z(z) = Z_0 \frac{1 + \Gamma(z) e^{j2\beta(z_L-z)}}{1 - \Gamma(z) e^{j2\beta(z_L-z)}}
$$

ou de manière équivalente, en utilisant la charge terminale $Z_L$ et la distance $\ell = z_L - z$ :

$$
Z_{in}(\ell) = Z_0 \frac{Z_L + j Z_0 \tan(\beta \ell)}{Z_0 + j Z_L \tan(\beta \ell)}
$$

### 9.2 Cas lossless (formule de l'abaque de Smith)

Pour une ligne idéale (lossless), l'impédance se transforme le long de la ligne selon :

$$
Z(z) = Z_0 \frac{Z_L + j Z_0 \tan(\beta(z_L - z))}{Z_0 + j Z_L \tan(\beta(z_L - z))}
$$

**Propriétés** :
- L'impédance oscille périodiquement avec la distance
- La périodicité est $\lambda/2 = \pi/\beta$
- À chaque demi-longueur d'onde, l'impédance revient à une valeur proportionnelle à $Z_L$

### 9.3 Cas particuliers

**Ligne demi-onde** ($\ell = n\lambda/2$, $n$ entier) :
$$
Z_{in} = Z_L \quad \text{(impédance = charge)}
$$

**Ligne quart-d'onde** ($\ell = (2n+1)\lambda/4$) :
$$
Z_{in} = \frac{Z_0^2}{Z_L} \quad \text{(inversion et adaptation possible)}
$$

**Ligne demi-onde court-circuitée** ($Z_L = 0, \ell = n\lambda/2$) :
$$
Z_{in} = 0 \quad \text{(court-circuit)}
$$

**Ligne quart-d'onde court-circuitée** ($Z_L = 0, \ell = (2n+1)\lambda/4$) :
$$
Z_{in} = \infty \quad \text{(circuit ouvert)}
$$

### 9.4 Rapport d'ondes stationnaires (SWR)

Le **Voltage Standing Wave Ratio** est défini comme :

$$
\text{SWR} = \frac{1 + |\Gamma|}{1 - |\Gamma|} = \frac{|V_{\max}|}{|V_{\min}|} = \frac{Z_L}{Z_0} \quad (\text{si } Z_L \text{ résistif})
$$

où :
- $|\Gamma|$ : module du coefficient de réflexion
- $V_{\max}, V_{\min}$ : maxima et minima de tension le long de la ligne

Pour une ligne adaptée ($Z_L = Z_0$) : $\text{SWR} = 1$ (pas d'ondes stationnaires).

---

## 10. Calcul de l'Impédance Caractéristique d'un Câble Coaxial

### 10.1 Géométrie et paramètres distribués

Un **câble coaxial** est composé de :
- **Conducteur central** de diamètre $d$
- **Diélectrique** de permittivité relative $\varepsilon_r$
- **Blindage extérieur** de diamètre intérieur $D$

Les paramètres distribués (par unité de longueur) sont :

**Inductance par unité de longueur** :
$$
L = \frac{\mu_0}{2\pi} \ln\left(\frac{D}{d}\right) \quad \text{(H/m)}
$$

où $\mu_0 = 4\pi \times 10^{-7}$ H/m. Cette formule provient du calcul du flux magnétique dans l'espace entre conducteurs.

**Capacité par unité de longueur** :
$$
C = \frac{2\pi \varepsilon_0 \varepsilon_r}{\ln(D/d)} \quad \text{(F/m)}
$$

où $\varepsilon_0 = 8.854 \times 10^{-12}$ F/m. Cette relation découle du calcul du champ électrique radial.

### 10.2 Dérivation de l'impédance caractéristique

L'impédance caractéristique d'un câble coaxial lossless est :

$$
Z_0 = \sqrt{\frac{L}{C}} = \sqrt{\frac{\frac{\mu_0}{2\pi} \ln(D/d)}{\frac{2\pi \varepsilon_0 \varepsilon_r}{\ln(D/d)}}}
$$

$$
Z_0 = \frac{1}{2\pi}\sqrt{\frac{\mu_0}{\varepsilon_0 \varepsilon_r}} \ln\left(\frac{D}{d}\right)
$$

En utilisant $c = 1/\sqrt{\mu_0 \varepsilon_0}$ (vitesse de la lumière) :

$$
Z_0 = \frac{138}{\sqrt{\varepsilon_r}} \log_{10}\left(\frac{D}{d}\right) \quad \text{(Ω)}
$$

ou plus rigoureusement en logarithme naturel :

$$
Z_0 = \frac{60}{\sqrt{\varepsilon_r}} \ln\left(\frac{D}{d}\right) \quad \text{(Ω)}
$$

### 10.3 Applications et exemples

**Câble coaxial standard 50 Ω** :
- Pour RG-58 : $d \approx 0.9$ mm, $D \approx 3.0$ mm, $\varepsilon_r \approx 2.0$
- Calcul : $Z_0 = \frac{60}{\sqrt{2.0}} \ln(3.0/0.9) \approx 50$ Ω

**Câble vidéo 75 Ω** :
- Géométrie plus espacée : $D/d$ plus grand
- Exemple : $D/d = 10$, $\varepsilon_r = 1.5$ donne $Z_0 \approx 75$ Ω

**Vitesse de propagation** :
$$
v_p = \frac{1}{\sqrt{LC}} = \frac{c}{\sqrt{\varepsilon_r}}
$$

Pour PTFE ($\varepsilon_r = 2.02$) : $v_p \approx 0.66c$.

### 10.4 Sensibilité aux paramètres

L'impédance caractéristique dépend **logarithmiquement** du ratio $D/d$, ce qui explique pourquoi :
- Des variations géométriques modérées affectent peu $Z_0$
- Le ratio diamétrique est plus critique que les dimensions absolues
- Des tolérances de fabrication de ±10% sur $D$ ou $d$ conduisent à ±3-5% sur $Z_0$

---

## 11. Abaque de Smith

### 11.1 Introduction et construction

L'**abaque de Smith** (ou **Smith chart**) est une représentation graphique du plan de réflexion complexe $\Gamma = \Gamma_r + j\Gamma_i$. Elle permet de passer visuellement entre les représentations en coefficient de réflexion et en impédance normalisée.

La transformation mathématique sous-jacente est :

$$
\Gamma = \frac{z - 1}{z + 1}
$$

où $z = Z/Z_0$ est l'impédance **normalisée** par rapport à l'impédance caractéristique.

### 11.2 Structure et grilles

L'abaque de Smith contient deux familles de courbes :

#### **Grille de résistance** (cercles concentriques centrés)

Les courbes de **résistance normalisée constante** $r_n = \text{Re}[z]$ satisfont :

$$
\left(\Gamma_r - \frac{r_n}{1+r_n}\right)^2 + \Gamma_i^2 = \left(\frac{1}{1+r_n}\right)^2
$$

- Centre : $\Gamma_r = \frac{r_n}{1+r_n}$
- Rayon : $\frac{1}{1+r_n}$

**Propriétés** :
- Pour $r_n = 0$ (circuit résistif pur) : cercle de rayon 1 (limite du Smith chart)
- Pour $r_n = 1$ (adaptation, $z=1$) : centre du graphique
- Pour $r_n \to \infty$ : dégénère au point $(1, 0)$ — circuit ouvert

#### **Grille de réactance** (courbes orthogonales)

Les courbes de **réactance normalisée constante** $x_n = \text{Im}[z]$ satisfont :

$$
\left(\Gamma_r - 1\right)^2 + \left(\Gamma_i - \frac{1}{x_n}\right)^2 = \left(\frac{1}{x_n}\right)^2
$$

- Centre : $(1, 1/x_n)$
- Rayon : $1/|x_n|$

**Propriétés** :
- Les courbes $x_n = 0$ correspondent à l'axe réel (résistances pures)
- $x_n > 0$ : inductif (demi-plan supérieur)
- $x_n < 0$ : capacitif (demi-plan inférieur)

### 11.3 Interprétation physique

**Région adaptée** : Zone près du centre $(1, 0)$ où $|\Gamma|$ est faible, et l'impédance est proche de $Z_0$.

**Région hautement réfléchissante** : Proche de la limite $|\Gamma| = 1$, où la majorité de l'énergie est réfléchie.

**Axe réel** :
- Point $(1, 0)$ : $\Gamma = 0$, adaptation parfaite, $z = 1$
- Point $(-1, 0)$ : $\Gamma = -1$, court-circuit, $z = 0$
- Point $(+1, 0)$ : $\Gamma = +1$, circuit ouvert, $z = \infty$

### 11.4 Rotation le long de la ligne de transmission

Quand on remonte une ligne de transmission (en régime lossless) vers la source, le point représentatif de l'impédance **tourne autour du centre** suivant un arc de cercle à résistance constante.

**Loi de rotation** :
$$
\theta_{\text{rotation}} = 2\beta \ell = 2\pi \frac{\ell}{\lambda}
$$

où $\ell$ est la distance parcourue vers la source.

- Pour une rotation d'une demi-longueur d'onde ($\ell = \lambda/2$) : rotation de $2\pi$, soit un tour complet
- Pour une rotation d'un quart de longueur d'onde ($\ell = \lambda/4$) : rotation de $\pi$, soit un demi-tour (transformation $z \to 1/z$)

### 11.5 Utilisation pratique

**Lecture directe d'impédance** :
1. Placer le point correspondant au coefficient de réflexion mesuré (traité comme un point dans le plan complexe)
2. Lire l'impédance normalisée directement sur les grilles de résistance et réactance

**Rotation sur la ligne** :
1. Pointer l'impédance terminale $z_L$
2. Tracer un arc circulaire centré au cœur du Smith chart (arc = cercle de $|\Gamma|$ constant)
3. Tourner de $2\beta \ell$ selon l'échelle de longueur d'onde en périphérie
4. Lire la nouvelle impédance au point d'arrivée

**Adaptation d'impédance** :
1. Placer la charge $Z_L$ sur le Smith chart
2. Chercher les positions à quart-d'onde : tourner de $\pi$ autour du center
3. Insérer des stub (tronçons de ligne) ou des éléments localisés pour ramener l'impédance vers le centre

### 11.6 Variantes du Smith chart

#### **Smith chart d'admittance** (Y-chart)

En inversant la transformation ($y = 1/z$), on obtient le **Smith chart d'admittance** :

$$
\Gamma = \frac{1 - y}{1 + y}
$$

Les grilles s'échangent : les courbes de conductance remplacent celles de résistance, et les courbes de susceptance remplacent celles de réactance.

#### **Smith chart hybride** (YZ-chart)

Superpose les grilles Z et Y sur le même graphique (codes couleur différents), facilitant les conversions rapides.

### 11.7 Calculs de matching networks

L'abaque de Smith simplifie grandement le **calcul de réseaux d'adaptation** :

**Matching serie-parallèle** :
1. Porter l'impédance de charge $Z_L$ sur le chart
2. Tourner sur le cercle de $|\Gamma|$ constant par une addition série
3. Traduire sur l'admittance chart pour placer un stub parallèle
4. Répéter jusqu'à ramener vers $z = 1$

**Matching à ligne quart-d'onde** :
1. La charge $Z_L$ est d'abord connectée à une ligne $Z_{opt} = \sqrt{Z_0 Z_L}$ de longueur $\lambda/4$
2. La sortie de cette section voit l'impédance $Z_0$ (adaptation)

---

## 12. Synthèse et Liens entre les Concepts

### 12.1 Hiérarchie conceptuelle

Équations des télégraphistes (R, L, G, C)
         ↓
Équations d'onde (γ = α + jβ)
         ↓
    ├─ Impédance caractéristique Z₀
    ├─ Vitesse de propagation v_p = ω/β
    └─ Coefficient de réflexion Γ
         ↓
Impédance d'entrée (transformation le long de z)
         ↓
Abaque de Smith (représentation graphique)

### 12.2 Chaîne causale

1. **Géométrie du câble** (d, D, εᵣ) → paramètres distribués (L, C)
2. **Paramètres distribués** → impédance caractéristique $Z_0 = \sqrt{L/C}$
3. **Charge terminale** $Z_L$ → coefficient de réflexion $\Gamma_L = (Z_L - Z_0)/(Z_L + Z_0)$
4. **Longueur de ligne** + $\Gamma_L$ → impédance d'entrée $Z_{in}$
5. **Impédance d'entrée** → paramètre de conception du circuit

### 12.3 Interprétations énergétiques

- **Adaptation ($Z_L = Z_0$)** : Transfert maximal de puissance, pas de réflexion, pas d'ondes stationnaires
- **Désadaptation** : Création d'ondes stationnaires, dissipation d'énergie, dégradation de bande passante
- **Quart-d'onde** : Permet l'inversion d'impédance pour des adaptations de puissance

### 12.4 Lien avec les paramètres S

Le coefficient de réflexion $\Gamma$ mesuré en entrée d'une ligne est directement le paramètre $S_{11}$ (réflexion en port 1) :

$$
S_{11} = \Gamma(z=0) = \Gamma_L e^{-2\gamma \ell}
$$

L'abaque de Smith est donc un outil graphique pour visualiser le diagramme de pôles-zéros et les lieux des paramètres S.

---

## 13. Conclusion

La théorie des lignes de transmission repose sur quatre piliers :

1. **Modèle distribué** (équations des télégraphistes) en liant R, L, G, C
2. **Propagation ondulatoire** (équations d'onde) avec réflexion et transmission
3. **Impédance caractéristique** déterminant l'interaction onde-ligne
4. **Transformation d'impédance** le long de la ligne, représentée visuellement par l'abaque de Smith

Ces concepts s'appliquent universellement dans les domaines suivants :
- Conception de circuits RF/Micro-ondes
- Adaptateurs d'impédance et filtres distribués
- Câblage haute fréquence et intégrité du signal
- Lignes de puissance en régime établi ou transitoire
- Antennes et propagation guidée

La maîtrise de ces outils permet une conception efficace et optimisée des systèmes haute fréquence modernes.

---

## Références

[1] Griffiths, D. J. (2013). *Introduction to Electrodynamics* (4th ed.). Pearson Education.

[2] Pozar, D. M. (2012). *Microwave Engineering* (4th ed.). John Wiley & Sons. Chapters 2-3.

[3] Bird, T. S. (2015). Definition and misuse of return loss. *IEEE Antennas & Propagation Magazine*, 51(2), 166-175.

[4] Steer, M. B. (2023). *Microwave and RF Design I: Transmission Lines*. NCState Libraries. Online resource.

[5] Smith, P. H. (1939). Transmission line calculator. *Electronics Magazine*, 12(1), 29-31.

[6] Collin, R. E. (1992). *Foundations for Microwave Engineering* (2nd ed.). McGraw-Hill. Chapter 2.

[7] Serway, R. A., & Jewett, J. W. (2018). *Physics for Scientists and Engineers* (10th ed.). Cengage Learning. Chapter 34 (Electromagnetic Waves).

[8] ITU-T Recommendation G.703. (2016). Physical and electrical characteristics of hierarchical digital interfaces. International Telecommunication Union.
