# Content

## /api/v2/content/(static\|video\|html5).json

The resource enables you to upload creatives that you can use for advertising. The creatives uploaded using this resource will be available only in the packages whose banner format has the "content" section.

Used object: [Content](https://ads.vk.com/en/doc/api/object/Content)

### POST

The request should have the type multipart/form-data. For the static.json and video.json methods, the "data" structure must contain values for the width and height parameters of the source creative.

Static images must be uploaded to [https://ads.vk.com/api/v2/content/static.json](https://ads.vk.com/api/v2/content/static.json).

Videos must be uploaded to [https://ads.vk.com/api/v2/content/video.json](https://ads.vk.com/api/v2/content/video.json).

HTML5 creatives must be uploaded to [https://ads.vk.com/api/v2/content/html5.json](https://ads.vk.com/api/v2/content/html5.json)
The file must meet the requirements for HTML5 banners ( [https://sales.mail.ru/ru/russia/main/latest/technical/#a75](https://sales.mail.ru/ru/russia/main/latest/technical/#a75)).

Request example:

```http

   curl -X POST -H "Authorization: Bearer LIDM…Io4Qj"  -H "Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW" -F "file=@[object Object]" -F 'data={"width":1612, "height":980}' "https://ads.vk.com/api/v2/content/static.json"
```

Response example:

```http

    {
       "variants": {
           "original": {
               "url": "https://r.mradx.net/img/17/B36CF7.jpg",
               "width": 90,
               "height": 75,
               "size": 3339
           }
       },
       "id": 1084236
   }
```

In case of an error the following response is returned:

```http

    {
        "error": {
            "code": "validation_failed",
            "fields": {
                "file": "<error\>"
            },
            "message": "Validation failed"
        }
    }
```

Possible errors for static.json and video.json:

- {"code": "format\_not\_supported", "message": "Unsupported content format."}
- {"code": "cannot\_upload", "message": "Cannot upload content"}
- {"code": "no\_file", "message": "Content not found in the request. Request must have multipart/form-data type with "file" field."}
- {"code": "broken\_content", "message": "Content is broken"}
- {"code": "content\_too\_large", "message": "Content is too large"}
- {"code": "content\_bad\_size", "message": "Content has bad size"}

Possible errors for html5.json:

- bad\_archive - error opening zip archive;
- no\_html\_file - the archive does not contain an html file;
- too\_many\_html\_files - the archive contains more than one html file;
- invalid\_file\_name - invalid file name;
- tag\_unclosed - tag unclosed;
- wrong\_symbols - wrong symbols in url;
- incorrect\_ad\_size - size of creative is not set in <meta name="ad.size">;
- href\_not\_found - "a" tag must have "href" attribute;
- null\_symbol - Html contains NULL symbol;
- external\_css - external CSS contains links to resources;
- validation\_error - common API v2 validation error;

For error details, see the "message" field.
