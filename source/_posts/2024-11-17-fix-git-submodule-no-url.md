---
title: fix git submodule no url
date: 2024-11-17 00:44:21
keywords: git, submodule
description: 'No url found for submodule path  in .gitmodules'
tags:
  - git
  - hexo
---

在使用hexo第三方主题，推送到gitub进行CI/CD的时候，报了下面这个错误

`No url found for submodule path 'themes/sky' in .gitmodules`

![/images/git-submodule-error](/images/git-submodule-error.png)

原因在于安装主题的时候只是按照常用的`git clone`方式，导致github获取不到git子仓库地址。

可参考netlify.com上面的回答， 解决办法

1. 删除theme文件夹

2. 将这次变更到git

3. 重新用git submodule的方式clone仓库

4. 更新submodule

5. 可以用 `git submodule status `来检查是否成功，`.gitmodules `是否创建了

![/images/git-submodule-error](/images/2024-11-17-git-submodule.png)

### 参考

[https://answers.netlify.com/t/error-checking-out-submodules-fatal-no-url-found-for-submodule-path-website-in-gitmodules/16435/7](https://answers.netlify.com/t/error-checking-out-submodules-fatal-no-url-found-for-submodule-path-website-in-gitmodules/16435/7)

