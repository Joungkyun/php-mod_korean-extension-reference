# substr_lib

## Proto type

```c
string substr_lib(string str, int start [, int length [, int utf8 ] ])
```

## Description

사용법은 substr 과 동일하다. 다른점은 내부적으로 2 byte 를 처리해 주며, KSX
1001 범위외의 문자 (똠방각하 나 아햏햏 와 같은 문자) 와 NCR code 들에 대한
처리 루틴이 포함이 되어 있다. utf8 문자열을 자르고 싶을 경우에는 4번째 파라
미터(int utf8) 을 1 로 지정을 하면 내부적으로 utf8 을 cp949 로 디코딩 한 후
자른다음 다시 utf8 로 인코딩을 해 주게 된다.

주의할 것은 utf8 파라미터는 cp949 와 euc-kr 일때만 지원이 된다.

0.1.5 부터는 utf8 옵션을 주지 않아도 내부에서 utf8 감지를 한다.

## Arguments


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
None


