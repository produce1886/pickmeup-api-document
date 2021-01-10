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
    * id: tag 아이디 \(number\)
    * tag: 내용 \(string\)

### RESPONSE EXAMPLE

```markup
{
    "tags": [
        {
            "id": 1,
            "tag": "모바일게임"
        },
        {
            "id": 2,
            "tag": "리액트"
        },
        ... // 이후 8개 같은 방식으로 반
    ]
}
```





