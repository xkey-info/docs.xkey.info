# XKeyScore API Docs

1. [Getting Started](#1-getting-started)
2. [Authentication](#2-authentication)
3. [Endpoints](#3-endpoints)
    - [3.1 Email Search API](#31-email-search-api)
    - [3.2 Person Search API](#32-person-search-api)
    - [3.3 Online Activity API](#33-online-activity-api)
4. [Code Examples](#4-code-examples)
    - [4.1 JavaScript](#41-javascript)
    - [4.2 Python](#42-python)

# 1. Getting Started

Welcome to our API documentation! In this guide, you will find information on how to authenticate, use, and interact with our API endpoints.
If you'd rather not write your own code, or want some code to start, you can check out some of our examples here or use popular third party software!

# 2. Authentication

For regular subscribers of XKeyScore, you'll need to include an 'Auth' header with your activation code for authentication. Activation codes generated within the past year should start with "xks", followed by 25 random characters.

**Normal API Users**

```shell
Auth: xks[...]
```

**Paid API Users**

```shell
Authorization: Bearer API_KEY_HERE
```

# 3. Endpoints

Our API provides the following endpoints:

## 3.1 Email Search API

This endpoint lets you search the XKeyScore database for leaked information on a given email.

**Required Parameters:**

* email (string: email address)

**Optional Parameters:**

* limit (int, default: 100)
* wildcard (boolean: true/false)


**Curl**

```shell
curl --request POST --url https://api.xkey.info/email/search \
--header "Auth: ACTIVATION_CODE" --header "Content-Type: application/json" \
--data '{"email":"example@gmail.com", "wildcard": false}'
```

**Request**

```shell
POST https://api.xkey.info/email/search
Content-Type: application/json
Auth: ACTIVATION_CODE
{
  "email": "example@gmail.com",
  "wildcard": false
}
```

**Example Response**

```js
{
  "count": 127,
  "time": 145
  "results": [
    {
      "address": "1813 w 64th st, Los Angeles, CA - 90047",
      "database_name": "XKeyScore Private SSNs",
      "date_added": "Fri, 04 Aug 2023 00:00:00 GMT",
      "date_leaked": "0000-00-00",
      "discord_tag": null,
      "discord_uid": null,
      "email_address": "ernest.mixon@yahoo.com",
      "fivem_uid": null,
      "full_name": "Ernest Mixon",
      "id": 359453,
      "ip_address": null,
      "is_private": true,
      "minecraft_uuid": null,
      "other_info": {
        "Bank_Account": "157139753",
        "Bank_Name": "CITIBANK FSB",
        "Country": "USA",
        "DOB": null,
        "Drivers_License_Number": "662",
        "Drivers_License_State": "CA",
        "SSN": "570719870"
      },
      "password_cracked": null,
      "password_hash": null,
      "phone_number": "3238196278",
      "skype_uid": null,
      "steam_name": null,
      "steam_uid": null,
      "username": null,
      "xbl_name": null,
      "xbl_uid": null
    }
  ], /* (...) */
}
```

## 3.2 Person Search API

This endpoint lets you search XKeyScore via full name, address, social security number or phone number.

**Semi-Optional Parameters:**
*one of these is required*

* ssn (string: `123-45-6789` would be `123456789`)
* name (string, `John Doe`)
* phone (string: `+1 (444) 123 4567` would be `4441234567`)

**Curl**

```shell
curl --request POST --url https://api.xkey.info/person/search \
--header "Auth: ACTIVATION_CODE" --header "Content-Type: application/json" \
--data '{ "phone": 9166441615 }'
```

**Request**

```shell
POST https://api.xkey.info/person/search
Content-Type: application/json
Auth: ACTIVATION_CODE
{
  "phone": 9166441615
}
```

**Example Response**

```js
{
  "count": 127,
  "time": 531
  "results": [
    {
      "address": "300 saint lucia way, Lincoln, CA - 95648",
      "date_added": "Fri, 04 Aug 2023 00:00:00 GMT",
      "date_leaked": "0000-00-00",
      "discord_tag": null,
      "discord_uid": null,
      "email_address": "smvpmicks@aol.com",
      "fivem_uid": null,
      "full_name": "Mickey Limon",
      "id": 268631,
      "ip_address": null,
      "is_private": true,
      "minecraft_uuid": null,
      "other_info": {
        "Bank_Account": "1920000000000",
        "Bank_Name": "ARVEST BANK-FAYETTEVILLE",
        "Country": "USA",
        "DOB": "1979-08-18 00:00:00",
        "Drivers_License_Number": "124187721",
        "Drivers_License_State": "CA",
        "SSN": "544322302"
      },
      "password_cracked": null,
      "password_hash": null,
      "phone_number": "9166441615",
      "skype_uid": null,
      "steam_name": null,
      "steam_uid": null,
      "username": null,
      "xbl_name": null,
      "xbl_uid": null
    }
  ], /* (...) */
}
```

## 3.3 Online Activity API

**Semi-Optional Parameters:**
*one of these is required*

* email (string: `example@example.com`)
* username (string, `johndoe123`)
* discordId (string: `793648128447742023`)
* discordUsername (string: `username#0000` or `username`)

**Curl**

```shell
curl --request POST --url https://api.xkey.info/online/search \
--header "Auth: ACTIVATION_CODE" --header "Content-Type: application/json" \
--data '{"email": "example@example.com", "username": "johndoe123", "discordId": "793648128447742023", "discordUsername": "username#0000"}'
```

**Request**

```shell
POST https://api.xkey.info/online/search
Content-Type: application/json
Auth: ACTIVATION_CODE
{
  {
    "email": "testing1@gmail.com", 
    "username": "testing1", 
    "discordId": "793648128447742023", 
    "discordUsername": "username#0000"
  }
}
```

**Example Response**

```js
{
  "accountsFound": 3189,
	"module": {
		"digdeepr": [
      "_souce": "username",
      "data": {
        {
          "_data": [
            { "followers": "148" },
            { "following": "0" }
          ],
          "_profilePicture": "//cdn1.picuki.com/hosted-by-instagram/q/0exhNuNYnjBcaS3SYdxKjf8V0fNwWgxSZ60STLepjSVmIR1vLHOapZA0mpCj4yRwKwVlASudYztk7IMvU1xYZFF+OULfTrWITjdc7KiZXYCg1zFg9JFokbc9KnYbZnSp9cQuOzjYMTIfQcYeDJT96uZUq6SwKGNb4i7Ra+JDhWccsseqUaxm3pAn8KOKzkjq5sIOKj518Wo1eRhundPZlTUCX6nqYdpA9rckReYW3uY91N39mgvsV2gudjNfNT21m5vgvc8ipAKudzY6pjbqEu8yKHMdgFazsik6t5VzsbL3Io9j1eo64pbNdDUlRm45nQRst6K7lATBYi77kkBRwTeel||W+eqN29qrRI9CwQ8||8+GzyWavzOuIZcHI||B||LOZw||bLuePDuRpt7JBLcwaw1e29zWTV5Lzmhx0WWMepxevVbFWBcKTx5C3+3ONgGnfpgI9.jpeg",
          "_source": "Instagram"
        },
        {
          "_data": [
            { "name": "Leo" },
            { "bio": "Leo | mountaineer" },
            { "followers": "0" },
            { "following": "9" }
          ],
          "_profilePicture": "//i.pinimg.com/280x280_RS/f3/87/39/f38739be287ec34bb15a50266a1a8006.jpg",
          "_source": "Pinterest"
        },
        {
          "_data": [
            { "nickname": "testing1" }
          ],
          "_profilePicture": "//avatars.githubusercontent.com/u/1868536?v=4?s=400",
          "_source": "Github"
        },
      }, /* (...) */
		],
		"duolingo": {
      "_source": "emailAddress",
      "data": {
        "bio": "test user!",
        "creationDate": 1611524852,
        "emailVerified": false,
        "hasFacebookId": false,
        "hasGoogleId": false,
        "hasPhoneNumber": false,
        "id": 727911321,
        "name": "john doe",
        "picture": "//simg-ssl.duolingo.com/avatar/default_2",
        "username": "testing206300"
      }
		},
		"mastodon": {
      "_source": "emailAddress",
      "data": {
        "accountEmail": "testing1@staging.mastodon.social",
        "created": "2022-02-25T00:00:00.000Z",
        "displayName": null,
        "locked": false,
        "note": "<p>Test Account!</p>",
        "username": "testing1"
      }
		}, /* (...) */
	}
}
```

# 4. Code Examples

Here are some examples on how to use our API:

## 4.1 JavaScript

Very simple code example showing the usage of XKeyScore's API with JavaScript.

**Requirements**

If you're using a NodeJS version older than NodeJS 18, you'll need to run:

```
> npm install node-fetch
```

And then add the following line to the very top of the file:

```js
const fetch = (...args) => import('node-fetch').then(({default: fetch}) => fetch(...args));
```

**Code**

```js
const xksAuth = 'API_KEY_HERE'
const xksAPI = 'https://api.xkey.info/'

// Re-usable function for the xks API
const sendRequest = async function (url, body = false) {
  const options = {
    method: (body) ? 'POST' : 'GET',
    headers: { 
      'Auth': xksAuth,
      'Content-Type': 'application/json',
    },
    body: (body) ? JSON.stringify(body) : null
  }
  const response = await fetch(xksAPI + url, options);
  return await response.json();
}

sendRequest('email/search', {
  email: "example@gmail.com",
  wildcard: false
}).then(response => console.log(response))

sendRequest('person/search', {
  phone: "9166441615",
  ssn: "000000000"
}).then(response => console.log(response))

sendRequest('online/search', {
  username: "testing1",
  email: "testing1@gmail.com"
}).then(response => console.log(response))
```

**Usage**

To use the code, add it to a file named "xks.js" and run this command in your terminal:

```
> node xks.js
```

## 4.2 Python

Very simple code example showing the usage of xks's API with Python.

**Requirements**

You'll need the httpx module to run this example, run this command in your terminal:

```
> python3 -m pip install httpx
```

**Code**

```python
import httpx

xks_auth = 'API_KEY_HERE'
xks_api = 'https://api.xkey.info/'

async def send_request(url, data=None):
    headers = {
        'Auth': xks_auth,
        'Content-Type': 'application/json',
    }
    async with httpx.AsyncClient() as client:
        if data:
            response = await client.post(xks_api + url, json=data, headers=headers)
        else:
            response = await client.get(xks_api + url, headers=headers)
        response_data = response.json()
        return response_data

async def main():
    email_response = await send_request('email/search', {
        'email': 'example@gmail.com',
        'wildcard': False
    })
    print(email_response)

    person_response = await send_request('person/search', {
        'phone': '9166441615',
        'ssn': '000000000'
    })
    print(person_response)

    online_response = await send_request('online/search', {
        'username': 'testing1',
        'email': 'testing1@gmail.com'
    })
    print(online_response)

if __name__ == '__main__':
    import asyncio
    asyncio.run(main())
```

**Usage**

To use the code, add it to a file named "xks.py" and run this command in your terminal:

```
> python3 xks.py
```
