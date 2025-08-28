# Lien entre pays et jeu

Une autre question qui peut se poser est de nature géographique. En effet, si certains pays semblent produire plus de joueurs esport que d'autres, je suis venue à me demander s'il existait également un lien entre l'origine des joueurs et les jeux auxquels ils se consacrent. Certains jeux seraient-ils plus populaires dans certains pays que d'autres? Existe-t-il une relation entre les pays d'origine des joueurs professionels et les jeux auxquels ils jouent?

## Les pays avec le plus grand nombres de joueurs

Pour commencer, j'ai fait une liste des pays regroupant le plus de joueurs uniques. 

![alt text](<https://github.com/enaxorb/esportplayers/blob/main/Documentation/Réponses%20aux%20questionnements/Images/Paysnbjoueur.png>)

Ce qu'on observe et que la majorité des joueurs proviennent d'un seul et même pays, le Q884 (La Corée du Sud), qui compte plus de six cent joueurs. Le deuxième pays a nettement moins de joueurs, avec moins de deux cent joueurs. Cette tendance indique qu'il peut y avoir un biais pour la Corée du Sud. Ainsi, les tendances observées pourrait surtout refléter les habitudes de jeux des joueurs coréens et non un schoma global.

## Test du chi carré

Pour répondre au questionnement initial, j'ai fait un test du chi carré, appliqué à un tableau de contingence croisant les pays et les jeux. Le résultat montre un p-value < 0,05, ce qui indique une dépendance significative. Cela suggère que certains jeux sont plus représentés dans certains pays que dans d'autres.

## Répartition des jeux les plus joués, par pays

Afin d'illustrer la répartition des jeux vidéos par pays, j'ai choisi de faire une heatmap.

![alt text](<https://github.com/enaxorb/esportplayers/blob/main/Documentation/Réponses%20aux%20questionnements/Images/Jeuxparpays.png>)

On peut à nouveau observer une dominance Coréenne parmis les joueurs, dans quatre des dix jeux.

Toutes mes tentatives de faire une visualisation d'une analyse factorielle des correspondances ont échouées. En effet, à cause de cette dominance de la Corée du Sud dans les pays d'origine des joueurs, les jeux et les pays se superposaient et ne permettait aucuns résultats clairs et satisfaisant.

L'échantillon utilisé ici n'est donc pas optimal pour une analyse bivariée des pays et des jeux. En effet, il y a une distribution déséquilibrée des joueurs par pays, ce qui introduit un biais. Les résultats sont par conséquent, surtout pertinent pour la Corée mais moins pour les autres pays.

