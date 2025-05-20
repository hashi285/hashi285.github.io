---
title: "잔디심기 오류"
excerpt: "잔디가 채워지지 않아요 ㅠㅠ"

categories:
  - github
tags:
  - [tag1, tag2]

permalink: /github/잔디 오류류

toc: true
toc_sticky: true

date: 2025-05-20
last_modified_at: 2025-05-20
---
## 잔디가 안 심어진다?

블로그 작업을 열심히 하고 커밋도 했는데, 잔디(Contributions)가 전혀 심어지지 않는다.  
이상하게 다른 일반 레포지토리에서는 커밋할 때마다 잔디가 잘 심어지는데, 내가 포크(fork)해서 사용 중인 블로그 레포지토리만 잔디가 비어 있다.

무엇이 문제일까? 일단 GitHub 공식 문서를 찾아봤다.  
그리고 알게 된 사실은:

> 포크한 레포지토리에서는 잔디가 기본적으로 심어지지 않는다.

씨발발...? 실망하고 며칠 동안 포기 상태로 있다가 우연히 한 블로그를 발견했다.

[깃허브 잔디 누락 현상 해결하기](https://kdjun97.github.io/git-github/plant-grass/)

링크를 따라가 보니, 나와 비슷한 상황에서 문제를 해결한 경험이 자세히 적혀 있었다.  
바로 따라해보자 

아래에 있는 방법들만 그대로 따라한다면 문제없이 잔디가 심어질 것이다.

---

## ✅ 선행 조건

먼저 기존에 사용하던 리포지토리의 이름을 바꾸고, 새로 리포지토리를 만든다.

- 기존에 사용하던 GitHub 블로그 레포: `hashi285.github.io` -> `hashi.github.io`
- 새로 만든 GitHub Pages 레포: `hashi285.github.io`

---

## 📌 전체 순서 요약

### 1. 기존 레포 이름 변경
GitHub 웹사이트에서 기존 블로그 레포(`hashi285.github.io`)의 이름을 변경 (예: `hashi.github.io`).

### 2. 새 레포 생성
`hashi285.github.io` 이름으로 새 레포지토리를 생성함.

### 3. 로컬에서 bare clone (기존 레포 전체 mirror용)
```
mkdir C:\Users\m5118\temp_repo
cd C:\Users\m5118\temp_repo
git clone --bare https://github.com/hashi285/_hashi.github.io.git
```
4. 새 레포로 mirror push
```
cd .\_hashi.github.io.git
git push --mirror https://github.com/hashi285/hashi285.github.io.git
```
⚠️ --mirror는 전체 히스토리(커밋, 브랜치, 태그)를 그대로 복사함.

5. 새 레포 clone 후 작업
```
cd ..
git clone https://github.com/hashi285/hashi285.github.io.git
cd .\hashi285.github.io
```
이후부터는 이 폴더에서 블로그 작업을 진행하면 된다.