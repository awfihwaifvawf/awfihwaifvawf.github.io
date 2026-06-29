### 在vscode打断点

react+vite项目作为示例

配置文件.lunch.json 文件

```
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "chrome",
            "request": "launch",
            "name": "Launch Chrome against localhost",
            "url": "http://localhost:8080",
            "webRoot": "${workspaceFolder}",
            "runtimeExecutable": "C:/Users/Administrator/AppData/Local/Google/Chrome/Bin/chrome.exe"
            
        }
    ]
}
```

不添加`runtimeExecutable` 会报错

```
Unable to launch browser: "Unable to find an installation of the browser on your
system.Try installing it,or providing an absolute path to the browser in the
"runtimeExecutable" in your launch.json."
```

添加后允许报错提示

```
Exception has occurred: ReferenceError: closeDescriptionPopup is not defined

  at HTMLAnchorElement.eval (eval at B (chrome-error://chromewebdata/:2:404), <anonymous>:1:41)    at y (chrome-error://chromewebdata/:6556:855)    at F.b (chrome-error://chromewebdata/:6564:108)    at F.g (chrome-error://chromewebdata/:6562:462)    at window.jstProcess (chrome-error://chromewebdata/:6565:847)    at chrome-error://chromewebdata/:6748:1366
```



