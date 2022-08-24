# Server Resource

### Server Object

#### Server Structure

| FIELD                     | TYPE     | DESCRIPTION                                                                                                                      |
|:--------------------------|:---------|:---------------------------------------------------------------------------------------------------------------------------------|
| id                        | string   | server id                                                                                                                        |
| name                      | string   | server name (2-25 characters, excluding trailing and leading whitespace)                                                         |
| description               | string   | the description of a server (0-1024 characters)                                                                                  |
| banner                    | integer  | banner id                                                                                                                        |
| owner?                    | boolean  | true if the user is the owner of the server                                                                                      |
| owner_id                  | ?string  | id of owner                                                                                                                      |
| type                      | integer  | [server type](#server-type)                                                                                                      |
| network                   | boolean  | true if the server is in modded network                                                                                          |
| access_type               | integer  | [server Access Type](#server-access-type)                                                                                        |
| approximate_online_count? | integer  | approximate number of online players in this server, returned from the `GET /servers/<id>` endpoint when `with_counts` is `true` |
| nsfw_level                | integer  | [server NSFW level](#server-nsfw-level)                                                                                          |
| expired                   | boolean  | true if this server is expired                                                                                                   |
| expire_time               | long     | server expiration date (UNIX time)                                                                                               |

#### Server Type

| VALUE | NAME          |
|:------|:--------------|
| 0     | Starter       |
| 1     | Expert        |
| 2     | Professionnel |

#### Server Access Type

| VALUE | NAME      | DESCRIPTION                                                             |
|:------|:----------|:------------------------------------------------------------------------|
| 0     | OFFICIAL  | Modded Official server                                                  |
| 1     | PRIVATE   | Access is restricted to only members of the server                      |
| 2     | PUBLIC    | Access is unrestricted                                                  |
| 3     | PROTECTED | Access is restricted to only members of the server and access by portal |

#### Server NSFW Level

| LEVEL          | VALUE   |
|:---------------|:--------|
| DEFAULT        | 0       |
| AGE_RESTRICTED | 1       |

#### Example Server

```json
{
  "id": "0bfbf8a421de41d5b9e30be141543024:5ed828be1f04491188d95c565dc436e3",
  "name": "Modded Server",
  "description": "This is a modded server!",
  "banner": 0,
  "owner_id": "0bfbf8a421de41d5b9e30be141543024",
  "type": 2,
  "network": true,
  "access_type": 1,
  "nsfw_level": 0,
  "expired": false,
  "expire_time": 1662659768000
}
```

### Server Member Object

#### Server Member Structure

| FIELD                     | TYPE                                           | DESCRIPTION                           |
|:--------------------------|:-----------------------------------------------|:--------------------------------------|
| user?                     | [user](/v2/resources/user?id=user-object) object | the user this server member represents |

## Get Server
**GET** `/servers/{server.id}`

Returns the [server](#server-object) object for the given id. If `with_counts` is set to true, this endpoint will also return `approximate_online_count` for the server.

#### Query String Params

| FIELD                     | TYPE     | DESCRIPTION                                                                   |
|:--------------------------|:---------|:------------------------------------------------------------------------------|
| with_counts?              | boolean  | when `true`, will return approximate number of online players for this server |

## Modify Server
**PATCH** `/servers/{server.id}`

Modify a server's settings. Returns the updated [server](#server-object) object on success.

> All parameters to this endpoint are optional

#### JSON Params

| FIELD                     | TYPE     | DESCRIPTION                                                               |
|:--------------------------|:---------|:--------------------------------------------------------------------------|
| id                        | string   | server id                                                                 |
| name                      | string   | server name (2-25 characters, excluding trailing and leading whitespace)  |
| description               | string   | the description of a server (0-1024 characters)                           |
| banner                    | integer  | banner id                                                                 |
| nsfw_level                | integer  | [server NSFW level](#server-nsfw-level)                                   |

## Start Server
**POST** `/servers/{server.id}/start`

Start a server. Returns `204 No Content` on success.

## Stop Server
**POST** `/servers/{server.id}/stop`

Stop a server. Returns `204 No Content` on success.

## Reset Server
**POST** `/servers/{server.id}/reset`

Reset a server (is **permanently**). Returns `204 No Content` on success.

## Get Server Member
**GET** `/servers/{server.id}/members/{user.id}`

Returns a server [member](#server-member-object) object for the specified user.

## List Members
**GET** `/servers/{server.id}/members`

Returns a list of server [member](#server-member-object) objects that are members of the server.

> All parameters to this endpoint are optional

#### Query String Params

| FIELD                     | TYPE     | DESCRIPTION                              | DEFAULT |
|:--------------------------|:---------|:-----------------------------------------|:--------|
| limit                     | integer  | max number of members to return (1-50)   | 1       |
| after                     | string   | the highest user id in the previous page | 0       |

## Add Server Member
**PUT** `/servers/{server.id}/members/{user.id}`

Adds a user to the server. Returns a `201 Created` with the server [member](#server-member-object) as the body, or `204 No Content` if the user is already a member of the server.

## Remove Server Member
**DELETE** `/servers/{server.id}/members/{user.id}`

Remove a member from a server. Returns a `204 No Content` on success.
