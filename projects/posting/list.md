---
description: 프로젝트 페이지에 있는 게시물 목록을 조건에 맞게 불러오는 API입니다
---

# 게시물 목록 불러오기

## METHOD

```text
GET
```

## URL

```text
/projects/list
```

## URL EXAMPLE
```http request
GET /projects/list?page=0&size=10&sort=viewNum,desc&region=서울&projectSection=창업
```

## QUERY STRING

|name|type|require|description
|---|---|---|---|
|page|number|선택, 기본값 = 0|불러올 페이지|
|size|string|선택, 기본값 = 20|불러올 게시물 개수|
|sort|string|선택|정렬 기준 / 기본값은 오름차순 정렬이며, 내림차순은 뒤에 `,desc`를 붙임 (ex: 최신순 `sort=createdDate,desc`)|
|category|string|선택|검색하는 카테고리|
|recruitmentField|string|선택|검색하는 구인분야|
|region|string|선택|검색하는 지역|
|projectSection|string|선택|검색하는 프로젝트 종류|
|keyword|string|선택|검색어, 주어질 경우 게시물 제목이나 내용에 검색어가 포함되는 게시물만 필터링|

> page에서부터 size만큼 게시물을 불러온다.  
> 빈 스트링으로 온 경우는 필터링을 하지 않는다. 예를 들어 category, recruitmentField, region, 
> projectSection, keyword가 모두 주어지지 않은 경우 모든 게시물을 sort 조건으로 정렬하여, size만큼 page별로 가져온다. 

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

```json
{
    "totalNum": 10,
    "projectList": [
        {
            "id": 123,
            "title": "example",
            "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur sit.",
            "category": "게임",
            "recruitmentField": "기획",
            "region": "서울",
            "projectSection": "창업",
            "projectTags": [],
            "createdDate": "2021-01-07T14:49:52",
            "modifiedDate": "2021-01-08T14:05:43",
            "user": {
                "id": 2,
                "email": "example@gmail.com",
                "username": "홍길동",
                "image": "https://example/photo.jpg"
            },
            "viewNum": 121,
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
            "projectTags": [
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
            "viewNum": 15,
            "commentsNum": 7
        },
        ... // 이후 반복
    ]
}
```





