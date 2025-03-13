# git rebase
Le **git rebase interactif** est tres utile dans la mesure où il permet de reorganiser les commits avant de les partager avec ses collaborateurs. 
En effet au cours de la mise en forme du projet, de nombreux commits sont effectués. Il peut arriver que ceux-ci comprennent des erreurs 
(orthographiques par exemple) ou que des soucis chronologiques se posent quant à l'historique des commits. Pour une meilleure lisibité et afin
de parfaitement coller avec la logique du projet, le git rebase est une solution judicieuse. Il permet notamment d’intégrer les 
dernières modifications d’une branche principale avant d’y pousser des changements loors du merge final evitant ainsi le risque de conflit.


# git cherry-pick
Le **git cherry-pick** a l'avantage de pouvoir selectionner un commit spécifique d'une branche pour l'appliquer à une autre, sans provoquer la fusion
de toute la branche d'origine. Cette fonction est tres avantageuse dans le cas où un correctif a été effectué par erreur sur la mauvaise branche et
que l'on souhaite le ramener sur la bonne. Il s'avère egalement pratique lorsqu'un tel meme correctif doit s'appliquer identiquement plusieurs fois en 
divers endroits
Employer un cherry-pick peut neanmoins avoir des consequences au niveau du suivi de version si effectué dans les mauvaises circonstances. 
Même si le git cherry-pick applique exactement les mêmes modifications, il crée en réalite un tout nouveau commit; Git ne considère donc pas cet autre commit 
comme identique à l’original. Il n'identifiera alors pas ce commit comme déjà présent, ce qui peut entraîner des doublons voire des conflits. Notons aussi le risque
de rendre difficile le retracage de l'origine dans l’historique d'un commit qui a été cherry-pick de nombreuses fois. Son emploi est donc à éviter si l'on souhaite
garder un historique clair et dans le cas où il est prévu de prochainnement fusionner les branches


# Questions théoriques supplémentaires

## 1. Quels sont les avantages et les risques d'utiliser git rebase par rapport à git merge dans un contexte collaboratif ? Expliquez les situations où l'un serait préféré à l'autre et comment minimiser les risques liés à un rebase mal utilisé.

Le **git rebase** nous permet d'organiser l'historique des commits après coup, en les appliquant par dessus une branche cible, ce qui donne un historique plus propre et plus linéaire. Cela peut être avantageux lorsqu'on veut garder un historique sans commit de fusion pour ne pas trop alourdir l'historique, ce qui rend le rend plus facile à lire et à suivre. On voit que les commit semblent directement réalisés sur la branche principale.

En revanche, **git merge** conserve tous les commits et crée un commit de fusion, ce qui est évidemment utile pour préserver la chronologie exacte des événements, notamment dans un travail collaboratif où chaque développeur a travaillé sur des fonctionnalités non-connexes. 

Le principal risque du rebase en contexte collaboratif est qu'il réécrit l'historique, ce qui peut entraîner des conflits si plusieurs personnes ont travaillé sur les mêmes commits ou branches. Afin de réduire ce risque, il est recommandé d'éviter d'utiliser le rebase sur des branches partagées et de l'appliquer plutôt sur des branches locales avant de pousser les modifications. 

En résumé, le **git merge** est préférable pour maintenir un historique collaboratif sécurisé, tandis que le **git rebase** permet d’avoir un historique plus net lorsqu'on travaille seul ou sur des branches privées.


## 2. Quel est l'intérêt d'utiliser les tags ? Expliquez en lien avec les requirements et la Semantic versioning method.


On utilise les **tags** sont utilisés pour marquer des étapes importantes dans l'historique d'un projet. En général, ils sont là pour signaler une version stable ou une release, c'est a dire une version prête à être utilisée. Ils nous permettent de pouvoir retrouver rapidement des versions spécifiques sans devoir éplucher tous les anciens commits un à un. L'intérêt des tags réside donc dans leur capacité à fournir un suivi clair de l'évolution du projet, tout en permettant de revenir aisément à des versions antérieures en cas de besoin.

Concernant le lien avec la Semantic versionin method, les tags respectent la convention de versionnement sous le format **MAJOR.MINOR.PATCH**. Cela permet de bien gérer les versions en indiquant explicitement si une version apporte respectivement des modifications majeures, des ajouts ou des corrections de bugs. Par exemple, une mise à jour de **1.0.0** à **2.0.0** indique un changement majeur, donc possiblement incompatible avec les versions précédentes, tandis qu'une mise à jour de **1.0.0** à **1.1.0** indique l'ajout de nouvelles fonctionnalités sans rupture de compatibilité. Enfin une mise à jour de **1.0.0** à **1.0.1** signifiera la correction de bug ponctuels ne mettant également absolument pas en péril toute compatibilité. 


## 3. Décrivez l'impact d'une mauvaise configuration du fichier .gitignore sur l'historique du projet. Quelles conséquences peut-on observer et comment rectifier la situation une fois le problème identifié ?

Une configuration defectueuse du fichier **.gitignore** peut exercer une influence significative sur le fil d'historique du projet. En effet, elle peut conduire à l'ajout de fichiers ou de dossiers indésirables dans le suivi, comme des fichiers temporaires, des logs ou des fichiers de configuration liés à l'environnement local. Cela alourdit l'historique des commits, complique sa lecture et peut même causer des conflits lors des merges. Par exemple, si un fichier volumineux comme un fichier de log est suivi par mégarde, il rendra assurément le projet plus lourd et provoquera des erreurs lors des push vers le dépôt distant.

Pour pallier à ce problème, il est tout d'abord naturellement nécessaire de commencer par ajouter les fichiers ou dossiers concernés dans le fichier **.gitignore**, afin de s'assurer qu'ils ne soient suivis à l'avenir. Ensuite, on peut utiliser la commande **git rm --cached <fichier>** pour supprimer ces fichiers de l'index Git tout en les conservant localement. Enfin, il faut effectuer un commit pour enregistrer cette modification dans l'historique et pousser les changements sur le dépôt distant afin de régler totalement le problème.



