# Users Resource

### User Object

#### User Structure

| FIELD         | TYPE              | DESCRIPTION                                                         |
|:--------------|:------------------|:--------------------------------------------------------------------|
| id            | string            | the user's id                                                       |
| username      | string            | the user's username (Minecraft username)                            |
| flags?        | integer           | the [flags](#user-flags) on a user's account                        |
| premium_type? | integer           | the [type of Rank subscription](#premium-types) on a user's account |

#### User Flags

| VALUE   | NAME                | DESCRIPTION                |
|:--------|:--------------------|:---------------------------|
| 1 << 0  | STAFF               | Modded Staff               |
| 1 << 1  | PARTNER             | Modded Partner             |
| 1 << 2  | CERTIFIED_MODERATOR | Modded Certified Moderator |

#### Premium Types

| VALUE | NAME    |
|:------|:--------|
| 0     | None    |
| 1     | Goggles |
| 2     | Jetpack |
| 3     | Chaos   |

#### Example User

```json
{
  "id": "bb577b99474a43dfbc28aac79d8b757f",
  "username": "Chaika9",
  "premium_type": 3,
  "flags": 1
}
```

## Get Current User
**GET** `/users/@me`

Returns the [user](#user-object) object of the requester's account.

## Get User
**GET** `/users/{user.id}`

Returns a [user](#user-object) object for a given user ID.

## Modify Current User
**PATCH** `/users/@me`

Modify the requester's user account settings. Returns a [user](#user-object) object on success.

> All parameters to this endpoint are optional.

**JSON Params**

| FIELD         | TYPE              | DESCRIPTION |
|:--------------|:------------------|:------------|
|               |                   |             |

## Get User Servers
**GET** `/users/@me/servers`

Returns a list of partial [server](/resources/server?id=server-object) objects user is a owner of.

#### Example Partial Server

```json
{
  "id": "5ed828be1f04491188d95c565dc436e3",
  "name": "Onigami Server",
  "description": "This is my modded server!"
}
```

> This endpoint returns 200 servers by default, which is the maximum number of servers.
> Therefore, pagination is not needed for integrations that need to get a list of the users' servers.

## List User Friends
**GET** `/users/@me/friends`

Returns a list of [user](#user-object) objects.

## Remove User Friend
**DELETE** `/users/@me/friends/{user.id}`

Remove user from friends. Returns a `204 No Content` on success.

## Request User Friend
**PUT** `/users/{user.id}/friends/requests`

Make a friend request to a user. Returns a `204 No Content` on success.

## List User Friends Requests
**GET** `/users/@me/friends/requests`

Returns a list of [user](#user-object) objects that are pending friends requests.

## Accept User Friend
**PUT** `/users/@me/friends/requests/{user.id}`

Accept a friend request from a user. Returns a `204 No Content` on success.

## Decline User Friend
**DELETE** `/users/@me/friends/requests/{user.id}`

Decline a friend request from a user. Returns a `204 No Content` on success.

## Get User Friends Servers
**GET** `/users/@me/friends/servers`

Returns a list of partial [server](/resources/server?id=server-object) objects user is a access of.

#### Example Partial Server

```json
{
  "id": "5ed828be1f04491188d95c565dc436e3",
  "name": "Ilias Server",
  "description": "May the Goddess Ilias protect you"
}
```

#### Query String Params

| FIELD                     | TYPE     | DESCRIPTION                                     | DEFAULT |
|:--------------------------|:---------|:------------------------------------------------|:--------|
| limit?                    | number   | number of servers to return (up to maximum 200) | 200     |
| before? *                 | string   | consider only servers before given server id    | null    |
| after? *                  | string   | consider only servers after given server id     | null    |

* Provide a server id to `before` and `after` for pagination. Servers will always be returned in ascending order by `server.id`. If both `before` and `after` are provided, only before is respected.
