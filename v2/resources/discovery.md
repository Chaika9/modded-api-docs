# Discovery Resource

#### Server Categorie

| VALUE | NAME      | DESCRIPTION            |
|:------|:----------|:-----------------------|
| 0     | OFFICIAL  | Modded Official server |
| 1     | PUBLIC    | Public server          |

## Get Servers Discovery
**GET** `/discoverable-servers`

Returns a list of partial [server](/resources/server?id=server-object) objects user from the selected category.

#### Query String Params

| FIELD                     | TYPE     | DESCRIPTION                               |
|:--------------------------|:---------|:------------------------------------------|
| categories?               | integer  | the server [categorie](#server-categorie) |

#### Example Partial Server

```json
{
  "id": "5ed828be1f04491188d95c565dc436e3",
  "name": "Onigami Server",
  "description": "This is my modded server!",
  "approximate_online_count": 0
}
