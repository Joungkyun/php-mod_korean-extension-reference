# human_fsize_lib

## Proto type

```c
string human_fsize_lib (int byte [, int sub [, int unit [, int cunit ] ] ])
```

## Description

byte 또는 bit 값을 읽기 쉬운 단위로 자동으로 표현을 해 준다. sub 의 값은 1 과 0 을 가지며 1 일 경우에는 변환된 값 뒤에 원 byte 값을 표시를 해 준다.

human_fsize_lib 함수는 Kbyte, Mbyte, Gbyte, Tbyte 를 표현해 주며, 각 단위에서 소수점 2 번째 자리에서 반올림이 이루어 진다.

unit 옵션은 1을 지정할 경우에는 Bit 로 처리가 되며, 지정이 되지 않거나 0일 경우에는 byte 로 계산이 된다.

cunit 의 경우 human_fsize_lib 함수가 기본값으로 1024 연산을 하는 것을 다른 수치로 할 수 있도록 지정을 할 수 있다. 이 값을 1000 으로 지정하면, human_fsize_lib 함수는 1000 을 단위로 작동을 한다.

## Arguments

* (int) byte - 변환할 raw data
* (int) sub - 1 or 0. 기본 값 0
  * 1 - 변환 값 뒤에 raw data를 붙여서 반환한다. 1 KB (1024 byte)
  * 0 - 변환 값만 반환한다.
* (int) unit - 1 or 0. 기본 값 0
  * 1 - Bit로 처리를 한다. (주어진 값에 8을 곱한다.)
  * 0 - Byte로 처리를 한다.
* (int) cunit
  * ___human_fzie_lib()___ 함수는 기본적으로 1024 단위로 계산을 한다. 이 파라미터가 지정이 되면, 계산 단위를 주어진 값으로 한다.

## Example

```php
<?php
$a = human_fsize_lib (1024);
echo $a; # 1.00 KB

$a = human_fsize_lib (1024, 1);
echo $a; # 1.00 KB (1024 Bytes) 
?>
```

## See also
None


