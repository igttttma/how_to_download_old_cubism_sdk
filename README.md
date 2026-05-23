# Cubism 旧版本 SDK 下载说明

Live2D Cubism 官网的 SDK 下载页通常只展示最新版本，因此需要旧版本，例如 Cubism 4 SDK for Web R7 时，页面上可能找不到直接入口。

但官网页面使用的下载脚本里仍然保留了历史版本信息。脚本地址为：

```text
https://cubism.live2d.com/sdk-web/js/download.js
```

## 解决思路

下载或打开该 `download.js`，可以看到几个关键字段：

```js
let FILE_BASE_URL = "https://cubism.live2d.com/sdk-web/bin/";

const fileDataArray = {
  '4-r.7': {
    date: "2023-05-25",
    version: "Cubism 4 SDK for Web R7",
    url: "CubismSdkForWeb-4-r.7.zip",
  },
}
```

其中：

- `FILE_BASE_URL` 是 SDK 文件的基础路径。
- `fileDataArray` 里保存了各个历史版本对应的 zip 文件名。
- 将二者拼接即可得到旧版本 SDK 的官方下载地址。

## Cubism 4 SDK for Web R7

针对 `4-r.7`，脚本中的文件名是：

```text
CubismSdkForWeb-4-r.7.zip
```

因此完整下载链接为：

```text
https://cubism.live2d.com/sdk-web/bin/CubismSdkForWeb-4-r.7.zip
```

可以用 PowerShell 下载：

```powershell
Invoke-WebRequest `
  -Uri "https://cubism.live2d.com/sdk-web/bin/CubismSdkForWeb-4-r.7.zip" `
  -OutFile "CubismSdkForWeb-4-r.7.zip" `
  -UseBasicParsing
```

## 备注

这个方法并不是破解或从第三方镜像下载，而是从 Live2D 官方脚本中读取历史版本文件名，并访问 Live2D 官方 CDN 上仍然存在的文件。

如果未来官方删除了对应 zip 文件，即使脚本中保留版本信息，该链接也可能失效。
