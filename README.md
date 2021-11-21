# gitflow_20174317

###getopt 및 getopts 명령어

***

#getopt

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

***while getopts "a:b:h" opt***

보통 다음과 같은 형식을 주로 사용하고 getopt는 첫번째 파라미터로 옵션으로 사용될 문자열을 입력 받고 다음에는 옵션으로 활용되는 변수를 사용합니다.
 
getopt를 사용할 때 주의해야 할 점은 **":"** 입니다. 기존적으로 getopt는 한개의 문자만을 구분자로 사용하며 사용할 문자열 뒤에 ":"을 붙이게 되면 뒤에 Value가 붙게 된다는 것을 의미합니다

<https://systemdesigner.tistory.com/17>

***

#gitopts

![getopts](https://user-images.githubusercontent.com/94783175/142760812-0c9df6ae-35e6-4ff1-b8bc-5d2f089058a3.png)

쉘 에서 명령을 실행할 때 옵션을 사용하는데요. 스크립트 파일이나 함수를 실행할 때도 동일하게 옵션을 사용할 수 있습니다. 

사용된 옵션은 다른 인수들과 마찬가지로 $1, $2, ... positional parameters 형태로 전달되므로 스크립트 내에서 직접 옵션을 해석해서 사용해야 됩니다. 

이때 옵션 해석 작업을 쉽게 도와주는 명령이 getopts 입니다.

