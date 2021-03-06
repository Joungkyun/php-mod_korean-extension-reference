# agentinfo_lib

## Proto type

```c
array agentinfo_lib(void)
```

## Description

agentinfo_lib() 함수는 접속하는 유저의 브라우져의 정보를 배열값으로 구하게 된다. 구할수 있는
브라우져의 정보는 다음과 같다.

```
[br] 브라우져 종류
  MSIE, Mozilla, Netscape, Lynx, Links, w3m, opera, Konqueror, other 을 구분함.

[os] 운영체제
  agent 정보에서 OS 를 구분할 수 있을 경우 OS 의 종류를 구함

[ln] 언어 (netscape, mozila)
  agent 정보에서 언어를 구분할 수 있을 경우 언어를 구함. ko 와 en 만 가능. 나머지는 other 로
  처리됨.

[vr] 브라우져 버젼 정보
  agent 정보에서 브라우져 버젼를 구분할 수 있을 경우 브라우져 버젼을 구함

[co] 브라우져 호환 정보
  브라우져간 비슷한 작동을 하는 것끼리의 모음 정보를 가진다.

  msie    => msie 의 계열로, msie, opera 가 여기에 해당된다.
  mozilla => mozilla 계열로, mozilla, netscape, konqueror 가 해당된다.
  TextBR  => lynx, links, w3m 등 텍스트 브라우져를 지칭
```

## Arguments
void

## Example

결과는 Windows 2000 의 IE 5.x 에서 접속했을 경우

```
browser : MSIE
os      : NT4.0
lang    :
version : 6.0
호환    : msie
```

과 같이 출력 된다.

```php
<?php
$a = agentinfo_lib();
echo "browser : $a[br]\n".
     "os      : $a[os]\n".
     "lang    : $a[ln]\n".
     "version : $a[vr]\n".
     "호환    : $a[co]\n";
?>
```

## See also
None

