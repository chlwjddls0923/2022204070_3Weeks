# Week 5 Assignment - Answers

### Q1.

`README.md`를 수정하기 전과 수정한 후 `git status`의 결과가 어떻게 달라졌는지 설명하세요.

**답변**

수정 전에는 Clone한 직후라 Local과 Remote의 내용이 같았기 때문에 `nothing to commit, working tree clean`으로 변경사항이 없다고 나왔습니다.

`README.md`를 수정하고 저장한 뒤에는 Git이 파일 변경을 감지해서 `README.md`가 `modified` 상태로 표시되었습니다. 아직 `git add`를 하지 않았기 때문에 Staging Area에 올라가지 않은 변경사항(`Changes not staged for commit`)으로 분류됩니다.

---

### Q2.

다음 세 명령어가 각각 어떤 역할을 수행하는지 간단히 설명하세요.

```
git add
git commit
git push
```

**답변**

| 명령어 | 역할 |
| --- | --- |
| `git add` | 작업 폴더에서 수정한 파일을 Staging Area에 올립니다. 다음 Commit에 어떤 변경사항을 포함할지 고르는 단계입니다. |
| `git commit` | Staging Area에 있는 변경사항을 하나의 버전(Commit)으로 Local Repository에 기록합니다. 메시지와 작성자, 시간 정보가 함께 저장됩니다. |
| `git push` | Local Repository에 쌓인 Commit을 GitHub 같은 Remote Repository로 전송합니다. Push를 해야 다른 사람도 변경사항을 볼 수 있습니다. |

---

### Q3.

`main` Branch에서 바로 파일을 수정하지 않고 별도의 Branch를 만들어 작업하는 이유는 무엇이라고 생각하나요?

1~3문장으로 작성하세요.

**답변**

`main`은 항상 정상적으로 동작하는 기준 버전이어야 하기 때문에, 작업 중인 코드나 검토되지 않은 변경이 바로 들어가면 안 됩니다. 별도 Branch에서 작업하면 `main`에 영향을 주지 않고 자유롭게 수정할 수 있고, 문제가 생겨도 해당 Branch만 버리면 됩니다. 또한 Pull Request를 통해 다른 사람의 Review를 거친 뒤에 `main`에 합칠 수 있어서 협업할 때 안전합니다.

---

### Q4.

Fork를 수행하면 원본 Repository가 자신의 계정으로 완전히 이동하는 것인지, 아니면 어떤 구조가 만들어지는 것인지 설명하세요.

**답변**

이동하지 않습니다. 원본 Repository(`leeyunhobbang/2022204025_3Weeks`)는 파트너 계정에 그대로 남아 있고, 내 계정에 복사본(`chlwjddls0923/2022204025_3Weeks`)이 새로 만들어집니다. 복사본 페이지에는 `forked from leeyunhobbang/2022204025_3Weeks`라고 표시되어 원본과 연결 관계가 유지됩니다.

---

### Collaborator와 Fork 비교

모든 GitHub 실습을 완료한 후 다음 표를 Notebook 또는 README에 작성하여 완성하세요.

| 항목 | Collaborator | Fork |
| --- | --- | --- |
| Repository 접근 방식 | 저장소 주인이 초대하면 원본 Repository에 쓰기 권한을 받아 직접 Clone해서 작업 | 원본을 내 계정으로 복사한 Fork Repository를 Clone해서 작업 |
| 상대방 Repository에 직접 Branch 생성 가능 여부 | 가능 (원본에 바로 Branch를 만들고 Push할 수 있음) | 불가능 (Branch는 내 Fork Repository에만 만들 수 있음) |
| 자신의 계정에 Repository 복사본 생성 여부 | 생성되지 않음 | 생성됨 (`forked from ...`으로 원본과 연결) |
| Pull Request 사용 여부 | 권한상 직접 Merge도 가능하지만, Review를 위해 Branch → `main` PR을 사용하는 것이 일반적 | 반드시 필요 (Fork의 Branch → 원본의 `main`으로 PR을 보내야만 반영됨) |
| 어떤 상황에서 적합한지 | 서로 신뢰하는 소규모 팀, 같은 팀원끼리 지속적으로 함께 개발하는 프로젝트 | 권한이 없는 외부 Repository, 오픈소스 프로젝트에 기여하는 경우 |

---

### Q5.

Collaborator 방식과 Fork 방식의 가장 큰 차이는 무엇인가요?

2~3문장으로 작성하세요.

**답변**

가장 큰 차이는 원본 Repository에 대한 쓰기 권한이 있는지입니다. Collaborator는 권한을 받았기 때문에 원본에 직접 Branch를 만들고 Push할 수 있지만, Fork는 권한 없이 내 계정의 복사본에서 작업한 뒤 Pull Request로만 원본에 변경을 요청할 수 있습니다. 그래서 Fork 방식에서는 원본 소유자가 PR을 Merge하기 전까지 원본이 전혀 바뀌지 않습니다.

---

### Q6.

같은 팀에서 지속적으로 프로젝트를 개발하는 경우 Collaborator와 Fork 중 어떤 방식이 더 편리할 것이라고 생각하나요?

이유와 함께 작성하세요.

**답변**

Collaborator 방식이 더 편리하다고 생각합니다. 팀원 모두가 하나의 원본 Repository에서 Branch를 만들고 Push하기 때문에 Fork Repository를 따로 관리하거나 원본의 최신 내용을 Fork에 계속 동기화할 필요가 없습니다. 이번 실습에서도 Fork 방식은 원본이 바뀌면 Fork를 다시 맞춰야 해서 충돌이 생겼는데, Collaborator 방식은 `git pull`만 하면 최신 상태를 바로 받을 수 있었습니다. 대신 모두가 쓰기 권한을 가지므로 `main`에 직접 Push하지 않도록 Branch와 PR 규칙을 정해 두는 것이 좋습니다.

---

### Q7.

자신이 소유하지 않은 공개 Open Source Repository에 기능을 추가하고 싶다면 Collaborator와 Fork 중 어떤 방식이 더 적절할 것이라고 생각하나요?

이유와 함께 작성하세요.

**답변**

Fork 방식이 적절합니다. 오픈소스 Repository는 불특정 다수가 기여하기 때문에 모든 사람에게 Collaborator 권한을 줄 수 없고, 관리자 입장에서도 모르는 사람에게 쓰기 권한을 주는 것은 위험합니다. Fork를 하면 권한 없이도 내 복사본에서 자유롭게 기능을 개발할 수 있고, 완성된 내용만 Pull Request로 제안하면 관리자가 Review 후 Merge 여부를 결정할 수 있어서 원본의 안전성이 유지됩니다.

---

### Q8.

Git의 Commit이 파일을 단순히 저장하는 것과 어떤 차이가 있다고 생각하는지 설명하세요.

**답변**

파일을 저장하면 마지막 상태만 남고 이전 내용은 덮어써지지만, Commit은 변경 시점마다 스냅샷을 하나의 버전으로 기록합니다. 각 Commit에는 누가, 언제, 무엇을, 왜 바꿨는지(작성자, 시간, 변경 내용, 메시지)가 함께 저장되고, 이전 Commit과 연결되어 있어서 `git log --oneline --graph --all`로 작업 흐름을 확인할 수 있습니다. 그래서 필요하면 특정 시점으로 되돌리거나 두 버전을 비교할 수 있고, Branch와 Merge를 통해 여러 사람의 작업을 합칠 수도 있습니다. 실습 중에 실수로 잘못된 Repository에 Push했을 때도, Commit 단위로 기록이 남아 있어서 그 Commit 하나만 정확히 제거할 수 있었습니다.

---

### Q9.

Pull Request에서 바로 Merge하지 않고 다른 사람이 변경사항을 Review하는 과정이 필요한 이유를 작성하세요.

**답변**

작성자 혼자서는 발견하지 못한 실수나 버그를 다른 사람이 확인해 줄 수 있기 때문입니다. Review 과정에서 변경된 파일과 내용, Commit을 보고 의도와 다른 수정이나 불필요한 변경이 없는지 검토하면 잘못된 코드가 `main`에 들어가는 것을 막을 수 있습니다. 또 팀원들이 서로의 변경사항을 알게 되어 프로젝트 전체 흐름을 공유할 수 있고, Approve 기록이 남아서 누가 검토하고 승인했는지 책임 소재도 명확해집니다.
