*Tehtävät on saatu osoitteesta: https://terokarvinen.com/2021/configuration-management-systems-palvelinten-hallinta-ict4tn022-spring-2021/#laksyt.

*Tehtäviä varten on tehty puhdas asennus kurssin opettajan suosimasta Xubuntusta VirtualBoxille.

# Harjoitus 3

## a) MarkDown. Tee tämän tehtävän raportti MarkDownina.
Aloitin luomalla GitHub-kansiooni (https://github.com/bgm064/schoulu) MarkDown-tiedoston valitsemalla valikosta Add File -> Create new file. Nimesin tiedoston Harjoitus 3.md:ksi.

Tämän jälkeen tallensin ensimmäisen version tiedostosta ja annoin koneellani komennon, jolla sain päivitettyä tiedoston myös koneelleni.

    $ git add . && git commit; git pull && git push

## d) Näytä omalla git-varastollasi esimerkit komennoista ‘git log’, ‘git diff’ ja ‘git blame’. Selitä tulokset.

## e) Tee tyhmä muutos gittiin, älä tee commit:tia. Tuhoa huonot muutokset ‘git reset –hard’. Huomaa, että tässä toiminnossa ei ole peruutusnappia.

## f) Tee uusi salt-moduli. Voit asentaa ja konfiguroida minkä vain uuden ohjelman: demonin, työpöytäohjelman tai komentokehotteesta toimivan ohjelman. Käytä tarvittaessa ‘find -printf “%T+ %p\n”|sort’ löytääksesi uudet asetustiedostot. (Tietysti eri ohjelma kuin aiemmissa tehtävissä, tarkoitushan on harjoitella Salttia)

## Lähteet

Tero Karvinen, 2016, Publish Your Project... Luettavissa: http://terokarvinen.com/2016/publish-your-project-with-github/. Luettu: 20.4.2021.
