# Scammer Number API Docs

### Introduction
The Scammer Number API allows for:
* GET scammer numbers
* POST scammer numbers numbers **<sup>1</sup>for review**
* GET reported scammer numbers
* PUT reporting scammer numbers **<sup>1</sup>for review** `//TODO: DO PUT`

### GET Scammer Numbers

This endpoint allows you to fetch a list of scammer numbers.

`GET https://api.collectivedev.com/numbers/`
```json
{
    "status": {
        "code": 200,
        "success": true,
        "message": "Successfully fetched numbers."
    },
    "numbers": [
        {
            "name": "John Doe",
            "country": 1,
            "number": 1234567890,
            "dateAdded": "1970-01-01T00:00:00.000Z",
            "id": "a98db973kwl8xp1lz94kjf0b"
        }
    ]
}
```

### POST Scammer Numbers

This endpoint allows you to post your scammer numbers for review.

In the body, you need to include:
```json
{
    "number": 1234567890,
    "country": 1,
    "name": "John Doe"
}
```

`POST https://api.collectivedev.com/numbers/add`
```json
{
    "status": {
        "code": 201,
        "success": true,
        "message": "Successfully added number for review."
    },
    "request": "+1 1234567890"
}
```

Be sure to format the body correctly or you will get:

```json
{
    "status": {
        "code": 400,
        "success": false,
        "message": "Missing or invalid request body. Please correct your request and try again."
    }
}
```

### GET Reported Scammer Numbers

This endpoint allows you to fetch a list of reported scammer numbers.

`GET https://api.collectivedev.com/numbers/report/`
```json
{
    "status": {
        "code": 200,
        "success": true,
        "message": "Successfully fetched reported numbers."
    },
    "numbers": [
        {
            "name": "John Doe",
            "country": 1,
            "number": 1234567890,
            "dateAdded": "1970-01-01T00:00:00.000Z",
            "id": "a98db973kwl8xp1lz94kjf0b"
        }
    ]
}
```

### PUT Report Scammer Numbers (Not Done)

This endpoint allows you to report other scammer numbers for review.

`PUT https://api.collectivedev.com/numbers/report/:id`
```json
{
    "status": {
        "code": 201,
        "success": true,
        "message": "Successfully reported number id a98db973kwl8xp1lz94kjf0b and will be reviewed."
    }
}
```

Be sure to include a proper ID or you will get:

```json
{
    "status": {
        "code": 400,
        "success": false,
        "message": "Missing or invalid request body. Please correct your request and try again."
    }
}
```

<sup>1</sup>Review process exists to verify scam numbers.
