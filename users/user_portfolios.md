---
description: 특정 사용자가 작성한 포트폴리오 게시물 목록을 불러오는 API입니다
---

# 유저의 포트폴리오 게시물 불러오기

## METHOD

```text
GET
```

## URL

```text
/user/:id/portfolios
```

* id: 사용자의 아이디 입니다 \(픽미업 DB 기준\)

## RESPONSE

| name          | type                       | description               |
| ------------- | -------------------------- | ------------------------- |
| totalNum      | number                     | 포트폴리오 게시글 총 개수 |
| portfolioList | `portfolio`(오브젝트) 배열 | 포트폴리오 게시글 리스트  |

* `portfolio` : 포트폴리오 정보(object)

| name             | type                 | description          |
| ---------------- | -------------------- | -------------------- |
| id               | number               | 게시물 고유 id       |
| title            | string               | 게시물 제목          |
| content          | string               | 게시물 내용          |
| category         | string               | 카테고리             |
| recruitmentField | string               | 구인분야             |
| createdDate      | string/DATETIME      | 게시물 작성 날짜     |
| modifiedDate     | string/DATETIME      | 게시물 수정 날짜     |
| portfolioTag     | `tag`(오브젝트) 배열 | 프로젝트 태그 리스트 |
| user             | `user`(오브젝트)     | 게시물 작성자        |
| viewNum          | number               | 조회수               |
| commentsNum      | number               | 댓글 수              |

* `tag` : 포트폴리오 태그 정보(object)

| name    | type   | description |
| ------- | ------ | ----------- |
| id      | number | 태그 id     |
| tagName | string | 태그 내용   |

* `user` : 게시물 작성자 정보\(object\)

| name     | type         | description               |
| -------- | ------------ | ------------------------- |
| id       | number(Long) | 사용자 고유 id            |
| username | string       | 사용자 이름               |
| email    | string       | 사용자 이메일             |
| image    | string(URI)  | 사용자 프로필 이미지 경로 |

### RESPONSE EXAMPLE

#### success

**HTTP Status code : 200 OK**

```markup
{
    "totalNum": 2,
    "portfolioList": [
        {
            "id": 123,
            "title": "example",
            "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur sit.",
            "category": "게임",
            "recruitmentField": "기획",
            "portfolioTag": [],
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
            "portfolioTag": [
                {
                    "id": 1,
                    "tag": "리액트"
                },
                {
                    "id": 2,
                    "tag": "reactjs"
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

#### fail

**HTTP Status code : 400 Bad Request**

```json
{
    "status": 400,
    "message": "존재하지 않는 계정입니다."
}
```

| name    | type   | description                                                  |
| ------- | ------ | ------------------------------------------------------------ |
| status  | number | HTTP status code(에러 상황에 따라 변할 수 있습니다. )        |
| message | string | 에러 메시지(메시지 내용은 에러 상황에 따라 변할 수 있습니다. ) |
