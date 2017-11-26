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

    ![image](https://github.com/skomefen/team_example/raw/master/git%E4%B9%A0%E9%A2%98/image/1.PNG)

  - 运行`git clone git@github.com:skomefen/team_example.git `该操作是从git服务器clone整个git文件

    ![image](https://github.com/skomefen/team_example/raw/master/git%E4%B9%A0%E9%A2%98/image/2.PNG)

2. 建立自己的试题文件夹

  - cd  team_example 进入试题文件夹
  - 输入mkdir fwm 创建自己名字缩写文件夹(注：git bash是模仿linux bash形式，所以可以运行部分bash命令)
    ![image](https://github.com/skomefen/team_example/raw/master/git%E4%B9%A0%E9%A2%98/image/3.PNG)

3. 认识文件的基本状态
   ![image](https://github.com/skomefen/team_example/raw/master/git%E4%B9%A0%E9%A2%98/image/4.PNG)

  - 看图，识别git 文件的四种状态。
>Untracked: 未跟踪, 此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过git add 状态变为Staged.

>Unmodify: 文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改, 而变为Modified. 如果使用git rm移出版本库, 则成为Untracked文件

>Modified: 文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过git add可进入暂存staged状态, 使用git checkout 则丢弃修改过, 返回到unmodify状态, 这个git checkout即从库中取出文件, 覆盖当前修改

>Staged: 暂存状态. 执行git commit则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为Unmodify状态. 执行git reset HEAD filename取消暂存, 文件状态为Modified

   git文件要么未跟踪要么已跟踪，后面三种状态都是已跟踪。文件被跟踪后一被修改就会变成Modified(已修改)状态，执行git add 操作文件就变成staged(暂存)状态，staged文件git commit之后就会保存进版本库中，变成UNmodeify状态，字面意思是未修改，其实也是已入库。

4. 对文件进行基本操作 
  - 运行 git help 查看git指令。

  - 输入指令vim  名字缩写/aaa ，该指令是进入vim编辑器，编辑名字缩写/aaa文件（其实这个是linux bash命令）然后按键盘ins健进入编辑模式，打上helloworld，按ESL退出编辑，输入:wq回车退出vim编辑器。

  - git status 查看刚刚你添加的文件状态此时（尝试按tag键补全指令）

    此时文件状态应该显示为 untracked files，因为未入版本库

    阅读提示，尝试翻译提示（use “git add \<file\>...”to include in what will be committed）灵活应用翻译软件，或者浏览器插件，或者直接百度有道翻译。理解这句话的意思
    
 - git add  你的文件，此时文件应该变成Modified已修改的状态
   
   重复 git status查看此时文件的状态

   重复理解提示，翻译整个句子。包括哪个 Changes to be committed是什么鬼意思
   
 - git commit ，commit之后会出现一个vim编辑界面，点击键盘ins 编辑题目，然后esc退出，输入:wq退出编辑模式
   
   翻译提示
   
   ![image](https://github.com/skomefen/team_example/raw/master/git%E4%B9%A0%E9%A2%98/image/5.PNG)
   
   看上图
   用自己的话说，上面commit每一句的信息是什么意思（git的提示很有用的基本没有废话）
   自己去百度（或者谷歌？）理解
   
   git status 查看状态，重复上面动作
   
5. 上交作业（下面照做就行了以后再解释）

  - 注册github
  - 点击头像，点击setting，点击SSH and GPG keys，New SSH key 并下载。因为没有这个key好像不可以上次东西到你自己的github上的。怎么搞，下载在哪里，百度，太久了我也忘了。（其实是我懒的实验了）
  - 重新进入习题项目哪里
    ![image](https://github.com/skomefen/team_example/raw/master/git%E4%B9%A0%E9%A2%98/image/6.PNG)
  - 点击fork
  - 这个时候应该就会把项目fork到你账号的仓库里，记住，在你账号仓库里的项目是我账号的项目的镜像，我项目更新不会影响你的仓库里的项目。至于为什么要fork是因为你只能把你的代码push到你自己的仓库里。
  - 回到git bash，运行git remote  -v，该命令可以查看有几个远程分支，这个时候你会看到一个origin 这个是你clone我仓库里的项目时候自动创建的远程分钟。你是只有fetch拉取我分支上的东西的权限，因为你没有我的ssh key。而且我也没有添加你ssh key做管理员。你可以尝试push这个分支，反正没用。
  ![image](https://github.com/skomefen/team_example/raw/master/git%E4%B9%A0%E9%A2%98/image/7.PNG)
  - 点击你项目上的 复制 clone with SSH的地址（git开头的）
  - 运行 git remote add my_origin 刚复制的地址
  - 运行 git remote -v查看你刚刚创建的链接，这个时候你会发现有两个远程分支一个是原来送的，一个是你自己创建的，当然你也可以选择删除它（你真的想这么做？）
  - 运行git push my_origin 好的，你的作业现在提交到你的仓库了
   ![image](https://github.com/skomefen/team_example/raw/master/git%E4%B9%A0%E9%A2%98/image/8.PNG)
  - 回到你仓库项目网页，刷新，点击new pull request。这个时候你的仓库会发送指令通知我有人pull request 给我啦。我同意之后我的项目就会merge你的东西，如果出现冲突，我会提示你fetch我仓库的东西，处理冲突成功再重复上述动作。然后就成功提交成功作业了。

6. 课外作业
  - 去查询为何要这样提交作业，提示，github上参与公共开源项目都是这样提交的。以后会解释为何这样操作。
  - 去试一下除了git for windows之外的git工具，比如eclipse的git插件。












[1]:https://git-for-windows.github.io/	"git for windows"