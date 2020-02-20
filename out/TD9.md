# La signature avec openSSL

Une signature permet de protéger des modifications exterieures On peut s'en servir pour vérifier qu'un programme à executer est bien un programme créée par un développeur "reconnu".
Seul ceux qui possède la clé pour signer peuvent modifier le code. Cela permet de limiter les modifications des fichiers importants.

## Protéger l'update d'un firmware

Pour protéger l'update d'un firmware on peut imaginer un petit programme de vérification des signatures qui empêcherais les programmes d'update non signé ou avec la mauvaise signature de se lancer.
