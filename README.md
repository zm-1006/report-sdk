# report-sdk

Report SDK for the H5

## Browser Support

![Chrome](https://raw.github.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png) | ![Firefox](https://raw.github.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png) | ![Safari](https://raw.github.com/alrra/browser-logos/master/src/safari/safari_48x48.png) | ![Opera](https://raw.github.com/alrra/browser-logos/master/src/opera/opera_48x48.png) | ![Edge](https://raw.github.com/alrra/browser-logos/master/src/edge/edge_48x48.png) | ![IE](https://raw.github.com/alrra/browser-logos/master/src/archive/internet-explorer_9-11/internet-explorer_9-11_48x48.png) |
--- | --- | --- | --- | --- | --- |
Latest ✔ | Latest ✔ | Latest ✔ | Latest ✔ | Latest ✔ | 11 ✔ |

[![Browser Matrix](https://saucelabs.com/open_sauce/build_matrix/axios.svg)](https://saucelabs.com/u/axios)

## Installing

Using npm:

```bash
$ npm install report-sdk
```

## SDK使用说明

### SDK引入

1、单页面（SPA）应用引入，以`vue`应用为例：

```javascript 1.8
// 入口 main.js 中引入
import './report-sdk.js'
// 挂载到 vue 实例上 
Vue.prototype.$SDK = $SDK

// 具体页面中使用
以 `this.$SDK.xxx` 的形式调用上报方法

```

2、传统的`html`多页面应用引入

**注意**：SDK必须先引入，再使用，顺序不能颠倒。最好在`onload`或者`ready`之后调用SDK的具体方法。

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>主页</title>
</head>
<body>

<h1>主页</h1>

<script src="./report-sdk.js"></script>
<script>

    $SDK.sendPageEvent({
        event_id: 'xxxxxx',
    })
    
</script>
</body>
</html>

```

### 实例方法

1、页面浏览事件

```javascript 1.8
$SDK.sendPageEvent({
    event_id: 'xxxxxx',
    data: { // 业务参数
        // 
    },
})
// or 在vue中
this.$SDK.sendPageEvent({
    event_id: 'xxxxxx',
    data: { // 业务参数
        // 
    }
})
// 没有业务参数，data 参数可省略  
```

2、用户操作事件（点击）

```javascript 1.8
/*
* 预留方法，暂勿使用
* */
$SDK.sendCommonEvent({
    event_id: 'xxxxxx',
    data: { // 业务参数
        // 
    },
})
// 没有业务参数，data 参数可省略  
```

2、用户信息参数，在登录或者授权，拿到相关信息之后调用

```javascript 1.8
$SDK.setUserInfo({
    userId: 'xxx',
    openId: 'xxx',
    unionId: 'xxx',
})
// 如果其中有参数未获取到，则传空字符串
```

3、beforeInit 方法，在页面不刷新的情况下，SDK上报方法之前调用

```javascript 1.8
$SDK.beforeInit({
    envType: 'dev' // 测试开发环境 dev  正式环境 prod
})
```

## License

MIT
