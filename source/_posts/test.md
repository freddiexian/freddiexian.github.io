---
title: 的静态方法和静态变量（类方法和类变量）
tags: test2
categories: test2
comments: false
---

{% centerquote %}blah blah blah{% endcenterquote %}

每次更改完 NexT 文档 都要手动部署到 GitHub Pages，重复的次数多了就显得很麻烦，出错的几率也会变大。文档源码放置在 master 分支，最终部署文件在 gh-pages 分支。当在 master 分支更改某些内容之后，通过运行 gulp dist 来生成最终部署的 HTML 文件到 dist 目录，随后再进入 dist 目录初始化 git 仓库、添加文件、提交文件，最后将提交强制推送到远程 gh-pages 分支（因当心我会误将最终部署的 HTML 文件提交到 master 分支导致源码丢失，我在 GitHub 上把 master 分支给锁定了）。除此之外还有另外一个问题：如果 master 分支有 Pull Requests，我需要先将更新取回本地，然后编译更新再提交回远程 gh-pages 分支。
<!-- more -->

年轻的想法

我就想这说将这个过程自动化。首先考虑了使用 GitHub Webhooks，这是 Github 提供的一种机制，使应用能与 Github 通讯。这种机制实际上就是 Pub/Sub，当 Github 监测到资源（如仓库）有变化就往预先设定的 URL 发送一个 POST 请求（Pub），告知变化情况，而后接收变化的服务器（Sub）即可做一些额外的事情。

这个思路需要有一个服务器并启动一个服务来接收 Github 的请求。这里又有种不同的策略，这两种策略都是基于源码放置在 Github 的前提。第一个是源码将最终文档直接部署在这台服务器上（如使用 Nginx），当接收到 Github 通知直接编译更新到服务器指定的文件夹下即可。另一种策略是当服务器接收到通知后编译更新，而后将编译后的版本提交到 Github 仓库的 gh-pages 分支，让 Github 做 Host。

```javascript
	describe('type: name', function() {
		var $scope, myService, $location;
		// 在每个测试用例执行之前，引用 app 模块
		beforeEach(module('app'));
  		// 在每个测试用例执行之前，注入依赖
  		beforeEach(inject(function($rootScope, _myService_, _$location_) {
    			$scope = $rootScope.$new();
    			myService = _myService_;
    			$location = _$location_;
  		}));
  		it('should work', function() {
    			// Do something
    			// Expect something
  		});
	});
```

{% note danger %} 
Content (md partial supported) 
Content (md partial supported) 
{% endnote %}

