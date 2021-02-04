---
description: 해당 id를 가진 포트폴리오 이미지의 파일을 바꾸거나 삭제하는 API입니다. 
---

# 게시물 이미지 수정/삭제

## METHOD

```text
PATCH
```

## URL

```text
/portfolios/image/:id
```

* id: [포트폴리오 상제 페이지](./get.md)의 리턴값에서 알아낼 수 있는 포트폴리오 이미지의 고유 id

## REQUEST BODY

|name|type|require|description
|---|---|---|---|
|image|multipart/form-data|필수|변경할 프로젝트 이미지|
> 현재 저장가능한 이미지로 `.jpg`, `.jpeg`, `.gif`, `.png`, `.img`, `.tiff`, `.heif` 확장자만 지원합니다.  
> `image`로 아무 값도 전달하지 않을 경우 유저 프로젝트 이미지를 삭제하는 것으로 간주합니다. 

## RESPONSE
#### 포트폴리오 이미지 수정
**HTTP Status code : 201 Created**
> Response Body는 따로 없습니다.  
> 대신, Http Location **헤더**에 생성된 자원의 경로를 붙여서 반환합니다.  
> 또한, [포트폴리오 게시물 정보 불러오기 API](./get.md)를 다시 한 번 호출하면, 바뀐 이미지 경로를 확인할 수 있습니다.

#### 포트폴리오 이미지 삭제
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

```json
{
    "status": 400,
    "message": "지원하지 않는 파일 형식입니다. "
}
```

```json
{
    "status": 500,
    "message": "파일 변환에 실패했습니다. "
}
```

|name|type|description|
|---|---|---|
|status|number|HTTP status code(에러 상황에 따라 변할 수 있습니다. )|
|message|string|에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. )|