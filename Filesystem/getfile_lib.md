# getfile_lib

## Proto type

```c
(string) getfile_lib (string path [, int size])
```

## Description

특정 파일의 내용을 반환 한다.

## Arguments

```
(string) path - file name or path
(int) size (optional)
   지정한 값 만큼만 반환 한다. 지정하지 않았을 경우, 전체 파일 내용을 반환한다.
```

## Example

```php
<?php
$path = "./doc/example.txt";
$text = getfile_lib ($path,250);
?>
```

## See also
* [putflie_lib ()](Filesystem/putflie_lib.md)
* [readfile_lib ()](Filesystem/readfile_lib.md)
