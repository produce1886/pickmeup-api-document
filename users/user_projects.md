---
description: 특정 사용자가 작성한 프로젝트 게시물 목록을 불러오는 API입니다
---

# 유저의 프로젝트 게시물 불러오기

## METHOD

```text
GET
```

## URL

```text
/users/:id/projects
```

* id: 사용자의 아이디 입니다 \(픽미업 DB 기준\)

## RESPONSE

* totalNum: 프로젝트 게시글 총 개수 \(number\)
* projectList: 프로젝트 게시글 리스트 \(project 배열\)
  * project
    * id: 게시물 고유 id \(number\)
    * title: 게시물 제목 \(string\)
    * content: 게시물 내용 \(string\)
    * category: 카테고리 \(string\) 
    * recruitmentField: 구인분야 \(string\)
    * region: 지역 \(string\)
    * projectSection: 프로젝트 종류 \(string\)
    * projectTags: 프로젝트 태그 \(tag 배열\)
      * tag
        * id: 태그 id \(number\)
        * tagName: 태그 내용 \(string\)
    * createdDate: 게시물 작성 날짜 \(string / DATETIME\)
    * modifiedDate: 게시물 수정 날짜 \(string / DATETIME\)
    * user: 게시물 작성자 정보\(object\)
      * id: 게시물 작성자의 데이터베이스에 저장된 고유 id \(number\)
      * email: 게시물 작성자의 이메일 \(string\)
      * username: 작성자 이름 \(string\)
      * image: 작성자 프로필 사진 \(이미지 링크 string or base64 encoded string / BLOB\)
    * viewNum: 조회수 \(number\)
    * commentsNum: 댓글 수 \(number\)

### RESPONSE EXAMPLE

### success

**HTTP Status code : 200 OK**

```json
{
    "totalNum": 2,
    "projectList": [
        {
            "id": 123,
            "title": "example",
            "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur sit.",
            "category": "게임",
            "recruitmentField": "기획",
            "region": "경기",
            "projectSection": "창업",
            "projectTag": [],
            "createdDate": "2021-01-07T14:49:52",
            "modifiedDate": "2021-01-08T14:05:43",
            "user": {
                "id": 2,
                "email": "example@gmail.com",
                "username": "홍길동",
                "image": "https://example/photo.jpg"
            },
            "viewNum": 15,
            "commentsNum": 2
        },
        {
            "id": 124,
            "title": "example2",
            "content": "PICK ME UP PLEASE",
            "category": "웹",
            "recruitmentField": "개발",
            "region": "부산",
            "projectSection": "창업",
            "projectTag": [
                {
                    "id": 1,
                    "tagName": "리액트"
                },
                {
                    "id": 2,
                    "tagName": "reactjs"
                }
            ],
            "createdDate": "2021-01-08T14:49:52",
            "modifiedDate": "2021-01-09T14:05:43",
            "user": {
                "id": 2,
                "email": "example@gmail.com",
                "username": "홍길동",
                "image": "https://example/photo.jpg"
            },
            "viewNum": 121,
            "commentsNum": 7
        }
    ]
}
```

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
