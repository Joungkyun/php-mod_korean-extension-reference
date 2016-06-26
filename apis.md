# APIs

## 1. [Check Functions](check_functions.md)


check 관련 함수들은 어떠한 값이나 상황을 체크하는 함수들을 모아놓은 함수 입니다.

* ___[check_filename_lib](Check/check_filename_lib.md)___ - GET 이나 POST 로 넘어오는 파일 경로 변수 체크
* ___[check_htmltable_lib](Check/check_htmltable_lib.md)___ - table 태그가 제대로 사용되었는지 검사
* ___[check_uristr_lib](Check/check_uristr_lib.md)___ -  GET 또는 POST 로 전달되는 파일 경로 변수 체크
* ___[get_microtime_lib](Check/get_microtime_lib.md)___ - 수행 시간을 밀리초로 구하는 함수
* ___[human_fsize_lib](Check/human_fsize_lib.md)___ - byte/bit 값을 읽기 쉽게 변환
* ___[is_email_lib](Check/is_email_lib.md)___ - email 주소를 체크
* ___[is_hangul_lib](Check/is_hangul_lib.md)___ - 문자 또는 문자열의 첫 바이트가 한글(EUC-KR/CP949)인지를 >검사.
* ___[is_iis_lib](Check/is_iis_lib.md)___ - 웹서버가 iis 인지 아닌지를 판단
* ___[is_url_lib](Check/is_url_lib.md)___ - URL 확인 함수
* ___[is_windows_lib](Check/is_windows_lib.md)___ - 운영되는 OS 가 windows 인지 체크
* ___[buildno_lib](Check/buildno_lib.md)___ - korean extension 의 빌드넘버를 출력
* ___[version_lib](Check/version_lib.md)___ - korean extension 의 버전을 출력

## 2. [Filesystem Functions](filesystem_functions.md)

File System 관련 함수는 파일 리스트, 파일 내용, 파일 쓰기등 파일 시스템과 관련된 함수들의 모음이다.

win32 용에서 파일 경로를 상대경로로 사용할 경우에는 realpath() 함수를 이용하여 절대 경로화를 해서
사용해야 한다.

* ___[filelist_lib](Filesystem/filelist_lib.md)___ - 지정 디렉토리의 파일 리스트를 가져옴
* ___[getfile_lib](Filesystem/getfile_lib.md)___ - 파일의 내용을 변수로 받음
* ___[getfiletype_lib](Filesystem/getfiletype_lib.md)___ - 파일 이름에서 확장자를 받아옴
* ___[putfile_lib](Filesystem/putfile_lib.md)___ - 파일을 기록하는 함수
* ___[readfile_lib](Filesystem/readfile_lib.md)___ - 파일이나 웹문서의 소스를 변수로 받음
* ___[pcregrep_lib](Filesystem/pcregrep_lib.md)___ - pcre 정규식을 이용한 grep

## 3. [HTML functions](html_functions.md)

* ___[agentinfo_lib](HTML/agentinfo_lib.md)___ - 브라우져의 정보를 구함
* ___[autolink_lib](HTML/autolink_lib.md)___ - TEXT 중 URL 이나 EMAIL 을 자동으로 링크
* ___[get_hostname_lib](HTML/get_hostname_lib.md)___ - IP 로 호스트 이름을 가져오는 함수
* ___[movepage_lib](HTML/movepage_lib.md)___ - 페이지를 이동시키는 함수
* ___[perror_lib](HTML/perror_lib.md)___ - 에러 메세지를 출력후 원하는 페이지로 이동
* ___[pnotice_lib](HTML/pnotice_lib.md)___ - 경고 메세지 또는 전달 메세지를 출력

## 4. [Charset functions](charset_functions.md)

EUC-KR/CP949 와 UTF-8 간의 변환 및 관련 함수를 제공 합니다.

* ___[ncrencode_lib](Charset/ncrencode_lib.md)___ - CP949 문자열을 UHC (ncr code) 로 변환
* ___[ncrdecode_lib](Charset/ncrdecode_lib.md)___ - NCR code 를 CP949 문자열로 변환
* ___[uniencode_lib](Charset/uniencode_lib.md)___ - CP949 테이블을 UNICODE 로 변환
* ___[unidecode_lib](Charset/unidecode_lib.md)___ - UNICODE 테이블을 EUC-KR, CP949 로 변환
* ___[utf8encode_lib](Charset/utf8encode_lib.md)___ - CP949 문자열을 utf-8 로 변환
* ___[utf8decode_lib](Charset/utf8decode_lib.md)___ - utf-8 문자열을 CP949로 변환
* ___[substr_lib](Charset/substr_lib.md)___ - 2 byte 를 처리하는 substr() 함수
* ___[posstposition_lib](Charset/posstposition_lib.md)___ - 해당 단어의 종성을 구분하여 조사를 정함

## 5. [Image functions](image_functions.md)

* ___[imgresize_lib](Image/imgresize_lib.md)___ - 이미지 사이즈를 조정하여 출력하거나 생성

## 6. [Mail functions](mail_functions.md)

PHP의 mail() function 과 관련 없이, 자체적으로 mail을 발송할 수 있는 환경을 제공 합니다.

* ___[mailsource_lib](Mail/mailsource_lib.md)___ - mail raw data를 생성
* ___[sockmail_lib](Mail/sockmail_lib.md)___ - SMTP에 의존하지 않고, socket으로 직접 메일 발송