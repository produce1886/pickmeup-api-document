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

* email: 사용자 이메일 \(string\)
* username: 사용자 이름 \(string\)
* birth: 사용자 생년월일 \(yyyy-MM-dd 형식\)
* university: 사용자 대학교 \(string\)
* major: 사용자 전공 \(string\)
* region: 사용자 활동 지역 \(string\)
* introduce: 사용자 간단 자기 소개 \(string\)
* image: 사용자 프로필 이미지 \(이미지 링크 혹은 base64 인코딩된 문자열\)
* interests: 사용자 관심분야 \(string\)
* isBirthPublic: 생년월일 공개 여부 \(boolean\)
* isUniversityPublic: 대학 공개 여부 \(boolean\)
* isRegionPublic: 활동 지역 공개 여부 \(boolean\)
* isInterestsPublic: 관심 분야 공개 여부 \(boolean\)

### RESPONSE EXAMPLE

```markup
{
    "email": "example@gmail.com",
    "username": "화연",
    "birth": null,
    "university": "이화여자대학교",
    "major": null,
    "region": "부산",
    "introduce": "안녕하세요!",
    "image": "",
    "interests": null,
    "isBirthPublic": null,
    "isUniversityPublic": true,
    "isRegionPublic": false,
    "isInterestsPublic": null
}
```





