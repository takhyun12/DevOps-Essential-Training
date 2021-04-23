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
