## Shell Script

### Shell Script에서의 return
* shell script에서는 우리가 아는 컴퓨터 언어에서의 `return` 반환값이 없습니다.
* shell script가 실행되는 프로세스에서 `exit`을 통해 상태 종료 표시만을 프로세스 실행 결과로 반환할 수 있습니다.
* 일반적으로 `0`은 성공을 나타내며 나머지인 `1 ~ 255`는 에러를 나타냅니다.
* `$?`는 방금 실행된 프로세스가 반환한 결과값을 저장하고 있습니다.

```
$ error_command
error_command: command not found
$ echo $?
127
```

### Shell Script에서의 return을 구현하는 방법

1) echo를 통해서 값 전달 받기

```
#!/bin/bash

get_result_func () {
	test=123456
	# echo 함수를 통해서 결과를 전달
	# return "Result is ${test}"라고 생각하시면 됩니다.
	echo "Result is ${test}"
}

# 다음 아래와 같이 함수 호출의 결과를 변수에 받습니다.
ret_value=$(get_result_func)

echo $ret_value
```

```
$ ./shell_script_practice.sh
Result is 123456
```

2) 변수 공유하기 : 변수를 전역으로 선언하고 해당 변수를 이용해서 사용할 수 있습니다.

```
#!/bin/bash

ret_value=""

get_result_func () {
	# Do Something
	ret_value="aaaaaaaaa"
}

get_result_func
echo $ret_value
```

```
$ ./shell_script_practice.sh
aaaaaaaaa
```
