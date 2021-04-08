---
layout: post
title:  "Permission to \"myrepo\" denied to \"userid\"" 
ref:  20210408a
date:   2021-04-08 12:00:00 +0800
categories: githubpage multilingual
tags: githubpage
lang: ko
---

짧은 깃헙 팁.

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