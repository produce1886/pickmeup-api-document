---
description: 해당 id를 가진 포트폴리오 페이지의 게시물을 삭제하는 API입니다
---

# 게시물 삭제

## METHOD

```text
DELETE
```

## URL

```text
/portfolios/:id
```

* id: 포트폴리오 페이지의 삭제하려는 게시물 고유 id

## RESPONSE

### success

**HTTP Status code : 204 No Content**

> Response Body는 따로 없습니다.  

### fail

**HTTP Status code : 400 Bad Request**

```json
{
    "status": 400,
    "message": "존재하지 않는 포트폴리오입니다. "
}
```

| name    | type   | description                                                  |
| :------ | ------ | ------------------------------------------------------------ |
| status  | number | HTTP status code(에러 상황에 따라 변할 수 있습니다. )        |
| message | string | 에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. ) |