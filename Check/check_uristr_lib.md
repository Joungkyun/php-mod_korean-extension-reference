# check_uristr_lib

## Proto type

```php
int check_uristr_lib (string variable)
```

## Description


문자열에 메타 캐릭터가 존재할 경우, 1을 리턴한다. 이 함수에서 걸리는 문자는 한글,알파벳, _, - 문자를 제외하고는 모두 에러메세지가 출력된다.

check_filename_lib 함수와의 다른점은 도트(.) 문자를 허락하지 않는다는 점이다.

## Arguments


## Example

```php
$s = "asdf..asdf";
if ( check_uristr_lib ($s)) {
  echo "사용할 수 없는 문자가 들어 있습니다.\n";
  exit;
}
```

## See also
* [check_filename_lib ()](Check/check_filename_lib.md)


