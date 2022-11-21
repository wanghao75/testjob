# openEuler社区单仓Pull Request合入方式指引
rebase merge: 变基合并，将所有的提交都合并到目标分支，且在目标仓库的目标分支的changelog中不包含pull request的title.<br>
rebase example:<br>
![rebase](https://github.com/wanghao75/testjob/blob/master/rebase.png)
![rebase-git](https://github.com/wanghao75/testjob/blob/master/rebase-git.png)
<br>
squash merge: 扁平化分支合并，将所有的提交合并为一个新的提交，并且合并到目标分支上.<br>
squash example: <br>
![squash](https://github.com/wanghao75/testjob/blob/master/squash.png)
![squash-git](https://github.com/wanghao75/testjob/blob/master/squash-git.png)
## 1.单一仓库文件增加merge_method字段配置方式
当前Gitee平台对PR的合入方式提供了三种：***merge***， ***rebase merge***， ***squash merge***，***merge***是默认的合入方式，可不用进行单独配置。

rebase example：
```yaml
name: A-Tune-BPF-Collection
description: A-Tune-BPF-Collection is BPF based tunning tools collection
branches:
- name: master
  type: protected
type: public
merge_method: rebase
```

squash example：
```yaml
name: A-Tune-BPF-Collection
description: A-Tune-BPF-Collection is BPF based tunning tools collection
branches:
- name: master
  type: protected
type: public
merge_method: squash
```

default example:
```yaml
name: A-Tune-BPF-Collection
description: A-Tune-BPF-Collection is BPF based tunning tools collection
branches:
- name: master
  type: protected
type: public
```

## 2.通过Pull Request评论的方式进行合入方式切换
命令使用方式说明：
<br>
en：https://gitee.com/openeuler/community/blob/master/en/sig-infrastructure/command.md
<br>
zh：https://gitee.com/openeuler/community/blob/master/zh/sig-infrastructure/command.md
### (1) 使用 "/rebase"命令
通过 ***/rebase*** 命令给Pull Request加上***merge/rebase***标签，标志着此合并请求将以变基合并的方式合入(rebase merge)，如果需要切换合并方式，
请使用 ***/rebase cancel*** 去掉***merge/rebase***标签。
### (2) 使用 "/squash"命令
通过 ***/squash*** 命令给Pull Request加上***merge/squash***标签，标志着此合并请求将以扁平化分支合并的方式合入(squash merge)，如果需要切换合并方式，
请使用 ***/squash cancel*** 去掉***merge/squash***标签。
### (3)两者均不使用
Pull Request将以默认的***merge***的方式进行合入。

## 3.更改合入方式生效的优先级
Pull Request评论方式 > 仓库文件中配置的merge_method字段
