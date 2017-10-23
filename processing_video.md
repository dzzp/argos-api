**method:** `GET`

**path:** `/processing/`

# Upload video -> Detection result

## 1. Request

```json
{
  "video_group": video_group_hash,
  "code": "is_detect",
}
```

## 2. Response

```json
{
  "total": total_video,
  "done": done_video,
  "code": "processing_detect",
}
```

# Detection result -> Re-id result

## 1. Request

```json
{
  "code": "is_reid",
}
```

## 2. Response

```json
{
  "code": "processing_reid",
}
```
