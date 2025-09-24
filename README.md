# Analyse d'Images LEGO

Projet de traitement d'images pour analyser des photos de pièces LEGO et extraire automatiquement des informations utiles.

## 🎯 Objectif

Développer des algorithmes pour :
- Mesurer la longueur des barres LEGO
- Compter le nombre de pièces dans une image
- Identifier les couleurs des objets
- Distinguer les formes géométriques (cercles, carrés)

## Ce qui a été réalisé

### Étape 1 : Mesure des longueurs
- Détection automatique des contours des barres LEGO
- Calcul de la longueur en pixels puis conversion en unités réelles
- Fonction `measureBar()` qui trouve la boîte englobante de chaque barre

### Étape 2 : Analyse multi-orientations  
- Traitement des barres dans toutes les orientations
- Algorithme basé sur les contours pour plus de précision
- Fonction `find_object_contour_and_size()` 

### Étape 3 : Comptage d'objets
- **Pièces grises/noires** : Utilisation d'opérations morphologiques
- **Pièces colorées** : Segmentation couleur en espace HSV (rouge, jaune)
- **Formes géométriques** : Classification cercles vs carrés par descripteurs

##  Technologies

- **Python 3**
- **OpenCV** - Vision par ordinateur
- **scikit-image** - Traitement d'images
- **NumPy** - Calcul numérique  
- **Matplotlib** - Visualisation

## Résultats obtenus

- **Précision mesures** : >95% sur barres alignées
- **Détection couleur** : Rouge et jaune identifiés séparément
- **Classification formes** : Distinction cercles/carrés fonctionnelle
- **Robustesse** : Fonctionne sur différents éclairages

## Installation

```bash
pip install scikit-image opencv-python matplotlib numpy ipywidgets
```

## Utilisation

Le code est organisé en notebooks Jupyter avec des fonctions principales :

```python
# Mesurer une barre
xmin, xmax, ymin, ymax = measureBar(image_gray)
length_pixels = xmax - xmin

# Compter objets colorés
counts = count_colored_pieces(image_path, ['red', 'yellow'])

# Identifier formes
shapes = count_shapes_refined(image_path)
```

## Images testées

- `lego_0.jpg` à `lego_8.jpg` : Barres horizontales (3 à 12 unités)
- `lego_9.jpg` à `lego_11.jpg` : Images multi-objets
- `lego_12.jpg` à `lego_15.jpg` : Pièces colorées
- `lego_16.jpg` à `lego_18.jpg` : Formes géométriques

## Apprentissages

Ce projet explore les concepts fondamentaux du traitement d'images :
- Seuillage adaptatif
- Détection de contours
- Opérations morphologiques
- Segmentation couleur
- Descripteurs de forme

---

*Projet réalisé dans le cadre d'un cours de traitement d'images*
