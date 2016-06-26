# mailsource_lib

## Proto type

```c
string mailsource_lib (string language, string from ,string to, string subject,
                       string body [, string plainbody [, string attach ]])
```

## Description

언어, 보내는 주소, 받는 주소, 메일 제목, 메일 본문, 첨부파일등의 주소를 이용하여 메일의 헤더와 본문을 파싱한다.

이 함수는 mail() 함수를 이용하여 첨부파일까지 발송할 수 있게 사용하는데 유용하다.  mail() 함수를 이용하여 첨부파일을 보내는 것은 하단의 예제를 참고하도록 한다.

메일 제목과 메일 본문은 BASE 64 인코딩을 하여 파싱하며, 첨부파일 역시 BASE64 인코딩을 지원한다. 본문의 경우에는 text/palin 과 text/html 의 Multi-Part 로 구성이 된다.

첨부파일의 갯수는 현재 1 개만 지원이 된다.

이 함수는 sockmail_lib() 를 지원하기 위한 함수이다. 이 함수는 서버의 메일 데몬에 의존하지 않고 oops php extension 자체에서 메일을 발송할 수 있도록 하기 위한 함수이다.

## Arguments
```
language  메일의 언어 타입을 설정한다. 현재는 ko/en 만 지원을 한다. ko 로 지정을 했을 경우에
          는 Charset 이 EUC-KR 로 설정이 되며, en 으로 설정을 했을 경우에는 iso-8859-1 로 지
          정이 된다. 값은 대소문자를 구분하지 않는다. 기본값은 en 이다.

from      보내는 이의 주소를 지정한다. 보내는 이의 주소는 다음의 표현 양식이 가능하다.
          sender@domain.com
          보내는이 <sender@domain.com>
          "보내는이" <sender@domain.com>

to        받는 이의 주소를 지정한다. 받는 이는 쉼표(,)를 이용하여 여러명을 지정할 수 있다.

subject   메일의 제목을 지정한다. base64 인코딩이 된다.

body      메일 본문을 지정한다. plain/html 모두 사용할 수 있다.

plainbody 생략 가능하다. body 를 html 양식으로 사용한다면, html 을 지원하지 않는 메일 클라이
          언트들을 위한 plain 으로 된 내용을 적어 주도록 한다. 만약 plainbody 를 지정하지 않
          을 경우에는 body 의 내용중에서 html tag 를 삭제한 내용을 plain part 로 보내게 된다.

attach    첨부파일의 절대 경로를 지정하도록 한다. 생략 가능하다.
```
## Example

### 1. 첨부 파일이 없을 경우
```php
<?php
$ln = 'ko';
$from = '보내는이 <sender@domain.org>';
$to = '받는 이 <reciever@to.org>, "어드민" <admin@domain.org>, who@domain.org';
$subject = 'subject 안에 "따옴표" 가 있습니다.';
$body = <<<EOF
<html>
    <head><title>>html 문서</title></head>
    <body>
        html 문서를 작성합니다.

        <table border="1" width="500">
        <tr>
            <td> 1 이죠</td>
            <td> 2 죠 </td>
        </tr>
        <tr>
            <td colspan=2>
                COLSPAN=2 입니다.
            </td>
        </tr>
        </table>
    </body>
</html>
EOF;

$a = mailsource_lib ($ln, $from, $to, $subject, $body);

echo $a . "\n";
?>
```

출력 결과는 다음과 같다. ***plain body***를 별도로 지정하지 않아서, body를 parsing 하여 ***plain/text*** part를 자동으로 생성한다.

```
Message-ID: <200208070334331454318271@sendar>
From: =?EUC-KR?B?ud60wsDM?= <gsendar@domain.org>
MIME-Version: 1.0
Date: Wed, 07 Aug 2002 03:34:33 KST
To: =?EUC-KR?B?ud60wiDAzA==?= <greciever@to.org>,
    =?EUC-KR?B?Ir7uteW5ziI=?= <admin@domain.org>, who@domain.org
Subject: =?EUC-KR?B?c3ViamVjdCC+yL+hICK1+7/Ix6UiILChIMDWvcC0z7TZLg==?=
Content-Type: multipart/alternative;
              boundary="--=_NextPart_000_0003_D5016B9B.16AFB9B6"


This is a multi-part message in MIME format.

----=_NextPart_000_0003_D5016B9B.16AFB9B6
Content-Type: text/plain; charset=EUC-KR
Content-Transfer-Encoding: base64

aHRtbCC5rrytDQoNCmh0bWwgua68rbimIMDbvLrH1bTPtNkuDQoNCg0KDQog
MSDAzMHSDQogMiDB0iANCg0KDQoNCkNPTFNQQU49MiDA1LTPtNku

----=_NextPart_000_0003_D5016B9B.16AFB9B6
Content-Type: text/html; charset=EUC-KR
Content-Transfer-Encoding: base64

PGh0bWw+CjxoZWFkPjx0aXRsZT5odG1sILmuvK08L3RpdGxlPjwvaGVhZD4K
PGJvZHk+Cmh0bWwgua68rbimIMDbvLrH1bTPtNkuCgo8dGFibGUgYm9yZGVy
PTEgd2lkdGg9NTAwPgo8dHI+Cjx0ZD4gMSDAzMHSPC90ZD4KPHRkPiAyIMHS
IDwvdGQ+CjwvdHI+Cjx0cj4KPHRkIGNvbHNwYW49Mj4KQ09MU1BBTj0yIMDU
tM+02S4KPC90ZD4KPC90cj4KPC90YWJsZT4KPC9ib2R5Pgo8L2h0bWw+

----=_NextPart_000_0003_D5016B9B.16AFB9B6--
```

### 2. 첨부 파일이 있을 경우

```php
<?php
$ln = 'ko';
$from = '보내는이 <sender@domain.org>';
$to = '받는 이 <reciever@to.org>, "어드민" <admin@domain.org>, who@domain.org';
$subject = 'subject 안에 "따옴표" 가 있습니다.';
$body = <<<EOF
<html>
    <head><title>>html 문서</title></head>
    <body>
        html 문서를 작성합니다.

        <table border="1" width="500">
        <tr>
            <td> 1 이죠</td>
            <td> 2 죠 </td>
        </tr>
        <tr>
            <td colspan=2>
                COLSPAN=2 입니다.
            </td>
        </tr>
        </table>
    </body>
</html>
EOF;
$attach = "/dev/shm/test.html";

$a = mailsource_lib ($ln, $from, $to, $subject, $body, '', $attach);

echo $a . "\n";
?>
```

결과물은 다음과 같다.

```
Message-ID: <200208070340371349604267@sendar>
From: =?EUC-KR?B?ud60wsDM?= <sendar@domain.org>
MIME-Version: 1.0
Date: Wed, 07 Aug 2002 03:40:37 KST
To: =?EUC-KR?B?ud60wiDAzA==?= <reciever@to.org>,
    =?EUC-KR?B?Ir7uteW5ziI=?= <admin@domain.org>, who@domain.org
Subject: =?EUC-KR?B?c3ViamVjdCC+yL+hICK1+7/Ix6UiILChIMDWvcC0z7TZLg==?=
Content-Type: multipart/mixed;
              boundary="--=_NextPart_000_0003_D5018259.34109528"


This is a multi-part message in MIME format.

----=_NextPart_000_0003_D5018259.34109528
Content-Type: multipart/alternative;
              boundary="--=_NextPart_000_0003_D5018259.F2109528"


----=_NextPart_000_0003_D5018259.F2109528
Content-Type: text/plain; charset=EUC-KR
Content-Transfer-Encoding: base64

aHRtbCC5rrytDQoNCmh0bWwgua68rbimIMDbvLrH1bTPtNkuDQoNCg0KDQog
MSDAzMHSDQogMiDB0iANCg0KDQoNCkNPTFNQQU49MiDA1LTPtNku

----=_NextPart_000_0003_D5018259.F2109528
Content-Type: text/html; charset=EUC-KR
Content-Transfer-Encoding: base64

PGh0bWw+CjxoZWFkPjx0aXRsZT5odG1sILmuvK08L3RpdGxlPjwvaGVhZD4K
PGJvZHk+Cmh0bWwgua68rbimIMDbvLrH1bTPtNkuCgo8dGFibGUgYm9yZGVy
PTEgd2lkdGg9NTAwPgo8dHI+Cjx0ZD4gMSDAzMHSPC90ZD4KPHRkPiAyIMHS
IDwvdGQ+CjwvdHI+Cjx0cj4KPHRkIGNvbHNwYW49Mj4KQ09MU1BBTj0yIMDU
tM+02S4KPC90ZD4KPC90cj4KPC90YWJsZT4KPC9ib2R5Pgo8L2h0bWw+

----=_NextPart_000_0003_D5018259.F2109528--

----=_NextPart_000_0003_D5018259.34109528
Content-Type: text/html; name="test.html"
Content-Transfer-Encoding: base64
Content-Disposition: inline; filename="test.html"

LyogCiAgICstLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0t
LS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tKwogICB8IFBIUCBW
ZXJzaW9uIDQgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAg
ICAgICAgICAgICAgICAgICAgIHwKICAgKy0tLS0tLS0tLS0tLS0tLS0tLS0t
LS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0t
LS0tLS0rCiAgIHwgQ29weXJpZ2h0IChjKSAxOTk3LTIwMDIgVGhlIFBIUCBH
cm91cCAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgfAogICArLS0t
LS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0t
LS0tLS0tLS0tLS0tLS0tLS0tLS0tLSsKICAgfCBUaGlzIHNvdXJjZSBmaWxl
IGlzIHN1YmplY3QgdG8gdmVyc2lvbiAyLjAyIG9mIHRoZSBQSFAgbGljZW5z
ZSwgICAgICB8CiAgIHwgdGhhdCBpcyBidW5kbGVkIHdpdGggdGhpcyBwYWNr
YWdlIGluIHRoZSBmaWxlIExJQ0VOU0UsIGFuZCBpcyAgICAgICAgfAogICB8
IGF2YWlsYWJsZSBhdCB0aHJvdWdoIHRoZSB3b3JsZC13aWRlLXdlYiBhdCAg
ICAgICAgICAgICAgICAgICAgICAgICAgIHwKICAgfCBodHRwOi8vd3d3LnBo
cC5uZXQvbGljZW5zZS8yXzAyLnR4dC4gICAgICAgICAgICAgICAgICAgICAg
ICAgICAgICAgICB8CiAgIHwgSWYgeW91IGRpZCBub3QgcmVjZWl2ZSBhIGNv
cHkgb2YgdGhlIFBIUCBsaWNlbnNlIGFuZCBhcmUgdW5hYmxlIHRvICAgfAog
ICB8IG9idGFpbiBpdCB0aHJvdWdoIHRoZSB3b3JsZC13aWRlLXdlYiwgcGxl
YXNlIHNlbmQgYSBub3RlIHRvICAgICAgICAgIHwKICAgfCBsaWNlbnNlQHBo
cC5uZXQgc28gd2UgY2FuIG1haWwgeW91IGEgY29weSBpbW1lZGlhdGVseS4g
ICAgICAgICAgICAgICB8CiAgICstLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0t
LS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0t
KwogICB8IEF1dGhvcjogUmFzbXVzIExlcmRvcmYgPHJhc211c0BsZXJkb3Jm
Lm9uLmNhPiAgICAgICAgICAgICAgICAgICAgICAgIHwKICAgKy0tLS0tLS0t
LS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0t
LS0tLS0tLS0tLS0tLS0tLS0rCiovCgoKLyogJElkOiByZWcuaCx2IDEuMTUg
MjAwMi8wMi8yOCAwODoyNjo0OSBzZWJhc3RpYW4gRXhwICQgKi8KCiNpZm5k
ZWYgUkVHX0gKI2RlZmluZSBSRUdfSAoKUEhQQVBJIGNoYXIgKnBocF9yZWdf
cmVwbGFjZShjb25zdCBjaGFyICpwYXR0ZXJuLCBjb25zdCBjaGFyICpyZXBs
YWNlLCBjb25zdCBjaGFyICpzdHJpbmcsIGludCBpY2FzZSwgaW50IGV4dGVu
ZGVkKTsKClBIUF9GVU5DVElPTihlcmVnKTsKUEhQX0ZVTkNUSU9OKGVyZWdp
KTsKUEhQX0ZVTkNUSU9OKGVyZWdpX3JlcGxhY2UpOwpQSFBfRlVOQ1RJT04o
ZXJlZ19yZXBsYWNlKTsKUEhQX0ZVTkNUSU9OKHNwbGl0KTsKUEhQX0ZVTkNU
SU9OKHNwbGl0aSk7ClBIUEFQSSBQSFBfRlVOQ1RJT04oc3FsX3JlZ2Nhc2Up
OwoKdHlwZWRlZiBzdHJ1Y3QgewoJSGFzaFRhYmxlIGh0X3JjOwp9IHBocF9y
ZWdfZ2xvYmFsczsKClBIUF9NSU5JVF9GVU5DVElPTihyZWdleCk7ClBIUF9N
U0hVVERPV05fRlVOQ1RJT04ocmVnZXgpOwpQSFBfTUlORk9fRlVOQ1RJT04o
cmVnZXgpOwoKCiNpZmRlZiBaVFMKI2RlZmluZSBSRUcodikgVFNSTUcocmVn
X2dsb2JhbHNfaWQsIHBocF9yZWdfZ2xvYmFscyAqLCB2KQojZWxzZQojZGVm
aW5lIFJFRyh2KSAocmVnX2dsb2JhbHMudikKI2VuZGlmCgojZW5kaWYgLyog
UkVHX0ggKi8=

----=_NextPart_000_0003_D5018259.34109528--
```

### 3. php mail() 함수와 같이 사용할 경우

```php
<?php
$ln = 'ko';
$from = '보내는이 <sender@domain.org>';
$to = '받는 이 <reciever@to.org>, "어드민" <admin@domain.org>, who@domain.org';
$subject = 'subject 안에 "따옴표" 가 있습니다.';
$body = <<<EOF
<html>
    <head><title>>html 문서</title></head>
    <body>
        html 문서를 작성합니다.

        <table border="1" width="500">
        <tr>
            <td> 1 이죠</td>
            <td> 2 죠 </td>
        </tr>
        <tr>
            <td colspan=2>
                COLSPAN=2 입니다.
            </td>
        </tr>
        </table>
    </body>
</html>
EOF;
$attach = "/dev/shm/test.html";

$a = mailsource_lib ($ln, $from, $to, $subject, $body, '', $attach);

$headsrc[] = "/(\r)?\n/i";
$headdes[] = "!!ENTER!!";
$headsrc[] = "/(.+!!ENTER!!)This is a multi-part message in MIME format.+/i";
$headdes[] = "\\1";
$headsrc[] = "/!!ENTER!!/i";
$headdes[] = "\r\n";
$head = trim (preg_replace ($headsrc, $headdes, $a));

$bodysrc[] = "/(\r)?\n/i";
$bodydes[] = "!!ENTER!!";
$bodysrc[] = "/.+!!ENTER!!(This is a multi-part message in MIME format.+)/i";
$bodydes[] = "\\1";
$bodysrc[] = "/!!ENTER!!/i";
$bodydes[] = "\r\n";
$body = trim (preg_replace ($bodysrc, $bodydes, $a));

mail($to, $subject, $body, $head, "-f $from");
?>
```

## See also
* [mail ()](http://php.net/manual/kr/function.mail.php)
* [sockmail_lib ()](Mail/sockmail_lib.md)


