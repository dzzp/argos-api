# ARGOS-API

## /cases

### GET
Get all cases

** Request **

- `/?search=` : Return recent
- `/?search=query` : Return search with query

** Response **

```json
{
    "cases": [
        {
            "title": case_title,
            "hash": case_hash,
            "memo": case_memo,
            "datetime": case_generated_datetime
        },
        {...}
    ]
}
```

### POST
Create new case

** Request **

```json
{
    "title": case_title,
    "memo": case_memo,
    "datetime": case_generated_datetime
}
```

** Response **

```json
{
    "title": case_title,
    "hash": case_hash,
    "memo": case_memo,
    "datetime": case_generated_datetime
}
```

## /cases/`case_hash`/videos

### GET
Get videos & processed data from case

** Response **

```json
{
    "videos": [
        {
            "path": video_path,
            "memo": memo,
            "lat": lat,
            "lng": lng,
            "datetime": shot_datetime,
            "video_hash": video_hash,
            "is_detection_done": true|false,
            "imgs": [
                {
                    "timedelta": calculated_datetime,
                    "persons": [
                        {
                            "hash": person_hash,
                            "bbox_path": bbox_path,
                            "orig_path": orig_path
                        },
                        {...}
                    ]
                }, {...}
            ]
        }, {...}
    ]
}
```

### POST

Upload new videos

** Request **

```json
{
    "videos": [
        {
            "path": video_path,
            "memo": video_memo
        },
        {...}
    ]
}
```

** Response **

```json
{
    "code": ok|error,
    "path": video_path,     // optional
    "detail": "File does not exist"|"Filetype error occured"    // optional
}
```


## /cases/`case_hash`/videos/`video_hash`

### GET
Get video info

** Response **

```json
{
    "path": video_path,
    "memo": memo,
    "lat": lat,
    "lng": lng,
    "datetime": shot_datetime,
    "video_hash": video_hash,
    "is_detection_done": true|false,
    "imgs": [
        {
            "timedelta": calculated_datetime,
            "persons": [
                {
                    "hash": person_hash,
                    "bbox_path": bbox_path,
                    "orig_path": orig_path
                },
                {...}
            ]
        }, {...}
    ]
}
```

### PUT

Put additional info

** Request **

```json
{
    "memo": memo,
    "lat": lat,
    "lng": lng,
    "datetime": shot_datetime
}
```

** Response **

```json
{
    "code": "ok"
}
```


## /cases/`case_hash`/probes

### GET
Get found persons

** Response **

```json
{
    "persons": [
        {
            "person_hash": person_hash,
            "video_hash": video_hash,
            "bbox_path": bbox_path,
            "orig_path": orig_path
        },
        {...}
    ]
}
```

### POST
Put new found persons

** Request **

```json
{
    "negatives": [
        person_hash,
        ...
    ],
    "positives": [
        person_hash,
        ...
    ]
}
```

** Response **

```json
{
    "code": ok|error
}
```

## /cases/`case_hash`/galleries

### GET
Get candidate persons based on found persons

** Response **

```json
{
    "persons": [
        {
            "person_hash": person_hash,
            "video_hash": video_hash,
            "bbox_path": bbox_path,
            "orig_path": orig_path,
            "distance": distance
        },
        {...}
    ]
}
```

## /cases/`case_hash`/processing/

### GET
Get detection processing status

** Response **

```json
{
    "total": [video_hash1, video_hash2, ...]
}
```
