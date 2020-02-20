# Le double free

Lorsque la mémoire allouée à une variable est supprimée deux fois, cela créé un état dans lequel un attaquant peut potentiellement modifier les registres Assembleur, et donc modifier l'exécution du code.

https://sensepost.com/blog/2017/linux-heap-exploitation-intro-series-riding-free-on-the-heap-double-free-attacks/
