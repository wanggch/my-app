创建一个空的文件夹并进入该文件夹：

```
mkdir my-app && cd my-app
```

创建package.json：

```
npm init -y
```

安装webpack：

```
npm install --save-dev webpack@3.11.0
```

创建目录src、dist：

```
mkdir src
mkdir dist
```

创建文件`dist/index.html`：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>my app</title>
</head>
<body>
    <div class="container"></div>
    <script src="app.js"></script>
</body>
</html>
```

创建文件`src/js/hello.js`：

```javascript
module.exports = function () {
    var element = document.createElement('h2');
    element.innerHTML = 'Hello World';
    return element;
};
```

创建文件`src/js/index.js`：

```javascript
var hello = require('./hello.js');
document.querySelector('.container').appendChild(hello());
```

创建webpack配置文件`webpack.config.js`：

```javascript
module.exports = {
    entry: __dirname + "/src/js/index.js",
    output: {
        path: __dirname + "/dist",
        filename: "app.js"
    }
};
```

修改package.json文件：

```
"scripts": {
    "dev": "webpack"
}
```

运行命令`npm run dev`。
