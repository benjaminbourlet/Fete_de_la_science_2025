# 🌆 POGL — Sculpture Dynamique : Mécanique et Lumière

## 🧠 Concept

Ce projet s’inscrit dans une démarche **POGL (Phénomène d’Occupation et de Gestion des Lieux)**, cherchant à **matérialiser l’influence de la population sur un espace urbain**.

L’installation associe **mouvement mécanique** et **ambiance lumineuse** pour représenter les différents **niveaux d’activité d’un lieu** :
- plus la “population” ou l’activité est élevée,  
- plus le **socle s’élève** et la **couleur lumineuse s’intensifie**.

> 🎯 L’objectif est de rendre visible, sensible et poétique la “respiration” d’un lieu urbain à travers un objet physique.

---

## ⚙️ Fonctionnement global

L’installation combine **un moteur pas à pas (ou servo)** et **un bandeau LED NeoPixel** contrôlés par un **ESP32**.

### 🔩 Étapes de fonctionnement

1. **État 1 — Calme / Faible affluence**  
   - Le **socle est en position basse**.  
   - Les **LEDs émettent une lumière bleu-gris claire** (calme, froide).  

2. **État 2 — Activité moyenne**  
   - Le **socle monte d’un palier**.  
   - La **couleur devient plus vive (bleu profond / turquoise)**.  

3. **État 3 — Forte affluence**  
   - Le **socle atteint sa position haute**.  
   - Les **LEDs virent au bleu-blanc lumineux**, la “ville” est en mouvement.  

Le passage d’un état à l’autre peut être déclenché :
- soit par **une API simulant l’affluence** (valeur numérique 0 → 1),  
- soit par un **bouton ou capteur** pour les tests physiques.

---

## 🔧 Matériel utilisé

| Composant | Rôle | Détails |
|------------|------|----------|
| 🧠 **ESP32** | Microcontrôleur principal | Gère moteur + LEDs + API |
| ⚙️ **Moteur pas à pas / Servo SG90** | Action mécanique du socle | 3 positions (basse, moyenne, haute) |
| 💡 **Bandeau LED NeoPixel** | Lumière d’ambiance | 12 LEDs RGB (WS2812B) |
| 🔋 **Alimentation 5V** | Source commune | Alimente moteur et LEDs |
| 🔌 **Résistance 330Ω + condo 1000µF** | Sécurité LED | (recommandé pour NeoPixel) |

---

## 🧰 Librairies Arduino

- `Adafruit_NeoPixel.h` → gestion des LEDs WS2812B  
- `Servo.h` ou `Stepper.h` → contrôle du moteur (selon le modèle choisi)

---

## 🔬 Structure logicielle

```text
main.ino
│
├── setup()        # Initialisation LEDs + moteur
├── loop()         # Boucle principale
│   ├── lireEtat() # récupère le niveau d'activité (API ou variable)
│   ├── majLEDs()  # adapte la couleur selon l’état
│   └── majMoteur()# déplace le socle selon l’état
│
└── fonctions utilitaires :
    ├── goToLevel(level)  # 0, 1, 2 → positions moteur
    └── setColor(level)   # renvoie une couleur RGB selon l’état
```
---

## 📚 Bibliographie
- https://github.com/benjaminbourlet/Fete_de_la_science_2025.git
- https://boxes.hackerspace-bamberg.de/
- https://docs.arduino.cc/
- https://www.pinterest.com/
