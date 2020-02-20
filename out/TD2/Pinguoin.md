* on peut trouver le fichier contenant a photo du pinguoin en décompressant progressivement avec binwalk puis en la cherchant à la main :


![center](https://github.com/LeaGiordano/2SU_2020_Giordano/blob/master/out/TD2/Capture%20du%202020-02-12%2010-51-28.png)



* __Ou__ on extrait les fichiers en une seule commande:

  `binwalk -e -d 8 vmlinuz-qemu-arm-2.6.20`

* on se place dans le dossier qui contient E7E0. Et on cherche où se trouve l'image avec un exdump on retoruve l'offset.

* on extrait le fichier tux.png grace à son offset:

  `dd skip=2984568 count=24656 if=E7E0 of=pingouin.png bs=1 conv=notrunc`
