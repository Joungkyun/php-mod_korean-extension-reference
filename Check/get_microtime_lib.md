# get_microtime_lib

## Proto type

```c
int get_microtime_lib(int start, int end)
```

## Description

php 의 microtime 을 이용하여 얻어지는 값을 비교하여 경과 시간을 밀리초로 구하는 함수

## Arguments

* (int) start - 시작 micro seconds. PHP [microtime](http://php.net/manual/kr/function.microtime.php) function으로 구할 수 있다.
* (int) end - 종료 micro senconds.

## Example

```php
<?php
$time1 = microtime();

blah_blah ();

$time2 = microtime();

$time = get_microtime_lib ($time1, $time2);
# print 0.01 sec
echo "$time sec";
?>
```

## See also
None


