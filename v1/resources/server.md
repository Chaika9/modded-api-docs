# Server Resource

### Server Object

#### Server Structure

| FIELD                     | TYPE     | DESCRIPTION                                                              |
|:--------------------------|:---------|:-------------------------------------------------------------------------|
| id                        | string   | server id                                                                |
| name                      | string   | server name (2-25 characters, excluding trailing and leading whitespace) |
| description               | string   | the description of a server (0-1024 characters)                          |
| bannerId                  | integer  | banner id                                                                |
| ownerId                   | string   | id of owner                                                              |
| type                      | string   | [server type](#server-type)                                              |
| isInNetwork               | boolean  | true if the server is in modded network                                  |
| accessType                | string   | [server Access Type](#server-access-type)                                |
| status                    | string   | approximate number of online players in this server                      |
| onlinePlayers             | integer  | approximate number of online players in this server                      |
| isExpired                 | boolean  | this server is expired                                                   |
| expireTime                | long     | server expiration date (UNIX time)                                       |

#### Server Type

| VALUE   | NAME          |
|:--------|:--------------|
| STARTER | Starter       |
| EXPERT  | Expert        |
| PRO     | Professionnel |

#### Server Access Type

| VALUE     | DESCRIPTION                                        |
|:----------|:---------------------------------------------------|
| OFFICIAL  | Modded Official server                             |
| PRIVATE   | Access is restricted to only members of the server |
| PUBLIC    | Access is unrestricted                             |

#### Example Server

```json
{
  "id": "bb577b99-474a-43df-bc28-aac79d8b757f:24d60409-6e96-42e6-9650-fec92a2a6986",
  "name": "Modded Server",
  "description": "This is a modded server!",
  "bannerId": 0,
  "ownerId": "bb577b99-474a-43df-bc28-aac79d8b757f",
  "type": "PRO",
  "isInNetwork": true,
  "accessType": "PRIVATE",
  "status": "CLOSE",
  "isExpired": false,
  "expireTime": 1662659768000
}
```
