# Structure des communautés de jeux vidéo basée sur les joueurs en commun
Les joueurs professionels ont-ils tendance à rester sur un seul type de jeux vidéos ou existe-t-il des mouvements au sein de la communauté?

De nombreux jeux vidéos compétitifs partagent des mécaniques de fonctionnements et des éléements gameplay similaires. Ainsi, on peut se demander si les joueurs professionels profitent de ces points communs pour jouer à différents jeux ou si, au contraire, ils préfèrent se spécialiser dans un seul jeu. 
Le but de cette analyse de réseau est de voir les liens qui peuvent exister entre les jeux en fonction des joueurs professionels qu'ils ont en commun. Ici, on s'intéresse donc aux dynamiques de spécialisation et de mobilité au sein de l'esport.

## Top 15 des jeux par nombre de joueurs uniques

Pour commencer, j'ai donc d'abord construit une liste des jeux les plus joués parmis les joueurs professionels, en terme de joueurs uniques. On remarque alors que la majorité des jeux ont moins de cent joueurs professionels. Seul quatre des quinze jeux observés dépassent ce chiffre. On peut donc rapidement voir que la plupart des jeux n'ont qu'une petite communauté de joueurs professionels.

![alt text](<https://github.com/enaxorb/esportplayers/blob/main/Documentation/Réponses%20aux%20questionnements/Images/top15parnbjoueur.png>)

## Structure des communautés basées sur les jeux en commun

Malgré le nombre majoritaire de petites communautés, il est intéressant de voir si elles sont connectées entre elles ou si, au contraire, restent plutôt isolées.

![alt text](<https://github.com/enaxorb/esportplayers/blob/main/Documentation/Réponses%20aux%20questionnements/Images/structurejeuxjoueurs.png>)

On peut observer que la densité du résau est faible et les arêtes reliant les jeux ont généralement un point faible, ce qui signifie que peu de joueurs participent à plusieurs jeux.

Il semble que le noeud Q8442146 joue un rôle important. En effet il a plusieurs connexions vers les deux communautés tout comme lee noeud Q18142874. Les deux noeuds servent de ponts entre les deux communautés et les relient entre elles. On observe également que ce sont deux jeux ayant plus de cent joueurs. Toutefois, Q223341 est le second jeu ayant le plus de joueurs mais reste malgré tout plutôt isolé. Ainsi, ce n'est pas nécessairement le nombre de joueurs unique qui va augmenter les connexions entre les communautés de jeux vidéos.

Ainsi, cela laisse penser que les joueurs tendent à se spécialiser dans un type de jeu, puisque les jeux compétitifs ne partage que peu de joueurs professionnels. L

Il est toutefois important de noter que l'échantillon utilisé pour faire cette analyse est assez petit. Ainsi, un échantillon plus large permettrait sans doute une meilleure appréciation de la mobilité des joueurs esport.