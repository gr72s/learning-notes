1. `--save-dev`：工程构建（开发、打包）时的依赖，保存至`package-lock.json`的`devDependencies`中
# npx
1. 安装：`npm install -g npx`。node自带
2. 用处
   1. 调用项目内部安装的模块。即安装在`node-modules`中的模块
   2. 避免全局安装。即将模块下载到一个临时目录，使用后会删除
   3. 允许指定版本
3. 参数
   1. `--no-install`：强制使用本地模块
   2. `--ignore-existing`：强制使用远程模块