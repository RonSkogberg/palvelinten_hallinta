# Versio
Tässä raportissa vastaan Tero Karvisen laatimaan tehtävänannon "h3 Versio" kaikkiin osioihin (Karvinen 2023). Suoritan tehtävät käyttäen hyödyksi toteutuksella aiemmin luomaani Debian 12 -virtuaalikonetta VirtualBoxilla. Huomiona vielä, että raportin alkupään kuvankaappaukset on otettu rautalaitteellani, kun taas myöhemmät kuvat on otettu virtuaalikoneellani. Tästä syystä kuvien ulkoasu vaihtelee hieman raportin aikana.

Ennen varsinaisen tehtävän aloittamista päivitin Linuxin pakettivarastot  ```$ sudo apt-get update``` komennolla, jonka jälkeen päivitin paketit ```$ sudo apt-get dist-upgrade -y```. Asensin myös Git:in virtuaalikoneelleni komennolla ```$ sudo apt-get install git-all -y``` ja tarkistin sen version komennolla  ```git version```. Git versioni näyttäisi olevan 2.39.2, eli se on todennettu asennetuksi. Kaikki tarpeellinen näyttäisi olevan päivitettynä, joten eiköhän aloiteta!

![1_DebianinPäivitys](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/9a501244-dc1b-4edb-b444-e84b4d28040a)

![4  GitAsennus](https://github.com/RonSkogberg/winter-duck/assets/148875466/5b4bc0f2-5a7b-44cd-a14c-c30d4a4eda14)

![5  GitTarkistus](https://github.com/RonSkogberg/winter-duck/assets/148875466/a2130879-dc11-496e-9512-12b625e5b732)

## a) Online
Tässä osiossa tehtävänäni on luoda GitHubiini uusi varasto ja vähintään yksi uusi tiedosto sinne. Uusi varasto toimii annetun tehtävän tulevien osioiden leikkikenttänä.

Kirjauduttuani GitHubiin käyttäjätunnuksillani, pystyin luomaan uuden varaston (repository) suoraan etusivulta painamalla "Create a new repository" painiketta. Täytin luontilomakkeen tiedot/asetukset. Varmistin myös, että loin pyydetyn README.md tiedoston, käytin pyydettyä "winter" nimikettä tehtävänannon mukaisesti sekä valitsin GNU General Public License 3 -lisenssin.

![2_repositorynLuominen](https://github.com/RonSkogberg/winter-duck/assets/148875466/4058c94d-5940-43f1-bf1b-6bc80413ab81)

Luotuani varaston varmistin vielä sen olemassaolon siirtymällä sinne.

![3_repoTodiste](https://github.com/RonSkogberg/winter-duck/assets/148875466/60d79fba-f6be-4eb5-8086-d3c60bc09c8c)

## b) Dolly
Tässä osiossa tehtävänäni on kloonata edellisessä osiossa luomani varasto, tehdä muutoksia sinne ja puskea ne palvelimelle. Lopuksi vielä tarkistin muutosten tapahtuneen.

Kohtasin ensimmäisen ongelman heti kättelyssä; kun olin aikeissa kopioida GitHubistani luomani winter-duck -varaston SSH-linkin. GitHub ilmoitti, ettei käyttäjääni ole yhdistetty yhtään julkista SSH-avainta. 

![7  SSHOnglema](https://github.com/RonSkogberg/winter-duck/assets/148875466/628f0914-953a-4c8c-9832-504d4b86bd43)

Muistin Karvisen luennolta, että hän kohtasi saman ongelman. Karvinen meni terminaaliinsa ja generoi avainparin ```$ ssh-keygen``` komennolla, josta hän lisäsi julkisen SSH-avaimen GitHub-käyttäjäänsä. Lähdin suorittamaan samaa toimenpidettä virtuaalikoneeni terminaalissa.

![6  Keygen](https://github.com/RonSkogberg/winter-duck/assets/148875466/56b68689-d8af-4af1-964d-c011f750bf02)

```$ ssh-keygen``` komento generoi tosiaan sekä julkisen, että yksityisen SSH-avaimen piilotettuun .ssh -hakemistoon (piste hakemiston edessä tarkoittaa, että se on piilotettu). Siirryin Debian-virtuaalikoneeni desktopille tarkistamaan hakemiston ja avaimien olemassa olon ja siellähän molemmat avaimeni olivat. Avasin id_rsa.pub-tiedoston LibreOffice Writerilla ja kopioin avaimen Githubin käyttäjälleni.

![ssholemassaolo](https://github.com/RonSkogberg/winter-duck/assets/148875466/1772b04c-b165-4d3d-b57e-a5d517a00b45)

![8_lisääSSHKEY](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/418cc0a6-edd7-4e81-a048-7e413352575c)

Lopuksi vielä tarkistin, että SSH-avain oli tosiaan lisätty, ja että tehtävän alussa esiintynyt ilmoitusteksti avaimen puuttumisesta oli poissa.

![9 SSHkeylisätty](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/3687a965-0c87-465e-bae3-bdc57e5743cf)

![10 SSHongelmahoidettu](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/652b3ab3-8001-4f8a-a635-5b6aacf07193)

Nyt kun sain kopioitua GitHubistani reponi kloonauslinkin, siirryin virtuaalikoneeni terminaalin puolelle viimeistelemään kloonauksen. Loin uuden hakemiston ```$ mkdir talviankka``` komennolla (myöhemmin huomatakseni, ettei se olisi ollut tarpeellista). Siirryin kyseiseen hakemistoon ja viimeistelin kloonauksen ```$ git clone git@githun.com:RonSkogberg/winter-duck.git``` komennolla. Kloonauksen aikana komentorivillä kysytään, että hyväksykö yhteyden luonnin siitäkin huolimatta, ettei GitHubin isäntäpalvelimen aitoutta voida varmentaa. Vastasin "yes", sillä pystyin tässä tapauksessa luottamaan yhteyden luotettavuuteen. Lopputuloksena syntyy "winter-duck" niminen hakemisto, johon siirryn seuraavaksi.

![12_cloonaawinter](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/c3e117db-5284-40f6-b857-90a216b25694)

Siirryttyäni kloonaamaani hakemistoon ```$ cd winter-duck``` komennolla, tarkistin vielä sen sisältävän samat tiedostot, kuin mitä olin GitHubin varastooni luonut. Tiedostot olivat samat. Halusin tehdä uuden tiedoston nano-tekstieditorilla, jonka nimesin dollyankka.md -tiedostoksi. Käytin ```$ git add .``` komentoa osoittamaan muutoksia seuraavia toimenpiteitä varten. Tätä komentoa seuraa ```$ git commit -m "tiedosto lisätty"```, joka tallentaa muutokset Git-varaston muutoshistoriaan.

![14 addcommitdolly](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/45c43793-14b8-463e-a37e-4867b7ba3e31)

Kun olen tehnyt tarvittavat muutokset, "työnnän" ne vielä luomaani GitHub-varastoon. Työntö tehdään komennolla ```$ git push origin main```. Terminaali ilmoittaa, että muutokset on tehty osoitteeseen github.com:RonSkogberg/winter-duck.git. Kävin myös varmistamassa GitHubin puolella, että tekemäni muutokset todellakin tapahtuivat. Lopputuloksesta näkee, että dollyankka.md-tiedosto on lisätty varastoon jälkikäteen.

![15 pushoriginmain](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/8739eeeb-c4db-4021-adeb-f967f4026cda)

![16 pushtulosonnistunut](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/11fbb618-719e-4797-9dd1-67d3e5e62045)

## c) Doh!
Tässä osiossa tehtävänäni on tehdä tyhmiä muutoksia gittiin, ilman committia. Lopuksi tuhoan tekemäni muutokset.

Oho! Dolly-Ankan kotiosoite ja vara-avaimen sijainti on vuotanut yhteen git-dokumenttiin. Tiedot on tuhottava välittömästi, ennen kuin rosvot huomaavat ne.

Muokkaan tässä tehtävässä aiemmin luomaani dollyankka.md -tiedostoa. Tiedostomuutokset tein nanolla ja varmistin cat-komennolla, että muutokset tulivat voimaan. Arkaluontoiset tiedot on tuhottava, ja tehokkain tapa siihen on käyttää ```$ git reset --hard``` komentoa. Komennon "git reset" osuus purkaa pelkästään commitin. Kun siihen lisätään "--hard" osuus, purkaa se commitin SEKÄ
poistaa indeksistä sekä työkopiosta kaikki viime commitin jälkeiset muutokset (Polvinen 2020).

Lopuksi tarkistin, että aiemmin lisätyt arkaluontoiset tiedot ovat peruutettu lukemalla dollyankka.md tiedoston sisällön. Tiedot ovat peruutettu ja Dolly-ankka voi nukkua yönsä rauhassa.

Huomautuksena vielä, että ```$ git reset --hard``` komentoa ei voi peruuttaa ja sitä tulisi käyttää harkiten, sillä se todellakin poistaa kaikki tallentamattomat muutokset.

![17 dog](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/3587a2da-79e1-4465-9080-7992e7eab2c1)


## References

Karvinen 2023: Infra as Code 2023. Luettavissa: https://terokarvinen.com/2023/configuration-management-2023-autumn/. Luettu 8.11.2023.

Polvinen 2020: Pieni Git-opas. 2.2 Paikallisen commitin muokkaus (git amend). University of Turku. Luettavissa: https://vm.utu.fi/document/fi_pieni-git-opas.pdf. Luettu: 11.11.2023.
