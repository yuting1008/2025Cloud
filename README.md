# 2025Cloud

Assignment for NTU 2025 Spring Cloud Development and Applications

## 使用 Docker 執行前後端

### 自行 build image 並執行

1. 建立 Docker Image

```bash
docker build -t yutingchen1008/2025cloud:frontend ./frontend
docker build -t yutingchen1008/2025cloud:backend ./backend
```

2.  運行 Container

```bash
docker run -d -p 3000:3000 --name nextjs_app yutingchen1008/2025cloud:frontend
docker run -d -p 8000:8000 --name django_app yutingchen1008/2025cloud:backend
```

3. 透過以下連結瀏覽前後端頁面：

- 前端：[http://localhost:3000](http://localhost:3000)
- 後端：[http://localhost:8000](http://localhost:8000)

---

### 直接從 Docker Hub 下載 image 並執行

1. 從 Docker Hub 拉取 Image

```bash
docker pull yutingchen1008/2025cloud:frontend
docker pull yutingchen1008/2025cloud:backend
```

2. 運行 Container

```bash
docker run -d -p 3000:3000 --name nextjs_app yutingchen1008/2025cloud:frontend
docker run -d -p 8000:8000 --name django_app yutingchen1008/2025cloud:backend
```

3. 透過以下連結瀏覽前後端頁面：

- 前端：[http://localhost:3000](http://localhost:3000)
- 後端：[http://localhost:8000](http://localhost:8000)

### 使用 Docker Compose

1. 執行 docker compose 啟動前後端

```bash
docker compose up --build
```

2.  透過以下連結瀏覽前後端頁面：

- 前端：[http://localhost:3000](http://localhost:3000)
- 後端：[http://localhost:8000](http://localhost:8000)
