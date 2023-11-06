# Karjaa

Tässä tiedostossa vastaan Tero Karvisen tekemään tehtävänantoon "h2 Karjaa" (Karvinen 2023a)

## Tiivistä

### What is the definition of "cattle not pets"?
DevOps-foorumilla käydyssä keskustelussa Richard Slater vastaa kysymykseen "What is the definition of "cattle not pets"?" viitaten digitaalisen vaikuttajan Randy Biasin kirjoittamaan blogitekstiin "The History of Pets vs Cattle and How to Use the Analogy Properly" (Slater 2017).

Tiivistän Slaterin vastauksen seuraavin pointein:
- Palvelimia voidaan kuvainnollisesti ajatella joko "lemmikkeinä" tai "karjana"
- Palvelin-"lemmikit" ovat manuaalisesti luotuja, käsinkonfiguroituja "yksilöitä", jotka suunniteltu olemaan aina aina päällä/elossa
- Palvelin-"karja" on useamman kuin kahden palvelimen joukko, jotka ovat automatisoituja ja suunniteltu ongelmatilanteissa helposti tuhottaviksi/korvattavaksi
- Palvelinten hallinta tulisi ohjata kohti "karja"-ajattelua, jossa palvelimiin ei "kiinnytä", vaan palvelimet olisivat suunniteltu niin, että niiden vioittuessa ne tuhotaan & korvataan korjaamisen sijaan
- "Karja"-palvelimen tuhoaminen ei kuitenkaan ole aina otollisin vaihtoehto, vaan tilanteesta riippuen niiden jäädyttäminen saattaa olla optimaalisempaa

### Vagrant Revisited – Install & Boot New Virtual Machine in 31 seconds
Tero Karvinen kertoo kirjoittamassaan artikkelissa lyhyen ohjeen, kuinka luoda sekä etäohjata uutta virtuaalikonetta 31 sekunnissa käyttäen Vagranttia ja Virtualboxia (Karvinen 2017). 

Tiivistän Karvisen ohjeen seuraavin pointein:
- Asenna Vagrant ja Virtualbox käyttäen seuraavia komentoja tässä järjestyksessä: ```$ sudo apt-get update``` & ```$ sudo apt-get -y install vagrant virtualbox```
- Alusta (init) uusi virtuaalikone käyttäen komentoa: ```$ vagrant init bento/ubuntu-16.04```
- Käynnistä kyseinen virtuaalikone käyttäen komentoa: ```$ vagrant up```
- Ota luomaasi virtuaalikoneeseen SSH-yhteys käyttäen komentoa: ```$ vagrant ssh```
- Näin olet luonut uuden virtuaalikoneen ja ottanut sen etähallintaasi noin 30 sekunnissa

### Salt Vagrant - automatically provision one master and two slaves
Tero karvinen kertoo kirjoittamasaan artikkelissa "Salt Vagrant - automatically provision one master and two slaves" vaiheittain siitä, kuinka voit ottaa käyttöösi valmiiksi luodun kolmen tietokoneen verkon, ja testailla sitä Saltin avulla (Karvinen 2023b).


Tiivistän Karvisen artikkelin seuraavin pointein:
- Asenna virtuaaliympäristö (Virtualbox & Vagrant). Luo "saltdemo" hakemisto ja sinne Vagrant-tiedosto
- Kopio Karvisen valmiiksi koodama kolmen koneen Vagrant-tiedoston sisältö luomaasi tiedostoon.
- Boottaa nämä kolme konetta komennolla: ```$ vagrant up``` Boottaus saattaa kestää useita minuutteja.
- Hyväksy orjat (koneet) kirjautumalla herra-koneelle (master). Kirjautumiskomento on: ```$ vagrant ssh tmaster```
- Orja-koneet ovat lähettäneet ennakoidusti avaimensa herra-koneelle. Hyväksy ne herra-koneella
- Testaa yhteyden toimivuus Komennolla ```$ sudo salt '*' test.ping```. Terminaaliin tulisi tulla arvot "True" orja-koneiden kohdalla
- Kun yhteys toimii, voit ohjata orja-koneita ja etsiä niistä tietoja käyttämällä esimerkiksi seuraavia komentoja: ```$ sudo salt '*' cmd.run 'hostname -I'``` & ```$ sudo salt '*' grains.items```
- Idempotenttisia komentoja tulisi suosia herra-orja -arkkitehtuurissa
- Voit käyttää kaikkia Saltin tilafunktiosta, kuten pkg, file, service, user, cmd
- Koska orjat ovat karjaa, ei lemmikkejä, tulisi ne päästää päiviltä heti, kun ne ovat suorittaneet velvollisuutensa ja kun niitä ei enää tarvita. Tämä onnistuu komennoilla: ```$ exit``` & ```$ vagrant destroy```

## Asenna Vagrant
Tässä osiossa asennan Vagrantin isäntäkäyttöjärjestelmälläni. Vagrantin asennusohjelman ja -ohjeet löysin HashiCorpin omilta sivuilta (HashiCorp Developer s.a) Itse asennus oli yksinkertainen; latasin Windowsille Vagrantin asennusohjelman ja suoritin sen seuraten asennussohjelman ohjeita.

![vagrabtin_asennus33](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/09dfc28c-3ec4-4d4b-8be5-7a695344abb8)

Lopuksi vielä tarkistin, että Vagrant oli asennettu käyttäen ```$ vagrant --version``` komentoa Windowsin Command Promtissa. Tämä tuotti vastauksen "Vagrant 4.2.0", joka kertoo että Vagrantin versio 4.2.0 on asennettuna.

![Vagrantin_asennus_checkkaus](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/2629dd8a-6a62-498c-9698-362ef069b501)

## Yksi maankiertäjä
Tässä osiossa loin virtuaalikoneen Vagrantin avulla, loin SSH yhteyden siihen ja testasin sen nettiyhteyden toimivuutta. (BrianC 2014)
Itse Vagrant-tiedoston luontiin käytin komentoa ```$ vagrant init hashicorp/precise32```. Tämä loi VagrantFilen. Seuraavaksi loin ja käynnistin uuden virtuaalikoneen ```$ vagrant up``` komennolla. Uusi virtuaalikone perustuu aiemmin luomaani VagrantFileen.

![ekavirtualikone](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/91258b58-c4e0-4efd-8510-03eef172bd75)

Loin SSH-yhteyden virtuaalikoneeseeni ```$ vagrant ssh``` komennolla. Komentorivi informoi, ettei Ubuntu versioni ole tuettu ja tarjosi mahdollisuuden päivittää sen ```$ do-release-upgrade``` komennolla. Kokeilin päivittää, mutta tuntemattomasta syystä se ei onnistunut. SSH-yhteyden luonti onnistui kuitenkin kuten.

![ssh_yhteysluonti](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/e2c58b4c-6abb-43be-979a-f7c80df9e395)

Lopuksi vielä testasin virtuaalikoneeni netin toimivuutta pingaamalla Googlen sivuille komennolla:
```$ ping google.com```. Pingaus toimi, eikä paketteja hävinnyt matkalla, joten yhteys toimii!

![ping](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/602a01c8-eac4-45e3-a316-d8c003be3018)

## Oma orjansa
Tässä osiossa luon Salt herran ja orjan samalle koneelleni. Osion tekemisessä käytin Karvisen ohjeistusta ja modifoituani versiota hänen konfiguroimasta Vagrant-tiedostosta (Karvinen 2023b).

Siirryin GUI:n kautta muokkaamaan aiemmassa tehtävässä luomaani VagrantFileä, jotta se luo virtuaalikoneen, jossa on sekä herra-, orjakäyttäjät. Koska tehtävänannossa pyydettiin vain yhtä orja-käyttäjää, sovelsin Karvisen konfiguroimaa Vagrant-tiedostoa, kuitenkin poistaen siitä toisen orja-käyttäjän luontikoodin (Karvinen 2023b).

![Vagrantfile_1](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/bc5ded52-b53e-4aab-9676-bfbc7c2b8eec)

Suoritin ```$ vagrant up``` komennon Command Promtissa, joka luo uuden virtuaalikoneen (sekä tehtävänannossa pyydetyt herran ja orjan) perustuen muokkaamaani VagrantFileen.

![vagrant_up_1](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/71fc94a1-d5fc-4637-ba2b-a7b83668ba96)
![vagrant_up2](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/14e6b99f-1165-43ad-8b62-d12c68f87747)

## Asenna Saltin herra-orja arkkitehtuuri toimimaan verkon yli

  
## References
Bias 2016: The History of Pets vs Cattle and How to Use the Analogy Properly. Luettavissa: http://cloudscaling.com/blog/cloud-computing/the-history-of-pets-vs-cattle/. Luettu 3.11.2023.

BrianC 2014. Error when trying vagrant up. Stack Overflow. Luettavissa: https://stackoverflow.com/questions/23874260/error-when-trying-vagrant-up. Luettu: 6.11.2023

HashiCorp Developer s.a. Install Vagrant. Luettavissa: https://developer.hashicorp.com/vagrant/docs/installation. Luettu 6.11.2023.

Karvinen 2017: Vagrant Revisited – Install & Boot New Virtual Machine in 31 seconds. Luettavissa: https://terokarvinen.com/2017/04/11/vagrant-revisited-install-boot-new-virtual-machine-in-31-seconds/. Luettu 3.11.2023.

Karvinen 2023a: Infra as Code 2023. Luettavissa: https://terokarvinen.com/2023/configuration-management-2023-autumn/. Luettu 3.11.2023.

Karvinen 2023b: Salt Vagrant - automatically provision one master and two slaves. Luettavissa: https://terokarvinen.com/2023/salt-vagrant/. Luettu: 3.11.2023.

Slater 2017: What is the definition of "cattle not pets"?. Luettavissa: https://devops.stackexchange.com/questions/653/what-is-the-definition-of-cattle-not-pets#654. Luettu: 3.11.2023.
