**Tehtävät on saatu osoitteesta: https://terokarvinen.com/2021/configuration-management-systems-palvelinten-hallinta-ict4tn022-spring-2021/#laksyt.*

**Tehtäviä varten on tehty puhdas asennus kurssin opettajan suosimasta Xubuntusta VirtualBoxille.*

# Harjoitus 3

## a) MarkDown. Tee tämän tehtävän raportti MarkDownina.
Aloitin luomalla GitHub-kansiooni (https://github.com/bgm064/schoulu) MarkDown-tiedoston valitsemalla valikosta Add File -> Create new file. Nimesin tiedoston Harjoitus 3.md:ksi.

Tämän jälkeen tallensin ensimmäisen version tiedostosta ja annoin koneellani komennon, jolla sain päivitettyä tiedoston myös koneelleni.

    $ git add . && git commit; git pull && git push
    
Komennon päivitin muistiini Tero Karvisen ohjeista osoitteesta: http://terokarvinen.com/2016/publish-your-project-with-github/.

## d) Näytä omalla git-varastollasi esimerkit komennoista ‘git log’, ‘git diff’ ja ‘git blame’. Selitä tulokset.
Annoin ensin 'git log' komennon ja terminaaliin tulostui muutosloki joka sisälsi seuraavat tiedot:

```
commit 3f64c6fdb272b23b9288c774b8dd9da9576116a1 (HEAD -> main, origin/main, origin/HEAD)
Author: bgm064 <82582770+bgm064@users.noreply.github.com>
Date:   Tue Apr 20 12:58:38 2021 +0300

   Update Harjoitus 3.md

commit 84c6f562d055bf32c104ff035fd251d42058e697
Author: bgm064 <82582770+bgm064@users.noreply.github.com>
Date:   Tue Apr 20 12:53:50 2021 +0300

   Create Harjoitus 3.md
```

Muutoslokissa kerrotaan mitä muutoksia on tehty ja milloin.

Seuraavaksi kokeilin 'git diff' komentoa. Komento ei tehnyt mitään, sillä koneeni ja GitHubin kansioiden sisällössä ei ollut eroavaisuuksia.

Loin tiedoston testitiedoston ja lisäsin sekä committasin sen Gitiin.

        $ sudo nano difftesti.txt
        
        $ git add . && git commit

Tämän jälkeen poistin tiedoston koneeltani 'rm' komennolla jonka jälkeen annoin uudestaan 'git diff' komennon ja sain vastaukseksi seuraavan:
```
diff --git a/difftesti.txt b/difftesti.txt
deleted file mode 100644
index e432d0f..0000000
--- a/difftesti.txt
+++ /dev/null
@@ -1 +0,0 @@
-Tämä on testi.
```

Kyseinen komento siis tulostaa tiedon koneen ja GitHubin kansioiden välisistä eroista.

Lopuksi kokeilin vielä 'git blame' komentoa. Vastaukseksi sain seuraavan:

```
4f612155 (bgm064 2021-04-20 13:48:36 +0300 24)    Update Harjoitus 3.md
4f612155 (bgm064 2021-04-20 13:48:36 +0300 25) 
4f612155 (bgm064 2021-04-20 13:48:36 +0300 26) commit 84c6f562d055bf32c104ff035fd251d42058e697
4f612155 (bgm064 2021-04-20 13:48:36 +0300 27) Author: bgm064 <82582770+bgm064@users.noreply.github.com>
4f612155 (bgm064 2021-04-20 13:48:36 +0300 28) Date:   Tue Apr 20 12:53:50 2021 +0300
```

Komento tulostaa tiedon siitä kuka viimeisimmät muutokset on tehnyt.

## e) Tee tyhmä muutos gittiin, älä tee commit:tia. Tuhoa huonot muutokset ‘git reset –hard’. Huomaa, että tässä toiminnossa ei ole peruutusnappia.
Poistin koneeni Git-kansiosta 'README.md' tiedoston 'rm' komennolla. Annoin tämän jälkeen komennon 'git reset --hard' joka palautti poistetun tiedoston.
```
jani@jani-vb:~/schoulu$ ls
'Harjoitus 3.md'   LICENSE   README.md
jani@jani-vb:~/schoulu$ sudo rm README.md 
jani@jani-vb:~/schoulu$ ls
'Harjoitus 3.md'   LICENSE
jani@jani-vb:~/schoulu$ git reset --hard
HEAD is now at 5c098d0 Merge branch 'main' of https://github.com/bgm064/schoulu into main
jani@jani-vb:~/schoulu$ ls
'Harjoitus 3.md'   LICENSE   README.md
```

## f) Tee uusi salt-moduli.
Päätin asentaa GIMP:in Saltin avulla. Aloitin luomalla kansion tälle ohjelmalle '/srv/salt' hakemistoon.

        $ sudo mkdir gimp

Tämän jälkeen vaihdoin kyseiseen kansioon 'cd' komennolla ja loin sen sisälle sls-tiedoston.

        $ sudoedit init.sls

Tähän tiedostoon lisäsin seuraavan funktion:

```
gimp:
  pkg.installed
```

Seuraavaksi ajoin luomani tilan salt minionilla.

        $ sudo salt '*' state.apply gimp
        
Noin minuutin odottamisen jälkeen sain ilmoituksen onnistuneesta asennuksesta:

        jani:
          ID: gimp
    Function: pkg.installed
      Result: True
     Comment: The following packages were installed/updated: gimp
     Started: 14:40:17.306023
    Duration: 57975.845 ms  

<details>
    <summary>Changes:</summary>

              ----------
              gimp:
                  ----------
                  new:
                      2.8.22-1
                  old:
              gimp-data:
                  ----------
                  new:
                      2.8.22-1
                  old:
              gimp-python:
                  ----------
                  new:
                      1
                  old:
              libamd2:
                  ----------
                  new:
                      1:5.1.2-2
                  old:
              libbabl-0.1-0:
                  ----------
                  new:
                      0.1.44-1
                  old:
              libblas.so.3:
                  ----------
                  new:
                      1
                  old:
              libblas3:
                  ----------
                  new:
                      3.7.1-4ubuntu1
                  old:
              libcamd2:
                  ----------
                  new:
                      1:5.1.2-2
                  old:
              libccolamd2:
                  ----------
                  new:
                      1:5.1.2-2
                  old:
              libcholmod3:
                  ----------
                  new:
                      1:5.1.2-2
                  old:
              libgegl-0.3-0:
                  ----------
                  new:
                      0.3.30-1ubuntu1
                  old:
              libgfortran4:
                  ----------
                  new:
                      7.5.0-3ubuntu1~18.04
                  old:
              libgimp2.0:
                  ----------
                  new:
                      2.8.22-1
                  old:
              liblapack.so.3:
                  ----------
                  new:
                      1
                  old:
              liblapack3:
                  ----------
                  new:
                      3.7.1-4ubuntu1
                  old:
              libmetis5:
                  ----------
                  new:
                      5.1.0.dfsg-5
                  old:
              libmng2:
                  ----------
                  new:
                      2.0.2-0ubuntu3
                  old:
              libraw16:
                  ----------
                  new:
                      0.18.8-1ubuntu0.3
                  old:
              libumfpack5:
                  ----------
                  new:
                      1:5.1.2-2
                  old:
              python-cairo:
                  ----------
                  new:
                      1.16.2-1
                  old:
              python-gobject-2:
                  ----------
                  new:
                      2.28.6-12ubuntu3
                  old:
              python-gtk2:
                  ----------
                  new:
                      2.24.0-5.1ubuntu2
                  old:
              python2.7-cairo:
                  ----------
                  new:
                      1
                  old:
              python2.7-gobject:
                  ----------
                  new:
                      1
                  old:
              python2.7-gobject-2:
                  ----------
                  new:
                      1
                  old:

</details>

```
Summary for jani
------------
Succeeded: 1 (changed=1)
Failed:    0
------------
Total states run:     1
Total run time:  57.976 s
```

Ajoin tilan vielä uudestaan ja sain ilmoituksen, että ohjelma on jo asennettu.

```
jani:
----------
          ID: gimp
    Function: pkg.installed
      Result: True
     Comment: All specified packages are already installed
     Started: 15:02:53.190934
    Duration: 1748.847 ms
     Changes:   

Summary for jani
------------
Succeeded: 1
Failed:    0
------------
Total states run:     1
Total run time:   1.749 s
```

![GIMP](https://user-images.githubusercontent.com/82582770/115393370-48c19f00-a1ea-11eb-9069-000535914a0c.JPG)


## Lähteet

Tero Karvinen, 2016, Publish Your Project... Luettavissa: http://terokarvinen.com/2016/publish-your-project-with-github/. Luettu: 20.4.2021.

GitHub, 2014, Mastering Markdown. Luettavissa: https://guides.github.com/features/mastering-markdown/. Luettu 20.4.2021.

