# openEuler社区单仓Pull Request合入方式指引
## 1.单一仓库文件增加merge_method字段配置方式
当前Gitee平台对PR的合入方式提供了三种：***merge***， ***rebase merge***， ***flattened merge***，***merge***是默认的合入方式，可不用进行单独配置。

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

flattened example：
```yaml
name: A-Tune-BPF-Collection
description: A-Tune-BPF-Collection is BPF based tunning tools collection
branches:
- name: master
  type: protected
type: public
merge_method: flattened
```

## 2.通过Pull Request评论的方式进行合入方式切换
### (1) 使用 "/rebase"命令
通过***/rebase*** 命令给Pull Request加上***merge/rebase***标签，标志着此合并请求将以变基合并的方式合入(rebase merge)，如果需要切换合并方式，
请使用***/rebase cancel*** 去掉***merge/rebase***标签。
### (2) 使用 "/flattened"命令
通过***/flattened*** 命令给Pull Request加上***merge/flattened***标签，标志着此合并请求将以变基合并的方式合入(flattened merge)，如果需要切换合并方式，
请使用***/flattened cancel*** 去掉***merge/flattened***标签。
### (3)两者均不使用
Pull Request将以默认的***merge***的方式进行合入。

## 3.更改合入方式生效的优先级
Pull Request评论方式 > 仓库文件中配置的merge_method字段
