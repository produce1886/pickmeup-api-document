---
description: 해당 id를 가진 댓글 하나를 불러오는 API입니다
---

# 댓글 읽기

## METHOD

```text
GET
```

## URL

```text
/projects/:id/comments/:commentId
```

* id: 해당 댓글이 작성된 \(프로젝트 페이지의\) 게시물 고유 id
* commentId: 해당 댓글의 고유 id

## RESPONSE

* createdDate: 댓 작성 날짜 \(string / DATETIME\)
* modifiedDate: 댓 수정 날짜 \(string / DATETIME\)
* id: 댓글 고유 id \(number\)
* content: 댓글 내용 \(string\)
* email: 댓글 작성자의 이메일 \(string\)

### RESPONSE EXAMPLE

```markup
{
    "id": 26,
    "content": "example comment",
    "email": "example@ewhain.net",
    "createdDate": "2020-11-16T17:04:01",
    "modifiedDate": "2020-11-16T17:04:10"
}
```





