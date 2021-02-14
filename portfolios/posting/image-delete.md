---
description: 해당 id를 가진 포트폴리오 이미지의 파일을 삭제하는 API입니다. 
---

# 게시물 이미지 삭제

## METHOD

```text
DELETE
```

## URL

```text
/portfolios/image/:id
```

* id: [포트폴리오 상제 페이지](./get.md)의 리턴값에서 알아낼 수 있는 포트폴리오 이미지의 고유 id

## RESPONSE
#### success
**HTTP Status code : 204 No Content**
> Response Body는 따로 없습니다.  

### fail
**HTTP Status code : 400 Bad Request or 500 Internal Server Error**

```json
{
    "status": 400,
    "message": "존재하지 않는 이미지입니다. "
}
```

|name|type|description|
|---|---|---|
|status|number|HTTP status code(에러 상황에 따라 변할 수 있습니다. )|
|message|string|에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. )|
