# Integrando Alexa en Home Assistant

## Esta no es una guía paso a paso. Para obtener indicaciones paso a paso tienes que ver el vídeo. Aquí sólo se presentan enlaces o configuraciones que aparecen en el vídeo.

Vídeo disponible en [Domótica Fácil](http://https://www.youtube.com/c/domoticafacilconjota "Domótica Fácil"): [youtube.com](https://www.youtube.com/watch?v=3b_UBIt8Z3M "youtube.com")

**Consola de desarrollador de Amazon**
https://developer.amazon.com/es/

**Centro de desarrolladores de AWS**
https://aws.amazon.com/es/developer/
***
> Una vez dentro de la consola para desarrolladores de AWS es importante seleccionar la localización correcta para el centro de datos. En el caso de España hay que utilizar Europa (Irlanda). Si estáis en América, podéis elegir una localización que os quede cerca.

***

**Consola de desarrollador de Alexa**
https://developer.amazon.com/alexa/console/ask

***
> En la consola de desarrollador de AWS hay que buscar por:
> "IAM"

***
> El nombre del ROL que yo he utilizado es: 
> "AWSLambdaBasicExecutionRole-HomeAssistant"

***
> En la consola de desarrollador de AWS hay que buscar por:
> "Lambda"

***
> Nombre de la función Lambda:
> "homeassistantAlexa"

***

**Código de la función Lambda:** [aquí](https://gist.github.com/matt2005/744b5ef548cc13d88d0569eea65f5e5b "aquí")


**Variables de entorno > llaves y valores:**

*BASE_URL* | https://tusubdominio.duckdns.org

*NOT_VERIFY_SSL* | false

*DEBUG* | false

> En Home Assistant añadir la siguiente línea al configuration.yaml:

    alexa: !include alexa.yaml

> En Home Assistant añadir la siguiente línea a alexa.yaml

    smart_home:
      filter:
        include_domains:
          - switch
***

**Código de pruebas (Test) para función Lambda:**
```json
{
  "directive": {
    "header": {
      "namespace": "Alexa.Discovery",
      "name": "Discover",
      "payloadVersion": "3",
      "messageId": "1bd5d003-31b9-476f-ad03-71d471922820"
    },
    "payload": {
      "scope": {
        "type": "BearerToken"
      }
    }
  }
}
```
**Variables de entorno > llave y valor:**

*LONG_LIVED_ACCESS_TOKEN* | generadoenhomeassistant

**Consola de desarrollador de Alexa > Account linking**
> Authorization URI: 

    https://tusubdominio.duckdns.org/auth/authorize

> Access Token URI:

    https://tusubdominio.duckdns.org/auth/token

> Client ID:

- Europa: https://layla.amazon.com/
- Estados Unidos: https://pitangui.amazon.com/
- Japón y Australia: https://alexa.amazon.co.jp/

> Your Secret:

    https://randomkeygen.com/

> Scope:

    smart_home

**Configuración de puertos en el Router**

> Nombre del servicio: **Alexa**

Puerto externo: **443**

Puerto interno: **8123** (o el que estéis utilizando para Home Assistant)

IP: **ip.de.la.raspi**

Protocolo: **TCP y UDP**
