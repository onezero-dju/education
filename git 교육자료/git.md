# git 초기 설정

> 로컬에 github 계정 등록
```bash
git config --global user.name "(본인 이름)"
git config --global user.email "(본인 이메일)"
git config --global user.password "페스워드"
# 검증
git config --global user.name
git config --global user.email
```

> 브랜치 명 master -> main 으로 변경
```bash
git config --global init.defaultBranch main
```

# git 사용 방법

> .git 설정 및 초기화
```bash
git init
```

>원격과 로컬 연결
```bash 
git remote add origin {github url}
```

> 변경 사항 확인
```bash
git status
```

> 변경사항 스테이지에 올리기
```bash
git add (파일명) # 단일 파일만 올릴 경우
git add . # 현 디렉터리 아래에 파일들을 모두 올릴 경우
```

> commit 
```bash 
git commit -m "커밋 메시지" 
```

> 로컬에서 원격으로 올리기 
``` bash 
git push
```