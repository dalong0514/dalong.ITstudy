## deeplearning-ai-video-downloader

[khengyun/deeplearning-ai-video-downloader](https://github.com/khengyun/deeplearning-ai-video-downloader)

Chrome 浏览器里要自己加载插件。

/Users/Daglas/dalong.tools/deeplearning-ai-video-downloader/extension


2025-02-17

项目 deeplearning-ai-video-downloader 在 docker 里占用的端口是 3000，跟 fastgpt 相同，冲突。将项目里所有的 3000 搜索替换成了 3002。

举例如下：


```
services:
  server:
    build: ./server
    ports:
      - "3002:3002"
    volumes:
      - ./server:/usr/src/app
      - /usr/src/app/node_modules
```


---


印象笔记里也有记录

Dockerfile 文件

```
    FROM node:18

    # Set the working directory inside the container
    WORKDIR /usr/src/app

    # Copy package.json and package-lock.json files
    COPY package*.json ./

    # Install the dependencies
    RUN npm install

    # Install ffmpeg with retries
    RUN apt-get update && \
        (apt-get install -y ffmpeg || apt-get install -y ffmpeg) && \
        apt-get clean && \
        rm -rf /var/lib/apt/lists/*

    # Copy the rest of the application code
    COPY . .

    # Expose the port the server will run on
    EXPOSE 3000

    # Command to run the server
    CMD ["node", "server.js"]
```

有两个坑：
1、node 由原项目中的版本 14 更改为 18。
2、ffmpeg下载的时候总是失败，更改如如下代码。

docker-compose.yml

```
services:
  server:
    build: ./server
    ports:
      - "3000:3000"
    volumes:
      - ./server:/usr/src/app
      - /usr/src/app/node_modules
```

开始的时候，运行 docker 显示如下状态，但 docker 里该容器并未跑起来。DeepSeek 根据报错信息做了如上修改。

```
WARN[0000] /Users/Daglas/dalong.tools/deeplearning-ai-video-downloader/docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion
[+] Running 2/2
 ✔ Network deeplearning-ai-video-downloader_default     Created                                                                                                                 0.0s
 ✔ Container deeplearning-ai-video-downloader-server-1  Started
```