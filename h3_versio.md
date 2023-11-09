# Versio
Tässä raportissa vastaan Tero Karvisen laatimaan tehtävänannon "h3 Versio" kaikkiin osioihin (Karvinen 2023a). Suoritan tehtävät käyttäen hyödyksi toteutuksella aiemmin luomaani Debian 12 -virtuaalikonetta VirtualBoxilla. Huomiona vielä, että raportin alkupään kuvankaappaukset on otettu rautalaitteellani, kun taas osa niistä on otettu virtuaalikoneellani. Tästä syystä kuvien ulkoasu vaihtelee hieman raportin aikana.

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

![7  SSHOnglema](https://github.com/RonSkogberg/winter-duck/assets/148875466/5c4cd424-9c8c-40db-bc27-ec2acccf759e)

Muistin edelliseltä luennolta, että Karvinen kohtasi saman ongelman, meni terminaaliinsa ja generoi avainparin ```$ ssh-keygen``` komennolla, josta hän lisäsi julkisen SSH-avaimen GitHub-käyttäjäänsä. Lähdin suorittamaan samaa toimenpidettä virtuaalikoneeni terminaalissa.

![6  Keygen](https://github.com/RonSkogberg/winter-duck/assets/148875466/56b68689-d8af-4af1-964d-c011f750bf02)

```$ ssh-keygen``` komento generoi tosiaan sekä julkisen, että yksityisen SSH-avaimen piilotettuun .ssh -hakemistoon (piste hakemiston edessä tarkoittaa, että se on piilotettu). 





## References

Karvinen 2023a: Infra as Code 2023. Luettavissa: https://terokarvinen.com/2023/configuration-management-2023-autumn/. Luettu 8.11.2023.
