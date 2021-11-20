# 20203156
과제
---
* ___getopt 명령어___
---
* ___getopt 명령어___
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
  * 연산자
    |연산자|의미|예제|
    | :---: | :---: | :---:|
    |[주소범위]/p|[주어진 주소 범위] 출력|/Chosun/p|
    |[주소범위]/d|[주어진 주소 범위] 삭제|5d|
    |s/pattern1/pattern2/|한 줄에서 처음 나타나는 pattern1을 pattern2로 치환|s/Unix/Linux/|
    |[주소범위]/s/pattern1/pattern2/|[주어진 주소 범위]에 대해서 한 줄에 처음 나타나는 pattern1을 pattern2로 치환|/Chosun/,/Window/s/Unix/Linux/|
    |[주소범위]/y/pattern1/pattern2/|[주어진 주소 범위]에 대해서 pattern1에 나타나는 어떤 문자라도 pattern2에 나타나는 문자로 바꿈|/Chosun/,/Window/y/Unix/Linux/|
    |g|입력의 일치하는 각 줄에서 발생하는 모든 패턴에 대해 동작|s/Unix/Linux/g|
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
 * 입력된 각 줄을 필드로 나눔
 * 파이프와 같이 사용할 수 있음
 * 주요 옵션은 -F, -v
  * -F : 문자열을 분리할 기준이 되는 분리 문자 입력
  * -v : 파라미터 전달
 * 내장 함수는 sub, gsub, index, length, substr, split, print, printf, system
 * 예제
