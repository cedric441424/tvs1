# TVS1 - 免费在线视频搜索与观看平台

<div align="center">
  <img src="./image/retrotv_5520.png" alt="TVS1 Logo" width="120">
  <br>
  <p><strong>自由观影，畅享精彩</strong></p>
</div>

## 📺 项目简介

TVS1 是一个轻量级、免费的在线视频搜索与观看平台，提供来自多个视频源的内容搜索与播放服务。无需注册，即开即用，支持多种设备访问。项目结合了前端技术和后端代理功能，可部署在支持服务端功能的各类网站托管服务上。

### Docker

使用 Docker 运行 TVS1：

```bash
docker run -d \
  --name TVS1 \
  -p 7788:80 \
  -e PASSWORD=TVS1
  zhangjiain/tvs1:latest
```

访问 `http://localhost:7788` 即可使用。

### Docker指令部署
### 1.使用Git Clone命令

```
git clone https://github.com/zhangjiain/tvs1.git
```

若提示报错 请到 https://github.akams.cn/ 选择能用的加速网址 使用前，先点击【节点检测】，选择延迟少的那个，再选择【Git Clone】

### 2.打开下载好的文件

```
cd tvs1
```

### 3.拉取最新最新镜像(需要在tvs1根目录里面执行)

```
docker-compose pull
```

### 4.重启项目容器(需要在tvs1根目录里面执行)

```
docker-compose down
```
先执行完上面的指令，再执行下面的指令

```
docker-compose up -d
```

### 5.结束

即可访问网站： `http://localhost:7788`

### 6.温馨提示：

请使用非大陆机部署，以免造成不必要的麻烦！
例如：无法使用（即无法搜索） 或 无法访问

### Docker Compose

 `docker-compose.yml` 文件：

```yaml
version: '3'
services:
  TVS1:
    image: zhangjiain/tvs1:latest
    container_name: TVS1
    ports:
      - "7788:80"
    environment:
      - PASSWORD=TVS1
    restart: unless-stopped
```

### 本地开发环境

项目包含后端代理功能，需要支持服务器端功能的环境：

```bash
# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

> ⚠️ 注意：使用简单静态服务器（如 `python -m http.server` 或 `npx http-server`）时，视频代理功能将不可用，视频无法正常播放。完整功能测试请使用 Node.js 开发服务器。

## 🔧 自定义配置

### 密码保护

要为您的 TVS1 实例添加密码保护，可以在部署平台上设置环境变量：

**环境变量名**: `PASSWORD` 
**值**: 您想设置的密码

平台设置方法：

- **Docker**: 使用 `-e PASSWORD=your_password` 参数

### API兼容性

TVS1 支持标准的苹果 CMS V10 API 格式。添加自定义 API 时需遵循以下格式：
- 搜索接口: `https://example.com/api.php/provide/vod/?ac=videolist&wd=关键词`
- 详情接口: `https://example.com/api.php/provide/vod/?ac=detail&ids=视频ID`

**添加 CMS 源**:
1. 在设置面板中选择"自定义接口"
2. 接口地址只需填写到域名部分: `https://example.com`（不要包含`/api.php/provide/vod`部分）

## ⌨️ 键盘快捷键

播放器支持以下键盘快捷键：

- **空格键**: 播放/暂停
- **左右箭头**: 快退/快进
- **上下箭头**: 音量增加/减小
- **M 键**: 静音/取消静音
- **F 键**: 全屏/退出全屏
- **Esc 键**: 退出全屏

## 🛠️ 技术栈

- HTML5 + CSS3 + JavaScript (ES6+)
- Tailwind CSS (通过 CDN 引入)
- HLS.js 用于 HLS 流处理
- DPlayer 视频播放器核心
- Cloudflare/Vercel/Netlify Serverless Functions
- 服务端 HLS 代理和处理技术
- localStorage 本地存储


## ⚠️ 免责声明

TVS1 仅作为视频搜索工具，不存储、上传或分发任何视频内容。所有视频均来自第三方 API 接口提供的搜索结果。如有侵权内容，请联系相应的内容提供方。

本项目开发者不对使用本项目产生的任何后果负责。使用本项目时，您必须遵守当地的法律法规。
