Date: 24/07/2024

La réalistation de mon projet a commencé par l'exécution des deux codes  déjà existant crée par Youssef. Le premier code consiste à imputer les valeurs manquantes dans les datasets avec 5% de valeur manquantes et à sauvegarder les résultats de l'évaluation en fichers csv. Pour cela, il a utilisé deux modèles: le SVR et le RNN.

En ce qui concerne le bloc de code du SVR, j'ai apporté quelques modifications mineures comme le changement du chemin de chargement des datasets et l'utilisation de df.at[i,'SensorGLU'] à la place de df['SensorGLU'][i].

Pour le bloc de code du RNN, j'ai rencontré plusieurs difficultés lors de son exécution. Ces problèmes sont notamment liés à la durée des sessions et aussi à la faible capacité de la RAM sur Kaggle et Google colab. Afin de résoudre le problème, j'ai réduit le nombre de datasetsà itérer dans la même boucle car la boucle itérait de 1 à 102. Dans la première partie, j'ai itéré de 1 à 39, dans la seconde partie j'ai itéré de 40 à 79 et dans la troisième partie de 80 à 102. J'ai également réduit le nombre de d'époques à 50, fixer le batch_size à 32, remplacer df['SensorGLU][i] par df.at[i,'SensorGLU'] et enfin utiliser tf.keras.backend.clear_session() pour libérer la mémoire tensorflow de la session après chaque itération. 

Date: 25/07/2024

Lors des modifications précédentes effectuées sur le bloc du RNN, j'ai commis une erreur lors du calcul des metrics d'évaluation dans la partie 2 et 3. En effet, le calcul de la métrique PRED nécessite la prise en compte de toutes les valeurs précédentes. Donc j'ai modifié le code de la partie 2 (nommée impution_code_bgl_part2.ipynb) et partie 3 (impution_code_bgl_final.ipynb) afin de charger les metriques calculées dans les parties précédentes. Par exemple dans la partie 2 je charge les metriques calculées dans la partie 1 (nommée impution_code_bgl_part1.ipynb) et je regroupe les réultats ensemble. Dans la partie 3 je charge les metriques calculée dans la partie 2.

Date: 27/07/2024

En me basant sur le code d'imputation des datasets avec 5% de missing values, j'ai créé les code d'imputation des datasets avec 10% et 20 % de valeurs manquantes. Ensuite j'ai réalisé l'imputation des valeurs manquantes sur les datasets à 10% de missing values. Ce travail a nécessité une imputation en 4 étapes lié à la faible capacité de la ram. J'ai par la suite calculé les metrics d'évaluation des modèles entrainés.