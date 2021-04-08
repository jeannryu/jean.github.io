---
layout: post
title:  "Permission to \"myrepo\" denied to \"userid\" + CVE-2021-28834" 
ref:  20210408a
date:   2021-04-08 12:00:00 +0800
categories: githubpage multilingual
tags: githubpage
lang: ko
---

짧은 깃헙 팁.

# 시스템에서 깃헙 유저 깔끔하게 변경

깃헙 아이디를 여러 개 쓸 때 어떤 아이디로 커밋/푸시를 하는지는

```
git config --global user.name username1
git config --global user.email your@email.com
```

--로 업데이트 하면 된다.

잘 바뀌었는지는 아래 커맨드로 확인하면 됨.

```
git config --list
```


문제: `username2` 에서 `username1` 로 계정을 제대로 바꾸고 확인도 했는데 자꾸 이 에러가 나와요. 왜 나의 로컬 환경은 자꾸 `username2`를 시도하나요?

{% highlight bash %}
remote: Permission to myrepo.git denied to username2.
{% endhighlight %}

솔루션: [`username2`로 로컬에 저장된 키체인을 지워준다.](https://superuser.com/questions/1064197/how-to-switch-git-user-at-terminal)

끝!

하는 김에 

# Kramdown 업데이트하기 (CVE-2021-28834)

Kramdown 버전을 `2.3.1` 로 올리라는 알림이 귀찮을 경우... 아래 순서대로 업데이트한다.

Github Page에 Gem이고 Kramdown이 없는 경우 [이 페이지의 `Install Bundler`부터 확인하면서 Gemfile을 만들어 준다.](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_publishing_github_pages.html) (Mac OS용 설명만 나와 있음.)

깃헙 페이지 디렉토리에서 `bundle init`하면 Gemfile이 생기는데, 여기서 Gemfile 안에

```
gem "kramdown", ">=2.3.1"
```

를 추가해준 후 `bundle install` 하면 `gemfile.lock` 안에 Kramdown 버전이 명시되어 만들어지고, 터미널에서도 잘 됐다고 알려줌.

{% highlight bash %}
Installing rexml 3.2.5
Using kramdown 2.3.1
Bundle complete! 1 Gemfile dependency, 3 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
{% endhighlight %}

다음은 만들어진 Gemfile과 Gemfile.lock을 스테이징하고, 커밋하고, 푸시하고 머지하면 CVE 해결.

Gem 설치 과정에서 

```
     You don't have write permissions for the /usr/bin directory.
```

퍼미션 문제가 있을 경우 이 커맨드 [`sudo gem install cocoapods -n /usr/local/bin`](https://stackoverflow.com/questions/2893889/how-do-i-fix-the-you-dont-have-write-permissions-into-the-usr-bin-directory) 를 대신 사용해도 된다.
