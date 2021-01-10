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

* id: 게시물 고유 id \(number\)
* title: 게시물 제목 \(string\)
* content: 게시물 내용 \(string\)
* category: 카테고리 \(string\) 
* recruitmentField: 구인분야 \(string\)
* portfolioTag: 포트폴리오 태그 \(tag 배열\)
  * tag
    * id: 태그 id \(number\)
    * tag: 태그 내용 \(string\)
* image: 이미지 \(base64 encoded string / BLOB **배열**\)
* createdDate: 게시물 작성 날짜 \(string / DATETIME\)
* modifiedDate: 게시물 수정 날짜 \(string / DATETIME\)
* user: 게시물 작성자 정보\(object\)
  * id: 게시물 작성자의 데이터베이스에 저장된 고유 id \(number\)
  * email: 게시물 작성자의 이메일 \(string\)
  * username: 작성자 이름 \(string\)
  * image: 작성자 프로필 사진 \(이미지 링크 string or base64 encoded string / BLOB\)
* viewNum: 조회수 \(number\)
* commentsNum: 댓글 수 \(number\)
* comments: 댓글 목록 \(comment 배열\)
  * comment
    * createdDate: 댓글 작성 날짜 \(string / DATETIME\)
    * modifiedDate: 댓글 수정 날짜 \(string / DATETIME\)
    * id: 댓글 고유 id \(number\)
    * content: 댓글 내용 \(string\)
    * user: 게시물 작성자 정보\(object\)
      * id: 댓글 작성자의 데이터베이스에 저장된 고유 id \(number\) 
      * email: 댓글 작성자의 이메일 \(string\)
      * username: 댓글 작성자 이름 \(string\)
      * image: 댓글 작성자 프로필 사진 \(이미지 링크 string or base64 encoded string / BLOB\)

### RESPONSE EXAMPLE

```markup
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





