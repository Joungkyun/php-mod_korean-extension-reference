# Charset Functions

EUC-KR/CP949 와 UTF-8 간의 변환 및 관련 함수를 제공 합니다.

## APIS
* ___[ncrencode_lib](Charset/ncrencode_lib.md)___ - CP949 문자열을 UHC (ncr code) 로 변환
* ___[ncrdecode_lib](Charset/ncrdecode_lib.md)___ - NCR code 를 CP949 문자열로 변환
* ___[uniencode_lib](Charset/uniencode_lib.md)___ - CP949 테이블을 UNICODE 로 변환
* ___[unidecode_lib](Charset/unidecode_lib.md)___ - UNICODE 테이블을 EUC-KR, CP949 로 변환
* ___[utf8encode_lib](Charset/utf8encode_lib.md)___ - CP949 문자열을 utf-8 로 변환
* ___[utf8decode_lib](Charset/utf8decode_lib.md)___ - utf-8 문자열을 CP949로 변환
* ___[substr_lib](Charset/substr_lib.md)___ - 2 byte 를 처리하는 substr() 함수
* ___[posstposition_lib](Charset/posstposition_lib.md)___ - 해당 단어의 종성을 구분하여 조사를 정함