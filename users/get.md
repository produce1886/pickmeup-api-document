---
description: 특정 사용자의 정보를 불러오는 API입니다
---

# 유저 정보 불러오기

## METHOD

```text
GET
```

## URL

```text
/users/:id
```

* id: 유저 정보를 불러올 유저의 픽미업 DB에서의 고유 id

## RESPONSE

|name|type|description|
|---|---|---|
|email|string|사용자 이메일|
|username|string|사용자 이름|
|image|string(URI)|사용자 프로필 이미지 경로|
|introduce|string|사용자 간단 자기 소개|
|birth|date \(yyyy-MM-dd 형식\)|사용자 생년월일|
|university|string|사용자 대학교|
|major|string|사용자 전공|
|region|string|사용자 활동 지역|
|interests|string|사용자 관심분야|
|birthPublic|boolean|사용자 생년월일 공개 여부|
|universityPublic|boolean|사용자 대학 공개 여부|
|regionPublic|boolean|사용자 활동 지역 공개 여부|
|interestsPublic|boolean|사용자 관심 분야 공개 여부|

### RESPONSE EXAMPLE

### success

**HTTP Status code: 200 OK**

```json
{
    "email": "example2@gmail.com",
    "username": "화연",
    "image": "",
    "introduce": "안녕하세요!",
    "birth": "2020-01-01",
    "university": "이화여자대학교",
    "major": null,
    "region": "부산",
    "interests": null,
    "birthPublic": true,
    "universityPublic": true,
    "regionPublic": false,
    "interestsPublic": false
}
```

### fail

**HTTP Status code: 400 Bad Request**

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





