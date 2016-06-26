# substr_lib

## Proto type

```c
string substr_lib(string str, int start [, int length [, int utf8 ] ])
```

## Description

사용법은 [substr](http://kr.php.net/manual/kr/function.substr.php) 과 동일하다. 다른점은 내부적으로 2 byte 를 처리해 주며, KSX1001 범위 외의 문자 (똠방각하 나 아햏햏 와 같은 문자) 와 NCR code 들에 대한 처리 루틴이 포함이 되어 있다. utf8 문자열을 자르고 싶을 경우에는 4번째 파라미터(int utf8) 을 1 로 지정을 하면 내부적으로 utf8 을 cp949 로 디코딩 한 후 자른 다음 다시 utf8 로 인코딩을 해 주게 된다.

주의할 것은 utf8 파라미터는 cp949 와 euc-kr 일때만 지원이 된다.

0.1.5 부터는 utf8 옵션을 주지 않아도 내부에서 utf8 감지를 한다.

## Arguments
```
(string) str - The input string. 한글자 이상 입력 되어야 한다.
(int) start
    양수로 지정이 되면, start 위치 부터 문자열을 반환한다. 예를 들어 문자열이 'abcdef'
    일 경우, 0의 위치는 'a', 2의 위치는 'c' 이다.
    
    start가 음수로 지정이 되면, start의 순서는 뒤에서 부터 카운팅 된다.

    문자열이 start로 지정된 수보다 짧을 경우에는 FASLSE를 반환한다.
(int) length (optional)
    길이가 양수로 지정이 되면, start 부터 시작해서 지정된 숫자 만큼의 문자열을 반환한다.

    If length is given and is negative, then that many characters will be omitted from
    the end of string (after the start position has been calculated when a start is
    negative). If start denotes the position of this truncation or beyond, FALSE will
    be returned.

    If length is given and is 0, FALSE or NULL, an empty string will be returned.

    If length is omitted, the substring starting from start until the end of the
    string will be returned.
(int) utf8 (optional)
    1 로 지정을 하면, 내부적으로 utf8 문자열을 CP949로 변환한 후에 수행을 한다.
    결과물은 다시 utf8로 변환하여 반환한다.
    
    주의할 것은 cp949와 euc-kr 일 경우만 지원을 한다. 0.1.5 부터는 이 옵션이
    지정되지 않아도 내부에서 utf8 감지를 자동으로 한다.
```
## Example

```php
<?php
$str = '한글a 와 똠방각하';
echo substr_lib ($str, 0, 10) . "\n";

$str = '한글a 와 똠방각하';
$str = utf8encode_lib ($str);
$str = substr_lib ($str, 0, 10, 1);
echo utf8decode_lib ($str, "cp949");
?>
```

## See also
* [substr](http://kr.php.net/manual/kr/function.substr.php)


