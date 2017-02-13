# Pastes

## List pastes

```shell
curl "https://api.paste.ee/v1/pastes"
  -H "X-Auth-Token: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "total": 0,
  "per_page": 0,
  "current_page": 0,
  "last_page": 0,
  "next_page_url": "string",
  "prev_page_url": "string",
  "from": 0,
  "to": 0,
  "data": [
    {
      "id": "string",
      "description": "string",
      "views": 0,
      "created_at": "string",
      "sections": [
        {
          "name": "string",
          "syntax": "string",
          "contents": "string"
        }
      ]
    }
  ]
}
```

This endpoint retrieves all pastes.

You can traverse pages by using `next_page_url` and `prev_page_url`. Please, when listing all pastes in an account, increase items per page to a reasonable amount to minimize requests.

<aside class="warning">If you're not using a user application key, you will get a 403 Forbidden response when trying to list pastes.</aside>

### HTTP Request

`GET https://api.paste.ee/v1/pastes`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
perpage | 25 | Items to return per page.
page | 1 | Page number

## Submit a new paste

```shell
curl "https://api.paste.ee/v1/pastes"
  -X "POST"
  -H "Content-Type: application/json"
  -H "X-Auth-Token: meowmeowmeow"
  -D '{"description":"test","sections":[{"name":"Section1","syntax":"autodetect","contents":"Testing!"}]}'
```

> The above command returns JSON structured like this:

```json
{
  "id": "<id>",
  "link": "https://paste.ee/p/<id>"
}
```

<aside class="warning">The syntax field is only linked to the short identifier given to syntaxes. More information [here](#_syntaxes).</aside>

This endpoint submits a paste to the database.

### HTTP Request

`POST https://api.paste.ee/v1/pastes`

Accepts data either as `application/x-www-form-urlencoded` or `application/json`

### Request Body

Parameter | Optional | Description
--------- | -------- | -----------
encrypted | true | Whether the paste should be treated as encrypted. Default: false
description | true | Overall paste description.
sections  | false | Array of sections.

### Sections

Key | Optional | Description
--- | -------- | -----------
name | true | Section name. Default: New Paste 1-10
syntax | true | Section syntax. Default: autodetect
contents | false | Section contents

## Submit a new paste with a multipart request/files

```shell
curl "https://api.paste.ee/v1/pastes"
  -X "POST"
  -H "X-Auth-Token: meowmeowmeow"
  -F "files[]=@test.txt"
  -F "names[]=test.md"
  -F "syntaxes[]=markdown"
  ```

> The above command returns JSON structured like this:

```json
{
  "id": "<id>",
  "link": "https://paste.ee/p/<id>"
}
```

<aside class="warning">The syntax field is only linked to the short identifier given to syntaxes. More information <a href="https://beta.paste.ee/wiki/API:v1:Syntaxes">here</a>.</aside>

### HTTP Request

`POST https://api.paste.ee/v1/pastes/file`

### Request Body

Parameter | Optional | Description
--------- | -------- | -----------
files[] | false | Array of files
names[] | true | Array of names, can also specify names for only specific files;
syntaxes[] | true | Array of syntaxes, can also specify syntaxes for only specific files.

## Get a paste

```shell
curl "https://api.paste.ee/v1/pastes/<id>"
  -H "X-Auth-Token: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "success":true,
  "paste": {
    "id":"<id>",
    "encrypted":false,
    "description":"",
    "views":123,
    "created_at":"2015-11-10 22:15:41",
    "expires_at":null,
    "sections":[
      {
        "id":0,
        "syntax":"autodetect",
        "name":"New Paste",
        "contents":"Something meow"
      }
    ]
  }
}
```

This endpoint gets a paste and it's contents.

### HTTP Request

`GET https://api.paste.ee/v1/pastes/<id>`

### Path parameters

Parameter | Description
--------- | -----------
id | The paste identifier.

## Remove a paste

```shell
curl "https://api.paste.ee/v1/pastes/<id>"
  -X "DELETE"
  -H "X-Auth-Token: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "success":true
}
```

This endpoint deletes a paste permanently.

### HTTP Request

`DELETE https://api.paste.ee/v1/pastes/<id>`

### Path parameters

Parameter | Description
--------- | -----------
id | The paste identifier.
