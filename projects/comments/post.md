---
description: 프로젝트 페이지의 게시물에 댓글을 생성하는 API입니다
---

# 댓글 생성

## METHOD

```text
POST
```

## URL

```text
/projects/:id/comments
```

* id: 프로젝트 페이지의 게시물 고유 id

## REQUEST BODY

* email: 댓글 작성자 이메일 \(string\)
* content: 댓글 내용 \(string\)

### REQUEST BODY EXAMPLE

```markup
{
        "email": "example@gmail.com",
        "content": "example comment content"
}
```





