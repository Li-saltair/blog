## Math部分
### 1、写一个函数，返回从min到max之间的随机整数，包括min不包括max 
```
function stochastic(min,max){
if(min === max){
        alert("两个数字是一样的~")
    }
    var num =parseInt(min +  Math.floor(Math.random() * (max-min)));
    return num;
}
console.log(stochastic(5,14))
```
### 2、写一个函数，返回从min都max之间的 随机整数，包括min包括max
```
function stochastic(min,max){
    if(min === max){
        alert("两个数字是一样的~")
    }
    var num =Math.floor(Math.random() * (max - min + 1) + min);
    return num;
}
console.log(stochastic(0,1))
```
### 3、写一个函数，生成一个长度为 n 的随机字符串，字符串字符的取值范围包括0到9，a到 z，A到Z。
```
function ranstr(num){
    if(typeof num === "number"){
        var str = "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
        var newString = "", 
            name;
        for(var i = 0; i < num; i++){
            name = parseInt(Math.random() * 62);
            newString += str[name];
        }
    }else{
        alert("请输入数字~");
    }
    return newString;
}
console.log(ranstr(rr));
```
### 4、写一个函数，生成一个随机 IP 地址，一个合法的 IP 地址为 0.0.0.0~255.255.255.255
```
function ipaddress(){
    var str = "";
    for(var i = 0; i < 4; i++){
       var variable = Math.floor(Math.random() * 255);
       str += variable + ".";
    }
    str = str.substr(0, str.length-2);
    return str;
}
console.log(ipaddress());
```
### 5、写一个函数，生成一个随机颜色字符串，合法的颜色为#000000~ #ffffff
```
function color(){
    let str = "";
    const strfix = "0123456789abcdef";
    for(let i = 0; i<6; i++){
        let num = parseInt(Math.random() * 16);
        let color = strfix[num];
        str += color;
    }
    str = "#" + str;
    return str;
}
console.log(color());
```

## 数组部分
### 1、数组方法里push、pop、shift、unshift、join、splice分别是什么作用？用 splice函数分别实现push、pop、shift、unshift方法
#### push
用于向数组最后添加一个元素。
#### pop
用于删除数组最后一位元素。
#### shift
用于从数组最前一位删除一个元素
#### unshift
用于在数组最前一位添加一个元素
#### join
将数组以一定的规则（join(参数)）拼接成一个字符串，返回的是一个字符串
#### splice
可以通过索引：删除某个元素，替换某个元素，添加某个元素。
#### 用splice实现其他几个的方法
例：
```
var arr = [0,1,2,3,4,5,6,7,8,9];
```
```
arr.push("orange");
//等价方法
arr.splice(arr.length,0,"orange");
```
```
arr.pop();
//等价方法
arr.splice(-1,1);
```
```
arr.unshift("bannan");
//等价方法
arr.splice(0,0,"bannan");
```
```
arr.shift("bannan");
//等价方法
arr.splice(0,1);
```
### 2、写一个函数，操作数组，数组中的每一项变为原来的平方，在原数组上操作
```
var arr = [0,-1,3,5,9,-2.2];
function arrsquare(arr){
    for(var i = 0; i<arr.length; i++){
        arr[i] = arr[i] * arr[i]
    }
    return arr;
}
console.log(arrsquare(arr))
console.log(arr)
```
### 3、写一个函数，操作数组，返回一个新数组，新数组中只包含正数，原数组不变
```
function filterPositive(arr){
    var newArr = []
    for(var i = 0; i<arr.length; i++){
        if(typeof arr[i] === "number"){
            newArr.push(arr[i])
        }
        if(newArr[i]<0){
           newArr.splice(i,1) 
        }
    }
    return newArr
}
var arr = [3, -1,  2,  '饥人谷', true]
var newArr = filterPositive(arr)
console.log(newArr) //[3, 2]
console.log(arr) //[3, -1,  2,  '饥人谷', true]
```

## Date 部分
### 1、写一个函数getChIntv，获取从当前时间到指定日期的间隔时间
```
var str = getChIntv("2017-02-08");
console.log(str);  // 距除夕还有 20 天 15 小时 20 分 10 秒
```
```
function getChIntv(timestr){
    var start = new Date().getTime();
    var end = new Date(timestr).getTime();
    var during = end - start;
    var days = parseInt(during/(1000*60*60*24))  //天
    var hours = parseInt((during%(1000*60*60*24))/(1000*60*60));    //小时
    var minutes = parseInt((during%(1000*60*60))/(1000*60)); //分钟
    var seconds = parseInt((during%(1000*60))/(1000));    //秒
    var time = '距离你输入的时间还有' + days + '天' + hours + '小时' + minutes + '分钟' + seconds + '秒';
    console.log(during);
    console.log(start);
    console.log(end);
    if(end > start){
       return time;
    }else{
        alert("起始时间大于现在哦~")
    }
}
var mytime = getChIntv('2017,7,1')
console.log(mytime);
```
### 2、把hh-mm-dd格式数字日期改成中文日期
```
var str = getChsDate('2015-01-08');
console.log(str);  // 二零一五年一月八日
```
```
function getChsDate(str){
    var dict = ["零","一","二","三","四","五","六","七","八","九","十","十一","十二","十三","十四","十五","十六","十七","十八","十九","二十","二十一","二十二","二十三","二十四","二十五","二十六","二十七","二十八","二十九","三十","三十一"]
    var time = str.split("-");  //得到一个数组
    var year = time[0];
    var yearstr = dict[parseInt(year[0])] + dict[parseInt(year[1])] +dict[parseInt(year[2])] +dict[parseInt(year[3])]
    var month = dict[parseInt(time[1])];
    var day = dict[parseInt(time[2])];
    var dateAndTime = yearstr + "年" + month + "月" + day + "日";
    if(typeof str === "string"){
        return dateAndTime;
    }else{
        alert("请输入正确格式的日期")
    }
}
console.log(getChsDate("2017-6-30"))
```
### 3、写一个函数，参数为时间对象毫秒数的字符串格式，返回值为字符串。假设参数为时间对象毫秒数t，根据t的时间分别返回如下字符串:
- 刚刚（ t 距当前时间不到1分钟时间间隔）
- 3分钟前 (t距当前时间大于等于1分钟，小于1小时)
- 8小时前 (t 距离当前时间大于等于1小时，小于24小时)
- 3天前 (t 距离当前时间大于等于24小时，小于30天)
- 2个月前 (t 距离当前时间大于等于30天小于12个月)
- 8年前 (t 距离当前时间大于等于12个月)
```
function friendlyDate(time){
    var one = time/1000     //得到秒
    var minutes = time/1000/60       //得到分钟
    var hours = time/1000/60/60       //得到小时
    var days = time/1000/60/60/24      //得到天
    var months = time/1000/60/60/24/30       //得到月
    var years = months/12      //得到年
    if(one < 60){
        return "刚刚~";
    }else if(one > 60 && minutes < 60){
        var twostr = parseInt(minutes) + "分钟前";
        return twostr;
    }else if(minutes > 60 && hours < 24){
        var threestr = parseInt(hours) + "小时前";
        return threestr;
    }else if(hours > 24 && days < 30){
        var fourstr = parseInt(days) + "天前";
        return fourstr;
    }else if(days > 30 && months < 12){
        var fivestr = parseInt(months) + "月前";
        return fivestr;
    }else if(months > 12){
        var sixstr = parseInt(years) + "年前";
        return sixstr;
    }
}
var str = friendlyDate( '1484286699422' ) //  47年前
var str2 = friendlyDate('3600') //刚刚
var str3 = friendlyDate('360000') //6分钟前
console.log(str)
console.log(str2)
console.log(str3)
```
