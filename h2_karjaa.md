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

## References
Bias 2016: The History of Pets vs Cattle and How to Use the Analogy Properly. Luettavissa: http://cloudscaling.com/blog/cloud-computing/the-history-of-pets-vs-cattle/. Luettu 3.11.2023.

Karvinen 2017: Vagrant Revisited – Install & Boot New Virtual Machine in 31 seconds. Luettavissa: https://terokarvinen.com/2017/04/11/vagrant-revisited-install-boot-new-virtual-machine-in-31-seconds/. Luettu 3.11.2023.

Karvinen 2023a: Infra as Code 2023. Luettavissa: https://terokarvinen.com/2023/configuration-management-2023-autumn/. Luettu 3.11.2023.

Karvinen 2023b: Salt Vagrant - automatically provision one master and two slaves. Luettavissa: https://terokarvinen.com/2023/salt-vagrant/. Luettu: 3.11.2023.

Slater 2017: What is the definition of "cattle not pets"?. Luettavissa: https://devops.stackexchange.com/questions/653/what-is-the-definition-of-cattle-not-pets#654. Luettu: 3.11.2023.
