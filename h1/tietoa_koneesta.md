# Tietoa koneesta

Suoritettuani seuraavan komennon/käskyn, sain paljon hyödyllistä tietoa (virtuaali)koneestani, joista tosin en puolia ymmärtänyt. Sain poimittua sieltä kuitenkin esimerkiksi koneeni prosessoritietoja ja DNS-palvelimen IP-osoitteita:

```$ sudo salt-call --local grains.items```

![tietoa](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/3e37397f-44f6-431e-ad41-389ec1db4289)

Suorittamalla seuraavan komennon/käskyn, sain vielä tietää (virtuaalikoneeni) käyttöjärjeslmätietoja:

```$ sudo salt-call --local grains.item osfinger```

![osfinger](https://github.com/RonSkogberg/palvelinten_hallinta/assets/148875466/0f103618-c016-4900-9be6-4f23c6012f2a)

## References
Karvinen 2023: Infra as Code 2023 https://terokarvinen.com/2023/configuration-management-2023-autumn/

Karvinen 2023: Run Salt Command Locally https://terokarvinen.com/2021/salt-run-command-locally/
