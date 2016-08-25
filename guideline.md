# Git工作流
## Git常用工作流
1. 集中式工作流
2. 特性分支工作流
3. Gitflow工作流
4. Fork工作流

## Gitflow工作流
![](pic/gitflow.jpg)
图1: Gitflow工作流的整体流程图

###下面以_"张三"_和_"李四"_两个开发者的操作为例,来看一下Gitflow工作流的具体操作：

 1. 首先，_"张三"_克隆远程仓库
![](pic/clone_repository.jpg)
 2. _"张三"_本地创建一个**[develop]**分支
![](pic/branch_develop.jpg)
 3. _"张三"_将**[develop]**分支推送至远程仓库
![](pic/push_develop_init.jpg)
 4. _"李四"_将克隆远程仓库
![](pic/clone_repository2.jpg)
 5. _"张三"_开发功能1，从**[develop]**分支发起分支**[z_feature1]**
![](pic/z_feature1_init.jpg)
 6. _"李四"_开发功能2，从**[develop]**分支发起分支**[l_feature2]**
![](pic/l_feature2_init.jpg)
 7. _"张三"_在分支**[z_feature1]**开发完功能1后，将更新合并至分支**[develop]**
![](pic/z_feature1_merge.jpg)
 8. _"李四"_在分支**[l_feature2]**开发完功能2后，将更新合并至分支**[develop]**
![](pic/l_feature2_merge.jpg)
 9. _"张三"_将**[develop]**分支推送到远程仓库(可能发生冲突)
![](pic/z_feature1_push.jpg)
 10. _"李四"_将**[develop]**分支推送到远程仓库(可能发生冲突)
![](pic/l_feature2_push1.jpg)
![](pic/l_feature2_push2.jpg)
![](pic/l_feature2_push3.jpg)
 11. 至此，已可以发布新的版本了，_"张三"_从**[develop]**分支发起分支**[release-1]**并推送至远程仓库
![](pic/release1_init.jpg)
 12. _"李四"_接到开发功能3的任务，从**[develop]**分支发起分支**[l_feature3]**
![](pic/l_feature3_init.jpg)
 13. _"李四"_在分支**[l_feature3]**开发完功能3后，将更新合并至分支**[develop]**
![](pic/l_feature3_merge.jpg)
 14. _"李四"_将**[develop]**分支推送到远程仓库(可能发生冲突)
![](pic/l_feature3_push.jpg)
 15. 预发布版本在测试时发现了问题，_"张三"_负责进行修改
![](pic/release1_fix1.jpg)
 16. _"张三"_将修正后的更新提交到分支**[release-1]**
![](pic/release1_fix2.jpg)
 17. _"张三"_将分支**[release-1]**的更新推送到远程仓库(可能发生冲突)
![](pic/release1_fix3.jpg)
 18. 此时，线上环境发现了一个的问题，并交给_"李四"_进行紧急处理。_"李四"_从**[master]**分支发起分支**[hotfix-1]**
![](pic/hotfix1_init.jpg)
 19. _"李四"_紧急修改后，将更新提交至分支**[hotfix-1]**
![](pic/hotfix1_fix1.jpg)
 20. _"李四"_将分支**[hotfix-1]**合并至分支**[master]**
![](pic/hotfix1_fix2.jpg)
 21. _"李四"_将分支**[master]**当前的状态打上标签，并推送至远程仓库
 ![](pic/hotfix1_fix3.jpg)
 22. _"李四"_将分支**[hotfix-1]**合并至分支**[release-1]**，并推送至远程仓库(如此时还没有release分支，则合并至分支**[develop]**)
 ![](pic/hotfix1_fix4.jpg)
 ![](pic/hotfix1_fix5.jpg)
 23. _"李四"_将分支**[hotfix-1]**删除(可选)
 ![](pic/hotfix1_fix6.jpg)
 24. 至此，预发布版本**[release-1]**已完成测试，可以发布到生产环境，由_"张三"_负责。_"张三"_将分支**[release-1]**的所有更新合并至**[master]**并打上标签
![](pic/release1_merge.jpg)
 25. _"张三"_将分支**[master]**推送到远程仓库(可能发生冲突)
![](pic/release1_push.jpg)
 26. _"张三"_将分支**[release-1]**合并至分支**[develop]**，并推送至远程仓库
 ![](pic/release1_merge_develop1.jpg)
 ![](pic/release1_merge_develop2.jpg)
 26. _"张三"_将分支**[release-1]**删除(可选)
 ![](pic/release1_delete.jpg)


> 参考：
> 1. ![](http://nvie.com/posts/a-successful-git-branching-model/)