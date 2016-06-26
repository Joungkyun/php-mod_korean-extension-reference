# putfile_lib

## Proto type

```c
int putfile_lib(string filename, stirng text, [ int mode, int debug ])
```

## Description

> 이 함수는 [file_put_contenst ()](http://php.net/manual/kr/function.file-put-contents.php) 함수가 만들어 지기 전에 작성이 되었다. 이 함수 대신 [file_put_contenst ()](http://php.net/manual/kr/function.file-put-contents.php) 함수를 사용 하도록 한다.

특정 내용을 파일에 기록을 한다.

이 함수는 쓰기 성공 시에는 0을 반환하며, 실패 시에는 -1 을 반환한다.

## Arguments
```
(string) filename - 저장할 파일 경로
(string) text - 저장할 내용
(int) mode (optional)
    mode 를 지정하지 않을 경우에는 기존의 파일이 존재 할 경우 덮어쓰기를 하게 되며,
    1로 지정을 할 경우에는 존재할 경우 덧붙이기를 하게되며, 존재하지 않을 경우에는
    새 파일로 기록을 하게 된다.
(int) debug (optional) - 디버그 메시지 출력
```
## Example

```php
<?php
$text = 'test';
$path = './doc/example.txt';
if ( putfile_lib ($path,$text,1) == -1 ) {
    echo "Failed\n";
} else {
    echo "Success\n";
}
?>
```

## See also
 * [file_put_contenst ()](http://php.net/manual/kr/function.file-put-contents.php)

