# API Reference

Modded's API is a HTTPS/REST API.

#### Base URL

```
https://api.modded.cloud
```

## API Versioning

Modded exposes different versions of our API. You should specify which version to use by including it in the request path like `https://api.modded.cloud/v{version_number}`. Omitting the version number from the route will route requests to the current default version (marked below).

#### API Versions

| VERSION | STATUS        | DEFAULT |
|:--------|:--------------|:--------|
| 2       | Not Available |         |
| 1       | Available     | ✓       |

## Error Messages

> Only for Modded API v2

#### Request Error

```
{
  "code": 50035,
  "message": "Invalid form body (returned for both application/json), or invalid Content-Type provided"
}
```
