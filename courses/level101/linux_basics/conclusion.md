# 결론 (Conclusion)

저희는 Linux 운영체제의 기본과 Linux에서 사용되는 기본 명령어들을 다루었습니다. 또한 Linux 서버 관리 명령어들도 다루었습니다.

이 과정이 여러분이 명령줄에서 더 쉽게 작업할 수 있도록 돕기를 바랍니다.

## SRE 역할에서의 적용 (Applications in SRE Role)

1. SRE로서 여러분은 이러한 Linux 서버에서 일부 일반적인 작업을 수행해야 합니다. 또한 문제 해결 시에도 명령줄을 사용하게 될 것입니다.
2. 파일 시스템 내에서 위치를 이동하려면 `ls`, `pwd`, `cd` 명령어의 도움이 필요합니다.
3. 로그 파일에서 특정 정보를 검색해야 할 수 있습니다. 이때 `grep` 명령어가 매우 유용합니다. 명령 출력 결과를 파일에 저장하거나 다른 명령어의 입력으로 전달하려면 I/O 리디렉션이 편리합니다.
4. `tail` 명령어는 로그 파일에서 가장 최근의 데이터를 확인하는 데 매우 유용합니다
5. 사용자마다 역할에 따라 다른 권한을 가지게 됩니다. 또한 보안상의 이유로 회사 내 모든 사람이 서버에 접근하는 것을 원하지 않을 것입니다. 사용자 권한은 `chown`, `chmod`, `chgrp` 명령어로 제한할 수 있습니다.
6. `ssh`는 SRE에게 가장 자주 사용되는 명령어 중 하나입니다. 서버에 로그인하여 문제 해결을 수행하고 기본적인 관리 작업을 수행하는 것은 서버에 로그인할 수 있어야만 가능합니다.
7. 서버에서 Apache 서버나 NGINX를 실행하고 싶다면 어떻게 해야 할까요? 먼저 패키지 관리자를 사용하여 이를 설치할 것입니다. 여기서 패키지 관리 명령어가 중요해집니다.
8. 서버의 서비스 관리는 SRE의 또 다른 중요한 책임입니다. `systemd` 관련 명령어는 문제 해결에 도움이 될 수 있습니다. 서비스가 중단되면, `systemctl start` 명령어를 사용하여 다시 시작할 수 있습니다. 필요하지 않은 경우 서비스를 중지할 수도 있습니다.
9. 모니터링은 SRE의 또 다른 핵심 책임입니다. 메모리와 CPU는 모니터링해야 할 두 가지 중요한 시스템 수준 지표입니다. `top`이나 `free`와 같은 명령어들이 이때 매우 유용합니다.
10. 서비스에 오류가 발생하면, 어떻게 그 오류의 **근본 원인(root cause)**을 찾아낼까요? 오류의 전체 **스택 추적(stack trace)**을 확인하기 위해 분명히 로그를 확인해야 할 것입니다. 로그 파일은 오류가 시작된 시간과 함께 오류 발생 횟수도 알려줄 것입니다.

## 유용한 과정 및 튜토리얼 (Useful Courses and Tutorials)

* [Edx basic linux commands course](https://courses.edx.org/courses/course-v1:LinuxFoundationX+LFS101x+1T2020/course/)
* [Edx Red Hat Enterprise Linux Course](https://courses.edx.org/courses/course-v1:RedHat+RH066x+2T2017/course/)
* [https://linuxcommand.org/lc3_learning_the_shell.php](https://linuxcommand.org/lc3_learning_the_shell.php)
