# gitflow_20174317

### getopt 및 getopts 명령어

***

# getopt

* getopt를 사용하는 이유는 

1) 다양한 입력 값이 존재할 경우 사용자와 개발자의 편의를 보장하기 위함 이고

2) 스크립트를 보다 체계적으로 관리할 수 있기 때문입니다.


* 샘플코드

```

 #!/bin/bash

## 도움말 출력하는 함수
help() {
        echo "splt [OPTIONS] FILE"
                echo "    -h         도움말 출력."
                echo "    -a ARG     인자를 받는 opt."
                echo "    -b ARG     인자를 받는 opt2."
                exit 0
}
while getopts "a:b:h" opt
do
case $opt in
a) arg_a=$OPTARG
echo "Arg A: $arg_a"
;;
b) arg_b=$OPTARG
echo "Arg B: $arg_b"
echo "$arg_b"
;;
h) help ;;
?) help ;;
esac
done

```

가장 중요한 부분은 아래의 구분인데 

***while getopts "a: b :h" opt***

보통 다음과 같은 형식을 주로 사용하고 getopt는 첫번째 파라미터로 옵션으로 사용될 문자열을 입력 받고 다음에는 옵션으로 활용되는 변수를 사용합니다.
 
getopt를 사용할 때 주의해야 할 점은 **":"** 입니다. 기존적으로 getopt는 한개의 문자만을 구분자로 사용하며 사용할 문자열 뒤에 ":"을 붙이게 되면 뒤에 Value가 붙게 된다는 것을 의미합니다

<https://systemdesigner.tistory.com/17>

***

# gitopts

![getopts](https://user-images.githubusercontent.com/94783175/142760812-0c9df6ae-35e6-4ff1-b8bc-5d2f089058a3.png)

* 쉘 에서 명령을 실행할 때 옵션을 사용하는데요. 스크립트 파일이나 함수를 실행할 때도 동일하게 옵션을 사용할 수 있습니다. 

* 사용된 옵션은 다른 인수들과 마찬가지로 $1, $2, ... positional parameters 형태로 전달되므로 스크립트 내에서 직접 옵션을 해석해서 사용해야 됩니다. 

* 이때 옵션 해석 작업을 쉽게 도와주는 명령이 ***getopts*** 입니다.

<https://mug896.github.io/bash-shell/getopts.html>

***

### sed 및 awk 명령어

# sed

* 기본적인 기능은 ed에서 가져왔다고 합니다. 
* 이 기능들은 모두 sed에 적용이 됩니다. 
* sed는 스트리밍 편집기라고 합니다. 
* 대화형 편집기는 입력 및 출력이 하나로 이루어지며, \n을 개행문자로 사용하는 스트리밍 에디터입니다.

![99EF243359E1DD1234](https://user-images.githubusercontent.com/94783175/142761734-b3fcc668-30c4-4ea4-ab54-582863afc607.png)

![99C2DB3359E1DD400B](https://user-images.githubusercontent.com/94783175/142761735-7b88ab54-0be7-4b9a-9bc1-f73279ce6f06.png)



1) 찾기(search), 출력(print)
 >sed -n '/abd/p' list.txt : list.txt 파일을 한줄씩 읽으면서(-n : 읽은 것을 출력하지 않음) abd 문자를 찾으면 그 줄을 출력(p)합니다.

2) 치환(substitute)
> sed 's/addrass/address/' list.txt : addrass를 address로 바꿉니다. 단, 원본파일을 바꾸지 않고 출력을 바꿔서 합니다.

> sed 's/addrass/address/' list.txt > list2.txt

> sed 's/\t/\ /' list.txt : 탭문자를 엔터로 변환합니다.

> sed 's/□□*/□/' list.txt : ( 표시: □ 는 공백 문자를 표시한다. ) 위의 구문은 한개이상의 공백문자열을 하나의 공백으로 바꿉니다.

3) 추가(insert)
> scriptfile - s/

4) 삭제(delete)
> sed '/TD/d' 1.html : TD 문자가 포함된 줄을 삭제하여 출력합니다.
> sed '/Src/!d' 1.html : Src 문자가 있는 줄만 지우지 않습니다.
> sed '1,2d' 1.html : 처음 1줄, 2줄을 지웁니다.
> sed '/^$/d 1.html : 공백라인을 삭제하는 명령입니다

<https://blog.wonizz.tk/2019/03/05/%EB%AA%85%EB%A0%B9%EC%96%B4-sed-%EB%B0%8F-awk-%EC%82%AC%EC%9A%A9%EB%B2%95/>


# awk 

* awk는 파일로부터 레코드(record)를 선택하고, 선택된 레코드에 포함된 값을 조작하거나 데이터화하는 것을 목적으로 사용하는 프로그램입니다. 
* 즉, awk 명령의 입력으로 지정된 파일로부터 데이터를 분류한 다음, 분류된 텍스트 데이터를 바탕으로 패턴 매칭 여부를 검사하거나 데이터 조작 및 연산 등의 액션을 수행하고, 그 결과를 출력하는 기능을 수행합니다.


![99C761465D1CBF9B28](https://user-images.githubusercontent.com/94783175/142761209-5b7c50a0-d43e-4784-8ef1-32dee3cc650b.png)


* awk는 ***"awk programming language"*** 라는 프로그래밍 언어로 작성된 프로그램을 실행합니다. 리눅스에서 쉘 스크립트(Shell Script)로 작성된 파일이 리눅스 쉘(Shell)에 의해 실행되는 것을 떠올리면, awk가 "awk programming language" 문법으로 작성된 코드를 실행한다는 것의 의미가 쉽게 이해되죠.



* awk는 기본적으로 입력 데이터를 라인(line) 단위의 레코드(Record)로 인식합니다. 그리고 각 레코드에 들어 있는 텍스트는 공백 문자(space, tab)로 구분된 필드(Field)들로 분류되는데요. 이렇게 식별된 레코드 및 필드의 값들은 awk 프로그램에 의해 패턴 매칭 및 다양한 액션의 파라미터로 사용됩니다. (참고로, 레코드 구분 문자(newline)와 필드 구분 문자(space, tab)는 awk 프로그램 옵션으로 변경할 수 있습니다.)


##awk 명령 사용 예제

|awk 사용 예|명령어 옵션|
|---|---|
|파일의 전체 내용 출력|awk '{ print }' [FILE]|
|필드 값 출력|awk '{ print $1 }' [FILE]|
|필드 값에 임의 문자열을 같이 출력|awk '{print "STR"$1, "STR"$2}' [FILE]|
|지정된 문자열을 포함하는 레코드만 출력|awk '/STR/' [FILE]|
|특정 필드 값 비교를 통해 선택된 레코드만 출력|awk '$1 == 10 { print $2 }' [FILE]|
|특정 필드들의 합 구하기|awk '{sum += $3} END { print sum }' [FILE]|
|여러 필드들의 합 구하기|awk '{ for (i=2; i<=NF; i++) total += $i }; END { print "TOTAL : "total }' [FILE]|
|레코드 단위로 필드 합 및 평균 값 구하기|awk '{ sum = 0 } {sum += ($3+$4+$5) } { print $0, sum, sum/3 }' [FILE]|
|필드에 연산을 수행한 결과 출력하기|awk '{print $1, $2, $3+2, $4, $5}' [FILE]|
|레코드 또는 필드의 문자열 길이 검사	|awk ' length($0) > 20' [FILE]|
|파일에 저장된 awk program 실행|awk -f [AWK FILE] [FILE]|
|필드 구분 문자 변경하기|awk -F ':' '{ print $1 }' [FILE]|
|awk 실행 결과 레코드 정렬하기|awk '{ print $0 }' [FILE]|
|특정 레코드만 출력하기|awk 'NR == 2 { print $0; exit }' [FILE]|
|출력 필드 너비 지정하기|awk '{ printf "%-3s %-8s %-4s %-4s %-4s\n", $1, $2, $3, $4, $5}' [FILE]|
|필드 중 최대 값 출력|awk '{max = 0; for (i=3; i<NF; i++) max = ($i > max) ? $i : max ; print max}' [FILE]|

<https://recipes4dev.tistory.com/171>
