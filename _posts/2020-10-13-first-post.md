---
title: "Jekyll GitHub Blog"
date: 2020-10-13 00:52:00 +0400
categories: jekyll configuration
---

Jekyll Blog 설정
--------------------------

### Git Repository 생성

1. GitHub에서 새 repository 만들기
- repository name: `<yourname>.github.io` 예)sangmile.github.io

2. `git init` 명령어

    ```bash
    git init sangmile.github.io
    cd sangmile.github.io
    ```

3. repo 추가 명령어

    ```bash
    git remote add origin https://github.com/sangmile/sangmile.github.io.git
    ```

4. `master` branch 생성

    ```bash
    git checkout -b master
    ```

### Jekyll Theme 설정

1. `_posts` 폴더 생성   

    `_posts` 폴더 아래에 새 글을 작성할 것임.   
    파일명은 다음 형식을 따라야 함.   
    `YEAR-MONTH-DAY-title.md`

    ```bash
    mkdir _posts
    ```

2. `_config.yml` 파일 생성
    
    ```bash
    touch _config.yml
    ```
    
    **a. 내용 입력**    
        원하는 theme의 `_config.yml` 내용을 복사 붙여넣기한다.  
        여기서는 minimal-misatakes-jekyll 테마를 사용.

    **b. 내용 수정**   
    
    ```yaml
    theme: "minimal-mistakes-jekyll"
    remote_theme: "mmistakes/minimal-mistakes"
    url: "https://sangmile.github.io"
    ```
        
3. `index.html` 파일 생성 후 아래 내용 입력:

    ```yaml
    ---
    layout: home
    author_profile: true
    ---    
    ```

4. 첫 글 만들고 포스트 하기:

    **a. 파일 생성**
    ```bash
    cd _posts
    touch 2020-10-13-first-post.md
    ```

    **b. 내용 입력**   
    > 각 파일마다 가장 위에 아래 포맷을 항상 입력해야 한다.

    ```m
    ---
    title: "Jekyll GitHub Blog"
    date: 2020-10-13 00:52:00 +0400
    categories: jekyll configuration
    ---    
    ```

### 로컬 테스트
사전조건
- ruby 설치
- bundler, jekyll 설치


1. ruby 설치:

    ```bash
    apt install ruby-full
    ```

2. bundler, jekyll 설치:

    Jekyll을 실행하기 위해 Bundler를 사용하는 것을 추천한다. Bundler는 Ruby gem 의존성을 관리함. 환경 관련 버그나 에러를 줄일 수 있음.

    ```
    apt install bundler jekyll
    ```

3. `Gemfile` 생성 후 다음 내용 입력:

    ```
    source "https://rubygems.org"
    gem "minimal-mistakes-jekyll"
    ```

4. `Bundler` 명령어 실행

    ```bash
    bundle
    ```

5. Local 테스트

    ```bash
    bundle exec jekyll serve
    ```

6. 로컬 접속
    > http://localhost:4000