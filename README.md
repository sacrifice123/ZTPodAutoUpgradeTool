# RMPodAutoUpgradeTool
pod私有库自动更新升级,开发人员修改私有模版库后不需要再去执行上传代码等任何操作，RMPodAutoUpgradeTool帮你一键上传私有库代码并更新索引库！
+------+--------------------+-------------+
|            fastlane summary             |
+------+--------------------+-------------+
| Step | Action             | Time (in s) |
+------+--------------------+-------------+
| 1    | cocoapods          | 2           |
| 2    | git_add            | 0           |
| 3    | git_commit         | 0           |
| 4    | push_to_git_remote | 3           |
| 5    | git_tag_exists     | 0           |
| 6    | remove_git_tag     | 0           |
| 7    | add_git_tag        | 0           |
| 8    | push_git_tags      | 0           |
| 9    | pod_lib_lint       | 5           |
| 10   | pod_push           | 7           |
+------+--------------------+-------------+
## 使用步骤

1.需要安装Fastlane（Fastlane是一个ruby脚本集合，它可以按照我们指定的路线，在指定位置执行我们所要执行的操作。详细安装请百度，但网上试了一些不严谨，强烈建议自己按照官方文档来操作）

2. 将fastlane拷贝到你的本地仓库的根目录
3. 打开Fastfile，找到pod_push并进行修改repo参数

repo：这个参数修改为你本地私有索引库文件的名称， 这个一般不会改变，所以可以写死不动
# 例如：
pod_push(path: "#{podspecName}.podspec", repo: "rm-ios-spec", allow_warnings: true, use_libraries: true)

4. 打开终端，cd到你的组件仓库的根目录下

# 注意几个参数
 message:git commit时写的日志，tag:版本号，specName:podspec文件名字

# 执行以下命令，例如：
fastlane RMPodAutoUpgradeTool message:pod私有库升级 tag:0.1.10 specName:RMLogin
