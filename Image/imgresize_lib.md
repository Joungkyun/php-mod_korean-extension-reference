# imgresize_lib

## Proto type

```c
void imgresize_lib (string file_path [, string new_type [, int new_width [, int new_height [, string new_path ] ] ] ])
```

## Description

imgresize_lib 함수는 원본 이미지의 사이즈를 조정하여 새로운 이미지를 생성하거나 사이즈가 조정된 이미지를 출력하는 기능을 한다. 섬네일 이미지를 만들 경우 유용하게 사용할 수 있다.

## Arguments

```
file_path  이미지 사이즈를 조정할 원본 이미지의 경로를 지정한다. 파일 경로에 http://
           프로토콜을 사용할 경우에는 웹상의 이미지를 컨트롤 할 수 있다.

new_type   새로 생성될 이미지의 확장자를 지정한다. jpg, png, gif 중에서 지정할 수
           있다. jpg 와 gif 는 gd 의 버젼에 따라 지원이 될 수도 안될 수도 있다.
           gd 1.6 미만 버젼에서는 jpg 대신 gif 가 지원이되며, 1.6 이상 버젼에서는
           gif 가 지원이 되지 않고 jpg 가 지원이 된다.

new_width  조정할 이미지 사이즈의 width 값을 지정한다. 지정하지 않을 경우 기본값
           으로 50 이 적용된다.

new_height 조정할 이미지 사이즈의 height 값을 지정한다. 지정하지 않았을 경우
           new_width 값의 비율에 맞추어 지정된다.

new_path   사이즈가 조정된 이미지를 저장할 파일 이름을 경로와 함께 지정한다. 지정
           되지 않았을 경우에는 이미지를 출력한다. 이미지를 저장하지 않고 직접 출력
           할 경우에는 Content-type 이 자동으로 출력이 된다.
```

win32 환경에서는 file_path 와 mew_path 를 지정할 때 상대 경로로 지정을 하려면 realpath() 함수를 이용하여 절대 경로화를 해 줘야 한다.


## Example

```php
<?php
# 50 * 50 사이즈의 jpeg 이미지를 출력
Header ('Content-Type: image/jpeg');
imgresize_lib("./org.jpg");
?>

<?php
# 50 * 50 사이즈의 png 이미지를 출력
Header ('Content-Type: image/png');
imgresize_lib("./org.jpg","png");
?>

<?php
# width 가 70 이며 height 값은 width 값의 비율에 의해 결정되는 png 이미지 출력
Header ('Content-Type: image/png');
imgresize_lib("./org.jpg","png",70);
?>

<?php
# 70 * 30 사이즈의 png 이미지 출력
Header ('Content-Type: image/png');
imgresize_lib("./org.jpg","png",70,30);
?>

<?php
# 70 * 30 사이즈의 png 이미지를 test.png 로 저장
Header ('Content-Type: image/png');
imgresize_lib("./org.jpg","png",70,30,"./test.png");
?>
```

## See also
None

