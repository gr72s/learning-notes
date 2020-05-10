1. 用处：将 ES6 代码转为 ES5 代码，从而在老版本的浏览器执行
2. 安装：`npm install --save-dev @babel/core`
3. 配置：
   * 基本格式
        ```javascript
        {
            "presets": [],
            "plugins": [
                "@babel/preset-react"
            ]
        }
        ```
     * `presets`字段设定转码规则
       * `npm install --save-dev @babel/preset-react`
4. 命令行转码
   * 安装：`npm install --save-dev @babel/cli`
   * 转码至标准输出：`npx babel example.js`
   * 转码写入文件：`npx babel example.js --out-file/-o compiled.js`
   * 转码整个目录：`npx babel src --out-dir/-d lib`
     * 生成`source map`文件：`npx babel src -d lib -s`
5. `babel-node`
   * 安装：`npm install --save-dev @babel/node`
   * 用处：@babel/node模块的babel-node命令，提供一个支持 ES6 的 REPL 环境。它支持 Node 的 REPL 环境的所有功能，而且可以直接运行 ES6 代码。
   * 使用：`npx babel-node`
6. `@babel/register`
   * 安装：`npm install --save-dev @babel/register`
   * 用处：改写require命令，每当使用require加载.js、.jsx、.es和.es6后缀名的文件，就会先用 Babel 进行转码