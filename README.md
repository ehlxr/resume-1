DeerResume
==========

![img](http://www.jobdeer.com/img/rd.png)

> 修改了DeerResume在线简历工具按照自己的需要定制。

主要修改如下：
- 可以将简历数据存储到本地。
- 支持本地设置阅读密码功能。
- 新增简历页面置顶功能。

~~[本地简历示例](http://www.deercv.com)。
初始密码:12345~~

最好用的MarkDown在线简历工具，可在线预览、编辑、设置访问密码和生成PDF

  - 可自行搭建，任意修改页面样式和风格
  - 免安装，可放置于任何支持静态页面的云和服务器（当然包括GitHub
  - 在线MarkDown编辑器+实时预览
  - 在浏览器中实时保存草稿
  - 支持阅读密码，您可以直接将网址和密码发送，供招聘方在线浏览
  - 一键生成简单雅致的PDF，供邮件发送及打印
  
原项目地址：https://github.com/geekcompany/DeerResume




### FAQ

如何修改访问密码？
- pwd.json中vpass字段存储的是访问密码（**MD5加密**）

修改访问密码后密码不好使?
- 修改js/app.js文件的第6行
```
 var pwdurl = 'pwd.json?v=1.0.0';
```
将后面的版本号随便修改一个数字
- 修改index.html文件的28行
```
  <script src="js/app.js?v=1.0.0"></script>
```
将后面的版本号随便修改一个数字

~~如何在显示输入密码的时候显示首页的标题和子标题~~
- ~~将data.json、err.json和pwd.json中的title字段和subtitle字段都写值即可。~~

如何编写自己的在线简历
- 自己编写完自己的markdown简历后，将内容复制到data.json中的content字段即可。


这里复制自己的markdown简历到data.json中的content字段时要注意简历中的换行符。需要替换成\r\n在一行显示才可以。
这里我是自己写java代码替换的，需要使用的有json-lib包和apache的common-io包，代码如下：
```
import java.io.File;
import java.io.IOException;
import org.apache.commons.io.FileUtils;
import net.sf.json.JSONObject;

public class GenJson {

	public static void main(String[] args) throws IOException {
		resume();
	}
	private static void resume() throws IOException{
		JSONObject jsonObject = new JSONObject();
		jsonObject.put("local", 1);
		jsonObject.put("errno", 0);
		jsonObject.put("show", 1);
		jsonObject.put("title", "Java程序员简历模板");
		jsonObject.put("subtitle", "-----------就是个模板");
		String content = FileUtils.readFileToString(new File("G:/test/jsontest.txt"), "UTF-8");
		jsonObject.put("content", content);
		System.out.println(jsonObject.toString());
	}
	
}
```
示例截图：
![][1]
![][2]

[1]:http://ofv7c2awe.bkt.clouddn.com/mima.jpg
[2]:http://ofv7c2awe.bkt.clouddn.com/DeerResume.jpg
