---
layout: post
title: "[Linux] Python 자동완성 기능"
subtitle: Vim 을 이용하여 자동완성 기능을 이용해보자.
catalog: true
tags: 
    - linux
    - setting
    - vim
    - python

---
### 리눅스에도 자동완성 기능을 이용할 수 있다.
윈도우 상에서 파이참을 이용하여 자동완성 기능에 물들어 있던 필자는 리눅스 환경에서 코딩작업을 해야할 상황이 생겼고, ~~어떻게 하면 꼼수를 부릴 수 있을까 .. 하다가~~
vim 을 이용하여 자동완성 기능을 이용할 수 있어서 세팅 방법을 적어보려 한다.

### 파이썬 하이라이트 설치
1. 파이썬 가독성을 위해 확장 스크립트를 설치한다.

```bash
cd ~/.vim/ # .vim 폴더 이동
git clone https://github.com/hdima/python-syntax.git #스크립트 설치
mv python-syntax/syntax syntax/ # 스크립트 파일 내부에 syntax 폴더 옮김
```

### 자동완성 기능 설치
1. 자동완성(pydiction) 설치

```bash
cd ~/.vim/ # .vim 폴더 이동
wget https://www.vim.org/scripts/download_script.php?src_id=21842 # pydiction ver 1.2.3
mv 'download_script.php?src_id=21842' pydiction.zip
unzip pydiction.zip
mv pydiction/after/ after/ #after 폴더를 .vim 폴더 아래 이동
```

### .vimrc 파일 수정
1. vim 환경을 적용하기 위해 .vimrc 파일을 수정한다.
```bash
# vim ~/.vimrc
syntax on
filetype plugin on
let python_version_3=1          # python ver3 사용
let python_highlight_all=1      # 색상 강조
set tabstop=8                   # 탭 길이
set expandtab
set softtabstop=4               # 탭 누를 때 벌어지는 간격
set autoindent                  # 자동 들여쓰기
set bg=dark                     # 배경 색
set nu                          # 라인 숫자 

let g:pydiction_location='/home/[user_id]/.vim/pydiction/complete-dict' # [user_id] 에 본인 linux 아이디 삽입
```

### 적용 결과
<img data-action="zoom" src='{{ "/img/post/auto_python.gif" | relative_url }}' alt='auto python'>
tab 버튼을 누르게 되면 자동완성이 실행된다.
