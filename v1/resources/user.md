# Users Resource

### User Object

#### User Structure

| FIELD         | TYPE              | DESCRIPTION |
|:--------------|:------------------|:------------|
| id            | string            | the user's id |
| rank          | string            | the [type of Rank subscription](#premium-types) on a user's account |

#### Premium Types

| VALUE   | NAME    |
|:--------|:--------|
| default | None    |
| goggles | Goggles |
| jetpack | Jetpack |
| chaos   | Chaos   |

#### Example User

```json
{
  "id": "bb577b99-474a-43df-bc28-aac79d8b757f",
  "rank": "chaos"
}
```

## Get User Servers
**POST** `/user/server/list`

Returns a list of servers id's user is a owner of.

> This endpoint returns 200 servers by default, which is the maximum number of servers.

**JSON Params**

| FIELD         | TYPE              | DESCRIPTION    |
|:--------------|:------------------|:---------------|
| sessionId     | jwt               | Modded Session |

## List User Friends
**POST** `/user/server/list/friend`

Returns a list of users id's.

**JSON Params**

| FIELD         | TYPE              | DESCRIPTION    |
|:--------------|:------------------|:---------------|
| sessionId     | jwt               | Modded Session |

## Remove User Friend
**POST** `/user/friend/remove`

Remove user from friends.

**JSON Params**

| FIELD         | TYPE              | DESCRIPTION    |
|:--------------|:------------------|:---------------|
| sessionId     | jwt               | Modded Session |
| targetUsers   | string array      | List of users to be removed from the friends list |

## Request User Friend
**POST** `/user/friend/invite`

Make a friend request to a user.

**JSON Params**

| FIELD         | TYPE              | DESCRIPTION    |
|:--------------|:------------------|:---------------|
| sessionId     | jwt               | Modded Session |
| targetUsers   | string array      | List of users to send a friend request |

## List User Friends Requests
**POST** `/user/friend/pending/list`

Returns a list of users id's that are pending friends requests.

**JSON Params**

| FIELD         | TYPE              | DESCRIPTION    |
|:--------------|:------------------|:---------------|
| sessionId     | jwt               | Modded Session |

## Accept User Friend
**POST** `/user/friend/pending/accept`

Accept a friend request from a user.

**JSON Params**

| FIELD         | TYPE              | DESCRIPTION    |
|:--------------|:------------------|:---------------|
| sessionId     | jwt               | Modded Session |
| targetUsers   | string array      | List of users to accept a friend request |

## Decline User Friend
**POST** `/user/friend/pending/decline`

Decline a friend request from a user.

**JSON Params**

| FIELD         | TYPE              | DESCRIPTION    |
|:--------------|:------------------|:---------------|
| sessionId     | jwt               | Modded Session |
| targetUsers   | string array      | List of users to decline a friend request |

## Clear User Friends Requests
**POST** `/user/friend/pending/clear`

Clear any friend requests.

**JSON Params**

| FIELD         | TYPE              | DESCRIPTION    |
|:--------------|:------------------|:---------------|
| sessionId     | jwt               | Modded Session |
