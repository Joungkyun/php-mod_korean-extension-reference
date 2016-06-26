# Filesystem Functions

File System 관련 함수는 파일 리스트, 파일 내용, 파일 쓰기등 파일 시스템과 관련된 함수들의 모음이다.

win32 용에서 파일 경로를 상대경로로 사용할 경우에는 realpath() 함수를 이용하여 절대 경로화를 해서
사용해야 한다.

## APIs
* ___filelist_lib___ - 지정 디렉토리의 파일 리스트를 가져옴
* ___getfile_lib___ - 파일의 내용을 변수로 받음
* ___getfiletype_lib___ - 파일 이름에서 확장자를 받아옴
* ___putfile_lib___ - 파일을 기록하는 함수
* ___readfile_lib___ - 파일이나 웹문서의 소스를 변수로 받음
* ___pcregrep_lib___ - pcre 정규식을 이용한 grep




