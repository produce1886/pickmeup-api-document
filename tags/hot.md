---
description: HOT한 순으로 상위 10개 태그를 불러오는 API입니다
---

# HOT한 태그 불러오기

## METHOD

```text
GET
```

## URL

```text
/tags
```

## RESPONSE

* tags: 태그 목록 \(tag 배열\)
  * tag
    * id: 태그 id \(number\)
    * tagName: 태그 내용 \(string\)

### RESPONSE EXAMPLE

### success

**HTTP Status code : 200 OK**

```json
{
    "tags": [
        {
            "id": 1,
            "tagName": "모바일게임"
        },
        {
            "id": 2,
            "tagName": "리액트"
        },
        ... // 이후 8개 같은 방식으로 반복
    ]
}
```

### fail

**HTTP Status code : 500 Internal Server Error**





