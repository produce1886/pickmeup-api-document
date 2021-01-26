---
description: 해당 id를 가진 프로젝트 페이지의 게시물을 수정하는 API입니다
---

# 게시물 수정

## METHOD

```text
PUT
```

## URL

```text
/projects/:id
```

* id: 프로젝트 페이지의 수정하려는 게시물 고유 id

## REQUEST BODY

|name|type|require|description|
|---|---|---|---|
|title|string|필수|수정할 게시물 제목|
|content|string|필수|수정할 게시물 내용|
|authorEmail|string|필수|현재 사용자 (기존 게시물의 작성자와 일치하지 않을 경우 에러 발생)|
|category|string|필수|수정할 카테고리|
|recruitmentField|string|필수|수정할 구인분야|
|region|string|필수|수정할 지역|
|projectSection|string|필수|수정할 프로젝트 종류|
|projectTags|string 배열|필수, 값이 없으면 빈 리스트로(`[]`)|수정할 태그 이름들|

### REQUEST BODY EXAMPLE

```json
{
        "title": "예시 프로젝트",
        "content": "Curabitur sit.",
        "authorEmail": "example@gmail.com",
        "category": "웹",
        "recruitmentField": "개발",
        "region": "서울",
        "projectSection": "해커톤",
        "projectTags": ["golang", "java"]
}
```

## RESPONSE

### success

**HTTP Status code: 200 OK**
> Response Body는 따로 없습니다.  


### fail

**HTTP Status code: 400 Bad Request**

```json
{
    "status": 400,
    "message": "필수항목을 입력해주세요. "
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
