JS关于基础类型和引用类型的数据请点击：[JS数据类型](http://note.youdao.com/noteshare?id=ccb51a3a4c6b5aeca342975e2878a61b&sub=EF8F7118B91C4706805226DDEEC96D4E)
请充分理解之后再来看这篇文章哦~
#### 基本类型的拷贝
先来看一段非常经典的代码
```
var a = 1;
var b = a;
a = 200;
console.log(a);      //200
console.log(b);      //1
```
我们应该知道基本类型“按值传递”，引用类型“按引用传递”，数值作为基本类型是保存在栈内存中，可以直接拿来用的，赋值是什么那么之后就一直是什么，不会受到传递元素的改变带来的影响，所以这里就不难理解上面的代码得到的值的原因了。
#### 引用类型的拷贝
简单说，引用类型是生成一个指针保存的堆内存中，当给引用类型赋值时，我们写的内容是在栈内存中，也就是说我们拿到的其实是一个指针（不会直接拿到栈内存中的内容）。这个指针是指向栈内存中这个引用类型的代码。
提到拷贝涉及到的两种拷贝类型：深拷贝和浅拷贝
##### 浅拷贝
浅拷贝针对对象中的基本类型的值生效，但是对引用类型中还有引用类型的情况就会失效。
```
var a = {
  name:"mary",
  age:20,
  hobby:"eat"
}

function shadowCopy(obj){
  var newObj = {};
  for(var key in obj){
     newObj[key] = obj[key];
  }
  return newObj;
}
var b = shadowCopy(a);
console.log(b)
```
这是得到的就是一个和a完全一样的对象，这个函数就是一个浅拷贝函数。
##### 深拷贝
深拷贝是针对对象中还有引用类型的情况，使用深拷贝可以使新创建的对象和原来的完全脱离关系
```
var a = {
  name:"mary",
  age:20,
  friend:{
    name:"哈哈",
    age:19,
    hobby:"eat"
  }
}

function deep(obj){
  var newobj = {};
  for(var key in obj){
    if(obj.hasOwnProperty(key)){
      if(typeof obj[key] === "number" || typeof obj[key] === "string" || typeof obj[key] === "boolean" || obj[key] === undefined || obj[key] === null){
         newobj[key] = obj[key];
      }else{
        newobj[key] = deep(obj[key]);
      }
    }
  }
  return newobj;
}
var b = deep(a);
a.friend.age = 29;        //此处修改了a对象中的某个值，但是经过函数处理，b里面的这个值不会发生改变
console.log(a);
console.log(b);
```
里面的hasOwnProperty这个属性请参考 [MDN的解释](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty)
