# 使用 Docker 執行前後端服務

### Option 1: 自行 build image 並執行

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

### Option 2: 直接從 Docker Hub 下載 image 並執行

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

### Option 3: 使用 Docker Compose

1. 執行 docker compose 啟動前後端

```bash
docker compose up --build
```

2.  透過以下連結瀏覽前後端頁面：

- 前端：[http://localhost:3000](http://localhost:3000)
- 後端：[http://localhost:8000](http://localhost:8000)

# Container Image 建立流程說明

本專案使用 GitHub Actions 實現 CI/CD，當有程式碼變更推送至 main 分支時，會自動建構並上傳 Container Image 至 Docker Hub Repo。

### 流程圖
![Screenshot 2025-05-07 at 8 48 47 PM](https://github.com/user-attachments/assets/c6146080-3878-43f5-9bf2-d85a485ad3d4)

### Tag 命名邏輯說明

目前 image 使用以下固定 tag：

| Tag 名稱   | 說明                        |
| ---------- | --------------------------- |
| `frontend` | 對應 `frontend/` Dockerfile |
| `backend`  | 對應 `backend/` Dockerfile  |

### GitHub Actions 說明

CI 設定檔位於 `.github/workflows/docker.yml`，其中包含以下功能：

- 使用 docker build 進行建構
- 使用 docker push 上傳到 Docker Hub
- 使用 GitHub Secrets (DOCKER_USERNAME, DOCKER_PASSWORD) 進行登入
