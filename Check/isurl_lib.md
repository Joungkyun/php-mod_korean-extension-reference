# is_url_lib

## Proto type

```c
int is_url_lib (string url)
```

## Description

url 이 정확한 것인지 검사하는 함수. url 이 맞으면 url 을 리턴하고 틀리면 null 값을 리턴한다.

## Arguments

* (string) url - 체크를 하기 위한 URL


## Example

```php
<?php
$url = 'htt://oops.org';
$url = is_url_lib ($url);
if ( ! $url ) {
    echo "Invalid URL\n";
    exit;
}
?>
```

## See also
 * [is_email_lib ()](Check/is_email_lib.md)

