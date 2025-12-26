# TP3 Deep Learning

**Auteur :** Franck NOUNDJEU  
**Date :** Novembre 2025

---

## Introduction

Ce TP3 explore les fondamentaux des **CNN (Convolutional Neural Networks)** et leurs applications avancées, incluant la segmentation d’images, la détection d’objets et le transfert de style neuronal. L’objectif est de comprendre la théorie, puis de mettre en pratique ces concepts sur des datasets et des architectures populaires.

---

## Partie 1 : Fondamentaux des CNN

### Concepts théoriques

- **Convolution :**  
  - Filtre (Kernel) : petite matrice (ex : 3x3) qui détecte des caractéristiques (bords, textures, motifs).  
  - Stride : déplacement du filtre à chaque étape.  
  - Objectif : extraire des **feature maps** représentatives des caractéristiques visuelles.

- **Pooling :**  
  - Max Pooling : conserve la valeur maximale d’une zone.  
  - Average Pooling : moyenne des valeurs d’une zone.  
  - Rôle : réduire la dimensionnalité et le coût de calcul tout en conservant l’invariance aux translations.

- **Flatten :**  
  Convertit les matrices 3D des feature maps en vecteurs 1D pour les couches denses.

- **Réseaux résiduels (ResNets) :**  
  Les connexions résiduelles (skip connections) permettent de résoudre le problème de gradient disparu dans les réseaux profonds en facilitant l’apprentissage de fonctions résiduelles.

### Préparation des données CIFAR-10

- Chargement et prétraitement des images pour l’entraînement des CNN.

---

## Partie 2 : Implémentation basique des CNN

### Exercice 1 : Architecture classique des CNN

- Création et entraînement d’un CNN simple pour la classification d’images.

### Exercice 2 : Introduction aux blocs résiduels (ResNets)

- Implémentation de la fonction `residual_block` pour permettre l’apprentissage dans des réseaux profonds.  
- **Avantage du skip connection :** apprentissage de la fonction résiduelle \(F(x) = H(x) - x\) pour éviter la dégradation des performances.

---

## Partie 3 : Applications avancées

### Exercice 3 : Reconnaissance et détection

#### Image Segmentation (U-Net)

- **Sortie :** masque de pixels de même taille que l’image d’entrée.  
- **Upsampling :** restaure la résolution spatiale pour classifier chaque pixel précisément.

#### Object Detection (Bounding Boxes)

- **Classification :** identifie la classe de l’objet.  
- **Régression :** prédit la position et la taille de la bounding box \((x, y, w, h)\).

### Exercice 4 : Neural Style Transfer

- **Content Loss :** conserve la structure et les objets de l’image de contenu.  
- **Style Loss :** conserve les textures et motifs de l’image de style via les matrices de Gram.

---

## Conclusion

Ce TP3 a permis de :

- Comprendre les principes fondamentaux des CNN et des ResNets.  
- Mettre en pratique des architectures pour la classification, la segmentation et la détection.  
- Explorer des applications avancées comme le neural style transfer.
