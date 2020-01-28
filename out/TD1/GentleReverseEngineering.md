# Emily tuto

## file 

 * la différence est du au fait que dans l'exemple le file (commande qui permet de voir le type d'un fichier) est executé sur MacOS et nous l'executons sur linux on obtient donc :

```
program: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=deba4fa68dbc989053118b9c30b0abcf5f78df23, not stripped 
```

* On peut ajouter l'option -no-pie lors de la compilation pour avoir un executable et pa un shared object, on obtient 

``` 
program: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=5249ded8e231e1b61b1292fc0d720b4a93a28bec, not stripped 
```

## hexdump

* le fichier executable n'étant pas le même que dans l'exemple car compilé par gcc sur linux, on remarque quand même au debut de la colonne de droite `ELF` qui nours montre bien que l'executable est en ELF.


## strings 

* strings permet d'afficher les caractères affichable contenue dans le fichier donné, on lui donne l'executable et on obtient:

``` 
poop
Please input a word:
That's correct!
That's not correct! 
```
## disassembling 

* objdump permet d'afficher le code en assembleur de notre executable.
```console
0000000000400686 <is_valid> (Offset dans le fichier : 0x686):
is_valid():
  400686:       55                      push   %rbp
  400687:       48 89 e5                mov    %rsp,%rbp
  40068a:       48 83 ec 10             sub    $0x10,%rsp
  40068e:       48 89 7d f8             mov    %rdi,-0x8(%rbp)
  400692:       48 8b 45 f8             mov    -0x8(%rbp),%rax
  400696:       48 8d 35 27 01 00 00    lea    0x127(%rip),%rsi        # 4007c4 <_IO_stdin_used+0x4> (Offset dans le fichier : 0x7c4)
  40069d:       48 89 c7                mov    %rax,%rdi
  4006a0:       e8 bb fe ff ff          callq  400560 <strcmp@plt> (Offset dans le fichier : 0x560)
  4006a5:       85 c0                   test   %eax,%eax
  4006a7:       75 07                   jne    4006b0 <is_valid+0x2a> (Offset dans le fichier : 0x6b0)
  4006a9:       b8 01 00 00 00          mov    $0x1,%eax 
  4006ae:       eb 05                   jmp    4006b5 <is_valid+0x2f> (Offset dans le fichier : 0x6b5)
  4006b0:       b8 00 00 00 00          mov    $0x0,%eax
  4006b5:       c9                      leaveq 
```
* Les 3 première ligne correspondent à la déclaration de la fonction, les deux suivantes au `strmcp`. 4006a5 :On fait le test et on retourne 1 ou 0 quand le test est vrai ou faux.
afin que le programme retourne toujours vrai on va chercher la position du byte à changer pour qu'il passe toujours par return 1, on doit donc modifier b8 `00` le byte 00 en 01. Ici à la position 1713. 
le programme nous retourne ensuite:
```
Please input a word: bla
That's correct!
```
# Partie 2

* Modifier un binaire peut permettre a l'attaquant de contourner les certifications et de créer une entrée pour prendre la main sur le code.


