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
/users/:id/portfolios
```

* id: 사용자의 아이디 입니다 \(픽미업 DB 기준\)

## RESPONSE

* totalNum: 포트폴리오 게시글 총 개수 \(number\)
* portfolioList: 포트폴리오 게시글 리스트 \(project 배열\)
  * portfolio
    * id: 게시물 고유 id \(number\)
    * title: 게시물 제목 \(string\)
    * content: 게시물 내용 \(string\)
    * category: 카테고리 \(string\) 
    * recruitmentField: 구인분야 \(string\)
    * region: 지역 \(string\)
    * portfolioSection: 포트폴리오 종류 \(string\)
    * portfolioTags: 포트폴리오 태그 \(tag 배열\)
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

#### success

**HTTP Status code : 200 OK**

```json
{
    "totalNum": 2,
    "portfolioList": [
        {
            "id": 1,
            "title": "example",
            "content": "주요내용",
            "category": "웹",
            "recruitmentField": "기획",
            "createdDate": "2021-01-23T04:34:35",
            "modifiedDate": "2021-01-23T04:43:13",
            "portfolioTags": [
                {
                    "id": 2,
                    "tagName": "두번째 태그"
                },
                {
                    "id": 3,
                    "tagName": "3번쨰 태그"
                }
            ],
            "user": {
                "id": 3,
                "username": "홍길동",
                "email": "example@gmail.com",
                "image": "https://example/photo.jpg"
            },
            "viewNum": 0,
            "commentsNum": 0
            },
            {
            "id": 2,
            "title": "example2",
            "content": "주요 내용2",
            "category": "게임",
            "recruitmentField": "개발",
            "createdDate": "2021-01-23T04:49:11",
            "modifiedDate": "2021-01-23T04:52:16",
            "portfolioTags": [],
            "user": {
                "id": 3,
                "username": "홍길동",
                "email": "example@gmail.com",
                "image": "https://example/photo.jpg"
            },
            "viewNum": 0,
            "commentsNum": 0
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

