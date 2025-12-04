# Représentation d'un Système de Transmission et Réponse Impulsionnelle du Canal
## Cas de l'Espace Libre avec Effet Doppler

---

## 1. Introduction et Contexte

La modélisation des canaux de transmission sans fil constitue une étape cruciale dans la conception de systèmes de communication modernes. Ce document traite de la représentation complète d'un système de transmission en espace libre en présence d'effet Doppler, incluant les notions de réponse impulsionnelle dépendante du temps, d'enveloppe complexe et de caractérisation simultanée en domaines temporel et fréquentiel[1].

L'effet Doppler sur un canal sans fil provient du mouvement relatif entre l'émetteur et le récepteur, ou entre ces derniers et les réflecteurs de l'environnement. Ce phénomène introduit une variance temporelle du canal qui doit être modélisée avec soin pour la performance des systèmes modernes de transmission numérique[2].

---

## 2. Architecture du Système de Transmission et Réception

### 2.1 Bloc Émetteur (Transmitter)

Le bloc émetteur effectue une transposition de fréquence du signal baseband vers la bande RF de transmission.

**Signal en bande de base (baseband):**
$$
\tilde{s}(t) = s_I(t) + j \, s_Q(t)
$$

où $s_I(t)$ et $s_Q(t)$ sont respectivement les composantes en phase (In-phase) et en quadrature (Quadrature).

**Transposition à la fréquence porteuse $f_c$:**

Le signal RF transmis s'écrit :
$$
s_{\text{RF}}(t) = \text{Re}\left\{\tilde{s}(t) \, e^{j 2\pi f_c t}\right\} = \tilde{s}(t) \, e^{j 2\pi f_c t} + \tilde{s}^*(t) \, e^{-j 2\pi f_c t}
$$

Par convention, on retient la partie complexe :
$$
s_{\text{RF}}(t) = \sqrt{2} \, \text{Re}\left\{\tilde{s}(t) \, e^{j 2\pi f_c t}\right\}
$$

**Schéma de l'émetteur:**

┌─────────────┐     ┌──────────┐     ┌──────────┐
│  Données    │ → │ Codage/  │ → │  Filtre  │ → s_RF(t)
│ binaires    │     │ Mod.     │     │  TX      │
└─────────────┘     └──────────┘     └──────────┘
                    ↑                 ↑
                 s_I(t)+jS_Q(t)    e^(j2πf_ct)
                    (Baseband)       (Porteuse)

### 2.2 Canal en Espace Libre avec Doppler

Le canal introduit :
- **Atténuation de puissance** : facteur $a$ dépendant de la distance $r$
- **Retard de propagation** : $\tau(t)$ dépendant du temps (mobilité)
- **Décalage Doppler** : $\nu_d(t)$ dépendant du vecteur vitesse relative

Pour une onde sphérique en espace libre :
$$
a = \frac{\lambda}{4 \pi r}
$$

où $\lambda = c / f_c$ est la longueur d'onde.

Le **décalage Doppler** s'exprime comme :
$$
\nu_d(t) = f_c \frac{v_r(t)}{c} = f_c \frac{\dot{r}(t)}{c}
$$

où $v_r(t) = \dot{r}(t)$ est la composante radiale de la vitesse relative, et $c$ la vitesse de la lumière.

**Doppler spread** (étalement Doppler) :
$$
B_D = f_{\max} - f_{\min} = 2 f_c \frac{v}{c}
$$

pour une vitesse maximale $v$ du récepteur.

### 2.3 Bloc Récepteur (Receiver)

**Signal reçu (passband RF):**

Le signal reçu en sortie du canal s'écrit :
$$
r_{\text{RF}}(t) = a(t) \, s_{\text{RF}}(t - \tau(t)) \, e^{j 2\pi \nu_d(t) t} + n(t)
$$

où $n(t)$ est le bruit additif blanc gaussien (AWGN).

**Démodulation (down-conversion):**

La transposition vers la bande de base s'effectue par multiplication avec le signal de référence local :
$$
c(t) = \sqrt{2} \, e^{j 2\pi f_c t}
$$

**Composantes down-converties:**
$$
i_{\text{down}}(t) = r_{\text{RF}}(t) \cos(2\pi f_c t)
$$
$$
q_{\text{down}}(t) = -r_{\text{RF}}(t) \sin(2\pi f_c t)
$$

**Signal complexe en bande de base:**
$$
\tilde{r}(t) = i_{\text{down}}(t) + j \, q_{\text{down}}(t)
$$

**Filtrage passe-bas d'image-rejet:**

Après filtrage passe-bas $H_{\text{LP}}(f)$ pour supprimer les images :
$$
\tilde{r}_{\text{LP}}(t) = \tilde{r}(t) * h_{\text{LP}}(t)
$$

**Schéma du récepteur:**

r_RF(t) ──┬──×─────→ cos(2πf_c t)  ──LP──┬──→ Décodeur
          │                               │
          ├──×─────→ -sin(2πf_c t) ──LP──┤
          │                               │
          └────────────────────────────────┘
                    ↓
                 i+jq (Baseband)

---

## 3. Réponse Impulsionnelle du Canal Dépendante du Temps

### 3.1 Définition Générale

Le **canal linéaire variant dans le temps** est caractérisé par sa réponse impulsionnelle (IRh) dépendante du temps :
$$
g(t, \tau) = \sum_{n=1}^{N} a_n(t) \, e^{j \phi_n(t)} \, \delta(\tau - \tau_n(t))
$$

où :
- $N$ est le nombre de trajets (composantes multi-trajets)
- $a_n(t)$ est l'amplitude du $n$-ième trajet (variant lentement)
- $\phi_n(t)$ est la phase variant rapidement du trajet $n$
- $\tau_n(t)$ est le retard de propagation du trajet $n$

La phase accumulée inclut l'effet Doppler :
$$
\phi_n(t) = \phi_{n,0} - 2\pi f_c \tau_n(t) + 2\pi \nu_{d,n}(t) \, t
$$

où $\nu_{d,n}(t) = f_c \dot{\tau}_n(t)$ est le décalage Doppler du trajet $n$.

### 3.2 Signal Reçu via Convolution

Le signal reçu (en bande de base équivalent) est donné par la convolution :
$$
\tilde{r}(t) = \int_0^{\infty} \tilde{g}(t, \tau) \, \tilde{s}(t - \tau) \, d\tau + \tilde{n}(t)
$$

où $\tilde{g}(t, \tau)$ est la réponse impulsionnelle équivalente en bande de base.

**Développement en trajets discrets:**
$$
\tilde{r}(t) = \sum_{n=1}^{N} c_n(t) \, \tilde{s}(t - \tau_n(t)) + \tilde{n}(t)
$$

avec le **gain complexe dépendant du temps:**
$$
c_n(t) = a_n(t) \, e^{j[\phi_n(t) - 2\pi f_c \tau_n(t)]}
$$

Dans le domaine de Fourier/Laplace, la fonction de transfert variant dans le temps s'écrit :
$$
T(t, f) = \int_0^{\infty} \tilde{g}(t, \tau) \, e^{-j 2\pi f \tau} \, d\tau = \sum_n c_n(t) \, e^{-j 2\pi f \tau_n(t)}
$$

---

## 4. Caractérisations de Canaux Particuliers

### 4.1 Canaux Plats en Fréquence (Frequency-Flat Channels)

Un canal est dit **plat en fréquence** si son étendue en délai (delay spread $\tau_d$) est négligeable devant l'inverse de la bande de base du signal.

**Condition:**
$$
\tau_d = \tau_{\max} - \tau_{\min} \ll \frac{1}{B}
$$

où $B$ est la bande d'intérêt du signal.

**Réponse impulsionnelle simplifié:**
$$
\tilde{g}(t, \tau) \approx g(t) \, \delta(\tau - \bar{\tau})
$$

avec gain complexe unique :
$$
g(t) = \sum_n a_n(t) \, e^{j[\phi_n(t) - 2\pi f_c \tau_n]}
$$

**Signal reçu:**
$$
\tilde{r}(t) = g(t) \, \tilde{s}(t - \bar{\tau}) + \tilde{n}(t)
$$

**Fonction de transfert (plat en fréquence):**
$$
T(t, f) = g(t) \, e^{-j 2\pi f \bar{\tau}}
$$

**Propriété clé:** L'amplitude $|T(t, f)| = |g(t)|$ est indépendante de $f$. Tous les composantes fréquentielles du signal subissent le même gain/atténuation (mais varient dans le temps).

### 4.2 Canaux Plats en Temps (Time-Flat Channels)

Un canal est dit **plat en temps** si le **Doppler spread** est négligeable :
$$
B_D = 2 f_c \frac{v}{c} \ll \frac{1}{T_s}
$$

où $T_s$ est la période symbole.

**Réponse impulsionnelle stationnaire:**
$$
\tilde{g}(\tau) = \sum_n a_n \, e^{j \phi_n} \, \delta(\tau - \tau_n)
$$

Pas de dépendance temporelle explicite. C'est le cas typique en **communications par câble** ou en milieux à faible mobilité.

**Signal reçu:**
$$
\tilde{r}(t) = \sum_n c_n \, \tilde{s}(t - \tau_n) + \tilde{n}(t)
$$

### 4.3 Canal Plat à la Fois en Temps et Fréquence

Condition combinée :
$$
\tau_d \ll \frac{1}{B} \quad \text{ET} \quad B_D \ll \frac{1}{T_s}
$$

**Réponse impulsionnelle:**
$$
\tilde{g}(t, \tau) = c(t) \, \delta(\tau)
$$

où $c(t)$ varie lentement (comparé à $1/T_s$).

**Signal reçu:**
$$
\tilde{r}(t) = c(t) \, \tilde{s}(t) + \tilde{n}(t)
$$

C'est le modèle du **canal à évanouissement plat** (flat fading channel). La fonction de transfert est :
$$
T(t, f) = c(t) = |c(t)| \, e^{j\arg(c(t))}
$$

---

## 5. Enveloppe Complexe du Signal Reçu

### 5.1 Définition de l'Enveloppe Complexe

Pour un signal RF passband :
$$
s(t) = \text{Re}\left\{\tilde{s}(t) \, e^{j 2\pi f_c t}\right\}
$$

l'**enveloppe complexe** (ou représentation en bande de base équivalente) est :
$$
\tilde{s}(t) = s_I(t) + j \, s_Q(t)
$$

### 5.2 Enveloppe Complexe Reçue en Cas d'Effet Doppler

La présence de **Doppler affecte la fréquence porteuse perçue**, créant un décalage :
$$
f_c' = f_c + \nu_d = f_c \left(1 + \frac{v_r}{c}\right)
$$

En démodulation à fréquence $f_c$ fixe (sans suivi Doppler), le signal reçu en bande de base contient une composante oscillante à fréquence résiduelle :
$$
\Delta \nu = \nu_d(t) = -f_c \frac{\dot{r}(t)}{c}
$$

**Enveloppe complexe reçue (avec effet Doppler non compensé):**
$$
\tilde{r}(t) = g(t) \, e^{j 2\pi \Delta \nu \, t} \, \tilde{s}(t - \tau) + \tilde{n}(t)
$$

**Pour un trajet unique en espace libre:**
$$
\tilde{r}(t) = a \, e^{-j 2\pi f_c \tau} \, e^{j 2\pi \nu_d t} \, \tilde{s}(t - \tau) + \tilde{n}(t)
$$

où le facteur $e^{j 2\pi \nu_d t}$ représente la **modulation Doppler** sur l'enveloppe.

### 5.3 Cas avec Enveloppe Lentement Variant

Sous l'hypothèse d'enveloppe complexe lentement variant (SLOWLY VARYING ENVELOPE APPROXIMATION - SVEA) :
$$
\left|\frac{d\tilde{s}(t)}{dt}\right| \ll 2\pi f_c |\tilde{s}(t)|
$$

et en ignorant les retards :
$$
\tilde{r}(t) \approx g(t) \, \tilde{s}(t) + \tilde{n}(t)
$$

où $g(t)$ inclut les effets Doppler lents et l'atténuation.

---

## 6. Fonction de Transfert et Fonction d'Étalement (Spreading Function)

### 6.1 Fonction de Transfert Variant dans le Temps

La fonction de transfert dans le domaine fréquentiel-temps s'écrit :
$$
T(t, f) = \int_0^{\infty} \tilde{g}(t, \tau) \, e^{-j 2\pi f \tau} \, d\tau
$$

**Propriétés:**
- $t$ : variable de temps (instant d'observation)
- $f$ : variable fréquence (sélectivité fréquentielle)

**Pour un canal à délai discrets:**
$$
T(t, f) = \sum_n c_n(t) \, e^{-j 2\pi f \tau_n(t)}
$$

### 6.2 Fonction d'Étalement Doppler-Délai (Spreading Function)

La représentation duale en domaines délai-Doppler est fournie par la **fonction d'étalement:**
$$
S_H(\tau, \nu) = \int_{-\infty}^{\infty} \tilde{g}(t, \tau) \, e^{-j 2\pi \nu t} \, dt
$$

où $\nu$ représente la **fréquence Doppler**.

**Interprétation physique:**
- $\tau$ : délai de propagation
- $\nu$ : décalage Doppler (fréquence-Doppler)

Pour un trajet avec Doppler pur :
$$
S_H(\tau, \nu) = c(\tau) \, \delta(\nu - \nu_d(\tau))
$$

**Propriété d'orthogonalité:**
$$
T(t, f) = \int_{-\infty}^{\infty} \int_0^{\infty} S_H(\tau, \nu) \, e^{j 2\pi(\nu t - f \tau)} \, d\tau \, d\nu
$$

### 6.3 Fonction de Cohérence Temps-Fréquence

**Temps de cohérence** (inversement lié à Doppler spread) :
$$
T_c \approx \frac{1}{2 \pi B_D} = \frac{c}{2\pi f_c v}
$$

**Bande de cohérence** (inversement liée à delay spread) :
$$
B_c \approx \frac{1}{5 \tau_d}
$$

---

## 7. Représentation Temporelle du Signal Reçu

### 7.1 Signal Réel en Sortie du Récepteur

Après démodulation et filtrage, le signal reçu complexe est :
$$
\tilde{r}(t) = \sum_n c_n(t) \, \tilde{s}(t - \tau_n(t)) + \tilde{n}(t)
$$

Le **signal réel** observable s'écrit :
$$
r(t) = \text{Re}\left\{\tilde{r}(t) \, e^{j 2\pi f_{IF} t}\right\}
$$

où $f_{IF}$ est une fréquence intermédiaire (éventuellement zéro pour accès direct en bande de base).

### 7.2 Graphiques Temporels Caractéristiques

**Enveloppe d'amplitude:**
$$
|g(t)| = \left|\sum_n a_n(t) \, e^{j \phi_n(t)}\right|
$$

manifeste des fluctuations rapides (fading rapide) si $B_D$ est grand, ou des fluctuations lentes (shadowing) sinon.

**Phase du gain complexe:**
$$
\psi(t) = \arg\{g(t)\} = \arg\left\{\sum_n a_n(t) \, e^{j \phi_n(t)}\right\}
$$

varie continuement si les trajets sont décorrélés.

---

## 8. Représentation Fréquentielle

### 8.1 Spectre du Signal Reçu

**Spectre du signal RF reçu:**
$$
R_{\text{RF}}(f) = \mathcal{F}\{r_{\text{RF}}(t)\}
$$

Pour un canal sans Doppler (stationnaire) :
$$
R_{\text{RF}}(f) = H(f) \cdot S_{\text{RF}}(f) + N(f)
$$

où $H(f) = |H(f)| e^{j\angle H(f)}$ est la réponse fréquentielle du canal.

### 8.2 Spectre en Bande de Base Équivalente

Après démodulation, le spectre en bande de base s'écrit :
$$
\tilde{R}(f) = \sum_n c_n \, S(f) \, e^{-j 2\pi f \tau_n} + \tilde{N}(f)
$$

Si le canal est **plat en fréquence** ($\tau_d \approx 0$) :
$$
\tilde{R}(f) = g \cdot S(f) + \tilde{N}(f)
$$

où $g$ est un gain complexe constant (dépendant du temps mais indépendant de $f$).

### 8.3 Densité Spectrale de Puissance avec Doppler

La **densité spectrale de puissance** (Power Spectral Density - PSD) du signal reçu inclut l'élargissement Doppler :
$$
S_r(f) = \int_{-\infty}^{\infty} |T(t, f + \nu)|^2 \, S_s(\nu) \, d\nu
$$

Pour un canal à Doppler uniforme (spectre classique de Jakes) :
$$
S_r(f) = \begin{cases}
\frac{1}{\pi B_D \sqrt{1 - (f/B_D)^2}} & |f| < B_D \\
0 & |f| \geq B_D
\end{cases}
$$

Cet **étalement en fréquence** est la marque de l'effet Doppler et rend nécessaires des techniques de suivi de fréquence (carrier recovery) dans le récepteur.

### 8.4 Fonction d'Autocorrélation Fréquentielle

Pour un canal présentant à la fois delay spread et Doppler spread :
$$
R_H(f_1, f_2, t) = E\{T^*(t, f_1) \, T(t, f_2)\}
$$

Le **bandwidth de cohérence** caractérise le domaine fréquentiel sur lequel le canal reste corrélé :
$$
B_c \sim \frac{1}{5 \, T_{max}}
$$

où $T_{max}$ est le délai maximal.

---

## 9. Synthèse Comparative des Régimes de Canal

\begin{table}
\begin{tabular}{|l|c|c|c|}
\hline
\textbf{Type de Canal} & \textbf{Delay Spread} & \textbf{Doppler Spread} & \textbf{Modèle} \\
\hline
Plat / Plat & $\tau_d \ll 1/B$ & $B_D \ll 1/T_s$ & $r(t) = g(t) \cdot s(t) + n(t)$ \\
\hline
Plat / Rapide & $\tau_d \ll 1/B$ & $B_D \gg 1/T_s$ & $r(t) = g(t) \cdot e^{j2\pi\nu_d t} \cdot s(t) + n(t)$ \\
\hline
Sélectif / Plat & $\tau_d \gg 1/B$ & $B_D \ll 1/T_s$ & $r(t) = \sum_n c_n \cdot s(t-\tau_n) + n(t)$ \\
\hline
Sélectif / Rapide & $\tau_d \gg 1/B$ & $B_D \gg 1/T_s$ & $r(t) = \sum_n c_n(t) \cdot e^{j2\pi\nu_d t} \cdot s(t-\tau_n) + n(t)$ \\
\hline
\end{tabular}
\caption{Régimes de canal et modèles correspondants}
\end{table}

---

## 10. Exemple Numériques et Cas Pratiques

### 10.1 Espace Libre sans Mobilité (Cas Trivial)

**Paramètres:**
- Distance: $r = 1000$ m
- Fréquence porteuse: $f_c = 900$ MHz
- Longueur d'onde: $\lambda = c/f_c = 0.33$ m
- Mobilité: $v = 0$ (stationnaire)

**Atténuation de puissance:**
$$
L = 20 \log_{10}\left(\frac{4\pi r}{\lambda}\right) = 20 \log_{10}\left(\frac{4\pi \cdot 1000}{0.33}\right) \approx 131 \text{ dB}
$$

**Doppler spread:** $B_D = 0$ (aucun effet Doppler).

**Canal:** Stationnaire, gain constant.

### 10.2 Espace Libre avec Mobilité (Haute Vitesse)

**Paramètres:**
- Véhicule à $v = 100$ km/h $\approx 27.8$ m/s
- Fréquence porteuse: $f_c = 2$ GHz
- Distance initiale: $r = 500$ m

**Décalage Doppler maximum:**
$$
\nu_d = f_c \frac{v}{c} = 2 \times 10^9 \times \frac{27.8}{3 \times 10^8} \approx 185 \text{ Hz}
$$

**Doppler spread** (approx, tous angles) :
$$
B_D = 2 \nu_d \approx 370 \text{ Hz}
$$

**Temps de cohérence:**
$$
T_c \approx \frac{1}{2\pi B_D} \approx \frac{1}{2\pi \times 370} \approx 0.43 \text{ ms}
$$

Pour une période symbole $T_s = 10$ µs, nous avons $T_c / T_s \approx 43 \gg 1$: le canal varie **lentement** (coherence time bien supérieure à durée symbole).

### 10.3 Espace Libre Multitrajet avec Mobilité

Supposons 3 trajets avec délais et Doppler différents:

\begin{table}
\begin{tabular}{|c|c|c|}
\hline
\textbf{Trajet $n$} & \textbf{Retard} $\tau_n$ (µs) & \textbf{Doppler} $\nu_{d,n}$ (Hz) \\
\hline
1 (direct) & 0.1 & +180 \\
2 (réfléchi 1) & 0.8 & -100 \\
3 (réfléchi 2) & 2.5 & +50 \\
\hline
\end{tabular}
\end{table}

**Delay spread:**
$$
\tau_d = 2.5 - 0.1 = 2.4 \text{ µs}
$$

**Bande de cohérence:**
$$
B_c \sim \frac{1}{5 \tau_d} = \frac{1}{5 \times 2.4 \times 10^{-6}} \approx 83 \text{ kHz}
$$

Si la bande du signal est $B = 1$ MHz, alors $B > B_c$: le canal est **fréquence-sélectif**.

**Doppler spread maximal:** $B_D = 180 - (-100) = 280$ Hz (écart entre trajets).

---

## 11. Techniques de Compensation et Traitement

### 11.1 Égalisation pour Canaux Sélectifs en Fréquence

En cas de delay spread significatif, un **égaliseur** (equalizer) est nécessaire:
$$
y(t) = \tilde{r}(t) * w(t)
$$

où $w(t)$ est le filtre d'égalisation adapté au canal estimé $\hat{g}(t, \tau)$.

### 11.2 Poursuite Doppler (Carrier Recovery)

Pour compenser le décalage Doppler résiduel après démodulation initiale :
$$
\hat{\nu}_d = \text{arg}\left\{\sum_i y_i \, y_{i-1}^*\right\} / (2\pi T_s)
$$

suivi d'une correction :
$$
y_{\text{corrected}}(t) = y(t) \, e^{-j 2\pi \hat{\nu}_d t}
$$

### 11.3 Estimation de Canal

L'estimation du canal variant dans le temps repose sur des **séquences de pilote** (pilot sequences) :
$$
\hat{g}(t, \tau) = \frac{\tilde{r}_{\text{pilot}}(t)}{\tilde{s}_{\text{pilot}}(t - \tau)}
$$

suivi d'une interpolation spatio-temporelle.

---

## 12. Conclusion

La représentation complète d'un système de transmission en espace libre avec effet Doppler requiert :

1. **Architecture transmetteur/récepteur:** Transpositions de fréquence (up-conversion/down-conversion) et filtrage adapté

2. **Réponse impulsionnelle variant dans le temps:** Modèle physique incorporant trajets multiples, délai et décalage Doppler

3. **Caractérisation duale:** Représentation joint délai-Doppler (spreading function) et représentation fréquence-temps

4. **Régimes particuliers:** Distinction entre canaux plats/sélectifs en fréquence et rapides/lents en temps

5. **Enveloppe complexe:** Modulation de l'enveloppe due au Doppler non-compensé, critique pour design du récepteur

6. **Représentations temporelle et fréquentielle:** Étalement Doppler observable en spectre, autocorrélation fonction du couple $(f, \tau)$

7. **Techniques de traitement:** Égalisation adaptative et poursuite Doppler essentielles pour performance optimale

Les paramètres clés—**Doppler spread** $B_D$, **delay spread** $\tau_d$, **temps de cohérence** $T_c$ et **bande de cohérence** $B_c$—dictent la complexité du système et le choix des stratégies de détection et d'estimation[3][4].

---

## Références

[1] Matz, G., Durisi, G., & Leus, G. (2011). Fundamentals of time-varying communication channels. In *Digital Signal Processing for 4G and 5G Communications* (pp. 1–50). Academic Press.

[2] Tse, D., & Viswanath, P. (2005). *Fundamentals of Wireless Communication*. Cambridge University Press. Chapter 2: The Wireless Channel.

[3] Rappaport, T. S. (2002). *Wireless Communications: Principles and Practice* (2nd ed.). Prentice Hall. Chapter 5: Mobile Radio Propagation.

[4] 3GPP TR 25.943. (2023). *Deployment aspects (Release 18)*. Technical Report. Specifications for channel modeling in cellular systems.
