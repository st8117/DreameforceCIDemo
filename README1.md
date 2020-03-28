2:在本地进入到上边儿工程文件夹进行初期化前提是本地安装了git											git config user.email
	echo "# DF-2018-Demo" >> README.md										
	git init										
	git add --all										
	git commit -m "first111 commit"										
	git remote add origin https://github.com/st8117/DF-2018-Demo.git										#git remote add origin [YOUR NEW .GIT URL] # 将新源地址写入本地版本库配置文件
	git push -u origin master										
3:用VS打开工程		提前安装SFDX									
4:关联你的开发环境，为创建Scrach环境做准备				SFDX:Set a default org				确保打开了DevHub功能			
05:创建Scratch环境				SFDX:Set a default scratchorg				Scratch org 可以设置有效期			
6:Push source to default scrach org											
7:Set UP CI											
 	1:打开CI 点击Add project										
	2:选择刚刚创建的Gitbub 库										
	3:Build Project -》Hello world										
8:操作Git把CI传递给Git的config文件Merge到Git仓库里。											
9:在https://github.com/st8117/DreameforceCIDemo/tree/master/build里下载build文件夹通过VS上传到Git上去。											
10:从上边git里找到CI Config文件，并且拷贝里边儿的内容到自己工程的Config文件里，并且仔细看一下，这个Config文件和build文件夹											
11:在CI的本工程的目录里，点击右上角的齿轮，进入到设定画面，进行CI的环境变量设定，这里也就是SFDC里的APPConnect的参数设定地方，											
12:在Salesforce里设定APPConnect,我们需要把【Consumer Key】和【digital signatures】设置到CircleCI里边儿去。											
	【digital signatures】的生成方法										
		使用Build文件夹里的。执行.generate-keys.sh									
		Country code:cn									
		Province:ln									
		city:dl									
		orgname:test									
		sectionname:01									
		HostName:test01									
		Password:Passw0rd									
13:在Circle CI的环境变量里设定以下参数											
	SFDC_SERVER_KEY = key file for certificate base64 encoded										
	SFDC_PROD_CLIENTID=connect app client id for product										
	SFDC_PROD_USER										
14:把Build文件夹下生成的，server.crt上传到ConnectApp里 .appconnect 里的授权登陆方式选择，预授权，并且把自己用户的Profile设置上，否则CI登陆不了。											
15:选择CircleCi的，Job菜单											
16:接下来可以测试一下了。											