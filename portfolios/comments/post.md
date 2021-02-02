---
description: 포트폴리오 페이지의 게시물에 댓글을 생성하는 API입니다
---

# 댓글 생성

## METHOD

```text
POST
```

## URL

```text
/portfolios/:portfolioId/comments
```

* portfolioId: 포트폴리오 페이지의 게시물 고유 id

## REQUEST BODY

| name        | type   | require | description          |
| ----------- | ------ | ------- | -------------------- |
| authorEmail | string | 필수    | 댓글 작성자의 이메일 |
| content     | string | 필수    | 작성할 댓글 내용     |

### REQUEST BODY EXAMPLE

```json
{
        "authorEmail": "example@gmail.com",
        "content": "example comment content"
}
```

## RESPONSE

### success

**HTTP Status code : 201 Created**

> Response Body는 따로 없습니다.  
> 대신, Http Location **헤더**에 생성된 자원의 경로를 붙여서 반환합니다.  

### fail

**HTTP Status code : 400 Bad Request**

```json
{
    "status": 400,
    "message": "존재하지 않는 계정입니다. "
}
```

| name    | type   | description                                                  |
| ------- | ------ | ------------------------------------------------------------ |
| status  | number | HTTP status code(에러 상황에 따라 변할 수 있습니다. )        |
| message | string | 에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. ) |
