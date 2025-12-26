# TP4 Deep Learning – Segmentation Sémantique

**Auteur :** NOUNDJEU NOUBISSIE FRANCK (5GI 21P318 ENSPY)  
**Date :** Décembre 2025

---

## Introduction

La segmentation sémantique est une tâche clé en vision par ordinateur, notamment dans l’imagerie médicale, où la localisation précise des structures anatomiques est essentielle pour le diagnostic et le suivi clinique. Contrairement à la classification classique, la segmentation attribue une étiquette à chaque pixel, nécessitant des architectures capables de capturer à la fois le contexte global et les détails fins.

Ce TP a pour objectif :

- D’étudier et mettre en œuvre l’architecture **U-Net** pour la segmentation d’images médicales.
- D’analyser des métriques spécifiques telles que le **coefficient de Dice** et l’**Intersection over Union (IoU)**.
- D’introduire les convolutions tridimensionnelles (**Conv3D**) pour le traitement des données volumétriques.
- De mettre en pratique de bonnes pratiques d’ingénierie avec **MLflow** pour le suivi des expériences.

---

## Partie 1 : Segmentation et Bonnes Pratiques MLOps

### Segmentation sémantique et architecture U-Net

- **Type et dimension de la sortie :**  
  Pour une segmentation binaire médicale, le modèle produit un tenseur de dimension `(N, H, W, C)` avec `C = 1` et activation sigmoïde.

- **Rôle du décodeur et des connexions de saut :**  
  Le décodeur restaure la résolution spatiale tout en produisant une prédiction pixel-par-pixel.  
  Les **skip connections** permettent de récupérer les informations spatiales perdues dans l’encodeur pour améliorer la précision.

- **Limites de la cross-entropy et Dice Loss :**  
  Dans les cas où la classe d’intérêt est très minoritaire, la cross-entropy classique est insuffisante. La **Dice Loss** est plus adaptée car elle favorise le recouvrement entre la prédiction et la vérité terrain.

### Bonnes pratiques d’ingénierie : suivi des expériences

- **Convention de nommage des expériences :**  
  Exemple : `UNet2D_Adam_DiceLoss`.

- **Journalisation des métriques personnalisées :**  
  Les métriques comme Dice ou IoU doivent être implémentées et loggées via `MLflow.log_metric()` pour comparer les expériences.

---

## Partie 2 : Segmentation sur données médicales

### Coefficient de Dice

\[
\text{Dice} = \frac{2 |A \cap B|}{|A| + |B|}
\]

Mesure le recouvrement entre le masque prédit et le masque réel. Particulièrement adapté aux objets de petite taille.

### Intersection over Union (IoU)

\[
\text{IoU} = \frac{|A \cap B|}{|A \cup B|}
\]

Métrique stricte qui pénalise davantage les erreurs, surtout pour de petites régions d’intérêt.

### Comparaison Dice vs IoU

- Dice : plus stable pour de petites cibles, tolérant aux petites erreurs.  
- IoU : plus sévère et stricte pour la qualité de segmentation.  

---

## Partie 3 : Convolutions 3D et données volumétriques

### Conv3D pour données volumétriques

- **Différence avec Conv2D :**  
  Conv2D agit sur `(H, W)`. Conv3D agit sur `(D, H, W)`, indispensable pour IRM ou scanners CT.

- **Contraintes mémoire et compromis :**  
  Les Conv3D sont coûteuses. On peut réduire la résolution, utiliser moins de filtres ou traiter des sous-volumes (patch-based learning).

---

## Conclusion

Ce TP illustre :

- L’importance des architectures spécialisées comme **U-Net** pour la segmentation médicale.
- L’utilisation de métriques adaptées (**Dice**, **IoU**).  
- Les défis des données volumétriques et l’importance des bonnes pratiques MLOps avec MLflow.
