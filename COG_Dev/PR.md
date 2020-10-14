## pull request
내가 작업한 코드가 있으니 내 브랜치를 당겨 검토 후 병합해주세요

---

## 왜 필요한가?

- 자연스러운 코드 리뷰를 위해서.
- push 권한이 없는 오픈 프로젝트에 기여할 때.
- Push로 협업했을때, 다른 사람의 commit을 볼 일이 많지 않기 때문에 master branch와 merge할 때서야 타인의 commit을 보게 되는 경우가 많다.
- Pull Request의 당장 merge하지 않는다는 규칙덕분에 Pull Request를 확인한 뒤, 타인의 코드를 살펴본 후 그 작업이 언제 적용되었는지 알 수 있다. 때문에 당황스러운 코드충돌을 줄일 수 있다.

---

## 작업 순서는?

1. Fork
2. clone, remote설정
3. branch 생성
4. 수정 작업 후 add, commit, push
5. Pull Request 생성
6. 코드리뷰, Merge Pull Reqest
7. Merge 이후 branch 삭제 및 동기화

---

### 1. fork

타겟 프로젝트의 저장소를 자신의 저장소로 fork 한다.

### 2. clone, remote 설정

fork로 생성한 Repository에서 clone or download 버튼을 누르고 표시되는 URL을 복사한다.

- 내 컴퓨터에 생성된 로컬저장소에 원격저장소를 추가한다.
- Github에서 새로운 Repository를 생성
- 위와 같은 방법으로  clone or download 버튼을 누르고 표시되는 URL을 복사한다.
- Clone했던 원본프로젝트저장소(origin)를 원격저장소(github)로 추가

```
$ git clone (복사한 URL)
```

### 3. branch 생성

내 컴퓨터의 Clone프로젝트 저장소(origin)에서 코드를 수정하거나 추가하는 작업은 branch를 만들어서 진행한다.

> 개발을 하다 보면 코드를 여러 개로 복사해야 하는 일이 자주 생긴다. 코드를 통째로 복사하고 나서 원래 코드와는 상관없이 독립적으로 개발을 진행할 수 있는데, 이렇게 독립적으로 개발하는 것이 브랜치다. - pro git book

- develop branch 생성

```
$ git checkout -b develop
```

- 생성된 2개의 branch를 확인할 수 있다.

```
$ git branch
* develop
  master
```

### 4. 수정 작업 후 add, commit, push

- editor를 통하여 코드를 수정한다.
- 작업이 완료되면 Github Repository(origin)에 add, commit, push한다.
- push할때 develop 브랜치의 수정내역을 origin으로 푸시한다.
- push 진행 중에 brunch의 이름을 명시해준다.

```
$ git push origin develop
```

### 5. Pull Request 생성

- push 완료후 자신의 github 저장소에서 compare & pull request 버튼이 활성화 되어있는걸 확인할 수 있다.
- 버튼을 선택해 Pull Request를 생성한다.

### 6. Merge Pull Request

- PR을 받은 관리자는 코드 변경내역을 환인하고 Merge여부를 결정하게 된다.

### 7. Merge 이후 동기화 및 branch 삭제

- Merge가 완료되면 로컬 코드와 원본의 코드를 병합하고 최신의 상태를 유지하게 위해 동기화한다.

```
$ git pull post (remote 별명)
```

```
$ git branch -d develop
```

- 위 명령어를 통해 동기화하고, 브랜치를 삭제한다.
