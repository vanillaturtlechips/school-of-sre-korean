# Linux 서버 관리

이 과정에서는 Linux 서버 관리자가 수행하는 일반적인 작업 중 일부를 다루려고 합니다. 먼저 특정 명령어가 무엇을 하는지 이해한 다음, 예시를 통해 명령어들을 이해해 볼 것입니다. Linux 명령어를 직접 실습하는 것이 매우 중요하다는 점을 명심하십시오.

## 실습 환경 설정 (Lab Environment Setup)

- 여러분의 시스템에 Docker를 설치하세요. - [https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/) 온라인을 사용하고 싶으면, [Docker playground](https://labs.play-with-docker.com/)

- 우리는 Red Hat Enterprise Linux (RHEL) 8 시스템에서 모든 명령어를 실행할 것입니다

  ![](images/linux/admin/image19.png)

- 이 모듈에서 사용되는 대부분의 명령어를 위의 Docker 컨테이너에서 실행할 것입니다.

## 다중 사용자 운영체제 (Multi-User Operating Systems)

운영체제가 여러 사람/사용자가 컴퓨터를 사용하고 서로의 파일이나 환경 설정에 영향을 주지 않도록 허용하면 **다중 사용자(multi-user)**로 간주됩니다. Linux 기반 운영체제는 여러 사용자가 동시에 시스템에 접근하도록 허용하므로 본질적으로 다중 사용자입니다. 일반적인 컴퓨터는 키보드와 모니터가 하나뿐이지만, 컴퓨터가 네트워크에 연결되어 있다면 여러 사용자가 SSH를 통해 로그인할 수 있습니다. SSH에 대해서는 나중에 더 자세히 다룰 것입니다.

서버 관리자로서 우리는 대부분 우리와 물리적으로 매우 멀리 떨어져 있는 Linux 서버에 관심을 가집니다. 우리는 SSH와 같은 원격 로그인 방법을 통해 이 서버들에 연결할 수 있습니다.

Linux는 다중 사용자를 지원하므로, 사용자들을 서로 보호할 수 있는 방법이 필요합니다. 한 사용자가 다른 사용자의 파일에 접근하거나 수정할 수 없어야 합니다.

## 사용자/그룹 관리 (User/Group Management)

- Linux의 사용자에게는 **UID(User ID)**라는 사용자 ID가 연결되어 있습니다.

- 사용자는 또한 자신과 연결된 홈 디렉토리와 로그인 셸을 가집니다.

- 그룹은 하나 이상의 사용자 모음입니다. 그룹은 사용자 그룹 간에 권한을 공유하는 것을 더 쉽게 만듭니다.

- 각 그룹에는 **GID(Group ID)**라는 그룹 ID가 연결되어 있습니다.

### id command

`id` 명령어는 사용자에게 연결된 **uid와 gid**를 찾는 데 사용될 수 있습니다. 또한 사용자가 속한 그룹 목록도 나열합니다.

루트 사용자(root user)와 연결된 `uid`와 `gid`는 0입니다.

![](images/linux/admin/image30.png)

Linux에서 현재 사용자를 확인하는 좋은 방법은 `whoami` 명령어를 사용하는 것입니다

![](images/linux/admin/image35.png)

**`root` 사용자 또는 슈퍼유저는 시스템의 모든 리소스에 무제한적인 접근 권한을 가진 가장 특권적인 사용자입니다. 이 사용자는 UID 0을 가집니다.**

### Important files associated with users/groups

| Files        | Description                                                                            |
|--------------|----------------------------------------------------------------------------------------|
| /etc/passwd  | 	사용자 이름, `uid`, `gid`, 홈 디렉토리, 로그인 셸 등을 저장합니다.                           |
| /etc/shadow  | 사용자와 연결된 **암호(password)**를 저장합니다.                                            |
| /etc/group   | 시스템의 다양한 그룹에 대한 정보를 저장합니다.                                                |

![](images/linux/admin/image23.png)

![](images/linux/admin/image21.png)

![](images/linux/admin/image9.png)

위 출력에서 논의된 각 필드를 이해하고 싶다면, 다음 링크들을 참고할 수 있습니다:

- [https://tldp.org/LDP/lame/LAME/linux-admin-made-easy/shadow-file-formats.html](https://tldp.org/LDP/lame/LAME/linux-admin-made-easy/shadow-file-formats.html)

- [https://tldp.org/HOWTO/User-Authentication-HOWTO/x71.html](https://tldp.org/HOWTO/User-Authentication-HOWTO/x71.html)

## 사용자 관리를 위한 중요한 명령어

Linux에서 사용자/그룹을 관리하는 데 자주 사용되는 명령어는 다음과 같습니다:

- `useradd` - 새 사용자를 생성합니다.
- `passwd` - 사용자의 암호를 추가하거나 수정합니다.
- `usermod` - 사용자의 속성을 수정합니다.
- `userdel` -  사용자를 삭제합니다.

### useradd

`useradd` 명령어는 Linux에 새 사용자를 추가합니다.

새 사용자 `shivam`을 생성하고 `/etc/passwd` 파일의 끝 부분을 확인하여 사용자가 생성되었는지 확인할 것입니다. 새로 생성된 사용자의 `uid`와 `gid`는 1000입니다. 사용자에게 할당된 홈 디렉토리는 `/home/shivam`이고, 로그인 셸은 `/bin/bash`입니다. 사용자 홈 디렉토리와 로그인 셸은 나중에 수정될 수 있다는 점을 유의하십시오.

![](images/linux/admin/image41.png)

홈 디렉토리나 로그인 셸과 같은 속성에 값을 지정하지 않으면, 기본값이 사용자에게 할당됩니다. 새 사용자를 생성할 때 이러한 기본값을 재정의할 수도 있습니다.

![](images/linux/admin/image54.png)

### passwd

`passwd` 명령어는 사용자의 암호를 생성하거나 수정하는 데 사용됩니다.

위 예시들에서 우리는 `shivam`이나 `amit` 사용자를 생성할 때 암호를 할당하지 않았습니다.

`shadow` 파일의 계정 항목에 있는 `!!` 표시는 사용자 계정은 생성되었지만, 아직 암호가 부여되지 않았음을 의미합니다.

![](images/linux/admin/image13.png)

이제 `shivam` 사용자의 암호를 생성해 봅시다.

![](images/linux/admin/image55.png)

나중에 유용하게 사용할 예시들이 있으므로 암호를 기억해 두십시오.

또한, 이제 루트 사용자의 암호를 변경해 봅시다. 일반 사용자에서 루트 사용자로 전환할 때 암호를 요청할 것입니다. 또한 루트 사용자로 로그인할 때도 암호를 요청할 것입니다.

![](images/linux/admin/image39.png)

### usermod

`usermod` 명령어는 홈 디렉토리 또는 셸과 같은 사용자의 속성을 수정하는 데 사용됩니다.

`amit` 사용자의 로그인 셸을 `/bin/bash`로 수정해 봅시다.

![](images/linux/admin/image17.png)

이와 유사한 방식으로 사용자의 다른 많은 속성도 수정할 수 있습니다. 수정 가능한 속성 목록을 보려면 `usermod -h`를 시도해 보세요.

### userdel

`userdel` 명령어는 Linux에서 사용자를 제거하는 데 사용됩니다. 사용자를 제거하면 해당 사용자와 관련된 모든 정보가 제거됩니다.

`amit` 사용자를 삭제해 봅시다. 사용자를 삭제한 후에는 `/etc/passwd`나 `/etc/shadow` 파일에서 해당 사용자에 대한 항목을 찾을 수 없을 것입니다.

![](images/linux/admin/image34.png)

## 그룹 관리를 위한 중요한 명령어

그룹 관리를 위한 명령어는 사용자 관리를 위한 명령어와 매우 유사합니다. 각 명령어는 매우 비슷하기 때문에 여기서는 자세히 설명하지 않습니다. 시스템에서 이 명령어들을 실행해 볼 수 있습니다.

| Command                | Description                     |
| -----------------------| ------------------------------- |
| groupadd <group_name\> | 새 그룹을 생성합니다               |
| groupmod <group_name\> | 그룹의 속성을 수정합니다.           |
| groupdel <group_name\> | 그룹을 삭제합니다.                 |
| gpasswd  <group_name\> | 그룹의 암호를 수정합니다.           |

![](images/linux/admin/image52.png)

이제 `shivam` 사용자를 위에서 생성한 그룹에 추가해 봅시다.

![](images/linux/admin/image33.png)

## 슈퍼유저 되기 (Becoming a Superuser)

**아래 명령어를 실행하기 전에, 위 섹션에서 설명한 `passwd` 명령어를 사용하여 `shivam` 사용자와 `root` 사용자에 대해 암호를 설정했는지 확인하십시오.**

`su` 명령어는 `Linux`에서 사용자를 전환하는 데 사용될 수 있습니다. 이제 `shivam` 사용자로 전환해 봅시다.

![](images/linux/admin/image37.png)

이제 `/etc/shadow` 파일을 열어 봅시다.

![](images/linux/admin/image29.png)

운영체제는 `shivam` 사용자가 `/etc/shadow` 파일의 내용을 읽는 것을 허용하지 않았습니다. 이 파일은 사용자의 암호를 저장하는 Linux의 중요한 파일입니다. 이 파일은 `root` 또는 `슈퍼유저 권한을 가진 사용자`만 접근할 수 있습니다.


`sudo` 명령어는 사용자가 root 사용자의 보안 권한으로 명령을 실행할 수 있도록 허용합니다. 루트 사용자는 시스템에 대한 모든 권한을 가진다는 점을 기억하십시오. `su` 명령어를 사용하여 루트 사용자로 전환하고 위 파일을 열 수도 있지만, 그렇게 하려면 루트 사용자의 암호가 필요합니다. 대부분의 최신 운영체제에서 선호되는 대안적인 방법은 `sudo` 명령어를 사용하여 슈퍼유저가 되는 것입니다. 이 방법을 사용하면 사용자는 자신의 암호를 입력해야 하며, `sudo` 그룹의 일부여야 합니다.

**다른 사용자에게 슈퍼 권한을 제공하는 방법은 무엇일까요?**

먼저 `su` 명령어를 사용하여 루트 사용자(root user)로 전환해 봅시다. 아래 명령어를 사용하려면 루트 사용자의 암호를 입력해야 한다는 점을 유의하십시오.

![](images/linux/admin/image44.png)

만약 루트 사용자의 암호를 설정하는 것을 잊었다면, `exit`를 입력하면 루트 사용자로 돌아갈 수 있습니다. 이제 `passwd` 명령어를 사용하여 암호를 설정하십시오.

**`/etc/sudoers` 파일에는 `sudo`를 호출할 수 있는 권한을 가진 사용자 이름이 담겨 있습니다. **. Red Hat 운영체제에서는 이 파일이 기본적으로 존재하지 않습니다. 우리는 `sudo`를 설치해야 합니다.

![](images/linux/admin/image3.png)

`yum` 명령어에 대해서는 나중 섹션에서 자세히 논의할 것입니다.

시스템에서 `/etc/sudoers` 파일을 열어보십시오. 파일에는 많은 정보가 있습니다. 이 파일은 사용자들이 `sudo` 명령어를 실행할 때 따라야 하는 규칙을 저장합니다. 예를 들어, `root`는 어디서든 모든 명령어를 실행하는 것이 허용됩니다.

![](images/linux/admin/image8.png)

사용자에게 루트 접근 권한을 제공하는 한 가지 쉬운 방법은 모든 명령어를 실행할 권한을 가진 그룹에 그들을 추가하는 것입니다. `wheel`은 Red Hat Linux에서 그러한 권한을 가진 그룹입니다.

![](images/linux/admin/image25.png)

이제 `shivam` 사용자에게도 `sudo` 권한이 있도록 이 그룹에 추가해 봅시다.

![](images/linux/admin/image48.png)

이제 `shivam` 사용자로 다시 전환하여 `/etc/shadow` 파일에 접근해 봅시다.

![](images/linux/admin/image56.png)

`sudo` 권한으로만 접근할 수 있기 때문에 명령어를 실행하기 전에 `sudo`를 사용해야 합니다. 우리는 이미 `shivam`을 `wheel` 그룹에 추가하여 `sudo` 권한을 부여했습니다.


## 파일 권한 (File Permissions)

Linux 운영체제에서 각 파일과 디렉토리는 파일의 소유자, 관련 사용자 그룹의 구성원, 그리고 나머지 모든 사람에 대한 접근 권한이 할당됩니다. 이는 한 사용자가 다른 사용자의 파일과 리소스에 접근할 수 없도록 보장하기 위함입니다.

파일의 권한을 보려면 `ls` 명령어를 사용할 수 있습니다. `/etc/passwd` 파일의 권한을 살펴봅시다

![](images/linux/admin/image40.png)

파일 권한과 관련된 출력의 몇 가지 중요한 필드를 살펴보겠습니다.

![](images/linux/admin/image31.jpg)


![](images/linux/admin/image57.png)

### Chmod command

`chmod` 명령어는 Linux에서 파일 및 디렉토리의 권한을 수정하는 데 사용됩니다.

`chmod` 명령어는 권한을 숫자 인수로 받습니다. 우리는 권한을 비트(bit)의 연속으로 생각할 수 있으며, 1은 True 또는 허용됨을, 0은 False 또는 허용되지 않음을 나타냅니다.

| Permission               | rwx     | Binary  |   Decimal |
| -------------------------| ------- | ------- | --------- |
| Read, write and execute  | rwx     | 111     | 7         |
| Read and write           | rw-     | 110     | 6         |
| Read and execute         | r-x     | 101     | 5         |
| Read only                | r--     | 100     | 4         |
| Write and execute        | -wx     | 011     | 3         |
| Write only               | -w-     | 010     | 2         |
| Execute only             | --x     | 001     | 1         |
| None                     | ---     | 000     | 0         |

이제 새 파일을 만들고 파일의 권한을 확인해 보겠습니다.

![](images/linux/admin/image15.png)

그룹 소유자는 이 파일에 쓸 수 있는 권한이 없습니다. `chmod` 명령어를 사용하여 그룹 소유자, 즉 root에게 쓰기 권한을 부여해 봅시다.

![](images/linux/admin/image26.png)

`chmod` 명령어는 이와 유사한 방식으로 디렉토리의 권한을 변경하는 데도 사용될 수 있습니다.

### Chown command

`chown` 명령어는 Linux에서 파일 또는 디렉토리의 소유자를 변경하는 데 사용됩니다.

명령어 구문: `chown \<new_owner\> \<file_name\>`

![](images/linux/admin/image6.png)

**`sudo` 권한이 없는 경우, `sudo` 명령어를 사용해야 합니다.**. `shivam` 사용자로 전환하여 소유자 변경을 시도해 봅시다. 또한 아래 명령어를 실행하기 전에 파일의 소유자를 `root`로 변경했습니다.

![](images/linux/admin/image12.png)

`chown` 명령어는 이와 유사한 방식으로 디렉토리의 소유자를 변경하는 데도 사용될 수 있습니다.

### Chgrp command

`chgrp` 명령어는 Linux에서 파일 또는 디렉토리의 그룹 소유권을 변경하는 데 사용될 수 있습니다. 구문은 `chown` 명령어와 매우 유사합니다.

![](images/linux/admin/image27.png)

`chgrp` 명령어는 이와 유사한 방식으로 디렉토리의 그룹 소유권을 변경하는 데도 사용될 수 있습니다.

## SSH Command

`ssh` 명령어는 원격 시스템에 로그인하거나, 시스템 간에 파일을 전송하거나, 원격 머신에서 명령어를 실행하는 데 사용됩니다. SSH는 Secure Shell의 약자로, 인터넷과 같은 안전하지 않은 네트워크를 통해 두 호스트 간에 암호화된 보안 연결을 제공하는 데 사용됩니다.

Reference:
[https://www.ssh.com/ssh/command/](https://www.ssh.com/ssh/command/)

이제 보안성이 높고 `ssh` 인증에 가장 일반적으로 사용되는 암호 없이 인증하는 방법에 대해 논의할 것입니다.

### SSH를 사용한 암호 없는 인증 (Passwordless Authentication Using SSH)

이 방법을 사용하면 암호를 입력하지 않고도 호스트에 `ssh`로 접속할 수 있습니다. 이 방법은 일부 스크립트가 `ssh` 관련 작업을 수행하도록 할 때도 유용합니다.

암호 없는 인증은 공개 키와 개인 키 쌍을 사용해야 합니다. 이름에서 알 수 있듯이, 공개 키는 누구와도 공유할 수 있지만, 개인 키는 비밀로 유지되어야 합니다

이 인증이 어떻게 작동하는지에 대한 세부 사항은 생략하겠습니다. 자세한 내용은 여기에서 더 읽어볼 수 있습니다.

[here](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)

원격 호스트와 암호 없는 인증을 설정하는 단계:

1. Generating public-private key pair  

    **If we already have a key pair stored in `~/.ssh` directory, we will not need to generate keys again.**

    Install `openssh` package which contains all the commands related to `ssh`.

    ![](images/linux/admin/image49.png)

    Generate a key pair using the `ssh-keygen` command. One can choose the
    default values for all prompts.

    ![](images/linux/admin/image47.png)

    After running the `ssh-keygen` command successfully, we should see two
    keys present in the `~/.ssh` directory. `id_rsa` is the private key and
    `id_rsa.pub` is the public key. Do note that the private key can only be
    read and modified by you.

    ![](images/linux/admin/image7.png)

2. Transferring the public key to the remote host

    There are multiple ways to transfer the public key to the remote server.
    We will look at one of the most common ways of doing it using the
    `ssh-copy-id` command.

    ![](images/linux/admin/image11.png)

    Install the `openssh-clients` package to use `ssh-copy-id` command.

    ![](images/linux/admin/image46.png)

    Use the `ssh-copy-id` command to copy your public key to the remote host.

    ![](images/linux/admin/image50.png)

    Now, `ssh` into the remote host using the password authentication.

    ![](images/linux/admin/image51.png)

    Our public key should be there in `~/.ssh/authorized_keys` now.

    ![](images/linux/admin/image4.png)

    `~/.ssh/authorized_key` contains a list of public keys. The users
    associated with these public keys have the `ssh` access into the remote
    host.


### How to run commands on a remote host ?

General syntax: 

```shell
ssh \<user\>@\<hostname/hostip\> \<command\>
```

![](images/linux/admin/image14.png)

### How to transfer files from one host to another host ?

General syntax:

```shell
scp \<source\> \<destination\>
```

![](images/linux/admin/image32.png)

## Package Management

Package management is the process of installing and managing software on
the system. We can install the packages which we require from the Linux
package distributor. Different distributors use different packaging
systems.
  
| Packaging systems      | Distributions                              |
| ---------------------- | ------------------------------------------ |
| Debian style (`.deb`)  |   Debian, Ubuntu                           |
| Red Hat style (`.rpm`) |   Fedora, CentOS, Red Hat Enterprise Linux |

**Popular Packaging Systems in Linux**

|Command                        | Description                                         |
| ----------------------------- | --------------------------------------------------- |
| yum install <package_name\>   | Installs a package on your system                   |
| yum update <package_name\>    | Updates a package to its latest available version   |
| yum remove <package_name\>    | Removes a package from your system                  |
| yum search <keyword\>         | Searches for a particular keyword                   |

[DNF](https://docs.fedoraproject.org/en-US/quick-docs/dnf/) is
the successor to YUM which is now used in Fedora for installing and
managing packages. DNF may replace YUM in the future on all RPM-based
Linux distributions.

![](images/linux/admin/image20.png)

We did find an exact match for the keyword `httpd` when we searched using
`yum search` command. Let's now install the `httpd` package.

![](images/linux/admin/image28.png)

After `httpd` is installed, we will use the `yum remove` command to remove
`httpd` package.

![](images/linux/admin/image43.png)

## Process Management

In this section, we will study about some useful commands that can be
used to monitor the processes on Linux systems.

### ps (process status)

The `ps` command is used to know the information of a process or list of
processes.

![](images/linux/admin/image24.png)

If you get an error "ps command not found" while running `ps` command, do
install `procps` package.

`ps` without any arguments is not very useful. Let's try to list all the
processes on the system by using the below command.

Reference:
[https://unix.stackexchange.com/questions/106847/what-does-aux-mean-in-ps-aux](https://unix.stackexchange.com/questions/106847/what-does-aux-mean-in-ps-aux)

![](images/linux/admin/image42.png)

We can use an additional argument with `ps` command to list the
information about the process with a specific process ID (PID).

![](images/linux/admin/image2.png)

We can use `grep` in combination with `ps` command to list only specific
processes.

![](images/linux/admin/image1.png)

### top

The `top` command is used to show information about Linux processes
running on the system in real time. It also shows a summary of the
system information.

![](images/linux/admin/image53.png)

For each process, `top` lists down the process ID, owner, priority, state,
CPU utilization, memory utilization and much more information. It also
lists down the memory utilization and CPU utilization of the system as a
whole along with system uptime and CPU load average.

## Memory Management

In this section, we will study about some useful commands that can be
used to view information about the system memory.

### free

The `free` command is used to display the memory usage of the system. The
command displays the total free and used space available in the RAM
along with space occupied by the caches/buffers.

![](images/linux/admin/image22.png)

`free` command by default shows the memory usage in kilobytes. We can use
an additional argument to get the data in human-readable format.

![](images/linux/admin/image5.png)

### vmstat

The `vmstat` command can be used to display the memory usage along with
additional information about IO and CPU usage.

![](images/linux/admin/image38.png)

## Checking Disk Space

In this section, we will study about some useful commands that can be
used to view disk space on Linux.

### df (disk free)

The `df` command is used to display the free and available space for each
mounted file system.

![](images/linux/admin/image36.png)

### du (disk usage)

The `du` command is used to display disk usage of files and directories on
the system.

![](images/linux/admin/image10.png)

The below command can be used to display the top 5 largest directories
in the `root` directory.

![](images/linux/admin/image18.png)

## Daemons

A computer program that runs as a background process is called a _daemon_.
Traditionally, the name of daemon processes ends with `d` - `sshd`, `httpd`,
etc. We cannot interact with a daemon process as they run in the
background.

Services and daemons are used interchangeably most of the time.

## Systemd

`systemd` is a system and service manager for Linux operating systems.
`systemd` units are the building blocks of `systemd`. These units are
represented by unit configuration files.

The below examples shows the unit configuration files available at
`/usr/lib/systemd/system` which are distributed by installed RPM packages.
We are more interested in the configuration file that ends with service
as these are service units.

![](images/linux/admin/image16.png)

### Managing System Services

Service units end with `.service` file extension. `systemctl` command can be
used to start/stop/restart the services managed by `systemd`.

| Command                         | Description                            |
| ------------------------------- | -------------------------------------- |
| systemctl start name.service    | Starts a service                       |
| systemctl stop name.service     | Stops a service                        |
| systemctl restart name.service  | Restarts a service                     |
| systemctl status name.service   | Check the status of a service          |
| systemctl reload name.service   | Reload the configuration of a service  |

## Logs 

In this section, we will talk about some important files and directories
which can be very useful for viewing system logs and applications logs
in Linux. These logs can be very useful when you are troubleshooting on
the system.

![](images/linux/admin/image58.png)
