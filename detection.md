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

# ETC

video file path = '/home/Jiyoon/video/example.mp4'인 경우,

detection result = '/home/Jiyoon/video/example/'에 저장

    - bbox = '/home/Jiyoon/video/example/bbox/(...).jpg'
    - feature = '/home/Jiyoon/video/example/feature/(...).txt'

> 사람 A에 대한 bbox는 000001.jpg, feature는 000001.txt로 저장됨

> bbox image는 crop된 형태로 저장됨
