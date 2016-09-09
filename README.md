# How_To_Use_Git

Git的使用(以下步骤是在安装了Git客户端并且配置了SSH)

一、本地创建项目

	1.创建一个java工程 How_To_Use_Git(包含一个测试类GitTest.java)
	2.创建.gitignore文件
		2.1使用命令如：	D:\workspace\How_To_Use_Git>echo bin/>>.gitignore	加入需要被忽略的文件。
		2.2也可以直接创建，并编辑。
	
二、创建远端仓库

	1.首先需要有github账号
	2.New repository(本人创建仓库时候使用了LICENSE)
	3.复制仓库地址(How_To_Use_Git---->Clone or download---->复制ssh地址或者https地址)
	
三、上传项目

	1.在项目根目录How_To_Use_Git下，右键-Git init here创建.git文件夹(用于git管理)
	2.右键-打开Git Gui---->远端---->add---->location---->输入步骤二中复制的ssh或者https地址和远程仓库的名字How_To_Use_Git---->add
	3.在项目根目录下打开Git bash命令窗口---->git pull把远程仓库的LICENSE文件拉下来
	4.git status查看有哪些文件可以提交
	5.在Git Gui窗口---->(重新扫描)缓存改动(通过点击文件图标进行选中或不选)---->填写提交描述---->提交---->上传	
	
四、修改上传

	1.修改readme文件
	2.git bash---->git status---->可以看见modified: README.md
	3.git gui---->重新扫描---->缓存改动(通过点击文件图标进行选中或不选)---->输入提交描述---->提交---->上传
	
五、新增文件
	
	1.新建HelloGit.java，TestLocalDelete.java文件
	2.git status---->发现有个Untracked files:src/com/lyle/git/HelloGit.java、TestLocalDelete.java
	3.git gui---->重新扫描---->缓存改动(通过点击文件图标进行选中或不选)---->输入提交描述---->提交---->上传
	
六、删除本地文件
	
	1.本地和远程当前是同步状态，删除本地文件TestLocalDelete.java
	2.git status---->发现有个 deleted:src/com/lyle/git/TestLocalDelete.java
	3.git gui---->重新扫描---->缓存改动(通过点击文件图标进行选中或不选)---->输入提交描述---->提交---->上传
	
七、修改多个文件时选择提交/上传

	1.同时修改两个文件HelloGit.java和GitTest.java
	2.git status---->modified:src/com/lyle/git/GitTest.java modified:src/com/lyle/git/HelloGit.java
	3.git gui---->重新扫描---->缓存改动(通过点击文件图标进行选中或不选)---->此时已缓存的改动(将被提交)有两个文件HelloGit.java和GitTest.java---->通过点击文件图标进行选中或不选----输入提交描述---->提交---->上传

八、冲突
	
	Ⅰ情景1
	1.直接在远程仓库修改GitTest.java文件
	2.本地修改readme文件
	3.git status---->modified:README.md
	4.git gui---->重新扫描---->输入提交描述---->提交(README.md)---->上传【失败】
		4.1 git pull How_To_Use_Git master---->同步远端的修改---->重新扫描---->缓存改动(通过点击文件图标进行选中或不选)---->此时发现没需要提交的文件---->直接上传(因为上一步已经提交了。)
	Ⅱ情景2
	1.本地和远端同时修改GitTest.java文件
	2.本地提交---->失败
	3.git pull How_To_Use_Git master---->此时GitTest.java文件的内容包括远端和本地的还有冲突的符号=====、>>>>>>>、<<<<<<< HEAD符号。
	4.解决冲突，删除不需要的代码和符号
	5.git gui---->重新扫描---->缓存改动(通过点击文件图标进行选中或不选)---->输入提交描述---->提交---->上传
	
九、合并

	1.待续。。。
	2.
	3.
	
十、忽略已经被github管理的文件

	1.git rm --cached xx/yy/a.java
	2.修改.gitignore文件，添加需要忽略的文件
	3.可以用通配符，如：
	```
	# 这是注释行，将被忽略
	*.a       # 忽略所有以.a为扩展名的文件    
	!lib.a    # 但是名为lib.a的文件或目录不要忽略，即使前面设置了对*.a的忽略
	/TODO     # 只忽略此目录下的TODO文件，子目录中的TODO文件不忽略
	build/    # 忽略所有build目录下的文件，但如果是名为build的文件则不忽略
	doc/*.txt # 忽略文件如doc/notes.txt，但是文件如doc/server/arch.txt不忽略
	```
十一、删除本地文件，如何恢复

	Ⅰ情景1
	1.本地删除，没有缓存，提交等：git checkout  -- Test.java  【git checkout -- file；撤销对工作区修改】
	Ⅱ情景2
	2.本地删除并且缓存： git reset HEAD Test.java 【git reset HEAD -- file；清空add命令向暂存区提交的关于file文件的修改（Ustage）】
	Ⅲ情景3
	3.本地删除并且提交： git checkout 0eb98179833e1fe885fa420867227d9eae11d854 Test.java【在Test.java所在路径下执行】
	Ⅳ情景4
	4.直接用远端覆盖更新本地：首先pull最新的远端，然后 git checkout ORIG_HEAD   -- Test.java【在Test.java文件路径下】



备注：使用Git bash和Git Gui结合，目的是让人更加容易掌握git的使用
