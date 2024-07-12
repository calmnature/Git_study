# Git 개인 공부
  <b>- 개인 노션 Git 정리 참조 : https://kdwstudy.notion.site/Git-f50c7667517741ddafcfef875bb28645</b>
## Notion을 이용하여 프로젝트를 개발했을 때 문제점
<b>1. 파일 업로드</b>
   - 유료 결제가 되어 있는 사람이 없을 경우 5MB이상의 파일을 업로드 할 수 없음
     - 코드 공유의 불편함
  
<b>2. 코드 통합의 번거로움</b>
  - 기존의 버전에서 새로운 기능의 개발 또는 오류 수정을 하였을 경우 어디를 수정한 것인지 모두 기록하거나 기억하고 있어야만 함
    - 달라진 부분을 일일히 하나하나 체크가 필요
  
<b>3. 버전 되돌리기</b>
  - 코드를 잘못 합치거나 잘못 손 댔을 경우 어떻게 되돌려야할 지 문제가 발생
      - 최악의 경우 이전 버전을 다운 받아서 다시 처음부터 코딩을 해야하는 경우 발생
  
<b>4. 이력(History)이 남지 않음</b>
  - 해당 버전에 어떠한 부분의 기능이 개발되었는지 또는 어느 오류가 해결되었는 지 별도로 텍스트 파일 또는 문서 파일로 기록을 해야함
<hr>

## Git을 사용해야 하는 가장 큰 이유
<b>1. 나의 Source Code 저장</b>
  - Github의 Remote Repository에 저장 가능
  - Notion을 사용했을 때 파일 업로드의 문제 해결

<b>2. 소스 코드의 공유</b>
  - 다른 사람들이 손 쉽게 코드를 다운 받을 수 있음

<b>3. 새로운 버전의 실험</b>
  - 기존에 구동 중인 것에 실험을 해서는 절대 안 됨
  - 새로운 Branch를 만들어 새로운 기능이나 오류들을 수정할 수가 있으며, 최악의 경우 이전 버전으로 돌아갈 수 있음

<b>4. 협업(팀플레이)</b>
  - 실무에서는 혼자 온전히 개발하는 경우는 극히 드물기 때문에 협업이 기본
  - Pull Request를 이용하여 개발한 코드를 Merge 하도록 요청하고, 잘못 되었을 경우 재 수정 요청 가능
  - commit을 하는 과정에서 해당 파일의 추가, 변경 부분(XX 기능 개발, XX 오류 수정) 등에 대한 메세지를 남길 수 있고 이력(History)가 남음
<hr>

## Git 명령어 정리
<table style="text-center border">
  <thead>
    <tr>
      <th>명령어</th>
      <th>설명</th>
      <th>비고</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>git config --global user.name "작업자 이름"</td>
      <td>작업자 이름 전역 설정</td>
      <td>History에 누가 작업했는지 확인 가능</td>
    </tr>
    <tr>
      <td>git config --global user.email "작업자 이메일"</td>
      <td>작업자 이메일 전역 설정</td>
      <td>History에 누가 작업했는지 확인 가능</td>
    </tr>
    <tr>
      <td>git config --list</td>
      <td>Git 설정 확인</td>
      <td>q 입력 시 빠져나옴</td>
    </tr>
    <tr>
      <td>git init</td>
      <td>Local Repository 생성</td>
      <td></td>
    </tr>
    <tr>
      <td>git status</td>
      <td>Git 상태 확인</td>
      <td></td>
    </tr>
    <tr>
      <td>git add 파일명</td>
      <td>파일 변화 관리</td>
      <td>git add . : 온점(.)은 모든 파일을 의미</td>
    </tr>
    <tr>
      <td>git commit (파일명) -m "메세지"</td>
      <td>Local Repository에 저장</td>
      <td>파일명은 생략 가능<br>메세지로 History를 남길 수 있음</td>
    </tr>
    <tr>
      <td>git rm 파일명</td>
      <td>Local REpository의 파일 삭제</td>
      <td>파일 탐색기에서 삭제할 경우 눈에 보이지 않을 뿐, Local Repository에는 남아있음</td>
    </tr>
    <tr>
      <td>git log</td>
      <td>Git 로그 확인</td>
      <td>해쉬코드, 작업자, 작업 날짜, 메세지 확인 가능</td>
    </tr>
    <tr>
      <td>git log --stat</td>
      <td>통계 정보 조회</td>
      <td>git log 정보에 더해 변화한 파일 개수, 추가, 삭제 등에 대한 더 자세한 정보 </td>
    </tr>
    <tr>
      <td>git log --pretty=oneline</td>
      <td>한 줄 간단 출력</td>
      <td>해쉬코드, commit 메세지 확인</td>
    </tr>
    <tr>
      <td>git log --pretty=format:"%h - %an, %ar : %s "</td>
      <td>날짜 정보 출력</td>
      <td>해쉬코드, 작업자 이름, 몇시간 전 수정, commit 메세지 확인</td>
    </tr>
    <tr>
      <td>git log --pretty=format:"%h - %an, %ar : %s " -- graph</td>
      <td>날짜 정보 그래프 출력</td>
      <td>위의 정보에 더해 Branch의 갈래까지 출력</td>
    </tr>
    <tr>
      <td>git checkout "코드 or Branch명"</td>
      <td>버전 되돌리기 or Branch 변경</td>
      <td>해쉬 코드를 입력하게 되면 해당 버전으로 변경<br>단, 권장하지 않는 방법</td>
    </tr>
    <tr>
      <td>git switch Branch명</td>
      <td>브랜치 이동</td>
      <td>git checkout은 복원 기능도 있어 혼란을 야기할 수 있어 브랜치 이동 전용 명령어 추가</td>
    </tr>
    <tr>
      <td>git branch Branch명</td>
      <td>Branch 생성</td>
      <td></td>
    </tr>
    <tr>
      <td>git checkout -b Branch명<br>git switch -c Branch명</td>
      <td>Branch 생성 + 변경</td>
      <td>-b : branch<br>-c : create</td>
    </tr>
    <tr>
      <td>git branch -d Branch명</td>
      <td>Branch 삭제</td>
      <td></td>
    </tr>
    <tr>
      <td>git branch</td>
      <td>Branch 리스트 조회</td>
      <td>Branch 리스트 조회 및 현재 Branch가 무엇인지 표시</td>
    </tr>
    <tr>
      <td>git merge Branch명</td>
      <td>현재 Branch와 해당 Branch 합치기</td>
      <td>MERGE_MSG 빠져나오는 방법 : ESC -> :wa -> Enter</td>
    </tr>
    <tr>
      <td>gitk</td>
      <td>Branch GUI(?)</td>
      <td></td>
    </tr>
    <tr>
      <td>git remote</td>
      <td>Remote 저장소 이름 확인</td>
      <td></td>
    </tr>
    <tr>
      <td>git remote -v</td>
      <td>Remote 저장소 이름 및 주소 확인</td>
      <td></td>
    </tr>
    <tr>
      <td>git remote add 별칭 주소</td>
      <td>Remote 저장소 추가</td>
      <td>해당 별칭으로 주소와 Mapping</td>
    </tr>
    <tr>
      <td>git remote rm 별칭</td>
      <td>해당 별칭의 remote 삭제</td>
      <td></td>
    </tr>
    <tr>
      <td>git push Remote명 Branch명<br>ex)git push origin master</td>
      <td>Local Repository -> Remote Repository Push</td>
      <td>Remote이름의 주소지에 Branch를 밀어넣음</td>
    </tr>
    <tr>
      <td>git push -u Remote명 Branch명</td>
      <td>축약 설정</td>
      <td>git push만 입력하여도 git push Remote명 Branch명이 되도록 설정</td>
    </tr>
    <tr>
      <td>git pull Remote명 Branch명</td>
      <td>Remote Repository -> Local Repository Pull</td>
      <td>해당 원격지의 Branch를 Local Repsotiroy로 가져옴<br>자동 병합(Merge)</td>
    </tr>
    <tr>
      <td>git pull Remote명 Branch명</td>
      <td>Remote Repository -> Local Repository Pull</td>
      <td>해당 원격지의 Branch를 Local Repsotiroy로 가져옴<br>자동 병합(Merge)</td>
    </tr>
    <tr>
      <td>git clone 원격지 주소</td>
      <td>Remote Repository -> Local Repository 복사</td>
      <td>해당 원격지의 모든 것을 Local Repsotiroy로 복사</td>
    </tr>
    <tr>
      <td>git reset --명령어 CommitID</td>
      <td>버전 되돌리기</td>
      <td>
        --hard : 코드&커밋 삭제<br>
        --soft : 코드 유지 & 커밋 삭제(git add 후 상태)<br>
        --mixed : 코드 유지 & 커밋 삭제(git add 전 상태)
      </td>
    </tr>
    <tr>
      <td>git revert CommitID</td>
      <td>버전 되돌리기</td>
      <td>git reset은 돌아가면 이력까지 삭제 되지만, revert는 해당 CommitID의 취소 이력(commit)이 새로 생성</td>
    </tr>
    <tr>
      <td>git stash -u -m "메세지"</td>
      <td>코드 임시 저장</td>
      <td>-u를 사용하지 않을경우 새로운 파일(commit되지 않은 파일)은 저장되지 않음</td>
    </tr>
    <tr>
      <td>git stash list</td>
      <td>임시 저장 내역 확인</td>
      <td></td>
    </tr>
    <tr>
      <td>git stash apply <stash@뒤 숫자></td>
      <td>임시 저장 로드</td>
      <td></td>
    </tr>
  </tbody>
</table>
