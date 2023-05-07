# Quest 17-B. 배포 파이프라인

## Introduction

- 이번 퀘스트에서는 CI/CD 파이프라인이 왜 필요한지, 어떻게 구축할 수 있는지 등에 대해 다룹니다.

## Topics

- Continuous Integration
- Continuous Delivery
- AWS Codebuild

## Resources

- [AWS: Continuous Integration](https://aws.amazon.com/ko/devops/continuous-integration/)
- [AWS: Continuous Delivery](https://aws.amazon.com/ko/devops/continuous-delivery/)
- [AWS Codebuild](https://aws.amazon.com/ko/codebuild/getting-started/)

## Checklist

- CI/CD는 무엇일까요? CI/CD 시스템을 구축하면 어떤 장점이 있을까요?
  > CI:Contioniois Integration, 코드 변경사항, 각 개발자들이 진행한 개발내용 등이 정기적으로 빌드/테스트되어 하나의 branch(또는 통합 저장소)로 통합되어 관리하는 방식이다. 즉 기존 코드를 관리하는 방식(개발 완료->품질 관리)에서 벗어나, 코드통합을 지속적으로 진행하면서 품질 관리르 동시에 수행한다는 개념이다. CI를 진행시 기능의 중복 및 충돌을 방지하고, 그만큼 긴밀함을 유지할 수 있다.
  > CD:Continuous Delivery & Continuous Deployment,지속적인 서비스 제공과 지속적인 배포
  > 저장소로 relase하는 과정을 자동화, 더 나아가 고객이 접하는 프로덕트 수준의 코드까지 운영서버에 자동으로 release한다는 개념이다.
  > 소프트웨어가 항상 최신버전을 유지하고, 고객대응(프로덕션)이 빠른 시간내 이루어질 수 있도록 배포과정을 자동으로 진행한다.
- CI 시스템인 Travis CI, Jenkins, Circle CI, Github Actions, AWS Codebuild 의 차이점과 장단점은 무엇일까요?

  > Jenkins:CI 시스템에서 가장 많이 활용한느 오픈 소스 CI 서버이다. 코드의 build, test, deploy를 지원해주는 tool이다

  > Circle CI:CI/CD 플랫폼을 제공하는 소프트웨어이다. 소프트웨어를 활용하여 CI/CD 과정을 자동화할 수 있도록 지원한다.

  > AWS Codebuild: AWS에서 제공하는 툴, 완전히 managed된 build service를 제공한다. 컴파일,실행,프로덕션까지 수행해주기 때문에 AWS Codebuild를 채택하면 별도의 build server를 관리하고 모니터링할 필요가 없다.

## Quest

- AWS Codebuild를 이용하여, 특정 브랜치에 푸시를 하면 린트와 테스트를 거쳐 서버 이미지를 빌드한 뒤, 직전 퀘스트의 EC2 인스턴스에 배포되는 시스템을 만들어 보세요.

## Advanced

- 빅테크 회사들이 코드를 빌드하고 배포하는 시스템은 어떻게 설계되고 운영되고 있을까요?
