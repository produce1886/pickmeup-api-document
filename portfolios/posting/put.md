---
description: 해당 id를 가진 포트폴리오 페이지의 게시물을 수정하는 API입니다
---

# 게시물 수정

## METHOD

```text
PUT
```

## URL

```text
/portfolios/:id
```

* id: 포트폴리오 페이지의 수정하려는 게시물 고유 id

## REQUEST

| name             | type             | description                      |
| ---------------- | ---------------- | -------------------------------- |
| title            | string           | 게시물 제목                      |
| content          | string           | 게시물 내용                      |
| authorEmail      | string           | 작성자 이메일                    |
| category         | string           | 카테고리                         |
| recruitmentField | string           | 구인분야                         |
| portfolioTags    | string 배열      | 포트폴리오 태그, 최대 5개        |
| image            | string(URI) 배열 | 포트폴리오 이미지 경로, 최대 5개 |

### REQUEST BODY EXAMPLE

```json
{
        "title": "예시 포트폴리오",
        "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur sit.",
        "authorEmail": "example@gmail.com",
        "category": "웹",
        "recruitmentField": "디자인",
        "portfolioTags": ["포토샵", "제플린"],
        "image": ["uri1", "uri2"]
}
```

## RESPONSE

### Success

**HTTP Status code : 200 Ok**

### fail

| name    | type   | description                                                  |
| ------- | ------ | ------------------------------------------------------------ |
| status  | number | HTTP status code(에러 상황에 따라 변할 수 있습니다. )        |
| message | string | 에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. ) |

#### RESPONSE BODY EXAMPLE

**HTTP Status code : 400 Bad Request**

```json
{
    "status": 400,
    "message": "존재하지 않는 포트폴리오입니다. "
}
```

```json
{
    "status": 400,
    "message": "필수항목을 입력해주세요. "
}
```

**HTTP Status code : 400 Forbidden**

```json
{
    "status": 403,
    "message": "권한이 없습니다. "
}
```

