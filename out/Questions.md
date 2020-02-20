* __Quels sont les chemins d'attaque possibles sur la signature d'un système embarqué?__

   D'abord une petite explication du fonctionnement de la signature. Les signatures sont faite à partir d'un chiffrement asymétrique on à donc besoin d'une clé publique et privée. Pour signer un fichier par exemple la perssone qui a la clé privée va hasher ses donné puis il va chiffrer le hash obtenu,asymetriquement avec sa clé privée. Ensuite toute les personne connaisxsant sa clé publiqsue pourront vérifier que le fichier est bien a la personne qu'il voulait. la signature permet donc d'authentifier des données.
   Les chemins d'attaques sont donc (il y en a sans doute d'autre) :
   
   __1.__ réussir a trouver la clé privée pour pouvoir signer des fichiers malveillants par exemple.
   
   __2.__ si le partager de la clé publique n'est pas protégé, l'attaquant peut envoyer sa clé publique a la place de la "vraie".
   
* __A quoi sert la chaine de confiance? Pourquoi est-elle nécessaire?__


* __Décrire la méthode pour aborder la sécurité sur un produit embarqué. Pourquoi établir un modèle d'attaquant est-il important?__
* __Trouver un moyen rapide de faire du debug embarqué (par exemple sur cible ARM)? Expliquer les avantages__
* __Lister les catégories de bug possibles et comment les exploiter et les défendre__
* __Quelles idées pour améliorer la sécurité en embarqué? (IA, Anti-debug, Obfuscation, Crypto ...) Choisissez une idée, chercher si elle existe et développer en quelques phrases quel avantage elle apporte et ses limites___
