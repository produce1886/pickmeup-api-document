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

## REQUEST BODY

| name             | type        | require                             | description               |
| ---------------- | ----------- | ----------------------------------- | ------------------------- |
| title            | string      | 필수                                | 게시물 제목               |
| content          | string      | 필수                                | 게시물 내용               |
| authorEmail      | string      | 필수                                | 작성자 이메일             |
| category         | string      | 필수                                | 카테고리                  |
| recruitmentField | string      | 필수                                | 구인분야                  |
| portfolioTags    | string 배열 | 필수, 값이 없으면 빈 리스트로(`[]`) | 포트폴리오 태그, 최대 5개 |

### REQUEST BODY EXAMPLE

```json
{
        "title": "예시 포트폴리오",
        "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur sit.",
        "authorEmail": "example@gmail.com",
        "category": "어플리케이션",
        "recruitmentField": "기획",
        "portfolioTags": ["포토샵", "제플린"]
}
```

## RESPONSE

### Success

**HTTP Status code : 200 Ok**

> Response Body는 따로 없습니다.  

### fail

**HTTP Status code : 400 Bad Request or 403 Forbidden**

```json
{
    "status": 400,
    "message": "필수항목을 입력해주세요. "
}
```

```json
{
    "status": 403,
    "message": "권한이 없습니다. "
}
```

| name    | type   | description                                                  |
| ------- | ------ | ------------------------------------------------------------ |
| status  | number | HTTP status code(에러 상황에 따라 변할 수 있습니다. )        |
| message | string | 에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. ) |

