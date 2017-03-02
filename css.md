# CSS 

## 目录

- [点击事件](#pointer-events)
- [默认菜单](#-webkit-touch-callout)
- [inline-block](#inline-block)
- [移动端 reset.css](#mobile-reset)

### pointer-events

* none , 元素捕获不到任何点击事件,事件会穿透到元素的下层
* auto , 事件不会穿透到下层

### -webkit-touch-callout

> 不规范属性

* none , 系统默认菜单被禁用
* default , 系统默认菜单不被禁用

### inline-block

起因: 在于 html 两个 inline-block 元素之间存在空格

解决: 一般父元素用  font-size:0 即可解决问题, 
      但是iphone 6 plus input 应用还是会存在空格, 根本方法就是在html中直接用注释或者不换行去掉空格


### mobile-reset


    html{
        box-sizing:border-box;
        color:#333;
        font-family: -apple-system, BlinkMacSystemFont, "PingFang SC","Helvetica Neue",STHeiti,"Microsoft Yahei",Tahoma,Simsun,sans-serif;
        -webkit-user-select:none;
        -moz-user-select:none;
        -ms-user-select:none;
        user-select:none;
        -webkit-font-smoothing:antialiased;
        -ms-touch-action:manipulation;
        touch-action:manipulation;
        -webkit-text-size-adjust: 100%;
    }
    *,:after,:before{
        box-sizing:inherit;
        -webkit-tap-highlight-color:transparent;
    }
    body,dd,dl,ol,ul{
        margin:0;
        padding:0;
    }
    ol,ul{
        list-style:none
    }
    h1,h2,h3,h4,h5,h6,p{
        margin:0;
        font-weight:400;
    }
    img{
        max-width:100%;
    }
    textarea{
        resize:none
    }
    a{
        outline:none;
        color:#333;
        text-decoration:none;
    }
    a:link{
        color: #333
    }
    a,img{
        -webkit-touch-callout:none;
    }
    button,input,select,textarea{
        outline:none;
        border:none;
        font-size:inherit;
        font-family:inherit;
        -moz-appearance:none;
        -webkit-appearance:none;
        background-color:transparent;
    }
    input:-webkit-autofill{box-shadow:inset 0 0 0 1.333333rem #fff}
    ::-moz-placeholder { color: #B3B3B3; }
    ::-webkit-input-placeholder { color:#B3B3B3; }
    :-ms-input-placeholder { color:#B3B3B3; }

