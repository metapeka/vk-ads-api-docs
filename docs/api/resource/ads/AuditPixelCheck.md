# AuditPixelCheck

## /api/v3/audit\_pixel.json

A resource that allows you to validate a pixel and find out which pixels can be generated based on it.

### POST

Request example:

```http

   POST /api/v3/audit_pixel.json?fields=audit_pixel,generated_audit_pixels

    {
        "audit_pixel": "https://top-fwz1.mail.ru/tracker?id=2930776;e=RG%3A/trg-pixel-2812993-1507041739095",
    }
```

Response example:

```http

    {
        "audit_pixel": "https://top-fwz1.mail.ru/tracker?id=2930776;e=RG%3A/trg-pixel-2812993-1507041739095",
        "generated_audit_pixels": [\
            {\
                "audit_pixel": "https://top-fwz1.mail.ru/tracker?id=2930776;e=RG%3A/trg-pixel-2812993-1507041739095&role=impression",\
                "role": "impression"\
            },\
            {\
                "audit_pixel": "https://top-fwz1.mail.ru/tracker?id=2930776;e=RG%3A/trg-pixel-2812993-1507041739095&role=playheadReachedValue50",\
                "role": "playheadReachedValue50"\
            }\
        ]
    }
```

Returned status codes:

- 200 - The pixel is valid.
- 400 - Validation error.

Example response in case of a validation error for the provided pixel:

```http

    {
        "error": {
            "code": "validation_failed",
            "message": "Validation failed",
            "fields": {
                "audit_pixel": {
                    "code": "invalid_audit_pixel",
                    "message": "Audit pixel is invalid"
                }
            }
        }
    }
```

Example response in case an invalid pixel value is provided:

```http

    {
        "error": {
            "code": "validation_failed",
            "message": "Validation failed",
            "fields": {
                "audit_pixel": {
                    "code": "bad_value",
                    "message": "Bad value",
                    "expected": "URL"
                }
            }
        }
    }
```

Example response in case parameters are provided in an invalid format:

```http

    {
        "error": {
            "code": "validation_failed",
            "message": "Validation failed",
            "fields": {
                "code": "object_required",
                "message": "Resource data must be an object",
            }
        }
    }
```

Example response in case of a server-side error:

```http

    {
        "error": {
            "message": "Remote service error"
            "code": "audit_pixel_service_error"
        }
    }
```
