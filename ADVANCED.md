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


## 2. Quel est l'intérêt d'utiliser les tags ? Expliquez en lien avec les requirements et la Semantic versioning method.


## 3. Décrivez l'impact d'une mauvaise configuration du fichier .gitignore sur l'historique du projet. Quelles conséquences peut-on observer et comment rectifier la situation une fois le problème identifié ?





