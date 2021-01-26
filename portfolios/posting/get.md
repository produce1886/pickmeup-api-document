---
description: 해당 id를 가진 포트폴리오 페이지의 게시물 하나를 불러오는 API입니다
---

# 게시물 읽기

## METHOD

```text
GET
```

## URL

```text
/portfolios/:id
```

* id: 포트폴리오 페이지의 읽으려는 게시물 고유 id

## RESPONSE

| name             | type                             | description               |
| ---------------- | -------------------------------- | ------------------------- |
| id               | number                           | 게시물 고유 id            |
| title            | string                           | 게시물 제목               |
| content          | string                           | 게시물 내용               |
| category         | string                           | 카테고리                  |
| recruitmentField | string                           | 구인분야                  |
| portfolioTag   | `tag` (오브젝트) 배열     | 포트폴리오 태그, 최대 5개 |
| image           | string(URI) 배열                 | 포트폴리오 이미지 경로    |
| createdDate      | string / DATETIME                | 게시물 작성 날짜          |
| modifiedDate     | string / DATETIME                | 게시물 수정 날짜          |
| user             | `user` (오브젝트) 배열    | 게시물 작성자 정보        |
| viewNum | number          | 조회수       |
| commentsNum | number          | 댓글 수      |
| comments | `comment` (오브젝트) 배열 | 댓글 목록     |

* `tag` : 포트폴리오 태그 정보(object)

| name    | type   | description |
| ------- | ------ | ----------- |
| id      | number | 태그 id     |
| tagName | string | 태그 내용   |

* `comment` : 댓글 정보(object)

| name         | type                   | description        |
| ------------ | ---------------------- | ------------------ |
| id           | number                 | 댓글 고유 id       |
| content      | string                 | 댓글 내용          |
| createdDate  | string / DATETIME      | 댓글 작성 날짜     |
| modifiedDate | string / DATETIME      | 댓글 수정 날짜     |
| user         | `user` (오브젝트) 배열 | 게시물 작성자 정보 |

- `user` : 게시물 작성자 정보(object)

| name     | type         | description               |
| -------- | ------------ | ------------------------- |
| id       | number(Long) | 사용자 고유 id            |
| username | string       | 사용자 이름               |
| email    | string       | 사용자 이메일             |
| image    | string(URI)  | 사용자 프로필 이미지 경로 |

### RESPONSE EXAMPLE

#### success

**HTTP Status code : 200 OK**

```json
{
    "id": 123,
    "title": "example",
    "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur sit.",
    "category": "게임",
    "recruitmentField": "기획",
    "portfolioTag": [
        {
            "id": 1,
            "tag": "모바일게임"
        }
    ],
    "image": ["base64 encoded string"],
    "createdDate": "2021-01-07T14:49:52",
    "modifiedDate": "2021-01-08T14:05:43",
    "user": {
        "id": 2,
        "email": "example@gmail.com",
        "username": "홍길동",
        "image": "https://example/photo.jpg"
    },
    "viewNum": 15,
    "commentsNum": 2,
    "comments": [
        {
            "createdDate": "2021-01-08T17:04:01",
            "modifiedDate": "2021-01-08T17:04:10",
            "id": 26,
            "content": "comment example",
            "user": {
                "id": 12,
                "email": "example2@ewhain.net",
                "username": "­이화연",
                "image": "https://example2/photo.jpg",
            }
        },
        {
            "createdDate": "2021-01-08T19:04:01",
            "modifiedDate": "2021-01-08T20:24:10",
            "id": 27,
            "content": "comment example2",
            "user": {
                "id": 12,
                "email": "example2@ewhain.net",
                "username": "­이화연",
                "image": "https://example2/photo.jpg",
            }
        }
    ]
}
```

#### fail

**HTTP Status code : 400 Bad Request**

```json
{
    "status": 400,
    "message": "존재하지 않는 계정입니다. "
}
```

```json
{
    "status": 400,
    "message": "존재하지 않는 포트폴리오입니다. "
}
```