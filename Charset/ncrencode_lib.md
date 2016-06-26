# ncrencode_lib

## Proto type

```c
string ncrencode_lib (string str [, int type])
```

## Description

ncrencode_lib() 함수는 CP949 테이블의 2 byte 문자를 16진수 NCR 코드로 변경을 한다.
type 을 1 로 지정했을 경우에는 EUC-KR 의 범위외의 2 byte 문자만 16 진수 NCR 코드로
변경을 한다.

이 함수는 GD 에서 한글을 사용할 때, GD 에 따로 한글 패치를 하지 않고 한글을 사용할때
유용하게 사용할 수 있다.

type 을 1 로 지정할 경우는, MSIE 의 경우에는 KSX1001 이외의 범위를 알아서 NCR 코드로
변환을 해 주나 타 브라우져에서는 잘 지원이 되지 않으므로 다른 브라우져의 호환성을 생각할
때 이 함수를 사용할 수 있다.

## Arguments


## Example

```php
<?php
$a = "한글a 와 똠방각하";
# return "&#54620;&#44544;a &#50752; &#46624;&#48169;&#44033;&#54616;"
$a = ncrencode_lib ($a);

$a = "한글a 와 똠방각하";
# return "한글a 와 &#46624;방각하"
$a = ncrencode_lib ($a,1);
?>
```

## See also
* [ncrdecode_lib ()](Charset/ncrdecode_lib.md)


