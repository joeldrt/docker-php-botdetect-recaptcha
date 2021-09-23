# docker-compose for run nginx and php containers

## To run

create folder `code` in the root of this project and inside it put all your php app related files

at the root of the project type

```bash
# detach mode
$ docker-compose up -d

# or verbose mode (better for debugging)
$ docker-compose up
```

your php app should be visible on [localhost:8080](localhost:8080)

<p>&nbsp;</p>

## Examample / Recapcha

As an example we can run captcha service. We are going to use the app provided by BotDetect

First we have to download project
https://captcha.com/captcha-download.html

Then we unzip all the content in the `code` folder

<p>&nbsp;</p>

https://captcha.com/react-captcha.html#h-plain-php-backend

The next file should be named `botdetect.xml` and be added in

`/botdetect-captcha-lib/config/`

```xml
<!-- botdetect.xml-->

<?xml version="1.0" encoding="UTF-8"?>
<botdetect xmlns="https://captcha.com/schema/php"
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="https://captcha.com/schema/php
            https://captcha.com/schema/php/botdetect-4.2.5.xsd">

    <captchaStyles>
        <captchaStyle>
            <name>yourFirstCaptchaStyle</name>
            <userInputID>yourFirstCaptchaUserInput</userInputID>
        </captchaStyle>
    </captchaStyles>
</botdetect>
```

We turn on the service by executing

```bash
$ docker-compose up
```

We can view the captcha by visiting next url

http://localhost:8080/botdetect-captcha-lib/simple-botdetect.php?get=html&c=yourFirstCaptchaStyle
