# Contacts and Contact
The character contacts resource allows an application to both read and write a characters contacts.

## Contacts
### Route
``/characters/<characterID:characterIdType>/contacts/``

### GET
* Cache: 5 minutes
* Scope: `characterContactsRead`

It is important to remember that adding or deleting a contact will not invalidate this cache. It is recommended that so long as you get the proper response code from CREST when you POST a new contact that you update any local cache at least temporarily.

```json
{
	"totalCount_str": "1024",
	"pageCount": 6,
	"items": [
		{
			"standing": 3.5,
			"character": {
				"name": "0men666",
				"corporation": {
					"name": "Far-East Corporation",
					"isNPC": false,
					"href": "https://api-sisi.testeveonline.com/corporations/98196279/",
					"id_str": "98196279",
					"logo": {
						"32x32": {
							"href": "https://image.testeveonline.com/Corporation/98196279_32.png"
						},
						"64x64": {
							"href": "https://image.testeveonline.com/Corporation/98196279_64.png"
						},
						"128x128": {
							"href": "https://image.testeveonline.com/Corporation/98196279_128.png"
						},
						"256x256": {
							"href": "https://image.testeveonline.com/Corporation/98196279_256.png"
						}
					},
					"id": 98196279
				},
				"isNPC": false,
				"href": "https://api-sisi.testeveonline.com/characters/1600000294/",
				"capsuleer": {
					"href": "https://api-sisi.testeveonline.com/characters/1600000294/capsuleer/"
				},
				"portrait": {
					"32x32": {
						"href": "https://image.testeveonline.com/Character/1600000294_32.jpg"
					},
					"64x64": {
						"href": "https://image.testeveonline.com/Character/1600000294_64.jpg"
					},
					"128x128": {
						"href": "https://image.testeveonline.com/Character/1600000294_128.jpg"
					},
					"256x256": {
						"href": "https://image.testeveonline.com/Character/1600000294_256.jpg"
					}
				},
				"id": 1600000294,
				"id_str": "1600000294"
			},
			"contact": {
				"id_str": "1600000294",
				"href": "https://api-sisi.testeveonline.com/characters/1600000294/",
				"name": "0men666",
				"id": 1600000294
			},
			"href": "https://api-sisi.testeveonline.com/characters/92095466/contacts/1600000294/",
			"contactType": "Character",
			"watched": true,
			"blocked": false
		}
	],
	"next": {
		"href": "https://api-sisi.testeveonline.com/characters/92095466/contacts/?page=2"
	},
  	"totalCount": 1024,
  	"pageCount_str": "6"
}
```

### POST
* Scope: `characterContactsWrite`

Returns the Location of the newly created contact in the Location header (also when contact already exists)

```json
{
	"standing": 3.5,
	"contactType": "Character",
	"contact": {
		"id_str": "1600000294",
		"href": "https://api-sisi.testeveonline.com/characters/1600000294/",
		"name": "0men666",
		"id": 1600000294
	},
	"watched": true
}
```

## Contact
### Route
``/characters/<characterID:characterIdType>/contact/<contactID:contactIdType>/``

### GET
* Cache: 5 minutes
* Scope: `characterContactsRead`

```
    Not Implemented!
```

### PUT
* Scope: `characterContactsWrite`

Used like adding, just set to the values you want to adjust.

```json
{
    "standing": "10.0",
    "contactType": "Character",
    "contact": {
        "id_str": "1600000294",
        "href": "https://api-sisi.testeveonline.com/characters/1600000294/",
        "name": "0men666",
        "id": 1600000294
    },
    "watched": false
}
```

### DELETE
No content required for this request. Expect it to delete whatever resource
it is sent to.

## Errors
Each of these errors should be presented to the user so they can take the required action.

### ContactsAddFull
* Message: "The contact list you are adding to is full. Please consider trimming your current list."
* Note: You can currently have no more than 1024 personal contacts.
