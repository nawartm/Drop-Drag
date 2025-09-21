# 🖐️ Interface Interactive par Reconnaissance Gestuelle de la Main (Drop - Drag )

## 📌 Présentation du Projet

Ce projet permet de **contrôler une interface graphique en temps réel** en utilisant simplement **vos mains**, grâce à la webcam de votre ordinateur. Il détecte les gestes de votre main (notamment le pincement entre le pouce et l’index) pour interagir avec des formes à l’écran : déplacer des rectangles et des cercles, en ajouter de nouveaux, ou en supprimer — le tout **sans souris ni clavier**.

---

## 🎯 À qui s’adresse ce projet ?

- ✅ **Pour les non-techniciens** : Imaginez pouvoir dessiner, organiser ou jouer avec des objets à l’écran… juste en bougeant vos doigts devant la caméra ! C’est intuitif, amusant, et accessible à tous.
- 🛠️ **Pour les développeurs et passionnés de tech** : Ce projet exploite des bibliothèques avancées de vision par ordinateur (MediaPipe, OpenCV) pour détecter les points clés de la main, calculer des distances en temps réel, et gérer des interactions basées sur des seuils et des événements temporels.

---

## ⚙️ Fonctionnalités Clés (Explication Technique & Simple)

### 1. 🖼️ Détection des mains en temps réel
- **Technique** : Utilisation de **MediaPipe Hands** (modèle léger `model_complexity=0`) pour détecter 21 points de repère par main, avec une confiance minimale de 0.5.
- **Simple** : La caméra voit votre main et comprend exactement où se trouvent vos doigts — comme une carte GPS de votre main !

### 2. ✋ Reconnaissance du geste de pincement
- **Technique** : Calcul de la **distance euclidienne** entre l’extrémité du pouce (`THUMB_TIP`) et de l’index (`INDEX_FINGER_TIP`). Si cette distance est inférieure à un seuil (`threshold_distance`), le geste est activé.
- **Simple** : Quand vous “pincez” vos doigts comme pour prendre un objet, le système comprend que vous voulez interagir.

### 3. 🖊️ Interaction avec les formes (rectangles & cercles)
- **Technique** : Vérification de collision entre la position de l’index et les coordonnées des formes. Déplacement via assignation dynamique des coordonnées.
- **Simple** : Pointez un rectangle ou un cercle, pincez, et déplacez-le où vous voulez — comme un aimant qui suit votre doigt !

### 4. ➕ ➖ Boutons interactifs (Ajouter / Supprimer / Quitter)
- **Technique** : Zones de détection rectangulaires avec temporisation (`start_time_X`, `click_duration`) pour éviter les clics accidentels.
- **Simple** : Restez quelques instants avec votre doigt sur un bouton, et l’action s’exécute — comme un clic long sur un smartphone.

### 5. 🔄 Boucle de traitement en temps réel
- **Technique** : Lecture continue de la webcam (`cv2.VideoCapture`), conversion BGR↔RGB, traitement MediaPipe, rendu OpenCV, affichage avec `cv2.imshow`.
- **Simple** : Tout se passe en direct, image par image, 30 à 60 fois par seconde — fluide et réactif.

---

## 🧩 Technologies Utilisées

| Bibliothèque      | Rôle                                                                 |
|-------------------|----------------------------------------------------------------------|
| **OpenCV (cv2)**  | Capture vidéo, affichage, dessin des formes et traitement d’images.  |
| **MediaPipe**     | Détection précise des points de la main en temps réel.               |
| **NumPy**         | Calculs mathématiques (distance, coordonnées, transformations).      |
| **time**          | Gestion des temporisations pour les interactions “longues”.          |

---

## 🚀 Comment exécuter le projet ?

> ⚠️ Ce projet est fourni sous forme de **fichier Jupyter Notebook (.ipynb)**. Vous devez donc l’exécuter dans un environnement Jupyter (local, Google Colab, etc.).

### Étape 1 : Installer les dépendances

Ouvrez un terminal ou une cellule Jupyter et exécutez :

```bash
pip install opencv-python mediapipe numpy
