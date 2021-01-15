---
description: 사용자 정보를 수정하는 API입니다
---

# 유저 정보 수정하기

## METHOD

```text
PUT
```

## URL

```text
/user/:id
```

* id: 유저 정보를 수정할 유저의 픽미업 DB에서의 고유 id

## REQUEST BODY

|name|type|require|description|
|---|---|---|---|
|username|string|필수|수정할 사용자 이름|
|introduce|string|선택|수정할 사용자 간단 자기 소개|
|birth|date \(yyyy-MM-dd 형식\)|선택|수정할 사용자 생년월일|
|university|string|선택|수정할 사용자 대학교|
|major|string|선택|수정할 사용자 전공|
|region|string|선택|수정할 사용자 활동 지역|
|interests|string|선택|수정할 사용자 관심분야|
|birthPublic|boolean|값 없을 시 자동으로 false|수정할 사용자 생년월일 공개 여부|
|universityPublic|boolean|값 없을 시 자동으로 false|수정할 사용자 대학 공개 여부|
|regionPublic|boolean|값 없을 시 자동으로 false|수정할 사용자 활동 지역 공개 여부|
|interestsPublic|boolean|값 없을 시 자동으로 false|수정할 사용자 관심 분야 공개 여부|

사용자가 정보를 입력한 적이 없으면 null이 기본값이며, username과 공개 여부 boolean 을 제외한 모든 값은 null이 들어갈 수 있습니다.  
**boolean 값들은 입력하지 않을 시, 자동으로 `false`로 설정됩니다.** 


### REQUEST BODY EXAMPLE
> 아래 세 가지 예시 모두 가능합니다.   

```json
{
    "username": "화연",
    "birth": null,
    "university": "이화여자대학교",
    "major": null,
    "region": "부산",
    "introduce": "안녕하세요!",
    "interests": null,
    "isBirthPublic": false,
    "isUniversityPublic": true,
    "isRegionPublic": false,
    "isInterestsPublic": false
}
```

```json
{
    "username": "화연",
    "university": "이화여자대학교",
    "region": "부산",
    "introduce": "안녕하세요!",
    "isBirthPublic": false,
    "isUniversityPublic": true,
    "isRegionPublic": false,
    "isInterestsPublic": false
}
```

```json
{
    "username": "화연",
    "university": "이화여자대학교",
    "region": "부산",
    "introduce": "안녕하세요!",
    "isUniversityPublic": true,
    "isInterestsPublic": false
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
    "status": "BAD_REQUEST",
    "message": "필수항목을 입력해주세요. "
}
```
```json
{
    "status": "BAD_REQUEST",
    "message": "존재하지 않는 계정입니다. "
}
```

#### REQUEST BODY
|name|type|description|
|---|---|---|
|status|number|HTTP status code(에러 상황에 따라 변할 수 있습니다. )|
|message|string|에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. )|
