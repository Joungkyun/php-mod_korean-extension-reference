# unidecode_lib

## Proto type

```c
string unidecode_lib (string str , string to_charset [, string start, string end] )
```

## Description

UNICODE 문자를 EUC-KR, CP949 문자셋으로 변환을 한다.

to_charset 은 변환할 문자셋을 지정하며, EUC-KR 과 CP949 로 지정을 할 수 있다. EUC-KR 로 지정을
했을 경우에는 EUC-KR 범위외의 2 byte 문자들을 NCR 코드로 변환해서 출력을 한다.

start 와 end 는 uniencode_lib() 함수와 동일하다.

## Arguments


## Example

```php
<?php
$a = "U+D55C;U+AE00;aU+C640; U+B620;U+BC29;U+AC01;U+D558;";

# return "한글a와 &#46624;방각하"
$a = unidecode_lib($a,"euc-kr","U+",";");

$a = "U-D55C;U-AE00;aU-C640; U-B620;U-BC29;U-AC01;U-D558;";

# return "한글a와 똠방각하"
$a = unidecode_lib($a,"cp949","U-",";");
?>
```

## See also
* [uniencode_lib ()](Charset/uniencode_lib.md)


