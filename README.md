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

## Dileu clec

* **URL**

    /api/Posting/DeletePost

* **Method**

    `POST`

* **URL Params**

    None

* **Data Params**

    `id=[integer]`

* **Success Response:**

    * **Code:** 200 <br />


* **Esiampl `curl`**

    ```bash
    export RHIFYN_POST=123
    
    curl -X POST https://www.clecs.cymru/api/Posting/DeletePost \
        -H "Content-Type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer $CLECS_TOKEN" \
        --data "id=$RHIFYN_POST"
    ```

## Postio gwen ar glec rhywun

* **URL**

    /api/Posting/PostASmile

* **Method**

    `POST`

* **URL Params**

    None

* **Data Params**

    `PostId=[integer]`

* **Success Response:**

    * **Code:** 200

* **Esiampl `curl`**

    ```bash
    curl -X POST https://www.clecs.cymru/api/Posting/PostASmile \
        -H "Content-Type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer $CLECS_TOKEN" \
        --data "PostId=$RHIFYN_POST"
    ```

## Darganfod defnyddwyr

* **URL**

    /api/Posting/FindUsers


* **Method**

    `GET`

* **URL Params**

    `toFind=[string]`

* **Data Params**

    None

* **Success Response**

    * **Code:** 200 <br />
      **Content:**

      ```json
      [
          {
	      "username": "CymorthClecs",
	      "namey": "Cymorth Clecs",
	      "avatar": "https://clecs.blob.core.windows.net/profileimages/**.png",
	      "profileUrl": "/Home/ProfilePage/CymorthClecs",
	      "followedBy": "60"
          },
	  {
	    "username": ...
	  }
      ]
      ```

    * **Esiampl `curl`**

    ```bash
    export END_DEFNYDDIWR=Clecs

    curl -X GET "https://www.clecs.cymru/api/Posting/FindUsers?toFind=$ENW_DEFNYDDIWR" \
        -H "Content-Type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer $CLECS_TOKEN"
    ```


## Chwilio am postiadau clecs

* **URL**

    /api/Posting/SearchLoadMore

* **Method**

    `GET`

* **URL Params**

    `toFind=[string]`

* **Data Params**

    None

* **Success Response:**

    * **Code:** 200 <br />
      **Content:**

      ```json
      [
          {
	      "postId": 1483,
	      "transactionAgainstPostId": 1483,
	      "myPost": true,
	      "postText": "Lorem ipsum dolor sit amet",
	      "postTextOriginal": "Lorem ipsum dolor sit amet",
	      "dateCreated": "7d",
	      "createdByUsername": "cymrobalch",
	      "createdByName": "Meical Jones",
              "createdByAvatar": "https://clecs.blob.core.windows.net/profileimages/***.png",
	      "profileUrl":"/cymrobalch",
	      "commentsQty": "0",
	      "smileQty": "5",
	      "sadQty": "0",
	      "smileSadNothing": 0,
	      "containsImage": false,
	      "imageUrl": null,
	      "quote": false,
	      "quotedPostId": null,
	      "share": false,
	      "sharereUsername": null
	  }
      ]
      ```

* **Esiampl `curl**

    ```bash
    export TESTUN_POST="Lorem+ipsum+dolor+sit+amet"
    
    curl -X GET "https://www.clecs.cymru/api/Posting/SearchLoadMore?toFind=$TESTUN_POST&idLast=0" \
        -H "Content-Type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer $CLECS_TOKEN"
    ```
