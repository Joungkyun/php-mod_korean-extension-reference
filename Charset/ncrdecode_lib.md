# ncrdecode_lib

## Proto type

```php
string ncrdecode_lib (string str)
```

## Description

ncrdecode_lib() 함수는 16 진수 NCR code 로 되어있는 문자를 CP949 테이블로 변환을 한다.

## Arguments


## Example

```php
<?php
$a = "한글a 와 똠방각하";
$a = ncrencode_lib ($a);
# print "한글a 와 똠방각하"
echo ncrdecode_lib ($a);
?>
```

## See also
* [ncrencode_lib ()](Charset/ncrencode_lib.md)


