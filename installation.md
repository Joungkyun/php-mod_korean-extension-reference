# Installation


먼저, https://github.com/OOPS-ORG-PHP/mod_korean/releases PHP 버전에 맞는 최신 버전을 다운로드를 받아서 압축을 풀어 놓습니다.

  * PHP7 - mod_korean 1.x
  * PHP4 or PHP5 - mod_korean 0.1.x

먼저, ***phpize*** 명령과 ***configure***를 이용하여 DSO 빌드 환경을 준비 합니다.

```bash
[root@host mod_korean-1.0.1]$ phpize
Configuring for:
PHP Api Version:         20151012
Zend Module Api No:      20151012
Zend Extension Api No:   320151012
[root@host mod_korean-1.0.1]$ # --with-libdir 옵션은 64bit 환경에서만 지정합니다.
[root@host mod_korean-1.0.1]$ ./configure --with-libdir=lib64 --enable-korean --enable-korean-gd=builtin
[root@host mod_korean-1.0.1]$ make && make install
```



설치가 완료 후, php.ini에 다음의 설정을 추가 합니다.

```ini
extension = korean.so
```