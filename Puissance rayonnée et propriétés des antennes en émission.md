# Puissance rayonnée et propriétés des antennes en émission

## 1. Introduction et notions générales

Une antenne est un dispositif qui permet la conversion entre des grandeurs électriques localisées (tension, courant aux bornes d’un port) et un champ électromagnétique rayonné dans l’espace. En émission, l’antenne transforme la puissance fournie par un générateur en onde électromagnétique propagative.  

Dans ce document, on se place dans le cadre classique des antennes linéaires fonctionnant dans le vide (ou l’air, supposé équivalent) et on adopte les conventions usuelles de l’électromagnétisme harmonique (variation temporelle en $e^{j\omega t}$). On introduit successivement :

- La puissance rayonnée à grande distance et le vecteur de Poynting réel et complexe.  
- Les notions de diagramme de rayonnement, d’intensité de rayonnement, de directivité et de gain.  
- La résistance de rayonnement et son interprétation en termes de circuit équivalent.  
- Le calcul explicite, dans l’approximation de champ lointain, des grandeurs précédentes pour un doublet de Hertz (dipôle élémentaire) puis pour un dipôle court.

---

## 2. Champs rayonnés et zones autour de l’antenne

### 2.1 Champs proche et lointain

Considérons une antenne localisée dans un volume fini autour de l’origine. Les champs électromagnétiques qu’elle crée peuvent être décomposés en :

- **Champ proche réactif** (near-field réactif) :  
  - Dominé par des composantes en $1/r^3$ et $1/r^2$.  
  - L’énergie oscille entre le champ électrique et le champ magnétique, mais ne contribue pas à un transport net d’énergie vers l’infini (puissance moyenne nulle).  
- **Champ rayonné (champ lointain, far-field)** :  
  - Dominé par des termes en $1/r$.  
  - L’énergie est transportée de manière irréversible vers l’infini.  
  - Les champs sont localement transverses (onde TEM approximative) avec $|\mathbf{E}| = \eta_0|\mathbf{H}|$, où $\eta_0 \approx 120\pi\ \Omega$ est l’impédance du vide.  

On définit généralement la **zone de Fraunhofer** (champ lointain) par la condition
$$
r \gtrsim \max\left(\frac{2D^2}{\lambda},\, 10\lambda\right),
$$
où $D$ est la dimension maximale de l’antenne et $\lambda$ la longueur d’onde[source:9].

Dans cette zone, le diagramme de rayonnement ne dépend plus de $r$ (il ne dépend que des angles $\theta,\phi$).

---

## 3. Vecteur de Poynting et puissance rayonnée

### 3.1 Vecteur de Poynting instantané

Le **vecteur de Poynting** instantané est défini, en régime temporel, par
$$
\mathbf{S}(\mathbf{r},t) = \mathbf{E}(\mathbf{r},t)\times \mathbf{H}(\mathbf{r},t),
$$
et représente la densité locale de flux de puissance électromagnétique (en W/m$^2$)[source:18].

### 3.2 Vecteur de Poynting complexe et puissance moyenne

En régime harmonique, on travaille avec les **phasors** $\mathbf{E}(\mathbf{r})$ et $\mathbf{H}(\mathbf{r})$ (dépendance temporelle $e^{j\omega t}$ implicite). On définit alors le **vecteur de Poynting complexe** :
$$
\mathbf{S}_c(\mathbf{r}) = \frac{1}{2}\,\mathbf{E}(\mathbf{r})\times \mathbf{H}^*(\mathbf{r}) \qquad [\text{W/m}^2],
$$
où $(\cdot)^*$ désigne le conjugué complexe[source:9][source:12][source:18].

- La **partie réelle** de $\mathbf{S}_c$,
  $$
  \langle \mathbf{S}(\mathbf{r})\rangle = \Re\{\mathbf{S}_c(\mathbf{r})\},
  $$
  est la densité de puissance moyenne transportée (puissance active).  
- La **partie imaginaire** de $\mathbf{S}_c$ est associée à la puissance réactive, stockée transitoirement dans le champ proche.

Dans le champ lointain d’une antenne, les champs sont quasi transverses, et on a typiquement (en coordonnées sphériques)
$$
\mathbf{E} \approx \hat{\boldsymbol{\theta}}\,E_\theta + \hat{\boldsymbol{\phi}}\,E_\phi,\qquad
\mathbf{H} \approx \hat{\boldsymbol{\phi}}\,H_\phi + \hat{\boldsymbol{\theta}}\,H_\theta,
$$
avec $E_\theta = \eta_0 H_\phi$, etc. Le vecteur de Poynting moyen est alors essentiellement radial :
$$
\langle \mathbf{S} \rangle \approx \hat{\mathbf{r}}\,\langle S_r\rangle,\quad 
\langle S_r \rangle = \frac{1}{2}\Re\{E_\theta H_\phi^* + E_\phi H_\theta^*\}.
$$

### 3.3 Puissance totale rayonnée

La **puissance totale rayonnée** par l’antenne est obtenue en intégrant le flux de Poynting moyen sur une sphère de rayon $r$ suffisamment grand (dans le champ lointain) :
$$
P_{\text{rad}} = \oint_{S_r} \langle \mathbf{S} \rangle\cdot d\mathbf{S}
= \int_0^{2\pi}\int_0^{\pi} \langle S_r(r,\theta,\phi)\rangle\,r^2\sin\theta\,d\theta\,d\phi.
$$
Dans la zone de champ lointain, $r^2\langle S_r\rangle$ ne dépend plus de $r$, ce qui permet de définir l’**intensité de rayonnement**.

---

## 4. Intensité de rayonnement et diagrammes de rayonnement

### 4.1 Intensité de rayonnement

On définit l’**intensité de rayonnement** $U(\theta,\phi)$ par
$$
U(\theta,\phi) = r^2\langle S_r(r,\theta,\phi)\rangle \quad [\text{W/sr}].
$$
C’est la puissance rayonnée par unité d’angle solide dans la direction $(\theta,\phi)$[source:7][source:16][source:19].

La puissance totale s’écrit alors
$$
P_{\text{rad}} = \int_{4\pi} U(\theta,\phi)\,d\Omega 
= \int_0^{2\pi}\int_0^{\pi} U(\theta,\phi)\sin\theta\,d\theta\,d\phi.
$$

### 4.2 Diagramme de rayonnement

Le **diagramme de rayonnement** (ou pattern de rayonnement) d’une antenne caractérise la variation angulaire du champ ou de la puissance rayonnée. On distingue plusieurs représentations :

- **Diagramme de champ** : proportionnel à $|E_\theta(\theta,\phi)|$ ou $|E_\phi(\theta,\phi)|$.  
- **Diagramme de puissance** : proportionnel à $U(\theta,\phi)$ ou à $|E(\theta,\phi)|^2$.  

En pratique, on normalise souvent $U(\theta,\phi)$ par sa valeur maximale :
$$
F(\theta,\phi) = \frac{U(\theta,\phi)}{U_{\max}},
$$
et on représente $F$ en dB :
$$
F_{\text{dB}}(\theta,\phi) = 10\log_{10}\left(\frac{U(\theta,\phi)}{U_{\max}}\right)\ \text{[dB]}.
$$

Le diagramme peut être donné :

- en **3D** (surface dans l’espace),  
- en **coupes 2D** caractéristiques (plans de coupe E et H pour les antennes linéaires[source:7][source:16]).

---

## 5. Directivité, gain et efficacité

### 5.1 Directivité

La **directivité** $D(\theta,\phi)$ d’une antenne mesure sa capacité à concentrer le rayonnement dans certaines directions par rapport à une source isotrope. Elle est définie par[source:7][source:16][source:19] :
$$
D(\theta,\phi) = \frac{U(\theta,\phi)}{U_{\text{moy}}},
$$
où
$$
U_{\text{moy}} = \frac{P_{\text{rad}}}{4\pi}
$$
est l’intensité de rayonnement moyenne sur $4\pi$ stéradians.

La **directivité maximale** (souvent simplement appelée « directivité ») est
$$
D_0 = \max_{\theta,\phi} D(\theta,\phi) = \frac{U_{\max}}{U_{\text{moy}}}
= \frac{4\pi U_{\max}}{P_{\text{rad}}}.
$$

Une antenne isotrope, rayonnant uniformément dans toutes les directions, a $D_0 = 1$ (0 dB). Pour un doublet de Hertz, on obtient typiquement $D_0 = 1{,}5$ (soit environ 1,76 dB)[source:1][source:5][source:11][source:14].

### 5.2 Efficacité et gain

La puissance fournie à l’antenne $P_{\text{in}}$ se répartit entre :

- la puissance **rayonnée** $P_{\text{rad}}$ ;
- les pertes **ohmiques** et diélectriques $P_{\text{pertes}}$ (échauffement, pertes dans le diélectrique, etc.).

On définit l’**efficacité de rayonnement** $\eta_{\text{rad}}$ par[source:7][source:16][source:19] :
$$
\eta_{\text{rad}} = \frac{P_{\text{rad}}}{P_{\text{in}}},\qquad 0 \le \eta_{\text{rad}} \le 1.
$$

Le **gain** $G(\theta,\phi)$ tient compte des pertes et se définit comme
$$
G(\theta,\phi) = \eta_{\text{rad}} D(\theta,\phi).
$$
Le **gain maximal** est
$$
G_0 = \eta_{\text{rad}} D_0.
$$

On exprime souvent $D_0$ et $G_0$ en dBi (dB par rapport à une antenne isotrope) :
$$
D_0\text{ [dBi]} = 10\log_{10}(D_0), \qquad G_0\text{ [dBi]} = 10\log_{10}(G_0).
$$

---

## 6. Résistance de rayonnement et modèle de circuit

### 6.1 Impédance d’antenne

L’antenne vue depuis ses bornes d’alimentation se comporte comme une **impédance équivalente** $Z_{\text{ant}}$ :
$$
Z_{\text{ant}} = R_{\text{rad}} + R_{\text{pertes}} + jX_{\text{ant}},
$$
où :

- $R_{\text{rad}}$ : **résistance de rayonnement**,  
- $R_{\text{pertes}}$ : **résistance de pertes** (ohmiques, diélectriques),  
- $X_{\text{ant}}$ : **réactance** (capacitance/inductance équivalente).

### 6.2 Définition de la résistance de rayonnement

La **résistance de rayonnement** est définie comme la résistance fictive qui dissiperait la même puissance que celle rayonnée lorsque l’antenne est parcourue par un courant $I_{\text{in}}$ à ses bornes[source:12][source:20] :
$$
P_{\text{rad}} = \frac{1}{2} |I_{\text{in}}|^2 R_{\text{rad}}.
$$
On en déduit
$$
R_{\text{rad}} = \frac{2P_{\text{rad}}}{|I_{\text{in}}|^2}.
$$

Physiquement, cette résistance représente le couplage entre le circuit d’alimentation et le champ rayonné : plus $R_{\text{rad}}$ est grande (pour un courant donné), plus l’antenne rayonne efficacement.

### 6.3 Efficacité en termes de résistances

Si l’on regroupe les pertes ohmiques dans une résistance $R_{\text{pertes}}$, alors
$$
P_{\text{pertes}} = \frac{1}{2} |I_{\text{in}}|^2 R_{\text{pertes}},
$$
et l’efficacité de rayonnement s’écrit
$$
\eta_{\text{rad}} = \frac{R_{\text{rad}}}{R_{\text{rad}} + R_{\text{pertes}}}.
$$

---

## 7. Doublet de Hertz (dipôle élémentaire)

Le **doublet de Hertz** est un modèle d’antenne élémentaire constitué d’un segment de courant de longueur $l$ très petite devant la longueur d’onde ($l \ll \lambda$), parcouru par un courant harmonique $I_0 e^{j\omega t}$ uniformément distribué. On le considère généralement orienté suivant l’axe $z$.

Ce modèle est fondamental car :

- Il permet une dérivation analytique simple du champ rayonné.  
- Tout courant distribué peut être décomposé en une superposition de doublets de Hertz (principe de superposition).  

### 7.1 Champs du doublet de Hertz en champ lointain

On se place dans le vide, avec $k = 2\pi/\lambda$ le nombre d’onde et $r$ la distance radiale. Pour un doublet de Hertz orienté selon $z$, de moment de dipôle
$$
\mathbf{p} = \hat{\mathbf{z}}\,I_0 l,
$$
les composantes de champ en coordonnées sphériques, dans la région de champ lointain ($kr\gg 1$), sont[source:1][source:5][source:11][source:14][source:16]:

- Champs **électrique** et **magnétique** non nuls principaux :
  $$
  E_\theta(r,\theta) \approx j\eta_0 \frac{k I_0 l}{4\pi r}\,e^{-jkr}\,\sin\theta,
  $$
  $$
  H_\phi(r,\theta) \approx j \frac{k I_0 l}{4\pi r}\,e^{-jkr}\,\sin\theta.
  $$
- Autres composantes ($E_r$, $E_\phi$, $H_r$, $H_\theta$) négligeables en champ lointain.

On a bien $E_\theta = \eta_0 H_\phi$ et $E_\theta, H_\phi \propto \dfrac{e^{-jkr}}{r}$.

### 7.2 Vecteur de Poynting et intensité de rayonnement du doublet de Hertz

Le vecteur de Poynting complexe radial vaut
$$
S_{c,r} = \frac{1}{2}E_\theta H_\phi^*.
$$
En insérant les expressions précédentes :
\[
\begin{aligned}
S_{c,r} &= \frac{1}{2}\left(j\eta_0 \frac{k I_0 l}{4\pi r}e^{-jkr}\sin\theta\right)
\left(j \frac{k I_0 l}{4\pi r}e^{+jkr}\sin\theta\right)^* \\
&= \frac{1}{2}\eta_0 \left(\frac{k I_0 l}{4\pi r}\right)^2 \sin^2\theta,
\end{aligned}
\]
car $|e^{-jkr}|^2 = 1$ et $j\cdot(-j) = 1$.

La **densité de puissance moyenne** est donc
$$
\langle S_r\rangle = \Re\{S_{c,r}\} 
= \frac{1}{2}\eta_0 \left(\frac{k |I_0| l}{4\pi r}\right)^2 \sin^2\theta.
$$

L’**intensité de rayonnement** s’écrit alors
$$
U(\theta) = r^2\langle S_r\rangle 
= \frac{1}{2}\eta_0 \left(\frac{k |I_0| l}{4\pi}\right)^2 \sin^2\theta.
$$

### 7.3 Diagramme de rayonnement du doublet de Hertz

On obtient, à un facteur multiplicatif près, le diagramme de rayonnement en puissance :
$$
U(\theta)\propto \sin^2\theta.
$$
Ce diagramme :

- est maximum dans le plan équatorial ($\theta = \pi/2$),  
- s’annule sur l’axe du dipôle ($\theta = 0$ et $\theta = \pi$),  
- est **tore** autour de l’axe $z$.

En champ, le diagramme est proportionnel à $|E_\theta(\theta)|\propto \sin\theta$.

### 7.4 Puissance totale rayonnée par le doublet de Hertz

Calculons la puissance totale :
\[
\begin{aligned}
P_{\text{rad}} &= \int_0^{2\pi}\int_0^{\pi} U(\theta)\sin\theta\,d\theta\,d\phi \\
&= 2\pi \int_0^{\pi} 
\left[\frac{1}{2}\eta_0 \left(\frac{k |I_0| l}{4\pi}\right)^2 \sin^2\theta \right]
\sin\theta\,d\theta \\
&= \eta_0 \left(\frac{k |I_0| l}{4\pi}\right)^2 \pi
\int_0^{\pi}\sin^3\theta\,d\theta.
\end{aligned}
\]
On utilise
$$
\int_0^{\pi}\sin^3\theta\,d\theta = \frac{4}{3}.
$$
Ainsi
\[
\begin{aligned}
P_{\text{rad}} &= \eta_0 \left(\frac{k |I_0| l}{4\pi}\right)^2 \pi \cdot \frac{4}{3} \\
&= \eta_0 \frac{k^2 |I_0|^2 l^2}{16\pi^2} \cdot \frac{4\pi}{3} \\
&= \eta_0 \frac{k^2 |I_0|^2 l^2}{12\pi}.
\end{aligned}
\]

En remplaçant $k = 2\pi/\lambda$ et $\eta_0 = \sqrt{\mu_0/\varepsilon_0}$ on obtient la forme usuelle[source:1][source:5][source:11][source:14][source:16] :
$$
P_{\text{rad}} = \frac{|I_0|^2}{2} R_{\text{rad}},
$$
avec
$$
R_{\text{rad}} = 80\pi^2\left(\frac{l}{\lambda}\right)^2\ \Omega
\quad\text{(doublet de Hertz)}.
$$

### 7.5 Directivité du doublet de Hertz

On dispose de
$$
U(\theta) = U_0 \sin^2\theta, \qquad U_0 = \frac{1}{2}\eta_0 \left(\frac{k |I_0| l}{4\pi}\right)^2.
$$
- Maximum : $U_{\max} = U_0$ (à $\theta = \pi/2$).  
- Moyenne :
  \[
  \begin{aligned}
  U_{\text{moy}} &= \frac{P_{\text{rad}}}{4\pi} 
  = \frac{1}{4\pi}\eta_0 \frac{k^2 |I_0|^2 l^2}{12\pi}
  = \frac{\eta_0 k^2 |I_0|^2 l^2}{48\pi^2}.
  \end{aligned}
  \]

La directivité maximale vaut donc
\[
\begin{aligned}
D_0 &= \frac{U_{\max}}{U_{\text{moy}}}
= \frac{U_0}{U_{\text{moy}}} 
= \frac{\frac{1}{2}\eta_0 \left(\frac{k |I_0| l}{4\pi}\right)^2}{\frac{\eta_0 k^2 |I_0|^2 l^2}{48\pi^2}} \\
&= \frac{\frac{1}{2}\eta_0 \frac{k^2 |I_0|^2 l^2}{16\pi^2}}{\frac{\eta_0 k^2 |I_0|^2 l^2}{48\pi^2}}
= \frac{\frac{1}{2}\cdot \frac{1}{16}}{\frac{1}{48}} 
= \frac{1/32}{1/48} = \frac{48}{32} = \frac{3}{2} = 1{,}5.
\end{aligned}
\]
Ce résultat est classique : **$D_0 = 1{,}5$ pour un doublet de Hertz** (soit $1{,}76$ dBi environ)[source:1][source:5][source:11][source:14][source:16].

---

## 8. Dipôle court (small dipole) et dipôle demi-onde

### 8.1 Dipôle court $l \ll \lambda$

Un **dipôle court** est un conducteur linéaire de longueur physique $l$ telle que $l \ll \lambda$, parcouru par un courant presque uniforme $I_0$.  

Dans cette approximation, les expressions de champ sont identiques à celles du doublet de Hertz, si l’on remplace $I_0 l$ par la **force électromotrice de dipôle** (moment de courant)
$$
I_0 l_{\text{eff}} \approx I_0 l,
$$
et les résultats pour $P_{\text{rad}}$, $R_{\text{rad}}$ et le diagramme restent valides[source:2][source:11][source:16]:

- Diagramme $\propto \sin^2\theta$,  
- $D_0 = 1{,}5$,  
- $R_{\text{rad}} \approx 80\pi^2 (l/\lambda)^2$.

Plus le dipôle est court devant la longueur d’onde, plus $R_{\text{rad}}$ est faible (et donc plus le couplage au rayonnement est « faible » à courant donné).

### 8.2 Dipôle demi-onde

Pour un dipôle de longueur voisine de $\lambda/2$ (dipôle demi-onde), la distribution de courant n’est plus uniforme. On adopte typiquement un profil sinusoïdal
$$
I(z) = I_0 \cos\left(k z\right), \quad -\frac{l}{2}\le z \le \frac{l}{2},\ l\approx \frac{\lambda}{2},
$$
et on recalcule le champ lointain par intégration. On obtient un diagramme de rayonnement toujours essentiellement $\sin\theta$ en amplitude, mais légèrement modifié en fonction de la longueur exacte.  

La **résistance de rayonnement** d’un dipôle demi-onde dans le vide est[source:2][source:11][source:16]:
$$
R_{\text{rad}} \approx 73\ \Omega,
$$
et la directivité vaut
$$
D_0 \approx 1{,}64 \quad (\approx 2{,}15\ \text{dBi}),
$$
valeurs très utilisées pour le dimensionnement et la comparaison d’antennes linéaires.

---

## 9. Interprétation physique : Poynting complexe et régions de champ

### 9.1 Interprétation du Poynting complexe

La quantité
$$
\mathbf{S}_c = \frac{1}{2}\mathbf{E}\times \mathbf{H}^*
$$
peut être interprétée comme un vecteur de puissance complexe[source:12][source:18] :

- $\Re\{\mathbf{S}_c\}$ : densité de puissance active (transport net d’énergie).  
- $\Im\{\mathbf{S}_c\}$ : densité de puissance réactive (énergie électromagnétique stockée localement, qui se prête et se rend au générateur sur un cycle).

Dans le champ proche réactif, $\Im\{\mathbf{S}_c\}$ domine, alors que dans le champ lointain, $\mathbf{S}_c$ est essentiellement réel.

### 9.2 Bilan de puissance et théorème de Poynting

Le **théorème de Poynting complexe** relie la puissance fournie par les sources, les pertes et l’énergie stockée au champ rayonné[source:12]. Intégré sur un volume entourant l’antenne, il donne :
- la relation entre la puissance fournie par le générateur et la somme  
  - de la puissance rayonnée (flux de Poynting sortant),  
  - de la puissance dissipée en pertes,  
  - de la variation d’énergie stockée.

En régime permanent, la variation d’énergie stockée moyenne est nulle ; la puissance moyenne fournie est donc égale à la somme de la puissance rayonnée et des pertes. C’est ce qui motive la représentation de l’antenne par une impédance $Z_{\text{ant}}$ contenant notamment $R_{\text{rad}}$.

---

## 10. Synthèse : propriétés d’émission d’un doublet de Hertz et d’un dipôle

Pour un **doublet de Hertz** (dipôle élémentaire) ou un **dipôle court** ($l\ll \lambda$) :

- **Champs en champ lointain** (dipôle orienté $z$) :
  $$
  E_\theta(r,\theta) \approx j\eta_0 \frac{k I_0 l}{4\pi r}e^{-jkr}\sin\theta,\quad
  H_\phi(r,\theta) \approx j \frac{k I_0 l}{4\pi r}e^{-jkr}\sin\theta.
  $$
- **Vecteur de Poynting moyen** :
  $$
  \langle S_r\rangle = \frac{1}{2}\eta_0 \left(\frac{k |I_0| l}{4\pi r}\right)^2 \sin^2\theta.
  $$
- **Intensité de rayonnement** :
  $$
  U(\theta) = r^2\langle S_r\rangle 
  = \frac{1}{2}\eta_0 \left(\frac{k |I_0| l}{4\pi}\right)^2 \sin^2\theta.
  $$
- **Diagramme de rayonnement** : 
  - en champ : $|E_\theta|\propto \sin\theta$,  
  - en puissance : $U(\theta)\propto \sin^2\theta$.
- **Puissance totale rayonnée** :
  $$
  P_{\text{rad}} = \eta_0 \frac{k^2 |I_0|^2 l^2}{12\pi}.
  $$
- **Résistance de rayonnement** :
  $$
  R_{\text{rad}} = \frac{2P_{\text{rad}}}{|I_0|^2}
  = 80\pi^2\left(\frac{l}{\lambda}\right)^2\ \Omega.
  $$
- **Directivité** :
  $$
  D_0 = \frac{3}{2} = 1{,}5\ (\approx 1{,}76\ \text{dBi}).
  $$

Pour un **dipôle demi-onde** ($l \approx \lambda/2$) :

- Le diagramme est encore de type sinusoïdal en $\theta$, légèrement différent du cas élémentaire.  
- La directivité vaut $D_0 \approx 1{,}64$ (soit 2,15 dBi).  
- La résistance de rayonnement vaut environ $R_{\text{rad}}\approx 73\ \Omega$.  

Ces résultats constituent la base des modèles d’antenne dipôle utilisés en télécommunications, en radio et en micro-ondes. Ils permettent de relier directement la puissance électrique fournie au dipôle, via $R_{\text{rad}}$ et l’impédance d’antenne, à la puissance rayonnée et à sa répartition angulaire (diagramme, directivité, gain).

---

## Références indicatives

[1] W. C. Chew, *Lecture 25: Radiation by a Hertzian Dipole*, notes de cours ECE 604, Purdue University, 2019–2020.  
[2] R. E. Collin, *Antennas and Radiowave Propagation*, McGraw-Hill, 1985.  
[3] J. D. Kraus, R. J. Marhefka, *Antennas for All Applications*, 3e éd., McGraw-Hill, 2002.  
[4] C. A. Balanis, *Antenna Theory: Analysis and Design*, 3e éd., Wiley, 2005.  
[5] W. C. Chew, *Radiation by a Hertzian Dipole*, ECE 604s20, Purdue University (PDF en ligne)[source:5].  
[6] A. Nikolova, *Lecture 4: Fundamental Antenna Parameters*, McMaster University, 2025[source:7].  
[7] MIT OCW, *6.013 Electromagnetics and Applications – 12.5 Complex Poynting’s Theorem and Radiation Resistance*[source:12].  
[8] Wikipedia, *Poynting Vector* (consulté 2025)[source:18].  
[9] NATO STO, *Fundamentals on Antennas and Antenna Definitions* (EN-SET-337-02)[source:19].  
[10] Antenna Basics, Michigan State University, Module 6: *Antennas*[source:20].
