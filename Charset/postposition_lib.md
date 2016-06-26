# postposition_lib

## Proto type

```c
string postposition_lib (string str, string postposition, int utf8)
```

## Description

해당 단어의 종성을 구분하여 조사를 결정한다. int utf8 의 값을 1 로 지정할 경우에는
utf8 로 인코딩된 문자열을 제어할 수 있다.

## Arguments

```
str          조사가 붙을 단어나 문장을 지정. 만약, 단어의 마지막이 영어일 경우에는
             마지막 글자가 영어 모음일 경우와 끝에서 2 글자가 "er, ed, or" 일 경우
             에는 종성이 없는 것으로 판단을 하여 처리 한다. 이 부분은 아마 계속 업
             데이트 되어야 할 문제일 것이다.

postposition str 에 붙일 조사를 지정. "이, 가, 은, 는, 을, 를, 아, 야" 중에서 지정
             한다. "이, 가" 와 "을, 를" 의 관계처럼 쌍으로 사용되는 것들은 "이" 또
             는 "가" 하나만 지정을 하면 postposition_lib() 함수에서 알아서 "이" 와
             "가" 중에 어느 것을 사용할 지를 판단을 한다.

utf8         utf8 로 인코딩된 문자열을 처리할 경우에는 이 값을 1 로 지정을 한다.
```

## Example

```php
<?php
$a = '철수';
$b = '영만';

# print "철수를"
echo $a . postposition_lib ($a, "을") . "\n";

# print "영만이"
echo $b . postposition_lib($b, "가") . "\n";

# print "철수가"
echo utf8encode_lib($a) . postposition_lib (utf8encode_lib($a), utf8encode_lib("가"), 1) . "\n";
?>
```

## See also
None


