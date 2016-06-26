# is_iis_lib

## Proto type

```c
int is_iis_lib(void)
```

## Description

웹서버가 iis 서버인지를 체크한다. 웹서버가 iis 이면 1 을 리턴하고 아니면 0 을 리턴한다.

## Arguments

void


## Example

```php
<?php
if ( is_iis_lib () )
  echo "This is IIS web server\n";
else
  echo "This is not IIS web server\n";
?>
```

## See also
 * [is_windows_lib ()](Check/is_windwos_lib.md)
