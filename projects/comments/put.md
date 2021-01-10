---
description: 프로젝트 페이지의 게시물에 있는 댓글을 수정하는 API입니다
---

# 댓글 수정

## METHOD

```text
PUT
```

## URL

```text
/projects/:id/comments/:commentId
```

* id: 해당 댓글이 작성된 \(프로젝트 페이지의\) 게시물 고유 id
* commentId: 수정할 댓글의 고유 id 

## REQUEST BODY

* content: 댓글 내용 \(string\)

### REQUEST BODY EXAMPLE

```markup
{
    "content": "example comment content"
}
```





