# get_hostname_lib

## Proto type

```c
string get_hostname_lib (int reverse [, string addr ])
```

## Description

reverse 는 ip address 의 hostname 을 찾을것인지 여부를 결정한다. 값은 0 과 1 로 지정을 한다.
0 은 hostname 을 찾지않으며, 1 은 hostname 을 검색을 하게 된다. IP_ADDR 은 REVERSE 의 값이 1
일때만 지정을 한다. 0 일 경우에는 지정할 필요가 없다.

IP_ADDR 을 지정할 경우는 이 함수의 외부에서 이미 ip address 를 구해 놓았고 이 ip address  의
hostname 을 검색하고 싶을 경우에 사용을 한다.(예제1)

IP_ADDR 을 지정 하지 않을 경우에는 이 함수 자체에서 IP address 를 구해야 할 경우에 사용을 한
다.(예제2, 3)

## Arguments


## Example

다음의 결과는

```111.111.111.111 의 hostname 은 domain.com 입니다.```

또는

```111.111.111.111 의 hostname 은 111.111.111.111 입니다.```

의 결과를 보이게 된다. 이는 hostname lookup 성공과 실패여부에 따라 출력되는 결과가 다르기 때문이다.

get_hostname_lib(0,$a) 는 아무 의미가 없다. 이미 ip address 가 구해져 있는데 REVERSE 를 0 으로 지정하면 ip address 값을 구하겠다는 것이 되므로 하나마나한 결과를 나오게 된다.

```php
<?php
$a = "111.111.111.111";
$b = get_hostname_lib(1,$a);

echo "$a 의 hostname 은 $b 입니다.";
?>
```
다음의 결과 값은 111.111.111.111 을 가지게 된다.

```php
<?php
$a = get_hostname_lib(0);
echo $a;
?>
```

다음의 결과 값은 ___111.111.111.111___ 또는 ___domain.com___ 을 가지게 된다.

```php
<?php
$a = get_hostname_lib(1);
echo $a;
?>
```

## See also
None


