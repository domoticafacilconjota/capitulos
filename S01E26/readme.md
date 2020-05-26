# Integrando Alexa en Home Assistant (Segunda parte)

## Esta no es una guía paso a paso. Para obtener indicaciones paso a paso tienes que ver el vídeo. Aquí sólo se presentan enlaces o configuraciones que aparecen en el vídeo.

Vídeo disponible en [Domótica Fácil](http://https://www.youtube.com/c/domoticafacilconjota "Domótica Fácil"): [youtube.com](https://www.youtube.com/watch?v=Es6H_ZGpPHQ "youtube.com")


**Códigos de idioma aceptados por Alexa**
    
    es-ES Spanish (ES)
    
    es-MX Spanish (MX)
    
    de-DE German (DE)
    
    en-AU English (AU)
    
    en-CA English (CA)
    
    en-GB English (UK)
    
    en-IN English (IN)
    
    en-US English (US)
    
    es-US Spanish (US)
    
    fr-CA French (CA)
    
    fr-FR French (FR)
    
    hi-IN Hindi (IN)
    
    it-IT Italian (IT)
    
    ja-JP Japanese (JP)
    
    pt-BR Portuguese (BR)


**URL's para el Endpoint**
- America: https://api.amazonalexa.com/v3/events
- Europa: https://api.eu.amazonalexa.com/v3/events
- Oriente: https://api.fe.amazonalexa.com/v3/events

***
**Client ID & Secret:**
https://youtu.be/3b_UBIt8Z3M?t=938

**Generador de entity_config:** [aquí]
https://jsfiddle.net/domojota/jybvzdk3/latest/


**Configuración de ejemplo para alexa.yaml:**
```yaml
smart_home:
  locale: es-ES
  endpoint: https://api.eu.amazonalexa.com/v3/events
  client_id: !secret amazon_client_id
  client_secret: !secret amazon_client_secret
  filter:
    include_domains:
      - switch
      - light
      - groups
    exclude_entities:
      - switch.regleta_pc_00_00_01_oficina_interior
  entity_config:
    switch.regleta_pc_00_00_01_oficina_interior:
      name: "Regleta de cargadores de la oficina"
      description: "Una descripción completamente innecesaria..."
      display_categories: SMARTPLUG

```

**Configuración de ejemplo para alexa.yam ALTERNATIVA**
> Sólo se puede usar una de las dos configuraciones /!\

```yaml
smart_home:
  locale: es-ES
  endpoint: https://api.eu.amazonalexa.com/v3/events
  client_id: !secret amazon_client_id
  client_secret: !secret amazon_client_secret
  filter:
    exclude_domains:
      - input_boolean
    include_entities:
      - input_boolean.regleta_pc_00_00_01_oficina_interior
  entity_config:
    input_boolean.regleta_pc_00_00_01_oficina_interior:
      name: "Regleta de cargadores de la oficina"
      description: "Una descripción completamente innecesaria..."
      display_categories: SMARTPLUG
```

