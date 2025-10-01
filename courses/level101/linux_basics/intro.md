# Linux 기본

## 소개
### 필수 지식 (Prerequisites)

- Windows, Linux 등 어떤 운영체제든 사용하는 데 익숙해야 합니다.
- 운영체제에 대한 기본적인 지식을 갖추고 있어야 합니다.

## What to expect from this course

이 과정은 세 부분으로 나뉩니다.

첫 번째 부분에서는 Linux 운영체제의 기본 개념을 다룹니다. Linux 아키텍처, Linux 배포판(distributions) 및 Linux 운영체제의 사용에 대해 이야기할 것입니다. 또한 GUI와 CLI의 차이점에 대해서도 다룹니다.

두 번째 부분에서는 Linux에서 사용되는 몇 가지 기본 명령어를 다룹니다. 파일 시스템을 탐색하고, 파일을 보거나 조작하며, I/O 리디렉션 등에 사용되는 명령어에 중점을 둘 것입니다.

세 번째 부분에서는 Linux 시스템 관리를 다룹니다. 여기에는 사용자/그룹 관리, 파일 권한 관리, 시스템 성능 모니터링, 로그 파일 관리 등 Linux 관리자가 수행하는 일상적인 작업이 포함됩니다.

두 번째와 세 번째 부분에서는 개념 이해를 돕기 위한 예시를 보여줄 것입니다.

## 이 과정에서 다루지 않는 내용

이 과정에서는 고급 Linux 명령어와 Bash 스크립팅은 다루지 않습니다. 또한 **Linux 내부 구조(Linux internals)**에 대해서도 다루지 않을 것입니다.

## 과정 목차

이 과정에서 다루는 주제는 다음과 같습니다:

-  [Introduction to Linux](intro.md)
    -  [What are Linux Operating Systems](#linux-운영체제란-무엇인가)
    -  [What are popular Linux distributions](#인기-있는-linux-배포판이란-무엇인가요)
    -  [Uses of Linux Operating Systems](#linux-운영체제의-사용처)
    -  [Linux Architecture](#linux-architecture)
    -  [Graphical user interface (GUI) vs Command line interface (CLI)](#그래픽-사용자-인터페이스gui-vs-명령줄-인터페이스cli)
-  [Command Line Basics](command_line_basics.md)
    -  [Lab Environment Setup](command_line_basics.md#lab-environment-setup)
    -  [What is a Command](command_line_basics.md#what-is-a-command)
    -  [File System Organization](command_line_basics.md#file-system-organization)
    -  [Navigating File System](command_line_basics.md#commands-for-navigating-the-file-system)
    -  [Manipulating Files](command_line_basics.md#commands-for-manipulating-files)
    -  [Viewing Files](command_line_basics.md#commands-for-viewing-files)
    -  [Echo Command](command_line_basics.md#echo-command)
    -  [Text Processing Commands](command_line_basics.md#text-processing-commands)
    -  [I/O Redirection](command_line_basics.md#io-redirection)
-  [Linux system administration](linux_server_administration.md)
    -  [Lab Environment Setup](linux_server_administration.md#lab-environment-setup)
    -  [User/Groups management](linux_server_administration.md#usergroup-management)
    -  [Becoming a Superuser](linux_server_administration.md#becoming-a-superuser)
    -  [File Permissions](linux_server_administration.md#file-permissions)
    -  [SSH Command](linux_server_administration.md#ssh-command)
    -  [Package Management](linux_server_administration.md#package-management)
    -  [Process Management](linux_server_administration.md#process-management)
    -  [Memory Management](linux_server_administration.md#memory-management)
    -  [Daemons and Systemd](linux_server_administration.md#daemons)
    -  [Logs](linux_server_administration.md#logs)
-  [Conclusion](conclusion.md)
    -  [Applications in SRE Role](conclusion.md#applications-in-sre-role)
    -  [Useful Courses and tutorials](conclusion.md#useful-courses-and-tutorials)

## Linux 운영체제란 무엇인가?

우리 대부분은 개인용 컴퓨터의 75% 이상에서 사용되는 Windows 운영체제에 익숙합니다. Windows 운영체제는 Windows NT 커널을 기반으로 합니다.

**커널(kernel)**은 운영체제의 가장 중요한 부분으로, 프로세스 관리, 메모리 관리, 파일 시스템 관리 등 핵심적인 기능을 수행합니다.

Linux 운영체제는 Linux 커널을 기반으로 합니다. Linux 기반 운영체제는 Linux 커널, GUI/CLI, 시스템 라이브러리 및 시스템 유틸리티로 구성됩니다. Linux 커널은 Linus Torvalds가 독자적으로 개발하고 배포했습니다. Linux 커널은 무료이며 오픈 소스입니다. (See 
[https://github.com/torvalds/linux](https://github.com/torvalds/linux)).

Linux는 커널일 뿐이며, 완전한 운영체제는 아닙니다. Linux 커널은 GNU 시스템과 결합하여 완전한 운영체제를 만듭니다. 따라서 Linux 기반 운영체제는 GNU/Linux 시스템이라고도 불립니다. GNU는 컴파일러, 디버거, C 라이브러리 등과 같은 방대한 무료 소프트웨어 모음입니다. (See
[Linux and the GNU  System](https://www.gnu.org/gnu/linux-and-gnu.en.html))

History of Linux -
[https://en.wikipedia.org/wiki/History_of_Linux](https://en.wikipedia.org/wiki/History_of_Linux)

## 인기 있는 Linux 배포판이란 무엇인가요?

**Linux 배포판(Linux distribution, distro)**은 Linux 커널과 패키지 관리 시스템을 기반으로 하는 운영체제입니다. 패키지 관리 시스템은 운영체제에 소프트웨어를 설치, 업그레이드, 구성 및 제거하는 데 도움을 주는 도구로 구성되어 있습니다.

소프트웨어는 일반적으로 특정 배포판에 맞게 조정되며, 배포판 고유의 형식으로 패키지화됩니다. 이러한 패키지는 배포판 고유의 **저장소(repository)**를 통해 제공됩니다. 패키지들은 **패키지 관리자(package manager)**에 의해 운영체제에 설치되고 관리됩니다.

**인기 있는 Linux 배포판 목록:**

- Fedora

- Ubuntu

- Debian

- Centos (EOS) -> Rocky

- Red Hat Enterprise Linux

- Suse

- Arch Linux


| Packaging systems      | Distributions                              | Package manager
| ---------------------- | ------------------------------------------ | -----------------
| Debian style (`.deb`)  |   Debian, Ubuntu                           |   APT
| Red Hat style (`.rpm`) |   Fedora, CentOS, Red Hat Enterprise Linux |  YUM

## Linux Architecture

![](images/linux/commands/image25.png)

- Linux 커널은 모놀리식(monolithic) 성격입니다.

- **시스템 호출(System calls)**은 Linux 커널 공간과 상호 작용하는 데 사용됩니다.

- 커널 코드는 오직 커널 모드에서만 실행될 수 있습니다. 비(非)커널 코드는 사용자 모드에서 실행됩니다.

- **장치 드라이버(Device drivers)**는 하드웨어 장치와 통신하는 데 사용됩니다.

## Linux 운영체제의 사용처

Linux 커널을 기반으로 하는 운영체제는 다음 분야에서 널리 사용됩니다.:

- 개인용 컴퓨터

- 서버

- 모바일 폰 - Android는 Linux 운영체제를 기반으로 합니다.

- 임베디드 장치 - 시계, TV, 신호등 등

- 위성

- 네트워크 장치 - 라우터, 스위치 등

## 그래픽 사용자 인터페이스(GUI) vs. 명령줄 인터페이스(CLI)

사용자는 사용자 인터페이스의 도움을 받아 컴퓨터와 상호 작용합니다. 이 사용자 인터페이스는 GUI 또는 CLI일 수 있습니다.

**그래픽 사용자 인터페이스(GUI)**는 사용자가 아이콘 및 이미지와 같은 그래픽을 사용하여 컴퓨터와 상호 작용하도록 허용합니다. 사용자가 컴퓨터에서 애플리케이션을 열기 위해 아이콘을 클릭하는 경우, 실제로 GUI를 사용하고 있는 것입니다. GUI를 사용하면 작업을 수행하기가 쉽습니다.

**명령줄 인터페이스(CLI)**는 사용자가 명령어를 사용하여 컴퓨터와 상호 작용하도록 허용합니다. 사용자가 터미널에 명령어를 입력하면 시스템이 이 명령어를 실행하는 것을 돕습니다. GUI 경험만 있는 새로운 사용자는 특정 작업을 수행하기 위해 명령어를 알고 있어야 하므로 CLI와 상호 작용하는 것이 어려울 수 있습니다.

## Shell vs Terminal

**셸(Shell)**은 사용자로부터 명령을 받아 운영체제가 처리하도록 전달하는 프로그램입니다. 셸은 **CLI(Command Line Interface)**의 한 예시입니다. Bash는 Linux 서버에서 가장 인기 있는 셸 프로그램 중 하나입니다. 다른 인기 있는 셸 프로그램으로는 zsh, ksh, tcsh 등이 있습니다.

**터미널(Terminal)**은 창을 열어 사용자가 셸과 상호 작용할 수 있도록 해주는 프로그램입니다. 터미널의 몇 가지 인기 있는 예시로는 GNOME-terminal, xterm, Konsole 등이 있습니다.

Linux 사용자들은 셸, 터미널, 프롬프트, 콘솔 등의 용어를 종종 혼용하여 사용합니다. 간단히 말해, 이 모든 것은 사용자로부터 명령을 받는 방법을 일컫습니다.