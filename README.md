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


## /api/Posting/PostAPost

### POST

Postio post ar eich wal

#### Gorchymyn ```curl```
    curl -X POST https://www.clecs.cymru/api/Posting/PostAPost \
        -H "Content-Type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer $CLECS_TOKEN" \
        --data "PostText=Lorem ipsum dolor sit amet"

## /api/Posting/DeletePost

Dileu post oddi ar eich wal

### POST

    export RHIFYN_POST=123
    
    curl -X POST https://www.clecs.cymru/api/Posting/DeletePost \
        -H "Content-Type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer $CLECS_TOKEN" \
        --data "id=$RHIFYN_POST"


## /api/Posting/PostASmile

Postio gwen i bost wal rhywun

### POST
    curl -X POST https://www.clecs.cymru/api/Posting/PostASmile \
        -H "Content-Type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer $CLECS_TOKEN" \
        --data "PostId=$RHIFYN_POST"

