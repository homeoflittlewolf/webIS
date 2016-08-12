------
* 特性：HTML5的新API扩展了window.history，使历史记录点更加开放了。可以存储当前历史记录点、替换当前历史记录点、监听历史记录点。
* 格式：`.pushState(data,title,url);.replaceState(data,title,url);`
* 属性方法： data状态对象：记录历史记录点的额外对象，可以为空; <br>
          title页面标题：目前所有浏览器都不支持;  	<br>							
          可选的url：浏览器不会检查url是否存在，只改变url，url必须同域，不能跨域;
          
------
安全性：由于这两个方法能在不刷新页面的情况下修改历史条目，所以可以在URL上动手攻击

------
典例：<br>
           1.大量伪造前进后退连接地址，充填历史记录，伪造历史<br>
            2.和短地址转换技术一起形成xss攻击<br>
                例如：` http://xxxx.com/?userid=&appid=<scrpt>document.erite(1)</script>`<br>
                       可转化成短地址`http://xx.xy/qxJuSF`<br>
                       虽然完美隐藏，但是在地址栏显示时，还是 `http://xxxx.com/?userid=&appid=<scrpt>document.erite(1)</script>`<br>
                       只隐藏一半，然而使用新标签时<br>
                      ` http://xxxx.com/?userid=&appid=<scrpt>history.pushState({},",location.href.split("?").shift());document.erite(1)</script>`<br>
            此时浏览器的地址栏就能被隐藏`http://xxxx.com/`并且代码还能被执行。
