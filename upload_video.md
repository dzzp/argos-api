# 1. Request

```json
{
  "videos": [
    {
      "lat": lat_value,
      "lng": lng_value,
      "path": video_file_path,
      "time": shot_time,
    },
    {
      "lat": ...,
      "lng": ...,
      "path": ...,
      "time": ...,
    }, ...
  ],
  "code": "detect_request",
}
```

# 2. Response

```json
{
  "videos": [
    {
      "lat": lat_value,
      "lng": lng_value,
      "path": video_file_path,
      "imgs": [
        {
          "time": calculated_datetime,
          "persons": [
            {
              "bbox_img": bbox_img_file_path,
              "person_idx": person_idx_value,
            },
            {
              "bbox_img": ...,
              "person_idx": ...,
            }, ...
          ],
        },
        {
          "time": ...,
          "persons": [ ... ]
        }, ...
      ]
    },
    {
      "lat": ...,
      "lng": ...,
      "path": ...,
      "imgs": [ ... ],
    }
  ],
  "code": "detect_response",
}
```
