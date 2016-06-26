# check_htmltbale_lib

## Proto type

```c
int check_htmltable_lib (string text)
```

## Description

html 을 사용하여 글을 쓰기가 가능할 때 table 입력이 잘못되어 디자인이 망가지는 것을 방지하거
나 또는 table 태그를 제대로 사용하였는지 체크를 하여 에러 코드를 반환하는 함수이다.

## Arguments

* (string) text - 검사할 문자열

## Example

```php
<?php
$str = "<table><tr><td>";
if ( check_htmltable_lib ($str) ) {
    echo "TABLE 태그를 잘못 사용하였습니다.\n";
    exit;
}
?>
```

## See also
None
