*Tehtävät on saatu osoitteesta: https://terokarvinen.com/2021/configuration-management-systems-palvelinten-hallinta-ict4tn022-spring-2021/#laksyt.

*Tehtäviä varten on tehty puhdas asennus kurssin opettajan suosimasta Xubuntusta VirtualBoxille.

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

## f) Tee uusi salt-moduli. Voit asentaa ja konfiguroida minkä vain uuden ohjelman: demonin, työpöytäohjelman tai komentokehotteesta toimivan ohjelman. Käytä tarvittaessa ‘find -printf “%T+ %p\n”|sort’ löytääksesi uudet asetustiedostot. (Tietysti eri ohjelma kuin aiemmissa tehtävissä, tarkoitushan on harjoitella Salttia)

## Lähteet

Tero Karvinen, 2016, Publish Your Project... Luettavissa: http://terokarvinen.com/2016/publish-your-project-with-github/. Luettu: 20.4.2021.
