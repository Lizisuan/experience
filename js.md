# Javascript（持续更新）

### RegExp 对象

RegExp 对象用于正则匹配 , 有 3 个方法 :

1. test() , 返回 true 或 false
2. exec() , 返回 匹配到的指定值 或 NULL
3. compile() , 改变匹配对象,同时重置 检索位置

#### 踩坑 :

当 全局检索 时 , 同一个对象的第二次匹配会从第一次检索结束开始 , 例如:

    let phone = new RegExp('((13[0-9])|(14[5,7])|(15[0-3,5-9])|(17[0,3,5-8])|(18[0-9])|(147))([0-9]{8})','g');
    phone.test(18815289916)  => true;
    phone.test(18815289916)  => false;

这个时候,只要如此即可

    phone.lastIndex = 0;


