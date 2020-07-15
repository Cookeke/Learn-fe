# NPM相关

### 1.常用功能

1. 查看版本号

   ```js
   npm -v
   npm --version
   ```

2. 全局插件安装目录配置

   ```js
   npm config set prefix "X:\nodejs\node_global"
   ```

3. 全局缓存目录配置

   ```js
   npm config set cache "X:\nodejs\node_cache"
   ```

4. 淘宝镜像配置

   ```js
   npm config set registry https://registry.npm.taobao.org 
   ```

5. 获取npm镜像源

   ```js
   npm config get registry
   ```

6. cnpm安装

   ```js
   npm install -g cnpm --registry=https://registry.npm.taobao.org
   ```

7. 使用npm安装模块

   ```js
   npm install vue
   ```

8. 全局安装与本地安装

   - 全局安装是指将插件安装到nodejs 全局插件目录下，本地安装是指将插件安装到项目node_modules目录下

   ```js
   #全局安装 两种方式均可
   npm install vue-cli -g
   npm install vue-cli --global
   
   #本地安装
   
   ##不会修改package.json
   npm install vue
   
   ##将在package.json的dependencies属性下添加vue
   ##在运行npm install命令时，会自动安装到node_modules目录中
   npm install vue --save
   
   ##将在package.json的devDFependencies属性下添加webpack
   ##在运行npm install命令时，会自动安装到node_modules目录中,但不会再生产模式下安装到node_modules中
   npm install webpack --save-dev
   ```

9. 卸载模块

   ```js
   npm uninstall vue
   ```

10. 更新模块

    ```js
    npm update vue
    ```

11. 创建模块

    ```js
    npm init
    ```

    

