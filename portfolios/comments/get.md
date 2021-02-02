---
description: 해당 id를 가진 댓글 하나를 불러오는 API입니다
---

# 댓글 읽기

## METHOD

```text
GET
```

## URL

```text
/portfolios/:portfolioId/comments/:commentId
```

* portfolioId: 해당 댓글이 작성된 \(포트폴리오 페이지의\) 게시물 고유 id
* commentId: 해당 댓글의 고유 id

## RESPONSE

| name         | type      | description          |
| ------------ | --------- | -------------------- |
| id           | number    | 댓글 고유 id         |
| content      | string    | 댓글 내용            |
| authorEmail  | string    | 댓글 작성자의 이메일 |
| createdDate  | TIMESTAMP | 댓글 작성 날짜       |
| modifiedDate | TIMESTAMP | 댓글 수정 날짜       |

### RESPONSE EXAMPLE

### success

**HTTP Status code : 200 OK**

```json
{
    "id": 26,
    "content": "example comment",
    "authorEmail": "example@ewhain.net",
    "createdDate": "2020-11-16T17:04:01",
    "modifiedDate": "2020-11-16T17:04:10"
}
```

### fail

- 고유 댓글 id의 존재 유무와 상관없이 해당 id의 포트폴리오 게시물이 없는 경우

```json
{
    "status": 400,
    "message": "존재하지 않는 포트폴리오입니다. "
}
```

- 해당 id의 포트폴리오 게시물은 있으나 해당 id의 댓글은 존재하지 않는 경우

```json
{
    "status": 400,
    "message": "존재하지 않는 댓글입니다. "
}
```

- 고유 id의 포트폴리오와 고유 id의 댓글이 존재하지만 잘못된 포트폴리오와 연관되어 호출된 경우

```json
{
    "status": 400,
    "message": "잘못된 경로로 접근했습니다. "
}
```

| name    | type   | description                                                  |
| ------- | ------ | ------------------------------------------------------------ |
| status  | number | HTTP status code(에러 상황에 따라 변할 수 있습니다. )        |
| message | string | 에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. ) |

