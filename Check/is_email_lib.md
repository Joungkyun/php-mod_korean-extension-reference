# is_email_lib

## Proto type

```c
string is_email_lib (string email)
```

## Description


E-MAIL 주소가 정확한 것인지 검사하는 함수. email 주소가 맞으면 email 주소를 리턴하고 틀리면
null 값을 리턴한다. 

## Arguments

* (string) email - 검사할 email 주소

## Example

```php
$email = 'oopsAToops.org';
if ( ($email = is_email_lib ($email)) == null ) {
    echo "Invalid email\n";
    exit;
}
```

## See also
* [is_url_lib ()](Check/is_url_lib.md)

