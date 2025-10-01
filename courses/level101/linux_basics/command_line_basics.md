# 명령줄 기본 (Command Line Basics)

## 실습 환경 설정 (Lab Environment Setup)

본 과정에 예시로 제공된 모든 명령어를 실행하기 위해 온라인 Bash 인터프리터를 사용할 수 있습니다. 이는 또한 다양한 Linux 명령어를 직접 체험하는 데 도움이 될 것입니다.

[REPL](https://repl.it/languages/bash) 은 Linux 명령어를 실행하는 데 널리 사용되는 온라인 Bash 인터프리터 중 하나입니다. 저희는 이 과정에서 언급된 모든 명령어를 실행하기 위해 이를 사용할 것입니다.

## 명령어란 무엇인가 (What is a Command)

명령어는 운영체제에게 특정 작업을 수행하도록 지시하는 프로그램입니다. 프로그램은 Linux에서는 파일로 저장됩니다. 따라서 명령어 또한 디스크 어딘가에 저장된 파일입니다.

명령어는 사용자로부터 추가적인 인수를 입력받을 수도 있습니다. 이러한 인수를 **명령줄 인수(command line arguments)**라고 합니다. 명령어를 사용하는 방법을 아는 것이 중요하며, 특히 Linux에서는 도움을 얻을 수 있는 여러 방법이 있습니다. 거의 모든 명령어에는 어떤 형태든 문서화가 있으며, 대부분의 명령어는 합리적인 양의 문서를 표시하는 -h 또는 --help 명령줄 인수를 가지고 있습니다. 하지만 Linux에서 가장 널리 사용되는 문서화 시스템은 man 페이지라고 불리며, 이는 manual pages의 줄임말입니다.

ls 명령어의 문서를 보기 위해 --help를 사용하는 예시입니다.

![](images/linux/commands/image19.png)

## 파일 시스템 구성 (File System Organization)

Linux 파일 시스템은 가장 높은 수준의 디렉토리가 root( / 로 표기)라고 불리는 계층적(또는 트리와 유사한) 구조를 가집니다. root 디렉토리 내부에 있는 디렉토리들은 시스템과 관련된 파일들을 저장합니다. 이 디렉토리들은 차례로 시스템 파일, 애플리케이션 파일 또는 사용자 관련 파일을 저장할 수 있습니다.

![](images/linux/commands/image17.png)

| Directory  | Description                                                                    |
|------------|--------------------------------------------------------------------------------| 
| bin        | 가장 일반적으로 사용되는 명령어의 실행 가능한 프로그램이 `bin` 디렉토리에 있습니다        |
| dev        | 이 디렉토리는 시스템의 장치와 관련된 파일들을 포함합니다.                              |
| etc        | 이 디렉토리는 모든 시스템 설정 파일들을 포함합니다.                                   |
| home       | 이 디렉토리는 사용자 관련 파일과 디렉토리들을 포함합니다.                              |       
| lib        | 이 디렉토리는 모든 라이브러리 파일들을 포함합니다.                                    |
| mnt        | 이 디렉토리는 시스템에 마운트된 장치와 관련된 파일들을 포함합니다.                      |
| proc       | 이 디렉토리는 시스템에서 실행 중인 프로세스와 관련된 파일들을 포함합니다.                |
| root       | 이 디렉토리는 root 사용자와 관련된 파일 및 디렉토리를 포함합니다.                      | 
| sbin       | 이 디렉토리는 시스템 관리를 위해 사용되는 프로그램들을 포함합니다.                      |
| tmp        | 이 디렉토리는 시스템에 임시 파일들을 저장하는 데 사용됩니다.                           |
| usr        | 이 디렉토리는 시스템의 애플리케이션 프로그램들을 저장하는 데 사용됩니다.                 |

## 파일 시스템 탐색 명령어 (Commands for Navigating the File System)

파일 시스템을 탐색하는 데 자주 사용되는 세 가지 기본 명령어가 있습니다:

- ls

- pwd

- cd

이제 각 명령어가 무엇을 하는지, 그리고 이 명령어들을 어떻게 사용하는지 이해해 보겠습니다. 또한 제공된 예시들을 온라인 Bash 셸에서 실습해 보는 것이 좋습니다.

### pwd (print working directory)

어느 순간이든 우리는 특정 디렉토리에 위치해 있습니다. 우리가 현재 위치한 디렉토리의 이름을 얻으려면 Linux에서 `pwd` 명령어를 사용할 수 있습니다.

![](images/linux/commands/image2.png)

이제 `cd` 명령어를 사용하여 다른 디렉토리로 이동한 다음, 작업 디렉토리를 출력해 보겠습니다.

![](images/linux/commands/image20.png)

### cd (change directory)

`cd` 명령어는 작업 디렉토리를 변경하는 데 사용할 수 있습니다. 이 명령어를 사용하여 한 디렉토리에서 다른 디렉토리로 이동할 수 있습니다.

아래 예시에서, 우리는 처음에 `root` 디렉토리에 있습니다. 그 다음 `cd` 명령어를 사용하여 디렉토리를 변경했습니다.

![](images/linux/commands/image3.png)

### ls (list files and directories)**

`ls` 명령어는 디렉토리의 내용물을 나열하는 데 사용됩니다. 이는 주어진 디렉토리에 존재하는 모든 파일과 폴더를 나열할 것입니다.

셸에 단순히 `ls`를 입력하면, 현재 디렉토리에 있는 모든 파일과 디렉토리를 나열합니다

![](images/linux/commands/image7.png)

`ls` 명령어에 디렉토리 이름을 인수로 제공할 수도 있습니다. 그러면 주어진 디렉토리 내부의 모든 파일과 디렉토리를 나열합니다.

![](images/linux/commands/image4.png)

## 파일 조작 명령어 (Commands for Manipulating Files)

파일을 조작하는 데 자주 사용되는 다섯 가지 기본 명령어가 있습니다.:

- touch

- mkdir

- cp

- mv

- rm

이제 각 명령어가 무엇을 하는지, 그리고 이 명령어들을 어떻게 사용하는지 이해해 보겠습니다. 또한 제공된 예시들을 온라인 Bash 셸에서 실습해 보는 것이 좋습니다.

### touch (create new file)

`touch` 명령어는 빈 새 파일을 생성하는 데 사용할 수 있습니다. 이 명령어는 다른 많은 목적으로도 매우 유용하지만, 여기서는 새 파일을 생성하는 가장 간단한 사용 사례를 다룰 것입니다.

`touch` 명령어의 일반적인 구문:

```shell
touch <file_name>
```

![](images/linux/commands/image9.png)

### mkdir (create new directories)

`mkdir` 명령어는 **디렉토리(폴더)**를 생성하는 데 사용됩니다. `ls` 명령어를 사용하여 새 디렉토리가 생성되었는지 확인할 수 있습니다.

`mkdir` 명령어의 일반적인 구문:

```shell
mkdir <directory_name>
```

![](images/linux/commands/image11.png)

### rm (delete files and directories)

`rm` 명령어는 파일과 디렉토리를 삭제하는 데 사용할 수 있습니다. 이 명령어가 파일과 디렉토리를 영구적으로 삭제한다는 점을 아는 것이 매우 중요합니다. `rm` 명령어를 성공적으로 실행한 후에는 이 파일과 디렉토리를 복구하는 것이 거의 불가능합니다. 이 명령어는 주의해서 실행하십시오.

`rm` 명령어의 일반적인 구문:

```shell
rm <file_name>
```

예시를 통해 `rm` 명령어를 이해해 봅시다. `touch` 및 `mkdir` 명령어로 각각 생성했던 파일과 디렉토리를 삭제해 보겠습니다.

![](images/linux/commands/image18.png)

### cp (copy files and directories)

`cp` 명령어는 파일과 디렉토리를 한 위치에서 다른 위치로 복사하는 데 사용됩니다. `cp` 명령어는 원본 파일이나 디렉토리를 변경하지 않습니다. `cp` 명령어를 성공적으로 실행한 후에는 원본 파일/디렉토리와 복사본이 모두 공존합니다.

`cp` 명령어의 일반적인 구문:

```shell
cp <source_path> <destination_path>
```

현재 우리는 `/home/runner` 디렉토리에 있습니다. `mkdir` 명령어를 사용하여 `test_directory`라는 새 디렉토리를 생성할 것입니다. 이제 `_test_runner.py` 파일을 방금 생성한 디렉토리로 복사해 보겠습니다.

![](images/linux/commands/image23.png)

원본 `_test_runner.py` 파일에는 아무 일도 일어나지 않았습니다. 여전히 현재 디렉토리에 있습니다. 그 파일의 새 복사본이 `test_directory` 내부에 생성되었습니다.

![](images/linux/commands/image14.png)

`cp` 명령어를 사용하여 전체 디렉토리를 한 위치에서 다른 위치로 복사할 수도 있습니다. 예시를 통해 이를 이해해 봅시다.

![](images/linux/commands/image12.png)

우리는 다시 `mkdir` 명령어를 사용하여 `another_directory`라는 새 디렉토리를 만들었습니다. 그런 다음 `cp` 명령어와 추가 인수 `-r`을 함께 사용하여 `test_directory`를 복사했습니다.

**mv (move files and directories)**

`mv` 명령어는 파일이나 디렉토리를 한 위치에서 다른 위치로 이동하는 데 사용되거나, 파일이나 디렉토리의 이름을 변경하는 데 사용될 수 있습니다. 파일을 이동하는 것과 복사하는 것은 매우 다르다는 점을 유의하십시오. 파일이나 디렉토리를 이동하면 원본 복사본은 사라집니다.

`mv` 명령어의 일반적인 구문:

```shell
mv <source_path> <destination_path>
```

이 예시에서, 우리는 `mv` 명령어를 사용하여 `_test_runner.py` 파일을 `test_directory`로 이동할 것입니다. 이 경우, 이 파일은 이미 `test_directory`에 존재합니다. `mv` 명령어는 그것을 덮어쓸 것입니다. `mv` 명령어가 성공적으로 실행된 후에는 원본 파일이 현재 디렉토리에 존재하지 않는다는 점에 유의하십시오.

![](images/linux/commands/image26.png)

`mv` 명령어를 사용하여 디렉토리를 한 위치에서 다른 위치로 이동할 수도 있습니다. 이 경우, `cp` 명령어를 사용할 때 필요했던 `-r` 플래그는 사용할 필요가 없습니다. `mv` 명령어를 사용하면 원본 디렉토리는 존재하지 않게 됩니다.

`mv` 명령어의 중요한 용도 중 하나는 파일과 디렉토리의 이름을 변경하는 것입니다. 이 명령어를 이름 변경에 어떻게 사용할 수 있는지 살펴봅시다.

먼저 위치를 `test_directory`로 변경했습니다. 그런 다음 `mv` 명령어를 사용하여 `_test_runner.py` 파일의 이름을 `test.py`로 변경했습니다.

![](images/linux/commands/image29.png)

## 파일 보기 명령어 (Commands for Viewing Files)

파일을 보는 데 자주 사용되는 다섯 가지 기본 명령어가 있습니다:

- cat

- head

- tail

- more

- less

이제 각 명령어가 무엇을 하는지, 그리고 이 명령어들을 어떻게 사용하는지 이해해 보겠습니다. 또한 제공된 예시들을 온라인 Bash 셸에서 실습해 보는 것이 좋습니다.

우리는 `numbers.txt`라는 새 파일을 만들고 이 파일에 1부터 100까지의 숫자를 삽입할 것입니다. 각 숫자는 별도의 줄에 있을 것입니다.

![](images/linux/commands/image21.png)

위 명령어에 대해 지금 걱정하지 마십시오. 이것은 숫자를 생성하는 데 사용되는 고급 명령어입니다. 우리는 그 다음 리디렉션 연산자를 사용하여 이 숫자들을 파일로 밀어 넣었습니다. I/O 리디렉션은 이후 섹션에서 논의할 것입니다.


### cat

`cat` 명령어의 가장 간단한 용도는 파일의 내용을 출력 화면에 인쇄하는 것입니다. 이 명령어는 매우 유용하며 다른 많은 목적으로도 사용될 수 있습니다. 다른 사용 사례는 나중에 학습할 것입니다.

![](images/linux/commands/image1.png)

위 명령어를 실행해 보면, 화면에 1부터 100까지의 숫자가 출력되는 것을 볼 수 있습니다. 모든 숫자를 보려면 위로 스크롤해야 할 것입니다.

### head

`head` 명령어는 기본적으로 파일의 처음 10줄을 표시합니다. 추가 인수를 포함하여 시작 부분에서 원하는 만큼의 줄을 표시할 수 있습니다.

이 예시에서는 `head` 명령어를 사용했을 때 파일의 처음 10줄만 볼 수 있습니다.

![](images/linux/commands/image15.png)

기본적으로 `head` 명령어는 처음 10줄만 표시합니다. 시작부터 보고 싶은 줄 수를 지정하려면, `-n` 인수를 사용하여 입력 값을 제공하십시오.

![](images/linux/commands/image16.png)

### tail

`tail` 명령어는 기본적으로 파일의 마지막 10줄을 표시합니다. 추가 인수를 포함하여 파일 끝에서 원하는 만큼의 줄을 표시할 수 있습니다.

![](images/linux/commands/image22.png)

기본적으로 `tail` 명령어는 마지막 10줄만 표시합니다. 끝에서부터 보고 싶은 줄 수를 지정하려면, `-n` 인수를 사용하여 입력 값을 제공하십시오.

![](images/linux/commands/image10.png)

이 예시에서는 명시적인 `-n` 옵션을 사용하여 `tail` 명령어를 사용했을 때 파일의 마지막 5줄만 볼 수 있습니다.

### more

`more` 명령어는 파일이 클 경우(예: 로그 파일), 한 화면씩 나누어 파일의 내용이나 명령어 출력을 표시합니다. 또한 파일 내에서 앞으로 이동과 제한적인 뒤로 이동을 허용합니다.

![](images/linux/commands/image33.png)

`more` 명령어는 현재 화면에 들어갈 수 있는 만큼을 표시하고, 사용자 입력이 있을 때까지 기다립니다. `Enter` 키를 누르면 한 줄씩 앞으로 이동하고, `Space` 키를 누르면 한 화면씩 앞으로 이동합니다.

### less

`less` 명령어는 `more`의 개선된 버전입니다. 이는 파일의 내용이나 명령어 출력을 한 페이지씩 표시합니다. 파일 내에서 뒤로 이동뿐만 아니라 앞으로 이동도 허용하며 검색 옵션도 있습니다. 화살표 키를 사용하여 한 줄씩 뒤로 또는 앞으로 이동할 수 있습니다. 한 페이지 앞으로 이동하려면 `Space`를 누르고, 한 페이지 뒤로 이동하려면 키보드의 `b`를 누릅니다. 파일의 처음과 끝으로 즉시 이동할 수 있습니다.

## Echo Command in Linux

`echo` 명령어는 셸에서 사용되는 가장 간단한 명령어 중 하나입니다. 이 명령어는 다른 프로그래밍 언어의 `print`와 동일합니다.

`echo` 명령어는 주어진 입력 문자열을 화면에 출력합니다.

![](images/linux/commands/image34.png)

## Text Processing Commands

이전 섹션에서 파일의 내용을 보는 방법을 배웠습니다. 많은 경우, 다음과 같은 작업을 수행하는 데 관심이 있을 수 있습니다:

- 특정 단어를 포함하는 줄만 출력

- 파일에서 특정 단어를 다른 단어로 교체

- 특정 순서로 줄 정렬

텍스트를 처리하는 데 자주 사용되는 세 가지 기본 명령어가 있습니다. :

- grep

- sed

- sort

이제 각 명령어가 무엇을 하는지, 그리고 이 명령어들을 어떻게 사용하는지 이해해 보겠습니다. 또한 제공된 예시들을 온라인 Bash 셸에서 실습해 보는 것이 좋습니다.

우리는 `numbers.txt`라는 새 파일을 만들고 이 파일에 1부터 10까지의 숫자를 삽입할 것입니다. 각 숫자는 별도의 줄에 있을 것입니다.

![](images/linux/commands/image8.png)

### grep

`grep` 명령어는 가장 간단한 형태로 텍스트 파일에서 특정 단어를 검색하는 데 사용할 수 있습니다. 이는 파일에서 특정 입력 문자열을 포함하는 모든 줄을 표시합니다. 검색하려는 단어는 `grep` 명령어에 인수로 제공됩니다.

`grep` 명령어의 일반적인 구문:

```shell
grep <word_to_search> <file_name>
```

이 예시에서, 우리는 파일에서 문자열 "1"을 검색하려고 합니다. `grep` 명령어는 이 문자열을 찾은 줄을 출력합니다.

![](images/linux/commands/image36.png)

### sed

`sed` 명령어는 가장 간단한 형태로 파일에서 텍스트를 교체하는 데 사용할 수 있습니다.

교체를 위한 `sed` 명령어의 일반적인 구문:

```shell
sed 's/<text_to_replace>/<replacement_text>/' <file_name>
```

`sed` 명령어를 사용하여 파일에서 "1"이 나타나는 모든 경우를 "3"으로 교체해 봅시다.

![](images/linux/commands/image31.png)

위 예시에서는 파일의 내용이 변경되지 않습니다. 내용을 실제로 변경하려면, 변경 사항이 파일에 반영되도록 `-i`라는 추가 인수를 사용해야 합니다.

### sort

`sort` 명령어는 인수로 제공된 입력을 정렬하는 데 사용할 수 있습니다. 기본적으로는 오름차순으로 정렬됩니다

정렬하기 전에 파일의 내용을 먼저 확인해 봅시다.

![](images/linux/commands/image27.png)

이제 `sort` 명령어를 사용하여 파일을 정렬해 보겠습니다. `sort` 명령어는 내용을 **사전 순서(lexicographical order)**로 정렬합니다.

![](images/linux/commands/image32.png)

위 예시에서는 파일의 내용이 변경되지 않습니다.

## I/O Redirection

각각의 열린 파일에는 **파일 디스크립터(file descriptor)**가 할당됩니다. 파일 디스크립터는 시스템에서 열린 파일에 대한 고유 식별자입니다. 시스템에는 항상 세 가지 기본 파일이 열려 있습니다: stdin (키보드), stdout (화면), stderr (화면에 출력되는 오류 메시지). 이 파일들은 리디렉션될 수 있습니다.

Linux에서는 모든 것이 파일입니다: 
[https://unix.stackexchange.com/questions/225537/everything-is-a-file](https://unix.stackexchange.com/questions/225537/everything-is-a-file)

지금까지 우리는 모든 출력을 **표준 출력(standard output)**인 화면에 표시했습니다. 우리는 몇 가지 특별한 연산자를 사용하여 명령어의 출력을 파일로, 또는 심지어 다른 명령어의 입력으로 리디렉션할 수 있습니다. I/O 리디렉션은 매우 강력한 기능입니다.

아래 예시에서, 우리는 `>` 연산자를 사용하여 `ls` 명령어의 출력을 `output.txt` 파일로 리디렉션했습니다.

![](images/linux/commands/image30.png)

아래 예시에서는 `echo` 명령어의 출력을 파일로 리디렉션했습니다.

![](images/linux/commands/image13.png)

우리는 또한 **파이프(pipes)**를 사용하여 명령어의 출력을 다른 명령어의 입력으로 리디렉션할 수 있습니다.

아래 예시에서, 우리는 파이프 (`|`) 연산자를 사용하여 `cat` 명령어의 출력을 `grep` 명령어의 입력으로 전달했습니다.

![](images/linux/commands/image6.png)

아래 예시에서, 우리는 파이프 (`|`) 연산자를 사용하여 `sort` 명령어의 출력을 `uniq` 명령어의 입력으로 전달했습니다. `uniq` 명령어는 입력에서 고유한 숫자만 출력합니다.

![](images/linux/commands/image28.png)

I/O redirection -
[https://tldp.org/LDP/abs/html/io-redirection.html](https://tldp.org/LDP/abs/html/io-redirection.html)
