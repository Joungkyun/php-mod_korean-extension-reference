# perror_lib

## Proto type

```c
string perror_lib(string str [, int use_java [, string move_page [, int move second ] ] ])
```

## Description

에러 메세지를 출력하고 이전 화면으로 돌아간다. 쉘에서 이 함수를 사용할 경우에는 use_java 를
0 으로 지정을 하여 java script 가 아닌 문자열 출력으로 되게 할 수 있다. move_page 를 지정했을
경우에는 지정한 페이지로 이동을 하게 된다. move_page 를 지정했을 경우 java 를 사용하는
경우에는 바로 이동을 하며, 자바를 사용하지 않는 경우에는 move second 에 지정한 초가 경과한 후에
이동을 한다. 지정을 하지 않았을 경우 기본값은 5초 이다.

use_java 를 1 로 지정을 했더라도 text browser (lynx, links, w3m) 의 경우에는 use_java 0 으로
작동을 한다. shell 에서 사용을 했을 경우 역시 마찬가지 이다. use_java 는 java script 가 지원이
되는 브라우져에서만 적용이 된다.

## Arguments


## Example

```php
<?php
if ( ! $string ) perror_lib ("문자열이 비었습니다.");
if ( ! $string ) perror_lib ("문자열이 비었습니다.", 1);
if ( ! $string ) perror_lib ("문자열이 비었습니다.", 1, "http://test.com/login.php");
if ( ! $string ) perror_lib ("문자열이 비었습니다.", 0, "http://test.com/login.php", 3);
?>
```

## See also
* [pnotice_lib ()](HTML/pnotice_lib.md)

