# utf8decode_lib

## Proto type

```c
string utf8decode_lib(string str, string type)
```

## Description

UTF8 문자셋을 type 에 지정된 문자셋으로 변환을 한다. type 에는 CP949, EUC-KR, BIG5, SJIS 를 지원한다. EUC-KR 로 지정을 했을 경우에는 EUC-KR 범위외의 2byte 문자를 NCR code 로 변환하여 반환한다.

## Arguments

```
(string) str - input string
(string) type - CP949, EUC-KR, BIG5, SJIS
```

## Example

```php
<?php
$str = "한글a와 똠방각하";
$str = utf8encode_lib($str);
echo utf8decode_lib ($str, 'CP949')."\n";
echo utf8decode_lib ($str, 'EUC-KR')."\n";
?>
```

## See also
* [iconv](http://kr.php.net/manual/kr/function.iconv.php)


