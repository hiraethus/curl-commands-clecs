# Sut i ddefnyddio ```Curl``` i weithio gyda [Clecs.cymru](http://clecs.cymru)

## Global variables

Er mwyn defnyddio'r gorchmynion isod, mae'n rhaid gosod y global variables yma:

    export CLECS_USERNAME=eich@ebost.com
    export CLECS_PASSWORD=eich_CyfriNAIR


## /Token

### POST

Anablu logio i mewn

#### Gorchymyn ```curl```
    curl -X POST https://www.clecs.cymru/Token \
        -H "Content-Type: application/x-www-form-urlencoded" \
        --data "username=$CLECS_USERNAME" \
        --data "password=$CLECS_PASSWORD" \
        --data "grant_type=password"
