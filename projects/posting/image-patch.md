---
description: 해당 id를 가진 프로젝트의 이미지를 바꾸는 API입니다. 
---

# 게시물 이미지 수정

## METHOD

```text
PATCH
```

## URL

```text
/projects/:id/image
```

* id: 프로젝트 페이지의 수정하려는 게시물 고유 id

## REQUEST BODY

|name|type|require|description
|---|---|---|---|
|image|multipart/form-data|필수|변경할 프로젝트 이미지|
> 현재 저장가능한 이미지로 `.jpg`, `.jpeg`, `.gif`, `.png`, `.img`, `.tiff`, `.heif` 확장자만 지원합니다.  

## RESPONSE
### success
**HTTP Status code : 201 Created**
> Response Body는 따로 없습니다.  
> 대신, Http Location **헤더**에 생성된 자원의 경로를 붙여서 반환합니다.  
> 또한, [프로젝트 게시물 정보 불러오기 API](./get.md)를 다시 한 번 호출하면, 바뀐 이미지 경로를 확인할 수 있습니다.

### fail
**HTTP Status code : 400 Bad Request or 500 Internal Server Error**

```json
{
    "status": 400,
    "message": "존재하지 않는 프로젝트입니다. "
}
```

```json
{
    "status": 400,
    "message": "필수항목을 입력해주세요. "
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
