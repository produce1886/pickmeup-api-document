---
description: 포트폴리오 페이지의 게시물을 생성하는 API입니다
---

# 게시물 생성

## METHOD

```text
POST
```

## URL

```text
/portfolios
```

## REQUEST BODY

* title: 게시물 제목 \(string\)
* content: 게시물 내용 \(string\)
* email: 작성자 이메일 \(string\)
* category: 카테고리 \(string\) 
* recruitmentField: 구인분야 \(string\)
* tags: 태그 - 최대 5개 \(string 배열\)
* image: 이미지 - 최대 5개 \(base64 encoded string / BLOB **배열**\)

### REQUEST BODY EXAMPLE

```markup
{
        "title": "예시 프로젝트",
        "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur sit.",
        "email": "example@gmail.com",
        "category": "웹",
        "recruimentField": "디자인",
        "tags": ["포토샵", "제플린”],
        “image”: [
                “base64 encoded string1",
                “base64 encoded string2"
                ]
}
```





