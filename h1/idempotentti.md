# Idempotentti
Idempontti IT-maailmassa tarkoittaa tilaa, jossa toistettaessa samaa komentoa/käskyä useita kertoja, ei sen tulokset ensimmäisen kerran jälkeen muutu. Esimerkiksi tehtävässä "Viisi tärkeintä" loin "directoryOfFiles.txt" tiedoston käyttäen komentoa:

```$ sudo salt-call --local -l info state.single file.managed /home/rontti/directoryOfFiles.txt```

Jos suoritan saman saman käskyn uudestaan, huomataan, että kyseinen tiedosto on jo olemassa. Täten uutta tiedostoa ei luoda, vaikka ensimmäisen kerran suorittaessa käskyn se loi kyseisen tiedoston. Täten vaikka toistaisimme kyseisen käskyn satoja kertoja, ei sen lopputulos muutu ensimmäisen käskykerran jälkeen.

![idempotentti](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/fda61368-8993-4320-8ddc-09409b869b1b)

## References
Karvinen 2023: Infra as Code 2023 https://terokarvinen.com/2023/configuration-management-2023-autumn/

Karvinen 2023: Run Salt Command Locally https://terokarvinen.com/2021/salt-run-command-locally/

Naziridis 2021, SSL: FAQ: Verkkohyökkäykset ja tietoturvaongelmat https://www.ssl.com/fi/FAQ/verkkohy%C3%B6kk%C3%A4ykset-ja-turvallisuuskysymykset/
