# pcregrep_lib


## Proto type

```c
string pcregrep_lib(string regex, string text [, int opt])
```

## Description

시스템의 grep 과 비슷한 역할을 한다. text 에 주어진 문자열에서 regex 와 매치되는 행을 변수로
받는다. opt 를 1 로 주었을 경우, regex 와 매치되지 않는 행만 변수로 받는다.

정규식은 pcre 호환 정규식이 적용이 된다.

## Arguments


## Example

```php
<?php
$a = <<<EOF
I'm a boy
You are the student
Am I Oh happy?
Oh no, I'm crazy
Oh no, I'M sexy girl
EOF;

echo pcregrep_lib ('/I\'m/i', $a);

/* RESUTL:
I'm a boy
Oh no, I'm crazy
Oh no, I'M sexy girl
 */


echo pcregrep_lib ('/I\'M/', $a);

/* RESULT:
Oh no, I'M sexy girl
 */

echo pcregrep_lib ('/I\'M/', $a, 1);

/* RESULT:
I'm a boy
You are the student
Am I Oh happy?
Oh no, I'm crazy
 */

echo pcregrep_lib('/^I/', $a, 1);

/* RESULT
You are the student
Am I Oh happy?
Oh no, I'm crazy
Oh no, I'M sexy girl
 */
?>
```

## See also
None

