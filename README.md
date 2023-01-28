## Commit message Convention
### Message Type List
![image](https://user-images.githubusercontent.com/96467030/198984702-a7dfecfa-f123-4cde-aaeb-97a74f0ecfec.png)
- 코드를 수정한 경우 Modify Type 사용
- Github issue 번호에 따라 다음과 같은 규칙으로 작성한다.
- issue number 26 → [Type]: [#[issue number]] [commit message] [message body]
- Type은 현재 시제로 작성하도록 하며, 대문자로 작성하지 않는다.
- Message는 무엇을 했으며 왜 했는지 적어준다.
![image](https://user-images.githubusercontent.com/96467030/200120111-6b186c72-c2af-4769-a669-efc1335b4938.png)
- **기능 구현 단위로 commit** 하도록 하고, 기능 구현이 완료되면 반드시 PR 및 코드 리뷰를 받도록 한다
- [AngluarJS commit convention (번역본)](https://velog.io/@outstandingboy/Git-커밋-메시지-규약-정리-the-AngularJS-commit-conventions#커밋-메시지-헤더-commit-message-header)

## Code Convention
### Frontend
- [클린코드 자바스크립트](https://github.com/ryanmcdermott/clean-code-javascript)
- [클린코드 타입스크립트](https://github.com/738/clean-code-typescript)
### Backend
- [캠퍼스 핵데이 Java 코딩 컨벤션](https://naver.github.io/hackday-conventions-java/)
- [좋은 코드를 위한 자바 변수명 네이밍](https://tecoble.techcourse.co.kr/post/2020-04-24-variable_naming/)
- [좋은 코드를 위한 자바 메소드 네이밍](https://tecoble.techcourse.co.kr/post/2020-04-26-Method-Naming/)
- [좋은 테스트 코드 작성(Mockito)](https://github.com/mockito/mockito/wiki/How-to-write-good-tests)
### DB
- [MySQL 네이밍 규칙](https://killu.tistory.com/52)

## Github Issue Convention
- 각 스프린트에 맞게 이슈를 발급한다 (**이슈 템플릿 사용하기!**)
- 완료, 진행중, 오류 3개의 라벨을 달아 현재 스프린트의 상태를 표시한다.
- 완료된 이슈는 PR 확인 후 Close 한다.
![image](https://user-images.githubusercontent.com/96467030/198984745-f80becbd-07f4-483c-b810-bb9b41c7364c.png)
## Github Branch Convention - Git flow 사용방법
- Mac OS 사용자의 경우 git flow 설치
    
    ```bash
    brew install git-flow-avh
    ```
    
- Windows OS 사용자의 경우 다음과 같이 설치
    
    ```bash
    wget -q -O - --no-check-certificate
    https://raw.github.com/petervanderdoes/gitflow-avh/develop/contrib/gitflow-installer.sh 
    install stable | bash
    ```
    
- git flow에 맞게 저장소 초기화
    
    ```bash
    git flow init
    
    Which branch should be used for bringing forth production releases?
       - main
    Branch name for production releases: [main] 
    Branch name for "next release" development: [develop] 
    
    # 별도의 설정 없이 엔터를 누른다.
    How to name your supporting branch prefixes?
    Feature branches? [feature/] 
    Bugfix branches? [bugfix/] 
    Release branches? [release/] 
    Hotfix branches? [hotfix/] 
    Support branches? [support/] 
    Version tag prefix? []
    Hooks and filters directory? [/Users/hee/Desktop/git-flow/.git/hooks]
    ```
    
- 다음과 같이 6개의 브랜치 prefix 가 생성된다. (향후 개발 시 브랜치명 앞에 다음과 같은 prefix를 붙여준다.)
    - main (master) : 사용자에게 배포되는 Stable 브랜치
    - develop : 다음 릴리즈를 위해 기능들을 모으는 최신 브랜치
    - feature : 특정 기능 개발을 위한 브랜치
    - release : 릴리즈를 위해 버그 픽스 (Bug fix)를 모으는 브랜치
    - hotfix : 긴급 버그 픽스를 위한 브랜치
    - support : 버전 호환성 문제를 위한 브랜치
- 새로운 개발 브랜치 feature 브랜치 생성 예시
    
    ```bash
    git flow feature start {branchName}
    ```
    
    - 해당 명령어를 입력하면 feature/branchName의 브랜치가 생성된다.
- PR 기능을 사용하려면 우선 리모트 저장소에 push 가 되어있어야 한다.
    
    ```
    git flow feature publish <feature name>
    ```
    
    - publish 명령을 수행하면 원격저장소에 feature브랜치를 push 한다.
- 반대로 원격 저장소에서 feature 브랜치를 가져오려면 다음 명령어를 사용한다.
    
    ```
    git flow feature pull origin <feature name>
    ```
- 해당 브랜치에 commit 하기
    
    ```bash
    git add .
    git commit -m "commit message"
    git flow feature publish {branchName}
    ```
    
- 모든 기능 구현 후 PR 후 Merge 시 해당 브랜치를 삭제한다.

#### 참고 자료
[우아한 형제들 기술블로그 - 우린 Git-flow를 사용하고 있어요](https://techblog.woowahan.com/2553/)  
[Git-Flow & Commit message & Issue 이용해서 협업하기](https://velog.io/@u-nij/Git-Flow-Commit-message-Issue-%EC%9D%B4%EC%9A%A9%ED%95%B4%EC%84%9C-%ED%98%91%EC%97%85%ED%95%98%EA%B8%B0)

## PR 및 Branch 생성 시 주의 사항

```
1. 머지 시 메인 브랜치와 충돌 날 우려가 있기 때문에 PR전 반드시 체크해주세요!
2. PR을 보낼 때는 수정 사항 및 구현 사항, 이에 대한 결과를 이미지와 함께 올려주세요.
3. 코드 리뷰 확인 후 머지 승인 시 머지 후 이슈를 닫아주세요.
4. 이슈번호와 브랜치번호를 일치시켜주세요.
5. 커밋 컨벤션을 지키고, 브랜치 번호를 일치시켜주세요. 브랜치 번호에 따라 이슈에
   커밋 메시지가 기록됩니다. 잘못된 번호가 기록되지 않게 주의하세요.
6. 만약 문제가 있다는 코멘트를 받으면, PR을 닫고 수정 후 다시 PR 날려주세요.
```
<img width="913" alt="스크린샷 2022-11-05 오후 11 30 40" src="https://user-images.githubusercontent.com/96467030/200124862-2f7f7393-1dde-4a33-907e-8a8b76d7cc15.png">
