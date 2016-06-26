# uniencode_lib

## Proto type

```c
string uniencode_lib (string str [, string start [, string end ] ] )
```

## Description


CP949 또는 EUC-KR 의 문자셋을 NATIVE UNICODE 로 변환을 한다.

start 는 NATIVE UNICODE 의 hex 값 앞쪽의 문자열을 지정하며, end 는 hex 값 뒤의 문자열을 의미한다. 이는 NATIVE UNICODE 의 경우 \uD55C 와 같이 표현을 하는데 여기서는 \u 가 start 가 된다.

uniencode_lib 함수에서는 start 와 end 가 지정이 되지 않았을 경우 기본값으로 start 는 "\u" 로 end 는 NULL 값을 가진다.

## Arguments


## Example

```php
<?php
$a = "한글a 와 똠방각하";

# return "\uD55C\uAE00a\uC640 \uB620\uBC29\uAC01\uD558"
$a = uniencode_lib($a);

$a = "한글a 와 똠방각하";

# return "U-D55C;U-AE00;aU-C640; U-B620;U-BC29;U-AC01;U-D558;"
$a = uniencode_lib($a,"U-",";");
?>
```

## See also
* [unidecode_lib ()](Charset/unidecode_lib.md)


