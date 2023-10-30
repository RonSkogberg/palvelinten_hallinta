# Viisi Tärkeintä
Tässä tehtävässä keskityn viiteen tärkeimpään Saltin tilafunktioon. Käytin tehtävässä Tero Karvisen tekemiä materiaaleja (Run Salt Command Locally & Infra as Code 2023)

## pkg.installed
![pkg_nano](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/ab5e5ab9-240a-464f-94d0-14d258b5408d)

```$ sudo salt-call --local -l info state.single pkg.installed nano```

Tässä annan paikallisen salt-käskyn, joka tarkistaa onko nano-tekstieditorin asennettu, ja kuten kuvasta näkyy, on se jo esiasennettuna, eikä täten latausta tapahdu.
Jos nanoa ei olisi ollut esiasennettuna, olisi tämä käsky ladannut ja asentanut sen.

```$ sudo salt-call --local -l info state.single pkg.removed nano```

Tällä salt-käskyllä olisin voinut poistaa kyseisen nano-tekstieditorin. En kuitenkaan halua tehdä sitä, sillä nano on mush-have työkalu tekstipohjaisessa käyttöliittymässä. ;)

## file.managed
![file_managed](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/3801e714-a697-4629-839c-8d2b69c07655)

```$ sudo salt-call --local -l info state.single file.managed /home/rontti/directoryOfFiles.txt```

Tällä salt-käskyllä pystyn tarkistamaan onko tiedosto (tässä tapauksessa "directoryOfFiles") olemassa. Koska kyseistä tiedostoa ei ollut olemassa, loi käsky sellaisen tiedoston.

```$ sudo salt-call --local -l info state.single file.absent /home/rontti/directoryOfFiles.txt```

Tällä pystyn poistamaan kyseisen tiedoston, jos se on jo olemassa.

## service.running
![apache2](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/36ff7f87-5bb5-444e-8ae3-bb2467b30e92)

```$ sudo salt-call --local -l info state.single service.running apache2 enable=True```

Tällä salt-käskyllä pystyn tarkistamaan onko esimerkiksi apache2 käynnissä. Käynnissähän se on!

```$ sudo salt-call --local -l info state.single service.dead apache2 enable=False```

Tällä käskyllä taas saan sen otettua pois päältä.

## user.present
![ope](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/765d24a6-37c6-4ef5-aea8-296b652808e2)

```$ sudo salt-call --local -l info state.single user.present ope```

Tällä salt-käskyllä pystymme tarkistamaan onko käyttäjää "ope" olemassa. Jos sitä ei ole, luo tämä käsky sellaisen. Käyttäjän tarkistus/poisto tapahtuu seuraavalla käskyllä:

```sudo salt-call --local -l info state.single user.absent ope```

## cmd.run
![get_update](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/21042a85-17fa-46ef-8272-f611178e0511)

```$ sudo salt-call --local -l info state.single cmd.run 'apt-get update'```

Tällä salt-käskyllä pystyn suorittamaan esimerkiksi päivityskomentoja mielivaltaisesti.

## References
Karvinen 2023: Infra as Code 2023 https://terokarvinen.com/2023/configuration-management-2023-autumn/

Karvinen 2023: Run Salt Command Locally https://terokarvinen.com/2021/salt-run-command-locally/

Github 2023: Creating and highlighting code blocks https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks
