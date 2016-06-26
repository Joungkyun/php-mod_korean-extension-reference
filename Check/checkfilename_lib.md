# check_filename_lib

## Proto type

```php
array filelist_lib (string path, [ string mode, [ string regex ] ])
```

## Description

지정한 디렉토리에 있는 디렉토리 리스트를 배열로 구하는 함수.  파일, 디렉토리, 링크 별로 리스
트를 구할 수 있으며, 조합 역시 가능하다.

win32 용에서 경로를 상대경로로 사용할 경우에는 realpath() 함수를 이용하여 절대 경로화를 해서
사용해야 한다.

## Arguments

* string ***path*** - 디렉토리 리스트를 가져올 경로
* char ***mode*** (optional)
  * f  : 지정한 디렉토리의 파일만 받음
  * d  : 지정한 디렉토리의 디렉토리만 받음
  * l  : 지정한 디렉토리의 링크만 받음
  * fd : 지정한 디렉토리의 파일과 디렉토리만 받음
  * fl : 지정한 디렉토리의 파일과 링크만 받음
  * dl : 지정한 디렉토리의 디렉토리와 링크만 받음
  * 아무것도 지정하지 않았을 경우에는 fdl 모두 받음
* string ***regex*** (optional) - mode 값 또는 전체 리스트에서 정규 표현식을 이용하여 리스트를 구함

## Example

```php
# /home/backup 하위의 디렉토리 리스트를 받을 경우
$a = filelist_lib ('/home/backup', 'd');
for( $i=0 ;$i<count ($a); $i++ ) {
  echo $a[$i]."\n";
}

# /home/backup 에 있는 파일 중, tar.gz 파일들만 받을 경우
$a = filelist_lib ('/home/backup', 'f', 'tar\.gz$');
for( $i=0; $i<count ($a); $i++ ) {
  echo $a[$i]."\n";
}
```

## See also
None