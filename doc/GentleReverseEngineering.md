## Différences de résultat

# file 

... la différence est du au fait que dans l'exemple le file (commande qui permet de voir le type d'un fichier) est executé sur MacOS et nous l'executons sur linux on obtient donc :

' program: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=deba4fa68dbc989053118b9c30b0abcf5f78df23, not stripped '

...On peut ajouter l'option -no-pie lors de la compilation pour avoir un executable et pa un shared object, on obtient 

' program: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=5249ded8e231e1b61b1292fc0d720b4a93a28bec, not stripped '

# hexdump

... le fichier executable n'étant pas le même que dans l'exemple car compilé par gcc sur linux, on remarque quand même au debut de la colonne de droite 'ELF' qui nours montre bien que l'executable est en ELF.


# strings 

... strings permet d'afficher les caractères affichable contenue dans le fichier donné, on lui donne l'executable et on obtient:

' poop
Please input a word: 
That's correct!
That's not correct! '

