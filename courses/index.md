# SRE 스쿨 (School of SRE)

<img src="img/sos.png" width=200 >

Site Reliability Engineers (SREs)는 소프트웨어 엔지니어링과 시스템 엔지니어링의 교차점에 위치합니다. 목표를 달성하기 위해 인프라와 소프트웨어 구성 요소를 조합하는 방법에는 무한한 순열과 조합이 존재할 수 있지만, 기초 기술에 집중함으로써 SREs는 이러한 시스템이 proprietary(독점적인), 3rd party(제3자), open systems(개방형 시스템)인지, run on cloud/on-prem infrastructure인지 등에 관계없이 복잡한 시스템과 소프트웨어를 다룰 수 있습니다. 특히, 이러한 시스템 및 인프라 영역이 서로 어떻게 관련되고 상호 작용하는지에 대한 깊은 이해를 얻는 것이 중요합니다. 소프트웨어 및 시스템 엔지니어링 기술의 조합은 드물며, 일반적으로 다양한 인프라, 시스템 및 소프트웨어에 대한 노출을 통해 시간이 지남에 따라 구축됩니다.

SREs는 사이트를 유지하기 위해 엔지니어링 관행을 도입합니다. 각 분산 시스템은 수많은 구성 요소들의 집합체입니다. SREs는 비즈니스 요구 사항을 검증하고, 이를 분산 시스템을 구성하는 각 구성 요소에 대한 SLAs로 변환하고, SLAs 준수 여부를 모니터링하고 측정하며, SLA 위반을 완화하거나 방지하기 위해 아키텍처를 재설계하거나 확장하고, 이러한 학습 내용을 새로운 시스템이나 프로젝트에 대한 피드백으로 추가하여 operational toil(운영 노고)을 줄입니다. 따라서 SREs는 day 0 design of the system(Day 0 설계)부터 중요한 역할을 수행합니다.

이 여정을 계속하면서, 저희는 이 캠퍼스들로부터 Site Reliability Engineering role이 정확히 무엇을 수반하는지? 그리고 성공적인 SRE가 되기 위해 관련된 기술과 역량을 어떻게 배울 수 있는지? 에 대한 많은 질문을 받기 시작했습니다.

몇 달이 빠르게 흐른 후, 이 캠퍼스 학생들 중 일부는 인턴 또는 정규직 엔지니어로 사이트 엔지니어링 팀의 일원이 되었으며, 저희는 전통적인 SRE background가 아닌 경력직 채용(lateral hires)도 조직에 영입했습니다. 바로 그때 저희 중 몇몇이 모여 신규 졸업 엔지니어들을 사이트 엔지니어링 팀에 어떻게 온보딩(onboard)할 수 있을지 고민하기 시작했습니다.

초급 SRE로서 습득해야 할 기본적인 기술 세트에 대해 안내하는 자료(resources)는 거의 없습니다. 이러한 자료가 부족하기 때문에, 개인이 업계의 공개 채용 포지션으로 진입하는 데 어려움을 겪고 있다고 느꼈습니다. 저희는 SRE로서의 경력(career)을 쌓고자 하는 모든 사람들을 위한 출발점(starting point)으로 School Of SRE를 만들었습니다.

이 과정(course)에서는 강력한 기초 기술을 구축하는 데 중점을 둡니다. 이 과정은 더 많은 실제 사례(real life examples)와 각 주제(topic)를 배우는 것이 SRE의 일일 업무 책임에서 어떻게 중요한 역할을 할 수 있는지를 제공하도록 구성(structured)되어 있습니다. 현재 School Of SRE에서 다루고 있는(covering) 주제는 다음과 같습니다.
 
-   Level 101
    -   기초 시리즈 (Fundamentals Series)
        -   [Linux Basics](https://linkedin.github.io/school-of-sre/level101/linux_basics/intro/)
        -   [Git](https://linkedin.github.io/school-of-sre/level101/git/git-basics/)
        -   [Linux Networking](https://linkedin.github.io/school-of-sre/level101/linux_networking/intro/)
    -   [Python and Web](https://linkedin.github.io/school-of-sre/level101/python_web/intro/)
    -   Data
        - [Relational Databases (MySQL)](https://linkedin.github.io/school-of-sre/level101/databases_sql/intro/)
        -   [NoSQL Concepts](https://linkedin.github.io/school-of-sre/level101/databases_nosql/intro/)
        -   [Big Data](https://linkedin.github.io/school-of-sre/level101/big_data/intro/)
    -   [Systems Design](https://linkedin.github.io/school-of-sre/level101/systems_design/intro/)
    -   [Metrics and Monitoring](https://linkedin.github.io/school-of-sre/level101/metrics_and_monitoring/introduction/)
    -   [Security](https://linkedin.github.io/school-of-sre/level101/security/intro/)

-   Level 102
    -   [Linux Intermediate](https://linkedin.github.io/school-of-sre/level102/linux_intermediate/introduction/)
    -   Linux Advanced
        -   [Containers and Orchestration](https://linkedin.github.io/school-of-sre/level102/containerization_and_orchestration/intro/)
        -   [System Calls and Signals](https://linkedin.github.io/school-of-sre/level102/system_calls_and_signals/intro/)
    -   [Networking](https://linkedin.github.io/school-of-sre/level102/networking/introduction/)
    -   [System Design](https://linkedin.github.io/school-of-sre/level102/system_design/intro/)
    -   [System Troubleshooting and Performance Improvements](https://linkedin.github.io/school-of-sre/level102/system_troubleshooting_and_performance/introduction/) 
    -   [Continuous Integration and Continuous Delivery](https://linkedin.github.io/school-of-sre/level102/continuous_integration_and_continuous_delivery/introduction/)

저희는 지속적인 학습이 더 깊은 지식과 역량을 습득하여 기술 세트를 확장하는 데 도움이 될 것이라고 믿습니다. 각 모듈에는 추가 학습을 위한 참고 자료(references)가 포함되어 있습니다. 저희의 희망은 이 모듈들을 거치면서 Site Reliability Engineer에게 요구되는 필수 기술을 구축할 수 있다는 것입니다.

LinkedIn에서는 이 커리큘럼을 비전통적인 채용 인력(non-traditional hires)과 신규 졸업자(new college grads)를 SRE role에 온보딩하는 데 사용하고 있습니다. 저희는 신규 직원들과 여러 차례 성공적인 온보딩 경험을 했으며, 이 과정은 그들이 매우 짧은 기간 내에 생산성을 갖추는 데 도움을 주었습니다.

이러한 성공에 힘입어, 저희는 다른 조직들이 신규 엔지니어들을 이 역할에 온보딩하는 것을 돕고, 이 역할에 도전하는 개인들에게 지침을 제공하기 위해 이 콘텐츠를 오픈 소스로 공개하게 되었습니다. 저희는 처음에 만든 이 콘텐츠가 단지 시작점(starting point)임을 인식하고 있으며, 커뮤니티가 이 콘텐츠를 다듬고 확장하는 여정에 도움을 줄 수 있기를 바랍니다. 참여를 시작하려면 [the contributing guide](./CONTRIBUTING.md) 를 확인하십시오.
