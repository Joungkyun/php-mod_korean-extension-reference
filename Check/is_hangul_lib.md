# is_hangul_lib

## Proto type

```c
int is_hangul_lib (string string)
```

## Description

이 함수에 들어온 문자 또는 문자열의 첫바이트가 한글의 범위 내 (0xA1A1 - 0xFEFE) 에 들어 있는 문자가 존재 하는지를 테스트하여 존재하면 1을 반환한다. 없으면 0을 반환한다.

이 함수에서 체크하는 한글의 범위라는 것은 EUC-KR 또는 CP949를 의미하여, 정확하게 한글 영역을 의미하는 것은 아니다. 이 함수는 부정확성이 높기 때문에 사용을 권장하지 않는다.

한글 관련하여 정확한 체크를 원한다면, [KSC5601](https://github.com/OOPS-ORG-PHP/KSC5601) pear package를 사용하는 것을 권장 한다.

## Arguments

* (string) string - 검사할 문자 또는 문자열.

## Example

```php
<?php
$str = "abcde한fg";

for ($i=0; $i<strlen($str); $i++ ) {
    if ( is_hangul_lib ($str[$i]) ) {
      $hangul_exists = 1;
    }
}
?>
```

## See also
None

