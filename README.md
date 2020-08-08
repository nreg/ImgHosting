# TyporaImages
typora的免费图床实现与自动上传图床的脚本，

GOTO：查看说明请转到：https://www.cnblogs.com/nreg/p/11992678.html



一、客户端：
任意版本的typora
二、客户端配置：
1.打开typora，文件-偏好设置，将图片地址设置为D:\图片库\${filename}\，路径没有要求    



配置作用：所有图片都在同一根目录下，便于管理

便于本插件检测到网络地址失效时用本地地址再次请求

2、配置window.html文件：

找到Typora的安装目录Typora\resources\app下的window.html文件：注意是安装目录

      

用任意编辑器打开，全局搜索：

<script src="./app/window/frame.js" defer="defer"></script>
搜到并在其后添加本插件地址：

<script src="./plugins/imgHosting/upload.js" defer="defer"></script>
说明：其实只要在window.html文件中window.require = undefined;代码之前加上即可

三、插件配置：
将本插件plugins文件夹复制到Typora的安装目录Typora\resources\app下：注意是安装目录

     

插件说明：

plugins\imgHosting\tosted.js：上传插件

plugins\imgHosting\upload.js：通知插件

四、主题配置：
将vue文件夹及vue.ccs移动到 C:\Users\用户名\AppData\Roaming\Typora\themes下：注意是系统目录  

      

使用说明：重启typora，菜单栏点击主题-选择vue即可

主题说明： 基于社区vue主题优化

扩展内容区域大小，解决图片被内容区域大小限制导致图片模糊

整体居中，图片相对居左对齐， 左右富裕空间始终一致（原版：整体居左，图片居中）

增加图片阴影及圆角，美化图片显示效果

五、服务器配置：
版本要求：

tomcat：7.0及以上
JDK：8U191及以上
环境要求：

可运行在win10、虚拟机、云服务器、树莓派中
端口要求：

8866
部署：将编译文件拖到tomcat的webapp目录下即可：

     

说明：
①、端口可以更改(每次变更都需要重启服务器)，相应的，客户端上传插件upload.js也需要更改(每次变更都需要重启typora)

②、服务端本身不存储图片，只用于请求第三方免费图床，不占用服务器空间

③、实现8个免费图床的请求与响应，图片网络地址可能失效，测试一年，没有失效的情况，客户端单击图片会检测网络地址是否失效，如果失效会自动以名称处的本地地址重新请求

③、开放源码，可自行添加更多图床实现

六、使用说明：
      

使用说明：

点击图片即可进行上传

文字选中处为图片名称显示处，用于插件判断网络地址失效时以用名称处的本地地址重新请求

不支持typora提供的缩放，使用缩放将导致上传插件失效

右下角为tosted.js的显示效果

文档关闭前请使用ctrl+s保存文档，否则图片地址将会回退。

七、版本变更：
2019年：1.0.0版，免费图床实现
2020年3月：1.0.1版，优化代码逻辑
2020年7月：1.0.2版，支持跨域、支持3种上传方式(详见upload.js)、优化通知
