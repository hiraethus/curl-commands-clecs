# Dogfen API [Clecs.cymru](http://clecs.cymru)

## Global variables

Er mwyn defnyddio'r gorchmynion isod, mae'n rhaid gosod y global variables yma:

    export CLECS_USERNAME=eich@ebost.com
    export CLECS_PASSWORD=eich_CyfriNAIR


## Logio i mewn

* **URL**

    /Token

* **Method**

    `POST`

* **URL Params**

    None

* **Data Params**

    `username=[string]`
    `password=[string]`
    `grant_type=password`

* **Success Response:**

    * **Code:** 200 <br />
      **Content:**

      ```json
	  {
	      "access_token": "EXlf...",
	      "token_type": "bearer",
	      "expires_in": "2591999",
	      "userName": "enw_defnyddiwr",
	      "userImage": "https://clecs.blob.core.windows.net.profileimages/***.png",
	      ".issued": "Sun, 26 Jan 1999 08:05:12 GMT"
	  }
	  ```

* **Esiampl `curl`**

    ```bash
    curl -X POST https://www.clecs.cymru/Token \
        -H "Content-Type: application/x-www-form-urlencoded" \
        --data "username=$CLECS_USERNAME" \
        --data "password=$CLECS_PASSWORD" \
        --data "grant_type=password"
    ```

## Postio clec i eich ffrwd

* **URL**

    /api/Posting/PostAPost

* **Method**

    `POST`

* **URL Params**

    None

* **Data Params**

    `PostText=[string]` - cyfyngu i 200 llythyren

* **Success Response:**

    * **Code:** 200 <br />

* **Esiampl `curl`**

    ```bash
    curl -X POST https://www.clecs.cymru/api/Posting/PostAPost \
        -H "Content-Type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer $CLECS_TOKEN" \
        --data "PostText=Lorem ipsum dolor sit amet"
    ```

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

## /api/Posting/FindUsers

Darganfod defnyddwyr

### GET
    export END_DEFNYDDIWR=Clecs
    curl -X GET "https://www.clecs.cymru/api/Posting/FindUsers?toFind=$END_DEFNYDDIWR" \
        -H "Content-Type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer $CLECS_TOKEN"

## api/Posting/SearchLoadMore

Chwilio am postiadau

    export TESTUN_POST="Lorem+ipsum+dolor+sit+amet"
    curl -X GET "https://www.clecs.cymru/api/Posting/SearchLoadMore?toFind=$TESTUN_POST&idLast=0" \
        -H "Content-Type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer $CLECS_TOKEN"



