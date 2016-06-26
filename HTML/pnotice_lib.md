# pnotice_lib

## Proto type

```c
void pnotice_lib(string str [, int use_java] )
```

## Description

지정한 문자열을 출력을 하고 다음을 진행한다. perror 와의 차이는 print_error 는 에러메세지를
출력하고 이전화면으로 전환되는 것에 비해 print_notice 는 메세지를 출력하고 그 다음을 진행하게
된다.

use_java 를 1 로 지정을 하면 JAVA script ALERT 을 이용하여 출력을 한다. 쉘에서 이 함수를 사용
할 경우에는 use_java 를 주지 않으면 된다.

## Arguments


## Example

```php
<?php
pnotice_lib("경고 예제 입니다.");
echo "이 메세지가 보여야 합니다.";
?>
```

## See also
* [perror_lib ()](HTML/perror_lib.md)


