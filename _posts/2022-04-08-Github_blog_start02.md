---
layout: post
title: "[Github blog] 깃허브 블로그 만들기(Jekyll)" 
tags: [GitHub, Gitpage, Jekyll, Programming, Ruby]
categories: [Git]
banner:
  image: /assets/images/banners/jekyll.png
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---


## macOS 용 Jekyll 블로그 생성 방법
***

<h3>1. Home brew 설치</h3>

macOS 패키지 관리자 Homebrew를 설치한다.

homebrew url : https://brew.sh/index_ko


<h3>2. Ruby 설치하기</h3>

~~~
brew install rbenv
~~~
Ruby build를 설치한다.


~~~
rbenv init
~~~
설치 상태 검사

~~~
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
~~~
이후 터미널을 재시작 후 

rbenv 로 ruby 최신버전을 설치 (등록일 기준 3.1.1 이 최신버전)

터미널에서 차례로 

~~~
rbenv install 3.1.1

rbenv global 3.1.1
~~~

실행한다.



~~~
ruby -v
~~~
루비 버전 확인한다. 루비 버전이 최신이면 완료 

<h3>3. Jekyll 설치</h3>


jekyll 을 설치한다.
~~~
gem install --user-install bunder jekyll
~~~
쉘 환경을 추가한다. x.x 에는 설치된 루비의 버전 앞 2자리를 넣는다.
루비 버전은 ruby -v 실행하면 알 수 있다.

~~~
" echo 'export PATH="HOME/.gem/ruby/X.X.0/bin:PATH"' >> ~/.bash_profile "
~~~

루비 경로가 홈 디렉토리를 가르키고 있는지 확인한다

~~~
ruby env
~~~
홈 디렉토리를 가르키고 있다면 완료.


<h3>4. Jekyll 테마 사용</h3>
jekyll theme 에서 원하는 테마를 다운로드 하여 git 경로로 지정할 디렉토리에 넣는다.

지킬 테마 url: http://jekyllthemes.org/

jekyll theme 폴더 경로로 들어가

~~~
bundle init
~~~

Gemfile 을 생성해준다.

~~~
gem install webrick
~~~

서버가 실행 될 수 있게 해준다.

~~~
bundle exec jekyll serve 
~~~
실행 - localhost:4000 에서 선택한 테마가 잘 작동하는지 확인한다.


<h3>5. Git 준비</h3>

깃 허브에 새 레파지토리를 만들어준다

바로 블로그 페이지로 이동하게 하기 위해 레파지토리 명을

~~~
(git아이디).github.io 
~~~
지정해둔다

공개하고 싶으면 public 비공개시 private 설정

생성시 새 레파지토리의 주소 url 이 생성된다.

<h3>6. git 과 연결하기</h3>
jekyll theme 폴더 안의 _config.yml 파일에 destination: ../폴더이름/ 를 지정해줌 << git 과 연결해줄 폴더
jekyll theme 의 부모 폴더 안 내가 지정해준 폴더 생성 확인 폴더 경로로 이동

~~~
git init  
~~~
.git 폴더가 생성 연동준비 완료

~~~
git remote add (이름) (git 레파지토리 주소)  
~~~
이름은 마음대로 해도 되나 보통은 origin을 사용

~~~
git remote -v 
~~~
리모트 이름과 경로 확인

~~~
git add <파일이름/경로> 
~~~
원하는 파일을 추가 가능

git add . 
실행하여 모든 파일을 추가할수도 있다 git status 로 add 상태 확인이 가능하다.

~~~
git commit  이렇게 하면 안된다. 

git commit -m "commit" 커밋에 내용을 넣고 엔터를 친다.
~~~
add한 파일들이 모두 commit 된다

~~~

~~~
커밋 올리겠다는 내용에 커밋을 넣어 커밋한다. 

~~~
git push (remote이름) 

ㄴ  git push origin 이걸 넣고 
~~~
commit된 파일들이 모두 github에 저장된다.









<img src="/assets/images/img/GithubBlog_Repository.PNG">
레포지토리의 이름을 자신의 깃허브 계정 이름인 github.io로 하여 생성해준다.
<br>
ex) yunsungjoong.github.io

<br>

~~~
$ gem install bundler
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.3.0 directory.
~~~


