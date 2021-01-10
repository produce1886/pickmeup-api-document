---
description: 포트폴리오 페이지에 있는 게시물 목록을 조건에 맞게 불러오는 API입니다
---

# 게시물 목록 불러오기

## METHOD

```text
POST
```

## URL

```text
/portfolios/list
```

## REQUEST BODY

* page: 불러올 페이지 \(number\)
* size: 불러올 게시물 개수 \(number\)
* sortBy: 정렬 기준\("createdDate"/"commentsNum"/"viewNum"\)
  * 순서대로 최신순, 댓글순, 조회순
  * 기본은 최신순으로 프론트에서 기본적으로 "createdDate"를 전달
* category: 검색하는 카테고리 \(string\) 
* recruitmentField: 검색하는 구인분야 \(string\)
* keyword: 검색어 \(string\)

page에서부터 size만큼 게시물을 불러온다.

sortBy, category, recruitmentField, keyword는 optional이고, 만약 사용자가 따로 지정하지 않은 경우는 각 key들의 value를 ""\(빈 문자열\)로 보냅니다. 이 경우, 필터링하지 않고 모든 게시물을 불러옵니다.   

### REQUEST BODY EXAMPLE

```markup
{
    "page": 0,
    "size": 10,
    "sortBy": "createdDate",
    "category": "",
    "recruitmentField": "개발",
    "keyword": "리액트"
}
```

포트폴리 게시물 중 recruitmentField가 개발로 되어 있는 게시들 중 "리액트" 검색어를 적용한 검색 결과를 응답합니다. 

## RESPONSE

* totalNum: 포트폴리오 게시글 총 개수 \(number\)
* portfolioList: 포트폴리오 게시글 리스트 \(portfolio 배열\)
  * portfolio
    * id: 게시물 고유 id \(number\)
    * title: 게시물 제목 \(string\)
    * content: 게시물 내용 \(string\)
    * image: 이미지 배열 중 첫번째 이미지 \(base64 encoded string / BLOB\)
      * 이미지가 아예 없는 경우 ""\(빈 문자열\) 보
    * category: 카테고리 \(string\) 
    * recruitmentField: 구인분야 \(string\)
    * portfolioTag: 포트폴리오 태그 \(tag 배열\)
      * tag
        * id: 태그 id \(number\)
        * tag: 태그 내용 \(string\)
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

```markup
{
    "totalNum": 162,
    "portfolioList": [
        {
            "id": 123,
            "title": "example",
            "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur sit.",
            "image": "",
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
            "image": "base64 encoded image",
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





