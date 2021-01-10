# 로그인

픽미업 서비스는 현재 구글 소셜 로그인만을 사용합니다.

본 API는 새 유저 정보를 픽미업의 데이터베이스에 저장하고 로그인한 유저의 픽미업 데이터베이스 사용자 테이블의 유저 정보 응답으로 환합니다.

BODY의 email을 기준으로 사용자 테이블에서 해당 사용자를 찾아 기존 사용자인지 신규 가입자인지 판단합니다.

* **새로 픽미업에 가입하는 경우 \(기존에 픽미업 서비스에 로그인 한적 없는 경우\):** 

  이 경우는 픽미업 DB에 로그인하는 유저에 대한 데이터가 없으니 새로 사용자 정보를 추가합니다. 추가한 다음 로그인한 유저의 픽미업 데이터베이스 사용자 테이블의 유저 정보를 응답으로 반환합니다.

* **이미 가입한 경우 \(DB에 이미 해당 사용자의 데이터가 있는 경우\):** 

   로그인한 유저의 픽미업 데이터베이스 사용자 테이블의 유저 정보를 응답으로 반환합니다.

{% hint style="info" %}
픽미업 서비스 자체에서 사용자가 원하는 닉네임과 프로필 이미지를 변경할 수 있기 때문에 신규 가입이 아닌 경우 데이터베이스의 내용을 수정하지 않습니다
{% endhint %}

## METHOD

```text
POST
```

## URL

```text
/login
```

## REQUEST BODY

* username: 사용자 이름 \(string\)
* email: 사용자 이메일 \(string\)
* image: 사용자 프로필 이미지 \(이미지 링크 or base 64 encoded image string\)

해당 리퀘스트의 바디로 보내는 이름, 이메일, 이미지는 소셜 로그인 api에서 제공하는 정보입니다. 현재는 구글 로그인만 사용하니 해당 사용자의 구글 계정에 설정한 이름, 이메일, 프로필 이미지가 되겠습니다.

### REQUEST BODY EXAMPLE

```markup
{
        "username": "이화연",
        "email": "example@gmail.com",
        "image": "https://example.png"
}
```

## RESPONSE

* id: 사용자 고유 id \(number\)
* username: 사용자 이름 \(string\)
* email: 사용자 이메일 \(string\)
* image: 사용자 프로필 이미지 \(이미지 링크 or base 64 encoded image string\)

리스폰스는 모두 픽미업 데이터베이스에 저장된 정보 기준입니다.

### RESPONSE EXAMPLE

```markup
{
    "id": 3,
    "username": "개발짱화여니",
    "email": "example@gmail.com",
    "image": "https://example2.png"
}
```



