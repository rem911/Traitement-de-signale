# Traitement-de-signale : etude Capteur Sonore
**Résumé du Rapport de Mission 2**

---

**Introduction**  
Le projet vise à concevoir un chariot mobile équipé d'un capteur sonore capable de détecter et d'analyser les sons de son environnement. Ce système a des applications variées, comme la surveillance industrielle ou agricole. Le chariot intègre un microphone électret, un circuit de filtrage et d'amplification, et un microcontrôleur pour l'acquisition et le traitement des données.

---

**Étude et conception du capteur sonore**  
1. **Microphone électret** :  
   - Fonctionne sur le principe d'un condensateur avec un matériau électret pour convertir les vibrations sonores en signal électrique.  
   - Un transistor FET amplifie le signal pour le rendre exploitable.  

2. **Câblage et tests** :  
   - Choix des composants : \( R1 = 10 \, \text{k}\Omega \), \( C1 = C2 = 1 \, \mu\text{F} \) pour un bon compromis entre performance et stabilité.  
   - Tests avec un oscilloscope :  
     - **Couplage AC** : Signal sinusoïdal propre (500 Hz).  
     - **Couplage DC** : Présence d'un offset à éliminer par un filtre passe-haut.  

---

**Amplification et filtrage**  
1. **Amplificateur de tension** :  
   - Gain de 100 pour adapter le signal (de 35,6 mV à 3,3 V) à la plage du microcontrôleur.  
   - Configuration non-inverseuse avec \( A1 = 1 \, \mu\text{F} \), \( A2 = 1 \, \text{k}\Omega \), \( A3 = 100 \, \text{k}\Omega \).  

2. **Filtre passe-haut** :  
   - Élimine l'offset DC et les bruits basse fréquence (e.g., 50 Hz).  
   - Fréquence de coupure choisie entre 20 Hz et 100 Hz.  

3. **Filtre anti-repliement (Sallen-Key)** :  
   - Passe-bas d'ordre 2 pour éviter l'aliasing.  
   - Composants : \( R1 = R2 = 15 \, \text{k}\Omega \), \( C1 = 8 \, \text{nF} \), \( C2 = 1 \, \text{nF} \).  

---

**Conversion et acquisition numérique**  
1. **Carte TIVA** :  
   - Conversion analogique-numérique avec une fréquence d'échantillonnage de 4 kHz (respect de Nyquist-Shannon).  
   - Formule : \( \text{Valeur numérique} = \frac{3,3 \, \text{V}}{\text{Tension d'entrée}} \times 1023 \).  

2. **Programmation** :  
   - Génération de fichiers CSV contenant 1024 à 4096 valeurs pour analyse.  
   - Visualisation des signaux avec et sans source sonore.  

---

**Conclusion**  
Cette mission a permis de maîtriser les étapes clés du traitement du signal : capture, filtrage, amplification, et conversion numérique. Les défis rencontrés ont été résolus par des ajustements techniques, comme l'optimisation des composants. Ces acquis sont essentiels pour la suite du projet, qui inclura le contrôle du chariot via des signaux sonores.  

**Mots-clés** : Microphone électret, amplification, filtrage, échantillonnage, carte TIVA, traitement du signal.
