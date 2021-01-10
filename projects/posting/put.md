---
description: 해당 id를 가진 프로젝트 페이지의 게시물을 수정하는 API입니다
---

# 게시물 수정

## METHOD

```text
PUT
```

## URL

```text
/projects/:id
```

* id: 프로젝트 페이지의 수정하려는 게시물 고유 id

## REQUEST BODY

* title: 게시물 제목 \(string\)
* content: 게시물 내용 \(string\)
* email: 작성자 이메일 \(string\)
* category: 카테고리 \(string\) 
* recruitmentField: 구인분야 \(string\)
* region: 지역 \(string\)
* projectCategory: 프로젝트 종류 \(string\)
* tags: 태그 - 최대 5개 \(string 배열\)
* image: 이미지 \(base64 encoded string / BLOB\)

### REQUEST BODY EXAMPLE

```markup
{
        "title": "예시 프로젝트",
        "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur sit.",
        "email": "example@gmail.com",
        "category": "웹",
        "recruitmentField": "디자인",
        "region": "서울",
        "projectCategory": "공모전",
        "tags": ["포토샵", "제플린”],
        “image”: “base64 encoded string”
}
```





