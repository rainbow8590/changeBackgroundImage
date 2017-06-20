# changeBackgroundImage
### 换肤效果
```
	由于jquery的特性，用jquery写这个换肤的效果很简单；
	用javascript的for循环来写这个效果，我使用的原理是：通过i的值和图片的对应关系来改变背景图片
	但是由于javascript的for循环的特性，我们需要通过一定的方法来获取i的值。
	方法一：使用自定义属性  
		for(var i = 0 ; i < lis.length ; i++){  
			lis[i].index = i;  
			lis[i].onclick = function(){  
				document.body.style.background = 'url(images/bd'+ (this.index+1) +'.jpg) no-repeat';  
			}  
		}  

	  方法二：闭包  
		for(var i = 0 ; i < lis.length ; i++) {  
		lis[i].onclick=function(i){  
			return function(){  
				document.body.style.background = 'url(images/bd'+ (i+1) +'.jpg) no-repeat';  
					console.log(i)  
			}
		}(i);
	 }

	 方法三：自执行函数
		for(var i = 0 ; i < lis.length ; i++){
			(function(n){
				lis[n].onclick=function(){
					document.body.style.background = 'url(images/bd'+ (n+1) +'.jpg) no-repeat';
				}
			})(i)
		}

	  方法四： ES6新语法 let
		for(let i=0;i<lis.length;i++){  
			lis[i].onclick = function(){  
				console.log(i)  
				document.body.style.background = 'url(images/bd'+ (i+1) +'.jpg) no-repeat';  
			}
		}
```
