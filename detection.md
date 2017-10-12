# 1. Request

**method:** `POST`

**path:** `/detection/`

```json
{
  "videos": [
    {
      "lat": lat_value,
      "lng": lng_value,
      "video_path": video_file_path,
      "time": shot_time,
      "memo": memo
    },
    {
      "lat": ...,
      "lng": ...,
      "video_path": ...,
      "time": ...,
      "memo": memo
    }, ...
  ],
  "code": "detect_request",
}
```

## Example

### request example 1

```JSON
{
  "videos": [
    {
      "lat": 37.503585,
      "lng": 127.044531,
      "video_path": "/data-picker/assets/test.mp4",
      "time": "2017-10-11T12:30",
      "memo": "hello world"
    },
    {
      "lat": 127.044531,
      "lng": 37.503585,
      "video_path": "/data-picker/assets/test2.mp4",
      "time": "2017-10-14T19:30",
      "memo": ""
    }
  ],
  "code": "detect_request"
}
```

### request example 2

```JSON
{
  "videos": [
    {
      "lat": 37.503585,
      "lng": 127.044531,
      "video_path": "/data-picker/assets/test3.mp4",
      "time": "2017-10-10T21:30",
      "memo": "road view"
    }
  ],
  "code": "detect_request"
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
      "memo": memo,
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
      "memo": ...,
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

## Error message

1. already exist

```JSON
{
    "video_path": [
        "video with this video path already exists."
    ]
}
```

2. field required

```JSON
{
    "video_path": [
        "This field is required."
    ]
}
```
