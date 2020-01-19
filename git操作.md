# 1. git使用

- 使用Git下载指定分支命令为：`git clone -b 分支名 仓库地址`
- 首次开发git操作流程
  - 本地创建公钥`ssh-keygen -t rsa -C "邮箱`并配置
  - 克隆项目`git clone`
  - 创建本地分支`git branch 分支名`
  - 查看本地分支`git branch`
  - 查看远程分支`git branch -a`
  - 切换分支`git checkout 分支名`
  - 将本地分支推送到远程分支`git push 远程仓库 本地分支:远程分支`

<img src="https://camo.githubusercontent.com/9ae53ba685e342dee7e0afb60468b8f83b6a99c0/687474703a2f2f7777772e7275616e796966656e672e636f6d2f626c6f67696d672f61737365742f323031352f6267323031353132303930312e706e67" alt="avatar" style="zoom:80%;" />

- 知识点
  1. **Remote:**远程主仓库；
  2. **Repository：**本地仓库；
  3. **Index：**Git追踪树,暂存区；
  4. **workspace：**本地工作区(即你编辑器的代码)

- 一般操作流程：
  -  `git status`查看工作区状态
  -  `git add .`将所有修改加入暂存区
  -  `git commit -m "提交描述"`将代码提交到本地仓库
  -  `git push`将本地仓库代码更新到远程仓库



# 2. git remote

- 主要为远程仓库制定别名，以便于管理远程主机，默认只有一个时为origin

1. 查看主机名：`git remote`

2. 查看主机名即网址：`git remote -v`

   - 默认克隆远程仓库到本地时，远程主机为origin，如需指定别名可使用

     `git clone -o <别名> <远程git地址>`

3. 查看主机的详细信息`git remote show <主机名>`

4. 添加远程主机`git remote add <主机名> <网址>`

5. 删除远程主机`git remote rm <主机名>`

6. 修改远程主机的别名：`git remote rename <原主机名> <新主机名>`



# 3. git fetch

- 将某个远程主机的更新，全部/分支 取回本地(此时更新了Repository)***它取回的代码对你本地的开发代码没有影响***，如需彻底更新需合并使用`git pull`

1. 远程主机的更新，全部取回本地`git fetch <远程主机名> 或 git fetch --all`
2. 将远程仓库特定分支更新到本地`git fetch <远程主机名> <分支名>`

3. 如果需要将更新拉取并合并到本地某一分支

   `git merge <被合并的远程分支> git merge origin/master` 

4. 在此基础上创建出新分支并切换

   `git checkout -b <分支名> <在此分支上创建> git checkout -b dev origin/dev`



# 4. git pull

- 拉取远程主机某分支的更新，再与本地的指定分支合并（相当与fetch加上了合并分支功能的操作）

1. 拉取远程某分支并与本地某一分支合并(没有则默认会创建):`git pull <远程主机名> <远程分支名>:<本地分支名>`
2. 如果远程分支是与当前所在分支合并，则冒号后面的部分可以省略:`git pull <远程主机名> <远程分支名>`
3. 如果当前分支与远程分支存在追踪关系,则可以省略远程分支名:`git pull <远程主机名>`
4. 如果当前分支只有一个追踪分支，则远程主机名都可以省略:`git pull`



# 5. git push

- 将本地分支的更新，推送到远程主机，其命令格式与`git pull`相似

1. 将本地分支推送到远程分支：`git push <远程主机名> <本地分支名>:<远程分支名> --- git push origin 14.0-18:dev`
2. 如果省略远程分支名，则默认为将本地分支推送到与之关联的远程分支：(一般本地分支与之关联的远程分支同名，防止混淆)`git push <远程主机名> <本地分支名>`
   - 如果对应的远程分支不存在，则会被创建
3. 如果省略本地分支名，则表示***删除***指定的远程分支，这等同于推送一个空的本地分支到对应远程分支：`git push origin :<远程分支>` 等同于 `git push origin --delete <远程分支>`
4. 如果当前分支与远程分支之间存在追踪关系，则本地分支和远程分支都可以省略`git push origin`
5. 如果当前分支只有一个追踪分支，那么主机名也可以省略：`git push`
6. 如果当前分支与多个主机存在追踪关系(使用场景相对较少)，可以使用-u指定默认推送主机`git push -u origin <主机名>`设置时候需推送便可以直接使用`git push`
7. 将本地的所有分支都推送到远程主机:`git push --all origin`
8. 如果远程主机的版本比本地版本更新，推送时Git会报错，要求先在本地做`git pull`合并差异，然后再推送到远程主机。如果一定要推送，可以使用`--force`选项强推(谨慎使用):`git push --force origin`

- **注意**:分支推送顺序的格式为**<来源地>:<目的地>**，所以`git pull`格式：**<远程分支>:<本地分支>**，`git push`格式为：**<本地分支>:<远程分支>**。



# 6. 分支操作

1. 创建本地分支：`git branch test`:(创建名为test的本地分支)
2. 切换分支：`git checkout test`:(切换到test分支)
3. 创建并切换分支`git branch -b test`:(相当于以上两条命令的合并)
4. 查看本地分支：`git branch`
5. 查看远程仓库所有分支：`git branch -a`
6. 删除本地分支：`git branch -d test`:(删除本地test分支)
7. 删除远程分支：`git branch -dr remote/test`:(删除远程test分支)
8. 分支合并：`git merge master`:(将master分支合并到当前分支)

- **分支关联：**

1. 查看当前的本地分支与远程分支的关联关系:`git branch -vv`
2. 把当前本地分支与远程某分支进行关联处理(通过 --set-upstream-to 命令):`git branch --set-upstream-to=origin/master

- **分支差异查看**

1. 查看本地当前分支与远程某一分支的差异：`git diff origin/master`
2. 查看本地特定分支与远程分支的差异：`git diff master origin/master `



# 7. 撤销

1. `git checkout -- <文件名>`：丢弃工作区的修改，就是让这个文件回到最近一次`git commit`或`git add`时的状态
2. `git reset HEAD <文件名>`：把暂存区的修改撤销掉，重新放回工作区。
3. `git reset --hard commit_id`：git版本回退，回退到特定的commit_id版本
   - `git log`查看提交历史，以便确定要回退到哪个版本(commit的ID)

4. `git reflog`查看命令历史，以便确定要回到未来的哪个版本



# 8. 配置

- `git config -l `// 陈列出所有的git配置项
- `git config core.ignorecase false` //配置git不忽略大小写（默认忽略）参照（git 大小写）



# 9. 参考资料

- [git操作游戏] https://learngitbranching.js.org/ 
- [Git 详细教程] https://juejin.im/entry/59b22efb6fb9a024a04b3726#_label3_2_3_4
- [团队合作必备的Git操作] https://juejin.im/entry/5b4fda04f265da0fac1e0e53
- [Git 常用操作总结] https://juejin.im/post/5a2cdfe26fb9a0452936b07f
- https://juejin.im/post/5b5596eae51d4519520e7951









# N.杂项

- git commit：提交本地仓库
- git branch：查看本地分支
- git merge ：合并其他分支到本分支
- git rebase ：合并本分支到其他分支
- git checkout：切换HEAD到xxx
- git checkout master^：切换到master上一个提交
- git checkout HEAD~3：切换到HEAD上第三个提交
- git branch -f master C3：强行指定master分支到c3提交
- git reset HEAD~1：HEAD向上调整并将影响的提交存入缓冲区
- git revert HEAD：撤销某次操作并向上回滚
- git cherry-pick C2 C4：在HEAD后追加c2、c4提交
- git rebase -i HEAD~4：调整HEAD前4个提交并追加到新的分支
- git tag v1 C1：给c1标注v1
- git checkout HEAD~^2~2：切换HEAD往第二个父分支向上调整两个
- git reset --hard commit_id：回退到指定的提交记录