# gitflow_20174317

###getopt 및 getopts 명령어

***

#getopt

* getopt를 사용하는 이유는 

1) 다양한 입력 값이 존재할 경우 사용자와 개발자의 편의를 보장하기 위함 이고

2) 스크립트를 보다 체계적으로 관리할 수 있기 때문입니다.


* 샘플코드

'''

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

'''
