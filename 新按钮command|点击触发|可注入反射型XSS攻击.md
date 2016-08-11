------
* 特性：标记定义一个命令按钮，比如单选按钮、复选框或按钮。<br>
    只有当 command 元素位于 menu 元素内时，该元素才是可见的。否则不会显示这个元素，但是可以用它规定键盘快捷键。
* 属性与方法：支持HTML5的全局属性和事件属性。<br>
    checked 	checked 	       定义是否被选中。仅用于 radio 或 checkbox 类型<br>
    disabled 	disabled       	 定义 command 是否可用<br>
    icon 	    url 	           定义作为 command 来显示的图像的url<br>
    label    	text 	           为 command 定义可见的 label<br>
    radiogroup 	groupname 	   定义command 所属的组名。仅在类型为 radio 时使用<br>
    type 	   checkbox command radio   定义该 command 的类型。默认是 “command”
* 格式：
    `<command onclick=cut()" label="cut">`
    
------
安全性：command作为命令按钮，自然具有img input等命令按钮的漏洞，触发反射型xss。<br>
        &nbsp;不过大多数类似的漏洞都被浏览器的规则限定住了，不能注入，<br>
        &nbsp;不过对于新兴标签的到来，匹配规则总有漏洞之处。
        
------
典例：
   例如谷歌上上的版本的规则漏洞：<br>
  ` <comment><img src="</comment><img src=x onerror=alert(1)//">`
