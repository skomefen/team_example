#  git习题
###  git概念

1. 请用自己的话说明什么是版本控制系统（__讲就行了，不用打出来__）
2. 请用自己的话说明什么是git（__讲就行了，不用打出来__）
3. 请用自己的话说明什么是github（__讲就行了，不用打出来__）
### git基本操作

1. 从github下载习题

  - 下载[git for windows][1]
  - 运行git bash
  - 新建一个文件夹
  - 在git bash 里 cd 到新建文件夹哪里

    ![image](https://github.com/skomefen/team_example/raw/master/git_example/image/1.PNG)

  - 运行`git clone git@github.com:skomefen/team_example.git `该操作是从git服务器clone整个git文件

    ![image](https://github.com/skomefen/team_example/raw/master/git_example/image/2.PNG)

2. 建立自己的试题文件夹

  - cd  team_example 进入试题文件夹
  - 输入mkdir fwm 创建自己名字缩写文件夹(注：git bash是模仿linux bash形式，所以可以运行部分bash命令)
    ![image](https://github.com/skomefen/team_example/raw/master/git_example/image/3.PNG)

3. 认识文件的基本状态
   ![image](https://github.com/skomefen/team_example/raw/master/git_example/image/4.PNG)

  - 看图，识别git 文件的四种状态。
>Untracked: 未跟踪, 此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过git add 状态变为Staged.

>Unmodify: 文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改, 而变为Modified. 如果使用git rm移出版本库, 则成为Untracked文件

>Modified: 文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过git add可进入暂存staged状态, 使用git checkout 则丢弃修改过, 返回到unmodify状态, 这个git checkout即从库中取出文件, 覆盖当前修改

>Staged: 暂存状态. 执行git commit则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为Unmodify状态. 执行git reset HEAD filename取消暂存, 文件状态为Modified

   git文件要么未跟踪要么已跟踪，后面三种状态都是已跟踪。文件被跟踪后一被修改就会变成Modified(已修改)状态，执行git add 操作文件就变成staged(暂存)状态，staged文件git commit之后就会保存进版本库中，变成UNmodeify状态，字面意思是未修改，其实也是已入库。

4. 对文件进行基本操作 
  - 运行 git help 查看git指令。

  - 输入指令vim  [名字缩写/aaa] 

    该指令是进入vim编辑器，编辑[名字缩写/aaa]文件（其实这个是linux bash命令）然后按键盘ins健进入编辑模式，打上helloworld，按ESL退出编辑，输入:wq回车退出vim编辑器。

  - git status 查看刚刚你添加的文件状态此时（尝试按tag键补全指令）

    此时文件状态应该显示为 untracked files，因为未入版本库

    阅读提示，尝试翻译提示（use “git add \<file\>...”to include in what will be committed）灵活应用翻译软件，或者浏览器插件，或者直接百度有道翻译。理解这句话的意思

 - git add  [名字缩写/aaa]，此时文件应该变成Modified已修改的状态

   重复 git status查看此时文件的状态

   重复理解提示，翻译整个句子。包括哪个 Changes to be committed是什么鬼意思

 - git commit ，commit之后会出现一个vim编辑界面，点击键盘ins 编辑题目，然后esc退出，输入:wq退出编辑模式

   翻译提示

   ![image](https://github.com/skomefen/team_example/raw/master/git_example/image/5.PNG)

   看上图
   用自己的话说，上面commit每一句的信息是什么意思（git的提示很有用的基本没有废话）
   自己去百度（或者谷歌？）理解

   git status 查看状态，重复上面动作

5. 上交作业（下面照做就行了以后再解释）

  - 注册github
  - 点击头像，点击setting，点击SSH and GPG keys，New SSH key 并下载。因为没有这个key好像不可以上次东西到你自己的github上的。怎么搞，下载在哪里，百度，太久了我也忘了。（其实是我懒的实验了）
  - 重新进入习题项目哪里
    ![image](https://github.com/skomefen/team_example/raw/master/git_example/image/6.PNG)
  - 点击fork
  - 这个时候应该就会把项目fork到你账号的仓库里，记住，在你账号仓库里的项目是我账号的项目的镜像，我项目更新不会影响你的仓库里的项目。至于为什么要fork是因为你只能把你的代码push到你自己的仓库里。
  - 回到git bash，运行git remote  -v，该命令可以查看有几个远程分支，这个时候你会看到一个origin 这个是你clone我仓库里的项目时候自动创建的远程分钟。你是只有fetch拉取我分支上的东西的权限，因为你没有我的ssh key。而且我也没有添加你ssh key做管理员。你可以尝试push这个分支，反正没用。
    ![image](https://github.com/skomefen/team_example/raw/master/git_example/image/7.PNG)
  - 点击你项目上的 复制 clone with SSH的地址（git开头的）
  - 运行 git remote add my_origin 刚复制的地址
  - 运行 git remote -v查看你刚刚创建的链接，这个时候你会发现有两个远程分支一个是原来送的，一个是你自己创建的，当然你也可以选择删除它（你真的想这么做？）
  - 运行git push my_origin 好的，你的作业现在提交到你的仓库了
     ![image](https://github.com/skomefen/team_example/raw/master/git_example/image/8.PNG)
  - 回到你仓库项目网页，刷新，点击new pull request。这个时候你的仓库会发送指令通知我有人pull request 给我啦。我同意之后我的项目就会merge你的东西，如果出现冲突，我会提示你fetch我仓库的东西，处理冲突成功再重复上述动作。然后就成功提交成功作业了。

6. 课外作业
  - 去查询为何要这样提交作业，提示，github上参与公共开源项目都是这样提交的。以后会解释为何这样操作。
  - 去试一下除了git for windows之外的git工具，比如eclipse的git插件。




### git本地中级操作

0. 一些基本操作的补充

      - .gitignore文件的使用。

        这个文件是放在项目目录下，作用是忽略掉一些不必要上传到github上的文件。比如说.class 为后缀的Java编译后文件，一些缓冲文件等等。

        如我们要忽略所有的.class文件，只需要新建.gitignore文件（注，windows是无法直接创建这个文件，可新建txt文件然后另存为.gitignore）在项目下，然后在第一行输入\*.class就可以了。

        具体忽略规则去看群文件pro\_git\_中文版本。学会使用ctrl+f 输入.gitignore快查来快速定位，不详细讲。这个文件一般就创建项目的时候直接去拷别人项目的忽略规则就够用了，很少改。

      - 快速提交命令git commit -a 

        这个命令的作用是把所有追踪过的文件，即不是所有不是Untracked的文件都commit成Unmodify，也就是提交的状态。就不用一个个add文件然后commit了。

        git的命令都会有不同的模式。比如这个-a，输入git help commit 可以查看所有commit的模式。  

        不过出来的都是纯英文，准备好浏览器翻译插件或者有道词典

   - 撤销最后一次提交git commit --amend

     有时候我们提交完了才发现漏掉了几个文件没有加，或者提交信息写错了。想要撤消刚才 的提交操作，可以使用 --amend 选项重新提交：

     如果刚才提交时忘了暂存某些修改，可以先补上暂存操作，然后再运行 --amend 提交：
     `$ git commit -m 'initial commit'` 
     `$ git add forgotten_file` 
     `$ git commit --amend`
     上面的三条命令最终得到一个提交，第二个提交命令修正了第一个的提交内容，即添加多一个forgotten_file文件



1. 基本概念的理解

   - 什么git分支（阅读pro\_git\_中文版本53页或者百度）
   - 理解git分支的工作方式
   - 思考为何要这样子设计

2. git分支的操作

   - **准备工作**
       - 新建个新的文件夹，名字叫test_branch
       - 在git bash里面cd到新建文件夹
       - 执行git init
       - touch a1 创建一个a1文件（linux命令来的）
       - git add a1
       - git commit -m "add a1"（-m这个是快速提交模式）
       - touch a2
       - git add a2
       - git commit -m "add a2"
       - git log 这个时候可以看到历史记录里有两个commit，git log显示方式可以定制的，这个不详细说

   - **创建分支**
       - git branch testing 新建一个testing分支，这个时候的testing分支是从add a2这个commit开始的。但目前还是在master分支，你只是新建了分支没有checkout过去。git bash上的蓝色字就是你所在的分支
       - git checkout testing 这个时候跳到了testing分支，显示switched to branch 'testing'，蓝色字也变成了testing（注，git checkout -b testing相当于执行上面两个命令，创建并跳到testing分支）
       - touch t1
       - vim a1 ，然后输入aaa，按ecs输入:wq退出
       - git add t1
       - git commit -a -m "add t1 and change a1" （之前已经追踪过a1，-a模式会自动把a1提交的）你可以注意下面的提示。使用的时候可以多注意提示，可以给到很多信息的
         ![image](https://github.com/skomefen/team_example/raw/master/git_example/image/9.PNG)
         意思是 该commit 是testing 分支，commit的SHA-1哈希值前七位为dea8329 commit 名字为 add t1 and change a1
          2个文件已被改变，其中插入了一行东西
          创建了文件 t1

   - **跳回原分支**
       - git checkout master 跳回到原来的master分支
       - 这个时候观察下你目录下的文件，会发现原来添加的t1和修改的a1部分都不见了。那是因为原来的master当前的commit并没有这些东西。现在还是原来的'add a2'的 commit里
       - touch a3
       - git add a3
       - git commit -m "add a3"

   - **合并分支**
       - git breach 可以看到目前有两个分支，当前分支是绿色的master
       - git merge testing 当前分支和testing合并，这个时候会生成新的commit把master最后一个commit和testing最后一个commit的文件合并。编辑commit退出就合并完成了
       - 查看你的文件夹，你就会发现t1出现了，a1也出现了aaa，所以合并操作就是把两个commit中的文件不同的
       - git breach 你会发现testing分支还在，因为你只是合并了它不是删除了它
       - git log 查看日志，你会发现两个分支的5个commit都在（注，太多信息的时候，回车可以看下面的信息，:wq可以退出查看）
       - git log --graph可以以树的形式查看
         ![image](https://github.com/skomefen/team_example/raw/master/git_example/image/10.PNG)

       - 这个只是合并没有冲突的情况，当两个分支同时修改一个文件的时候就会出现合并冲突的可能，因为git不知道应该如何合并。这个时候就需要手动处理冲突
       - git checkout -b conflict_branch 创建分支并跳到该分支
       - vim a2 输入abcdefg并关闭
       - git commit -a -m "change a2"
       - git checkout master
       - vim a2 原来在conflict_branch的修改不存在了。在第一行输入 ”123456“
       - git commit -a -m "change a2 with 123456"
       - git merge conflict_branch
       - 这个时候显示a2冲突，然后进入（master|MERGING）模式（蓝色字）等待你处理冲突
       - 这个时候输入git status，显示冲突对象a2。出现同时修改
       - 我们vim a2看看变成什么样

         ![image](https://github.com/skomefen/team_example/raw/master/git_example/image/11.PNG)
         <<<<<< HEAD代表来自HEAD指针所在的commit，因为HEAD指向的分支就是当前分支，所以也是可以当作当前分支的commit
         \>>>>>>> conflict_branch表示要合并的分支。
         中间=======分割开了他们冲突的部分。
         你可以全部删掉改成abc123。意思是分别采纳了两个分支冲突内容的一部分。
         ![image](https://github.com/skomefen/team_example/raw/master/git_example/image/11.PNG)

       - git add a2  重新添加a2
       - git commit 合并成功
       - 另外运行 git mergetool 可以用可视化工具来处理冲突。这个自己研究哈。

   - 分支删除
       - 运行git branch 现在可以看到有三条分支
       - 运行git log --graph 可以看到现在的分支线
       - git branch -d testing
       - git branch -d conflict_branch
       - 再运行git branch 现在只剩下master分支
       - 运行git log --graph 发现原来的历史记录都还在的。原来哪些commit并不会因为分支删除而删除。你会发现git倾向于把所有的历史commit都记录在案
       - 如果未合并的分支是不可以用上面用的-d模式删除。但可以运行git branch -D [分支名] 强制删除。这个自己可以试下。






[1]:https://git-for-windows.github.io/	"git for windows"