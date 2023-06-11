# Semantic-text-similarity

## Recherche sémantique de FAQ

Un système de recherche de FAQ compare des phrases courtes (les requêtes) à des phrases tout aussi courtes : la partie question d'une paire (question-réponse) de la FAQ. 
À cette fin, notre modèle de recherche basé sur Transformer (Camembert) représente nos questions de FAQ sous forme de vecteurs dans un espace d’embeddings à haute dimension. Notre modèle trouve ensuite les vecteurs les plus proches de lui, en utilisant la distance cosinus comme mesure de similarité.

Le modèle utilisé pour la représentation des phrases est capable d’aller au-delà du littéral et de capter le sens d'une requête donnée (c'est-à-dire la sémantique)
Bien que le système compare nos requêtes aux questions (ou plutôt à leurs embeddings) de la base de données, nous voulons qu'il renvoie la réponse associée à cette question.

## Tableau comparatif des résultats:

![image](https://github.com/EL-MEHDI-git/Semantic-text-similarity/assets/66147690/7c4a9e2f-2753-4f34-96a0-5553d693738d)

Dans l’approche fondée sur la similarité textuelle, nous avons commencé par appliquer le camembert, la version française des modèles de langages naturel basé sur Transformers, pré-entrainé sur des corpus français. En effet, nous avons élaboré le modèle CamemBERT dans deux architectures : bi-encoder (Siamese) et cross-encoder. Ensuite, nous avons effectué des hybridations dont nous avons alimenté la sortie du camembert avec des réseaux neuronaux récurrents voire le LSTM et le Bi-LSTM au niveau des deux architectures. Comme déjà détaillé dans le chapitre de la conception, nous avons effectué plusieurs modifications sur les modèles tels que l’ajout de mean-pooling, l’utilisation du [cls]Token, etc. Le tableau ci-dessus décrit les résultats de tous les modèles conçus. Ceux appuyés sur l’architecture cross-encoder ont souvent achevé les meilleures performances, notamment celui composé de camembert couplé avec le Bi-LSTM et une opération de mean-pooling avec une corrélation Pearson de 84.67%. Pour l’architecture Siamese le meilleur résultat était celui du modèle camembert suivi de mean-pooling avec un score de 82.29 %. Les résultats obtenus confirment parfaitement les travaux de l’état de l’art ayant conclu le succès des modèles cross-encoder mais cette fois ci au niveau du langage français
