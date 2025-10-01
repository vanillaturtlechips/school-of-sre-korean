저희는 처음에 만든 콘텐츠가 단지 **시작점(starting point)**임을 인식하고 있으며, 커뮤니티가 콘텐츠를 다듬고 확장하는 여정에 도움을 줄 수 있기를 희망합니다.

기여자(contributor)로서 귀하가 제출하는 콘텐츠는 **표절(plagiarised)**되지 않았음을 진술하는 것입니다. 콘텐츠를 제출함으로써 귀하(및 해당되는 경우 귀하의 고용주)는 제출된 콘텐츠를 Creative Commons Attribution 4.0 International Public License에 따라 LinkedIn 및 오픈 소스 커뮤니티에 라이선스를 부여하는 것입니다.

*Repository URL*: [https://github.com/linkedin/school-of-sre](https://github.com/linkedin/school-of-sre)

### Contributing Guidelines
다음 지침을 준수해 주십시오:

* 원칙 및 개념에 관한 내용이어야 하며, 이는 어떤 회사나 개인 프로젝트에서도 적용될 수 있어야 합니다. (시간이 지남에 따라 변동되기 쉬운) 특정 도구나 기술 스택에 초점을 맞추지 마십시오.
* 행동 강령을 준수하십시오. [Code of Conduct](/school-of-sre/CODE_OF_CONDUCT/).
* SRE의 역할과 책임에 관련된 내용이어야 합니다
* (테스트 단계를 참조하여) 로컬에서 테스트되었고 형식이 잘 갖추어져 있어야 합니다.
* Pull Request를 제출하기 전에 먼저 이슈(Issue)를 열어 변경 사항에 대해 논의하는 것이 좋은 관행입니다. 이렇게 하면 작업을 시작하기 전에 다른 사람들의 아이디어를 통합할 수 있습니다.

### 로컬에서 빌드 및 테스트하기 (Building and testing locally)
Pull Request를 열기 전에 다음 명령어를 실행하여 로컬에서 사이트를 빌드하고 확인하십시오.

```shell
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdocs build
mkdocs serve
```

### Opening a PR
Follow the [GitHub PR workflow](https://guides.github.com/introduction/flow/) for your contributions.

이 저장소(repo)를 포크(Fork)하고, 기능 브랜치(feature branch)를 생성한 후, 변경 사항을 커밋(commit)하고 이 저장소로 PR을 여십시오.