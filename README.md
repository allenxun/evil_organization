这个目录是用来记录和总结读论文的新的。四个目录是四个人。

每周一到两篇，有时间就多发呗。

我们的目标是先C后A。

#################################
git下载与安装

官方网站地址：https://git-scm.com/downloads

安装一直点下一步就好了
#################################
github使用

	github是一个仓库网站，用户可以上传自身的文档。大致可以分为三步。第一步，表明并验证身份；第二步，创建并同步远程仓库；第三步，使用git维护仓库。
	1.表明身份
		首先，使用自身的邮箱（allenxun521@google.com）在使用git的机器上面生成密钥。
		ssh-keygen -t rsa -C "allenxun521@google.com"
		其次，在“C:\Users\.ssh”文件中找到id_rsa.pub，获取ssh公钥。
		然后，将公钥放在github用户设置中。
		最后，验证是否成功。输入命令之后，如果出现success的提示，表明成功。
		ssh -T git@github.com

		通过以上4步骤，我们就将使用的机器注册到github相关账户中。
		在操作仓库之前，我们需要使用下面两条命令设置一下上传的用户名和邮箱。
		git config --global user.name "your name"
		git config --global user.email "your_email@163.com"
	2.创建并同步远程仓库
		首先，我们需要在项目文件下初始化。本文中在指定位置创建evil_organization文件夹，进入之后使用命令。
		git init
		其次，使用命令关联仓库。
		git remote add origin git@github.com:allenxun/evil_organization.git
		然后，我们就可以等待远程仓库和本地仓库同步了。
	3.使用git
		我们直接在本地的evil_organization进行编辑，然后上传即可。每次编辑完成之后，上传步骤如下：
		首先，我们查询一下当前文档状态。git会提示我们到哪一步。
		git status
		其次，我们添加新编辑的文件或者是文件夹。
		git add newfile
		然后，我们可以提交文件。
		git commit -a “上传说明”
		最后，我们可以上传文件。
		git push
	4.其他
		其他git的使用，可以查看git的官方文件，或者输入git查看使用说明。
##############################################################
latex使用

	为什么要用latex，因为我用sublime写东西写习惯了。
	1.下载的软件
		MiKTeX （https://miktex.org/download）或者是texlive （https://www.tug.org/texlive/）
		Sublime Text
		LaTeXTools （建议使用sublime中的Package Control 安装，离线安装包地址是https://github.com/SublimeText/LaTeXTools）
		Sumatra PDF （LaTeXTools 默认使用它来预览生成的 https://www.sumatrapdfreader.org/download-free-pdf-viewer.html)
	2.为下载的软件配置环境变量
	3.在sublime中选择Preferences | Package Settings | LaTeXTools | Settings – User修改相应的环境变量。*****是重点需要修改的
	"windows": {
        // Path used when invoking tex & friends; "" is fine for MiKTeX
        // For TeXlive 2011 (or other years) use
        // "texpath" : "C:\\texlive\\2011\\bin\\win32;$PATH",
        "texpath" : "C:\\texlive\\2017\bin\\win32;$PATH",                                            ***************
        // TeX distro: "miktex" or "texlive"
        "distro" : "TeXlive",                                                                        ***************
        // Command to invoke Sumatra. If blank, "SumatraPDF.exe" is used (it has to be on your PATH)
        "sumatra": "C:\\Program Files\\SumatraPDF\\SumatraPDF.exe",                                  ***************
        // Command to invoke Sublime Text. Used if the keep_focus toggle is true.
        // If blank, "subl.exe" or "sublime_text.exe" will be used.
        "sublime_executable": "",
        // how long (in seconds) to wait after the jump_to_pdf command completes
        // before switching focus back to Sublime Text. This may need to be
        // adjusted depending on your machine and configuration.
        "keep_focus_delay": 0.5
    },
    4.设置反向代理
    随便写一个tex文件，如下：
    \documentclass{article}
	\begin{document}
    	hello, world
	\end{document}
	编译之后，在生成的pdf中“设置|选项”中配置反向代理，注意环境变量。
	"C:\Program Files\Sublime Text 3\sublime_text.exe" "%f:%l"
