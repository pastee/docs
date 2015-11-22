# Users

## User/key information

```shell
curl "https://api.paste.ee/v1/users/info"
  -H "X-Auth-Token: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "type":"UserApplication"
}
```

This endpoint will return information about the current api key.

### HTTP Request

`GET https://api.paste.ee/v1/users/info`

## User Authentication

```shell
curl "https://api.paste.ee/v1/users/authenticate"
  -H "X-Auth-Token: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "key": "<new or existing user application key>"
}
```

This endpoint authenticates users for UserApplications, allowing further api functionality like listing pastes and submitting them while attaching them to the user's account.

You can also use the url `https://paste.ee/account/api/authorize/<application key>` to have the user generate a token themselves.

### HTTP Request

`POST https://api.paste.ee/v1/users/authenticate`

### Request Body

Parameter | Description
--------- | ------------
username | The user's username.
password | The user's password.
