---
description: 프로젝트 페이지의 게시물을 생성하는 API입니다
---

# 게시물 생성

## METHOD

```text
POST
```

## URL

```text
/projects
```

## REQUEST BODY
|name|type|require|description
|---|---|---|---|
|authorEmail|string|필수|작성자 이메일|
|title|string|필수|게시물 제목|
|content|string|필수|게시물 내|
|category|string|필수|카테고리|
|recruitmentField|string|필수|구인분야|
|region|string|필수|지역|
|projectSection|string|필수|프로젝트 종류|
|projectTags|String 배열|필수, 값이 없으면 빈 리스트로(`[]`)|프로젝트 태그|
|image|string(URI)|선택|프로젝트 이미지 경로|

해당 리퀘스트의 바디로 보내는 이름, 이메일, 이미지는 소셜 로그인 api에서 제공하는 정보입니다. 현재는 구글 로그인만 사용하니 해당 사용자의 구글 계정에 설정한 이름, 이메일, 프로필 이미지가 되겠습니다.

### REQUEST BODY EXAMPLE

```json
{
    "authorEmail": "example@gmail.com",
    "title": "예시 프로젝트",
    "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur sit.",
    "category": "웹", 
    "recruitmentField": "디자인",
    "region": "서울",
    "projectSection": "공모전",
    "projectTags": ["포토샵", "제플린"],
    "image": "https://example.png"
}
```


## RESPONSE
### success
**HTTP Status code : 201 Created**
> Response Body는 따로 없습니다.  
> 대신, Http Location **헤더**에 생성된 자원의 경로를 붙여서 반환합니다.  

### fail
**HTTP Status code : 400 Bad Request**
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
