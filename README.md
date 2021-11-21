# 20203156
과제
---
* ___getopt 명령어___
---
* ___getopts 명령어___
---
* ___sed 명령어___
  * 비대화형 모드의 텍스트 파일 에디터 (줄 단위 편집기)
  * 표준입력이나 파일에서 덱스트를 입력으로 받아 한 줄 씩 데이터를 처리해 표준출력이나 파일로 내보냄
  * 파이프와 같이 사용할 수 있음
  * sed를 사용할 때 쿼우팅을 해야 됨 (ex. $ sed '/Chosun/p' sample.txt)
  * sed는 임시 버퍼를 사용하여 원본에 영향을 주지 않음
  * 주요 옵션은 -e, -n, -i, -f
    * -e : 다중 편집이 가능
    * -n : 패턴이 일치하는 라인 출력
    * -i : 원본 파일에 덮어 씀 
    * -f : 처리할 명령을 저장한 파일을 지정
  * 주요 연산자
    |연산자|의미|예제|
    | :---: | :---: | :---: |
    |[주소범위]/p|[주어진 주소 범위] 출력|/Chosun/p|
    |[주소범위]/d|[주어진 주소 범위] 삭제|5d|
    |s/pattern1/pattern2/|한 줄에서 처음 나타나는 pattern1을 pattern2로 치환|s/Unix/Linux/|
    |[주소범위]/s/pattern1/pattern2/|[주어진 주소 범위]에 대해서 한 줄에 처음 나타나는 pattern1을 pattern2로 치환|/Chosun/,/Window/s/Unix/Linux/|
    |[주소범위]/y/pattern1/pattern2/|[주어진 주소 범위]에 대해서 pattern1에 나타나는 어떤 문자라도 pattern2에 나타나는 문자로 바꿈|/Chosun/,/Window/y/Unix/Linux/|
    |g|입력의 일치하는 각 줄에서 발생하는 모든 패턴에 대해 동작|s/Unix/Linux/g|
  * s, r, w, a, c, q 등 다양한 명령어들이 있음
  * 예제
   ```bash
   $ cat color.txt
   blue
   yellow
   red
   purple
   black
   
   $ sed 's/l/a/g' color.txt
   baue
   yeaaow
   red
   purpae
   baack
   
   ```
---
* ___awk 명령어___
 * C 형태의 문법을 갖는 필드 단위의 패턴 처리 언어
 * 파일에서 패턴이 일치하는 행을 찾아서 지정한 조치를 수행해주는 명령어
 * 입력된 각 줄을 필드로 나눔
 * 레코드 : 입력된 파일의 한 줄
 * 필드 : 입력된 레코드에서 스페이스(space) 또는 탭(tap)으로 구분되는 문자
 * 구조
   * 시작 (BEGIN) : 파일을 읽기 전에 실행
   * 실행 : 파일의 각 레코드 라인을 읽어들일 떄 마다 실행
   * 끝 (END) : 파일을 다 읽어들인 뒤 실행
 * 형식
   * awk '패턴' 파일명
   * awk '{액션}' 파일명
   * awk '패턴' '{액션}' 파일명
 * 파이프와 같이 사용할 수 있음
 * 시스템 변수
   * FILENAME : 현재 파일명
   * FS : 입력 필드 구분 문자
   * RS : 입력 레코드 구분 문자 (디폴트 : newline)
   * NF : 현재 레코드 필드 갯수
   * NR : 입력 시작 점에서 현재 레코드의 순서 값
   * FNR : 현재 파일에서 현재 레코드의 순서 값
   * ORS : 결과 출력 시 레코드 구분 문자 (디폴트 : newline)
   * OFS : 결과 출력 시 필드 구분 문자 (디폴트 : space)
   * OFMT : 문자열을 출력할 때 사용하는 형식
   * ARGV : 커맨드 라인의 인자를 포함하는 배열
   * ARGC : 커맨드 라인의 인자 갯수
   * RSTART : 지정한 매칭 연산을 만족하는 문자열의 시작 위치
   * RLENGTH : 지정한 매칭 연산을 만족하는 문자열의 길이
   * ENVIRON : 환경변수들을 모아둔 관계형 배열
   * CONVFMT : 문자열을 숫자로 변경할 때 사용하는 형식
   * $0 : 입력 레코드
   * $n : 입력 레코드 N번째 필드
 * 주요 옵션은 -F, -f, -v
   * -F (필드구분자) : 문자열을 분리할 기준이 되는 분리 문자 입력 (기본 필드구분자는 공백임)
   * -f (파일명) : 스크립트 파일을 불러옴
   * -v : 파라미터 전달
 * 내장 함수는 sub, gsub, index, length, substr, split, print, printf, system 등이 있음
   |함수|의미|
   | :---: | :---: |
   |sub|지정한 문자열 치환|
   |gsub|문자열 일괄 치환|
   |index|주어진 문자열과 일치하는 문자의 인덱스 반환|
   |length|문자열의 길이 반환|
   |substr|시작위치에서 주어진 길이 만큼의 문자열 반환|
   |split|문자열을 분리해 배열로 반환|
   |print|문자열 출력|
   |printf|지정한 포맷에 따라 함수 출력|
   |system|명령 실행|
 * 명령어
   * 문자열 연산
     * sub
     * gsub
     * index
     * length
     * substr
     * split
     * match
     * toupper
     * tolower
   * 수치 연산
     * int
     * long
     * exp
     * sqrt
     * srand
     * rand
     * sin
     * cos
     * atan2
   * 입출력 / 프로세스
     * print
     * printf
     * sprintf
     * system
     * close
     * delete
     * next
     * getline
 * 제어문은 C의 제어문과 같음
 * 예제
  ```bash
  $ echo "Hi how are you?" | awk '{ print $3 }
  are
  ```
---
