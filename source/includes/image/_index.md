
# Image Search

## <img src="images/image-search_icon.png" alt="image-search_icon" width="28px" height="auto"> The Image Search Query Object

> **Example:** Image Search Query Object

```json
{
	"image_uri": "https://example.com/images/1.png",
	"catalogs": [
	    {
	        "_id": "catalog-id-1"
	    },
	    {
	        "_id": "catalog-id-2"
	    }
	]
}
```

> **Example:** Image Search Query Object with Options

```json
{
    "image_uri": "https://example.com/images/1.png",
    "catalogs": [
        {
            "_id": "catalog-id-1"
        },
        {
            "_id": "catalog-id-2"
        }
    ],
    "options": {
        "limit": 30,
        "relevance": 50
    }
}
```

> **Example:** Image Search Query Object with Attributes

```json
{
    "image_uri": "https://example.com/images/1.png",
    "catalogs": [
        {
            "_id": "catalog-id-1"
        },
        {
            "_id": "catalog-id-2"
        }
    ],
    "options": {
        "attributes": true
    }
}
```

> **Example:** Image Search Query Object with Auto detect gender in the input image

```json
{
    "image_uri": "https://example.com/images/1.png",
    "catalogs": [
        {
            "_id": "catalog-id-1"
        },
        {
            "_id": "catalog-id-2"
        }
    ],
    "options": {
        "auto_detect_gender": true
    }
}
```

A **Image Search Query** (object) defines a visual search query for an image.

Attribute 		| Type 									| Description
------- 		| -------								| -------
`image_uri` 	| String								| A valid image URI. **<small>required</small>**
`gender`        | Array                                 | `['men', 'women']` or a sub array of both. __By default we return all gender results.__
`catalogs` 		| [Array&lt;Catalog&gt;](#catalog)		| List of catalogs (public or private) - which will be included the visual search scope.
`options`       | Object                                | A list of options that we support. Currently we support the options below

### Options for Search

These options give you the flexibility to control how our visual search is performed.

Attribute               | Type                                  | Description
-------                 | -------                               | -------
`limit`                 | Number                                | Number of results to return. Default `30`
`relevance`             | Number                                | How relevant you want the results to be. Default `50`. This takes precedence over `limit`
`auto_detect_gender`    | Boolean                               | Auto detect gender in the input image to scope search to specific genders, takes precedence over `gender` above. Currently in **alpha**. Note that this does introduce a slow down of a few 100ms in search.
`attributes`            | Boolean                               | Return [attributes](#supported-attributes) for every [catalogItem](#catalog-items), for both the searched input image and the images in the results. Note that this does introduce a slow down
of a few 100ms in search.
