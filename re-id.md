# Request

```json
{
  "imgs": [
    {
      "path": selected_person_img_file_path,
    },
    {
      "path": ...,
    }, ...
  ],
  "code": "reid_request",
}
```

# Response

```json
{
  "results": [
    {
      "img": reid_result_person_file_path,
      "lat": lat_value,
      "lng": lng_value,
      "time": calculated_shot_date_time,
    },
    {
      "img": ...,
      "lat": ...,
      "lng": ...,
      "time": ...,
    }, ...
  ],
  "code": "reid_response
}
```
