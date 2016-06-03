# How_To_Use_Git

Git的使用(以下步骤是在安装了Git客户端并且配置了SSH)

一、本地创建项目

	1.创建一个java工程 How_To_Use_Git(包含一个测试类)
	2.创建.gitignore文件
		2.1使用命令如：	D:\workspace\How_To_Use_Git>echo bin/>>.gitignore	加入需要被忽略的文件。
		2.2也可以直接创建，并编辑。
	
二、创建远端仓库

	1.首先需要有github账号
	2.New repository(本人创建仓库时候使用了LICENSE)
	3.复制仓库地址(How_To_Use_Git---->Clone or download---->复制ssh地址或者https地址)]
	
三、上传项目

	1.在项目根目录How_To_Use_Git下，右键-Git init here创建.git文件夹(用于git管理)
	2.右键-打开Git Gui---->远端---->add---->location---->输入步骤二中复制的ssh地址和远程仓库的名字How_To_Use_Git---->add
	3.在项目根目录下打开Git bash命令窗口---->git pull把远程仓库的LICENSE文件拉下来
	4.git status查看有哪些文件可以提交
	5.在Git Gui窗口---->(重新扫描)缓存改动---->填写提交描述---->提交---->上传	
	
四、修改上传

	1.修改readme文件
	2.git bash---->git status---->可以看见modified: README.md
	3.git gui---->重新扫描---->缓存改动---->输入提交描述---->提交---->上传
	
五、新增文件
	
	1.新建HelloGit.java文件
	2.git status---->发现有个Untracked files:src/com/lyle/git/HelloGit.java
	
	
	
	
备注：使用Git bash和Git Gui结合，目的是让人更加直观，明了掌握git的使用