---
description: 사용자 프로필 이미지를 삭제하는 API입니다. 
---

# 유저 프로필 이미지 삭제하기

## METHOD

```http
DELETE
```

## URL

```http
/users/:id/image
```

* id: 유저 정보를 수정할 유저의 픽미업 DB에서의 고유 id


## RESPONSE
### success
**HTTP Status code : 204 No Content**
> Response Body는 따로 없습니다.  

### fail
**HTTP Status code : 400 Bad Request or 500 Internal Server Error**

```json
{
    "status": 400,
    "message": "존재하지 않는 계정입니다. "
}
```

|name|type|description|
|---|---|---|
|status|number|HTTP status code(에러 상황에 따라 변할 수 있습니다. )|
|message|string|에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. )|
