# readfile_lib

## Proto type

```c
string readfile_lib (string filename [, int use_include_path])
```

## Description

> 이 함수는 [file_get_contents ()](http://php.net/manual/kr/function.file-get-contents.php) 함수가 생기기 전에 작성 되었다. 이 함수 대신에 [file_get_contents ()](http://php.net/manual/kr/function.file-get-contents.php) 함수를 사용 하도록 한다.


PHP 의 정규함수 readfile() 함수와 동일한 기능을 가지고 있으나, readfile() 함수가 변수로 받지 않고 출력을 하는 것에 반해 readfile_lib() 함수는 변수로 해당 값을 받게 된다. 파일과 url 상의 파일의 내용을 모두 변수로 받을 수 있다.

readfile 을 이용하여 readfile_lib 와 같이 하려면 다음의 과정과 같다.

```php
<?php
ob_start()
readfile($path);
$text = ob_get_contents();
ob_end_clean();
?>
```

은

```php
<?php
$text = readfile_lib($path);
?>
```

와 같은 결과를 가진다.

use_include_path 의 값을 1 로 지정하고 path 가 존재하지 않는 파일을 지정할 경우 에는 php 의 include_path 에서 파일을 찾게 된다.

win32 용에서 파일 경로를 상대 경로로 사용할 경우에는 realpath() 함수를 이용하여 절대 경로화를 해서 사용해야 한다.

## Arguments

```
(string) filename
     source file

(int) use_include_path (optional)
     파일이 존재하지 않을 경우, include_path 에서 파일을 찾는다.
```


## Example

```php
<?php
$file = "http://test.com/index.html";
$value = readfile_lib ($file);

$file = "/home/httpd/html/test.txt";
$value = readfile_lib ($file);
?>
```

## See also
* [file_get_contents ()](http://php.net/manual/kr/function.file-get-contents.php)
* [readfile ()](http://php.net/manual/kr/function.readfile.php)

