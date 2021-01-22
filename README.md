# 我的博客

> 欢迎你的到来~~~


# 第一步 安装 node



# 第二步 npm 安装 docsify-cli
```bash
D:\mxz_code\my-github\my-doc>npm i docsify-cli -g
C:\Users\mxz\AppData\Roaming\npm\docsify -> C:\Users\mxz\AppData\Roaming\npm\node_modules\docsify-cli\bin\docsify

> docsify@4.11.6 postinstall C:\Users\mxz\AppData\Roaming\npm\node_modules\docsify-cli\node_modules\docsify
> opencollective-postinstall

Thank you for using docsify!
If you rely on this package, please consider supporting our open collective:
> https://opencollective.com/docsify/donate

npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.3.1 (node_modules\docsify-cli\node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.3.1: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})

+ docsify-cli@4.4.2
added 209 packages from 92 contributors in 15.985s

D:\mxz_code\my-github\my-doc>
```

# 第三步 初始化
```bash
D:\mxz_code\my-github>mkdir docsify-blog

D:\mxz_code\my-github>cd docsify-blog

D:\mxz_code\my-github\docsify-blog>docsify init ./
./ already exists.
√ Are you sure you want to rewrite it? (y/N) true

Initialization succeeded! Please run docsify serve ./
```


# 第四步 本地启动
```bash
D:\mxz_code\my-github\docsify-blog>docsify serve ./

Serving D:\mxz_code\my-github\docsify-blog now.
Listening at http://localhost:3000
```

