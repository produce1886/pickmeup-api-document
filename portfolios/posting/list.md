---
description: 포트폴리오 페이지에 있는 게시물 목록을 조건에 맞게 불러오는 API입니다
---

# 게시물 목록 불러오기

## METHOD

```text
GET
```

## URL

```text
/portfolios/list
```

## URL EXAMPLE

```http
GET /portfolios/list?page=0&size=10&sort=viewNum,desc&recruitmentField=개발&keyword=리액트
```

> 포트폴리오 게시물 중 recruitmentField가 개발로 되어 있는 게시들 중 "리액트" 검색어를 적용한 검색 결과를 조회 순이 많은 순으로
> 정렬하여 10개 중 첫번째 페이지를 가져옵니다. 

## QUERY STRING

|name|type|require|description
|---|---|---|---|
|page|number|선택, 기본값 = 0|불러올 페이지|
|size|string|선택, 기본값 = 20|불러올 게시물 개수|
|sort|string|선택|정렬 기준 / 기본값은 오름차순 정렬이며, 내림차순은 뒤에 `,desc`를 붙임 (ex: 최신순 `sort=createdDate,desc`)|
|category|string|선택|검색하는 카테고리|
|recruitmentField|string|선택|검색하는 구인분야|
|keyword|string|선택|검색어, 주어질 경우 게시물 제목이나 내용에 검색어가 포함되는 게시물만 필터링|

> page에서부터 size만큼 게시물을 불러옵니다.  
> 쿼리 파라미터로 오지 않은 경우나 빈 스트링으로 왔을 경우에는 필터링을 하지 않습니다.  
> 
> 예를 들어 category, recruitmentField, keyword가 
> 모두 주어지지 않은 경우 모든 게시물을 sort 조건으로 정렬하여, size만큼 page별로 가져옵니다. 


## RESPONSE

* totalNum: 조건에 만족하는 포트폴리오 게시글 총 개수 \(number\)
* portfolioList: 포트폴리오 게시글 리스트 \(portfolio 배열\)
  * portfolio
    * id: 게시물 고유 id \(number\)
    * title: 게시물 제목 \(string\)
    * content: 게시물 내용 \(string\)
    * firstImage: 이미지 배열 중 첫번째 이미지 \(string\)
      * 이미지가 아예 없는 경우 `""`\(빈 문자열\) 보냄
    * category: 카테고리 \(string\) 
    * recruitmentField: 구인분야 \(string\)
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

### success
```json
{
    "totalNum": 162,
    "portfolioList": [
        {
            "id": 123,
            "title": "리액트",
            "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur sit.",
            "firstImage": "",
            "category": "게임",
            "recruitmentField": "개발",
            "portfolioTag": [],
            "createdDate": "2021-01-07T14:49:52",
            "modifiedDate": "2021-01-08T14:05:43",
            "user": {
                "id": 2,
                "email": "example@gmail.com",
                "username": "홍길동",
                "image": "https://example/photo.jpg"
            },
            "viewNum": 159,
            "commentsNum": 2
        },
        {
            "id": 124,
            "title": "example2",
            "content": "PICK ME UP PLEASE 리액트",
            "firstImage": "https://example/portfolio-photo.png",
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

```json
{
    "totalNum": 0,
    "portfolioList": []
}
```

### fail
**HTTP Status code : 500 Internal Server Error**