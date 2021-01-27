---
description: 해당 id를 가진 포트폴리오 페이지의 게시물을 수정하는 API입니다
---

# 게시물 수정

## METHOD

```text
PUT
```

## URL

```text
/portfolios/:id
```

* id: 포트폴리오 페이지의 수정하려는 게시물 고유 id

## REQUEST

| name             | type             | description                      |
| ---------------- | ---------------- | -------------------------------- |
| title            | string           | 게시물 제목                      |
| content          | string           | 게시물 내용                      |
| authorEmail      | string           | 작성자 이메일                    |
| category         | string           | 카테고리                         |
| recruitmentField | string           | 구인분야                         |
| portfolioTags    | string 배열      | 포트폴리오 태그, 최대 5개        |
| image            | string(URI) 배열 | 포트폴리오 이미지 경로, 최대 5개 |

### REQUEST BODY EXAMPLE

```json
{
        "title": "예시 포트폴리오",
        "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur sit.",
        "authorEmail": "example@gmail.com",
        "category": "웹",
        "recruitmentField": "디자인",
        "portfolioTags": ["포토샵", "제플린"],
        "image": ["uri1", "uri2"]
}
```

