---
description: 해당 id를 가진 프로젝트의 이미지를 삭제하는 API입니다. 
---

# 게시물 이미지 삭제

## METHOD

```text
DELETE
```

## URL

```text
/projects/:id/image
```

* id: 프로젝트 페이지의 수정하려는 게시물 고유 id

## RESPONSE
### success
**HTTP Status code : 204 No Content**
> Response Body는 따로 없습니다.  

### fail
**HTTP Status code : 400 Bad Request or 500 Internal Server Error**

```json
{
    "status": 400,
    "message": "존재하지 않는 프로젝트입니다. "
}
```

|name|type|description|
|---|---|---|
|status|number|HTTP status code(에러 상황에 따라 변할 수 있습니다. )|
|message|string|에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. )|
