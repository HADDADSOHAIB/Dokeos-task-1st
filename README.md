# Project Repository:
https://github.com/HADDADSOHAIB/let-learn
# Live link:
https://let-learn.herokuapp.com/

# FR
## Introduction:
Dans le cadre du projet final durant ma formation dans le bootcomp [Microverse](https://www.microverse.org/), j'ai realisé un clone simplifie de Twitter avec un sytem de communication text en temps reel.
## Architurcture:
La plateform doit permettre aux utilisateurs de creer des idees (thougths), sur les quelles on peut commenter(comments) et aimer(likes), les utilisateurs peuvent aussi suivre(follow) autre utilisateur et envoyer des messages(messages, rooms).

Pour arriver à ces objectif, l'architucture de la base de donnée suivant est adopté:  
https://drive.google.com/file/d/1bD-r-JkC48blAIxTjaPwHIK3TLJEudKq/view?usp=sharing
![diagrame data base](./let-learn-chart.png)

### Follow feature:
![diagrame data base](./1.png)  
Pour permettre aux utilisateur de suivre les autres utilisateurs, un tableau intermédiare est créé pour gérer ça avec 2 element: follower_id et followed_id, l'objectif d'avoir ces 2 élements est de donner un sens de direction, utlisateur 1 follow utilisateur 2 ne veut pas dire que utilisateur 2 follow utilisateur 1 aussi.

### Thougths, comment and likes:
![diagrame data base](./2.png)  
Chaque utilisateur peut publier des idees (thougths), sur ces idees, on peut ajouter les commentaires(comments) et les aimes(likes), alors les tables comments et likes sont lié aux tables thougths et users.

### Messaging feature:
![diagrame data base](./3.png)  
Un utilisateurs peut creer des messages qui appartients aux chaines (rooms) specifiques. une chaine peut avoir plusieurs utilisatuers (communication 1 à 1, communication de groupe) et un utilisateur peut être dans plusieurs chaines.
Pour chaque utilisauer, on a besoin d'afficher le nombre des messages n'est pas encore lit sur chaque chaines, alors on a mit cette information sur la table "join_user_room" vue que un record unique existe pour chaque combinaison d'utilsateur et chaine.

### choix de base de données:
La base de données utilisée dans cette application est Postgres. Le scope de ce projet est limité (projet de fin d'etude), la plateforme ne sera pas mettre à l'échelle (scaling), alors le choix d'un base de donnée SQL est faites vue que ça nous offre une interface simple pour query les données, et le choix de Postgres est faite vue que la solution est open source.

### Api
La communication entre le front et le back est faite avec un api REST. La structure de donnés est simple pour cet application (seulement 8 tables), alors un choix comme graphql ne sera pas justifie.
### Real time messaging:
Pour assure la communication en temps reel, la technologie de websockets est utilisé, le framework de Ruby On Rails fournit une solution integere (ActionCable) pour utiliser cette technologie. 