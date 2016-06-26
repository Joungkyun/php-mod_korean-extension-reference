# sockmail_lib

## Proto type

```c
int sockmail_lib (string mail [, string from [, string to [, string helo_host [, int debug ] ] ] ])
```

## Description

sockmail_lib 함수는 서버의 smtp daemon 에 의존하지 않고 php korean extension 자체의 기능으로
메일을 발송하는 함수이다.

이 함수는 메일 발송 실패시에 실패한 메일 주소 (rcpt to) 를 배열로 반환을 한다. 모두 성공했을
경우, 빈 배열이 반환이 된다. to 에는 메일이 1개 이상이면 모두 반영 되며, 1 개이상의 to 일 경
우에도 실패한 메일 주소들은 배열로 반환이 된다. (하단 예제 참조)

참고로 cc 역시 to 로 인식한다.

## Arguments

* (string) mail  
메일 본문이 들어간다.  헤더부터 메일 본문까지 완벽하게 구성이 되어져 있어야 한다. 이는 mailsource_lib 함수를 이용하여 생성을 할 수 있다. 만약 임의로 구성을 할 경우에는, From 과 To 는 꼭 한 라인씩으로 구성해야 한다.  <br><br>
잘못된 예:
```
      To: test@test.com, sender@sender.com
          recv@recv.com
```
* (string) from  
보내는 사람의 주소를 지정한다. 이 파라미터를 지정하지 않았을 경우에는 위의 mail 파라미터의 헤더의 From: 부분에서 파싱을 하여 값을 얻는다.  from 의 값은 아래의 형태로 지정이 가능하다.

 * "보낸이" &lt;sender@sender.com&gt;
 * 보낸이 &lt;sender@sender.com&gt;
 * &lt;sender@sender.com&gt;
 * sender@sender.com

* (string) to  
받을 사람의 메일주소를 지정한다. 받을 사람의 메일주소는 from 의 형식을 따른다. 또한 to 파라미터는 쉼표(,) 를 사용하여 여러명에게 메일을 발송할 수 있다. 아래의 예를 참고한다.

```
    "보낸이" <sender AT sender.com>, sender AT sender.com, test AT test.com
```

* (string) helo_host  
SMTP 에 HELO 구문에 적어줄 호스트 명을 적는다. sendmail 의 -f 옵션과 동일하다고 보면 된다.
      
* (int) debug  
메일 발송 처리 과정을 출력을 한다.

## Example

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

<table border=1 width=500>
    <tr>
        <td> 1 이죠</td>
        <td> 2 죠 </td>
    </tr>
    <tr>
        <td colspan=2>COLSPAN=2 입니다.</td>
    </tr>
</table>

</body>
</html>
EOF;
$attach = '/dev/shm/test.html';

$mailmsg = mailsource_lib ($ln, $from, $to, $subject, $body, '', $attach);

$ret = sockmail_lib ($mailmsg, $from, $to);

if ( is_array ($ret) ) {
    foreach ( $ret as $v ) {
        echo "$v 로의 발송에 실패했습니다.\n"
    }
}
?>
```

## See also
None
