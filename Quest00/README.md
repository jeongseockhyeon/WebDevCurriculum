# Quest 00. 형상관리 시스템

# start

## Introduction

- git은 2021년 현재 개발 생태계에서 가장 각광받고 있는 버전 관리 시스템입니다. 이번 퀘스트를 통해 git의 기초적인 사용법을 알아볼 예정입니다.

## Topics

- git
  - `git clone`, `git add`, `git commit`, `git push`, `git pull`, `git branch`, `git stash` 명령
  - `.git` 폴더
- GitHub

## Resources

- [Resources to learn Git](https://try.github.io)
- [Learn Git Branching](https://learngitbranching.js.org/?locale=ko)
- [Inside Git: .Git directory](https://githowto.com/git_internals_git_directory)

## Checklist

- 형상관리 시스템은 왜 나오게 되었을까요?

  > 소프트웨어의 변경사항을 체계적으로 추적하고 통제하기 위해 개발된 시스템이다. 즉 이 시스템은 어떠한 문서나 파일이 변경된 겨우, 변경된 내용과 그 원인을 기록하였다가 나중에 필요한 경우 찾아볼 수 있도록 관리한다.

- git은 어떤 형상관리 시스템이고 어떤 특징을 가지고 있을까요? 분산형 형상관리 시스템이란 무엇일까요?

  > git은 분산형 형상관리 시스템을 사용하며 git의 특징은 설치가 간단하고 빠른 속도를 자랑한다. 또한 브랜치 병합이 매우 빠르고 사용법도 상당히 간단하다. 분산형 형상관리 시스템은 레포지토리를 여러 곳에 분산시켜서 관리하는 시스템이다.

- git은 어떻게 개발되게 되었을까요? git이 분산형 시스템을 채택한 이유는 무엇일까요?
  예전에는 협업을 위해 서로 Bitkeeper라는 상용 프로그램을 사용했었다. 예전에도 개발자마다의 서로 다른 버전관리가 굉장히 중요한 포인트 중 하나였으며 리눅스 커널 개발 시에도 사용 중이었다. 그만큼 분산형을 통한 Bitkeer의 중요도가 매우 높아져있던 상태였는데 이 시기에 Bitkeeper가 유료화되면서 절대적 오픈소스를 지향하던 Linus Torvalds가 git을 개발하여 대체하였다.

- git과 GitHub은 어떻게 다를까요?

  > github는 git 저장소를 관리하는 클라우드 기반 호스팅 서비스로 다른 사람과 소스코드 공유하며 git의 기본적인 기능을 확장하여 제공한다. 즉 한 프로젝트에 여러 명의 사람이 참여하여 버전 제어 및 공동 작업이 가능하게 한다. 간단하게 정리하면 git은 버전 관리 프로그램, github은 버전 관리,소스 코드 공유, 분산 버전 제어 등등이 가능한 원격 저장소이다.

- git의 clone/add/commit/push/pull/branch/stash 명령은 무엇이며 어떨 때 이용하나요? 그리고 어떻게 사용하나요?

  > clone:저장소를 복제해 새 디렉터리로 가져오는 명령어 git clone <url>
  > add:파일을 staging area에 추가하는 명령어, 파일을 staged 상태로 바꾼다. git add <파일명>
  > commit:변경사항을 저장소에 기록하는 명령어, staged 상태인 파일만 commit 할 수 있다. git commit -m <메시지>
  > push:저장소에 기록한 변경사항을 업데이트하는 명령어 git push origin <브랜치명>
  > branch:branch 생성 및 제거, 확인 등의 기능을 하는 명령어
  > branch 생성: git branch <브랜치명>
  > branch 목록 확인: git branch
  > branch 생성 및 이동: git branch -d <브랜치명>
  > branch 제거: git branch -d <브랜치명>
  > stash:아직 마무리하지 않은 작업을 스택에 잠시 저장할 수 있도록 하는 명령어, 이를 통해 완료하지 않은 일을 commit하지 않고 나중에 다시 꺼내와 마무리할 수 있다. git stash/ git stash save

- git의 Object, Commit, Head, Branch, Tag는 어떤 개념일까요? git 시스템은 프로젝트의 히스토리를 어떻게 저장할까요?

  > Object:모든 컨텐츠를 저장하는 데이터 베이스
  > Commit:변경이력 값을 기억하는 객체
  > Head:커밋을 가르키는 포인터
  > Branch:하나의 프로젝트를 여러 갈래로 나누어서 관리할 수 있게 하는 작업 트리, 각각의 독립된 Branch에서 마음대로 소스코드를 변겨하여 작업 한 후 원래 버전과 비교하여 merge 등을 통해 새로운 버전을 만들 수 있다.
  > Tag:커밋을 참조하기 쉽도록 알기 쉬운 태그를 달아두는 것으로 릴리즈할 때 보통 사용한다.
  > 저장법: object 데이터 베이스에는 각 객체들이 별도의 파일로 저장되는데 한 디렉터리 내에 너무 많은 파일들이 생성되지 않도록 객체 ID의 첫 두 글자를 이름으로 하는 하위 디렉터리를 한 단계 더 만들어서 저장한다
  > 즉 객체ID의 40글자 첫 두 글자는 디렉터리 이름, 나머지 38글자는 파일 이름으로 사용한다.

- 리모트 git 저장소에 원하지 않는 파일이 올라갔을 때 이를 되돌리려면 어떻게 해야 할까요?
  > git rm -r <파일명> 로컬, 원격 저장소 모두 삭제
  > git rm --cached -r <파일명> 원격 저장소만 삭제

## Quest

- GitHub에 가입한 뒤, [이 커리큘럼의 GitHub 저장소](https://github.com/KnowRe-Dev/WebDevCurriculum)의 우상단의 Fork 버튼을 눌러 자신의 저장소에 복사해 둡니다.
- Windows의 경우 같이 설치된 git shell을, MacOSX의 경우 터미널을 실행시켜 커맨드라인에 들어간 뒤, 명령어를 이용하여 복사한 저장소를 clone합니다.
  - 앞으로의 git 작업은 되도록 커맨드라인을 통해 하는 것을 권장합니다.
- 이 문서가 있는 폴더 바로 밑에 있는 sandbox 폴더에 파일을 추가한 후 커밋해 보기도 하고, 파일을 삭제해 보기도 하고, 수정해 보기도 하면서 각각의 단계에서 커밋했을 때 어떤 것들이 저장되는지를 확인합니다.
- `clone`/`add`/`commit`/`push`/`pull`/`branch`/`stash` 명령을 충분히 익혔다고 생각되면, 자신의 저장소에 이력을 push합니다.

## Advanced

- Mercurial은 어떤 형상관리 시스템일까요? 어떤 장점이 있을까요?
- 실리콘밸리의 테크 대기업들은 어떤 형상관리 시스템을 쓰고 있을까요?
