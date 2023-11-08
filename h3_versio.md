# Versio
Tässä raportissa vastaan Tero Karvisen laatimaan tehtävänannon "h3 Versio" kaikkiin osioihin (Karvinen 2023a). Suoritan tehtävät käyttäen hyödyksi toteutuksella aiemmin luomaani Debian 12 -virtuaalikonetta VirtualBoxilla. Huomiona vielä, että osa alkupään kuvankaappaukset on otettu rautalaitteellani, kun taas myöhemmät ovat otettu virtuaalikoneellani (siksi kuvien ulkoasu saattaa vaihdella). 

Ennen varsinaisen tehtävän aloittamista päivitin Linuxin pakettivarastot  ```$ sudo apt-get update``` komennolla, jonka jälkeen päivitin paketit ```$ sudo apt-get dist-upgrade -y```. Asensin myös Git:in virtuaalikoneelleni komennolla ```$ sudo apt-get install git-all -y``` ja tarkistin sen version komennolla  ```git version``` todeten samalla asennuksen onnistumisen. Kaikki tarpeellinen näyttäisi olevan päivitettynä, joten eiköhän aloiteta!

![1_DebianinPäivitys](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/9a501244-dc1b-4edb-b444-e84b4d28040a)

![4  GitAsennus](https://github.com/RonSkogberg/winter-duck/assets/148875466/5b4bc0f2-5a7b-44cd-a14c-c30d4a4eda14)

![5  GitTarkistus](https://github.com/RonSkogberg/winter-duck/assets/148875466/a2130879-dc11-496e-9512-12b625e5b732)

## a) Online
Tässä osiossa tehtävänäni on luoda GitHubiini uusi varasto ja vähintään yksi uusi tiedosto sinne. Uusi varasto toimii tehtävän tulevien osioiden leikkikenttänä.

Kirjauduttuani GitHubiin käyttäjätunnuksillani, pystyin luomaan uuden varaston (repository) suoraan etusivulta painamalla "Create a new repository" painiketta. Täytin luontilomakkeen tiedot/asetukset. Varmistin myös, että loin pyydetyn README.md tiedoston, käytin pyydettyä "winter" nimikettä tehtävänannon mukaisesti ja asetan GNU General Public License 3 -lisenssin.

![2_repositorynLuominen](https://github.com/RonSkogberg/winter-duck/assets/148875466/0155a6bb-71ef-4b7d-a9a0-473766b50330)

Luotuani varaston varmistin vielä sen olemassaolon siirtymällä sinne.

![3_repoTodiste](https://github.com/RonSkogberg/winter-duck/assets/148875466/60d79fba-f6be-4eb5-8086-d3c60bc09c8c)

## b) Dolly



## References

Karvinen 2023a: Infra as Code 2023. Luettavissa: https://terokarvinen.com/2023/configuration-management-2023-autumn/. Luettu 8.11.2023.
