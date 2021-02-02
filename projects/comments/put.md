---
description: 프로젝트 페이지의 게시물에 있는 댓글을 수정하는 API입니다
---

# 댓글 수정

## METHOD

```text
PUT
```

## URL

```text
/projects/:projectId/comments/:commentId
```

* projectId: 해당 댓글이 작성된 \(프로젝트 페이지의\) 게시물 고유 id
* commentId: 수정할 댓글의 고유 id 

## REQUEST BODY

| name         | type      |require| description          |
| ------------ | --------- | ------|---------------------- |
| authorEmail  | string    | 필수 | 댓글 작성자의 이메일 (기존 작성자와 일치하지 않을 경우 에러 발생)|
| content      | string    | 필수 | 수정할 댓글 내용            |

### REQUEST BODY EXAMPLE

```json
{
        "authorEmail": "example@gmail.com",
        "content": "example comment content"
}
```

## RESPONSE

### success

**HTTP Status code: 200 OK**
> Response Body는 따로 없습니다.  


### fail

**HTTP Status code: 400 Bad Request or 403 Forbidden**

```json
{
    "status": 400,
    "message": "잘못된 경로로 접근했습니다. "
}
```
```json
{
    "status": 403,
    "message": "권한이 없습니다. "
}
```

#### REQUEST BODY
|name|type|description|
|---|---|---|
|status|number|HTTP status code(에러 상황에 따라 변할 수 있습니다. )|
|message|string|에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. )|





