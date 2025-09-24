# Projet de Classification MNIST

## Description
Ce projet utilise un réseau de neurones artificiels implémenté avec TensorFlow/Keras pour classer les chiffres manuscrits du jeu de données MNIST. L'objectif est de construire un modèle capable de reconnaître les chiffres de 0 à 9 à partir d'images en niveaux de gris de 28x28 pixels.

Le modèle est un réseau fully-connected avec une couche cachée de 512 neurones, une régularisation par Dropout, et une couche de sortie avec activation softmax pour la classification multiclasse. Le modèle est entraîné sur 60 000 images et testé sur 10 000 images, atteignant une précision élevée sur les données de test.

## Dépendances
- Python 3.x
- TensorFlow 2.x
- NumPy
- Google Colab (pour l'exécution dans un environnement cloud)

## Installation
1. Clonez ce dépôt :
   ```bash
   git clone https://github.com/frankettheofranckettheo/Advanced-ML-Project.git
   cd Advanced-ML-Project
   ```
2. Si vous utilisez Google Colab, ouvrez le notebook `mnist_classification.ipynb` directement depuis GitHub via l'interface Colab.

## Utilisation
1. **Dans Google Colab** :
   - Ouvrez le notebook `mnist_classification.ipynb`.
   - Exécutez toutes les cellules pour charger les données MNIST, entraîner le modèle, et sauvegarder le modèle entraîné dans Google Drive (`/content/drive/MyDrive/Models/mnist_model.keras`).
   - Le modèle est sauvegardé au format `.keras` pour une réutilisation facile.

2. **Localement** :
   - Assurez-vous que les dépendances sont installées :
     ```bash
     pip install tensorflow numpy
     ```
   - Exécutez le script Python ou le notebook localement.

## Structure du projet
- `mnist_classification.ipynb` : Notebook contenant le code principal pour charger, entraîner et évaluer le modèle.
- `mnist_model.keras` : Modèle entraîné sauvegardé (stocké dans Google Drive ou dans le dépôt si poussé).
- `README.md` : Ce fichier, décrivant le projet.

## Résultats
- Le modèle atteint une précision d'environ 98 % sur les données de test après 5 époques d'entraînement.
- La perte utilisée est `sparse_categorical_crossentropy`, adaptée à la classification multiclasse.
- L'optimiseur `Adam` est utilisé pour une convergence rapide et stable.

## Prochaines étapes
- Expérimenter avec d'autres architectures (par exemple, CNN pour améliorer la précision).
- Ajuster les hyperparamètres (nombre d'époques, taille des lots, taux de dropout).
- Ajouter des visualisations des performances (courbes de perte/précision).

## Auteur
- [Votre Nom] (https://github.com/frankettheofranckettheo)
