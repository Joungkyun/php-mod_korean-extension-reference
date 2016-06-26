# utf8encode_lib

## Proto type

```c
string utf8encode_lib (string str [, string charset])
```

## Description

charset 으로 지정된 2 byte 문자셋을 UTF8 로 변환한다. charset 이 지정되지 않으면, 기본값으로 EUC-KR 이다. 지원되는 charset 은 EUC-KR, BIG5, SJIS 이다. KSX 1001 범위외의 문자 역시 EUC-KR 로 지정하여 내부적으로 처리가 가능 하므로, 한국어 처리를 ECU-KR 로 한다고 생각을 하면 된다.

## Arguments

```
(stirng) str - input string
(string) charset
    지정되지 않으면, 기본값으로 EUC-KR 이다. 지원되는 charset 은 EUC-KR, BIG5, SJIS
    이다. KSX 1001 범위외의 문자 역시 EUC-KR 로 지정하여 내부적으로 처리가 가능 하므로,
    한국어 처리를 ECU-KR 로 한다고 생각을 하면 된다.
```

## Example

```php
<?php
$str = "한글a와 똠방각하";
$str = utf8encode_lib ($str, "EUC-KR");
echo $str . "\n";
?>
```

## See also
* [utf8decode_lib ()](Check/utf8decode_lib.md)


