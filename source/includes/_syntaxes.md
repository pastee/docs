# Syntaxes

## List Syntaxes

```shell
curl "https://api.paste.ee/v1/syntaxes"
  -H "X-Auth-Token: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
   "syntaxes":[
      {
         "id":1,
         "short":"autodetect",
         "name":"Auto Detect"
      },
      {
         "id":2,
         "short":"text",
         "name":"Text"
      }
   ],
   "success":true
}
```

This endpoint lists available syntaxes.

### HTTP Request

`GET https://api.paste.ee/v1/syntaxes`

## Get syntax

```shell
curl "https://api.paste.ee/v1/syntaxes/<id>"
  -H "X-Auth-Token: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
   "syntax":{
     "id": "1",
     "short": "text",
     "name": "Text"
   },
   "success":true
}
```

This endpoint returns information about a syntax.

### HTTP Request

`GET https://api.paste.ee/v1/syntaxes/<id>`
