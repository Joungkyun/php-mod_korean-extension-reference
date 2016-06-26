# APIs

## Check Functions


check 관련 함수들은 어떠한 값이나 상황을 체크하는 함수들을 모아놓은 함수 입니다.

* ___check_filename_lib___ - GET 이나 POST 로 넘어오는 파일 경로 변수 체크
* ___check_htmltable_lib___ - table 태그가 제대로 사용되었는지 검사
* ___check_uristr_lib___ -  GET 또는 POST 로 전달되는 파일 경로 변수 체크
* ___get_microtime_lib___ - 수행 시간을 밀리초로 구하는 함수
* ___human_fsize_lib___ - byte/bit 값을 읽기 쉽게 변환
* ___is_email_lib___ - email 주소를 체크
* ___is_hangul_lib___ - 문자 또는 문자열의 첫 바이트가 한글(EUC-KR/CP949)인지를 검사.
* ___is_iis_lib___ - 웹서버가 iis 인지 아닌지를 판단
* ___is_url_lib___ - URL 확인 함수
* ___is_windows_lib___ - 운영되는 OS 가 windows 인지 체크
* ___buildno_lib___ - korean extension 의 빌드넘버를 출력
* ___version_lib___ - korean extension 의 버전을 출력

## Filesystem Functions

File System 관련 함수는 파일 리스트, 파일 내용, 파일 쓰기등 파일 시스템과 관련된 함수들의 모음이다.

win32 용에서 파일 경로를 상대경로로 사용할 경우에는 realpath() 함수를 이용하여 절대 경로화를 해서
사용해야 한다.

* ___filelist_lib___ - 지정 디렉토리의 파일 리스트를 가져옴
* ___getfile_lib___ - 파일의 내용을 변수로 받음
* ___getfiletype_lib___ - 파일 이름에서 확장자를 받아옴
* ___putfile_lib___ - 파일을 기록하는 함수
* ___readfile_lib___ - 파일이나 웹문서의 소스를 변수로 받음
* ___pcregrep_lib___ - pcre 정규식을 이용한 grep

## HTML functions

* ___agentinfo_lib___ - 브라우져의 정보를 구함
* ___autolink_lib___ - TEXT 중 URL 이나 EMAIL 을 자동으로 링크
* ___get_hostname_lib___ - IP 로 호스트 이름을 가져오는 함수
* ___movepage_lib___ - 페이지를 이동시키는 함수
* ___perror_lib___ - 에러 메세지를 출력후 원하는 페이지로 이동
* ___pnotice_lib___ - 경고 메세지 또는 전달 메세지를 출력

## Charset functions

EUC-KR/CP949 와 UTF-8 간의 변환 및 관련 함수를 제공 합니다.

* ___ncrencode_lib___ - CP949 문자열을 UHC (ncr code) 로 변환
* ___ncrdecode_lib___ - NCR code 를 CP949 문자열로 변환
* ___uniencode_lib___ - CP949 테이블을 UNICODE 로 변환
* ___unidecode_lib___ - UNICODE 테이블을 EUC-KR, CP949 로 변환
* ___utf8encode_lib___ - CP949 문자열을 utf-8 로 변환
* ___utf8decode_lib___ - utf-8 문자열을 CP949로 변환
* ___substr_lib___ - 2 byte 를 처리하는 substr() 함수
* ___posstposition_lib___ - 해당 단어의 종성을 구분하여 조사를 정함

## Image functions

* ___imgresize_lib___ - 이미지 사이즈를 조정하여 출력하거나 생성

## Mail functions

PHP의 mail() function 과 관련 없이, 자체적으로 mail을 발송할 수 있는 환경을 제공 합니다.

* ___mailsource_lib___ - mail raw data를 생성
* ___sockmail_lib___ - SMTP에 의존하지 않고, socket으로 직접 메일 발송