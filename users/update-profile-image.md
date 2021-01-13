---
description: 사용자 프로필 이미지를 바꾸는 API입니다. 
---

# 유저 프로필 이미지 수정하기

## METHOD & URL

```http request
PATCH /user/:id/image
```

* id: 유저 정보를 수정할 유저의 픽미업 DB에서의 고유 id

## REQUEST BODY
|name|type|require|description
|---|---|---|---|
|image|multipart/form-data|필수|사용자 프로필 이미지|

### REQUEST BODY EXAMPLE
![example on POSTMAN](../.gitbook/assets/update-profile-image.png)


## RESPONSE
### success
**HTTP Status code : 201 Created**
> Response Body는 따로 없습니다.  
> 대신, Http Location **헤더**에 생성된 자원의 경로를 붙여서 반환합니다.  
> 또한, 유저 정보 불러오기 API를 다시 한 번 호출하면, 바뀐 이미지 경로를 확인할 수 있습니다.

### fail
**HTTP Status code : 500 Internal Server Error**
```json
{
    "status": 500,
    "message": "파일 변환에 실패했습니다. "
}
```

#### REQUEST BODY
|name|type|description|
|---|---|---|
|status|number(Long)|HTTP status code|
|message|string|에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. )|
