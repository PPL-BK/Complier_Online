# Backend Compiler

**Nên tạo dự án cho riêng mình và ghi vào CV nha theo từng bước + mở rộng thêm**

## 1. 🚀 CS Compiler

Dự án này triển khai một trình biên dịch (compiler) cho **ngôn ngữ CS**, được phát triển dựa trên bài tập lớn trong môn PPL1.

**Compiler sẽ:**
- 📥 Đọc file nguồn .cs
- ⚙️ Biên dịch thành bytecode .class
- ▶️ Chạy chương trình bằng Java Virtual Machine (JVM)

**🧱 Kiến trúc tổng quan**
```
.cs source code
      ↓
  Compiler (Python)
      ↓
 .class (Java bytecode)
      ↓
     JVM (java)
      ↓
   Output
```

**📝 Ví dụ chương trình CS**
```
// ------------ Program --------------
const a = 2;
const b = 3 + a;
print(a + b);
// ------------------------------------
```

**▶️ Cách chạy**
```
➜  compiler# python3 run.py main.cs 
/Backend/compiler/src/runtime
Compile success
➜  compiler# (cd src/runtime && java CS)            
7
```

---

## 2. 🚀 CS Compiler Backend API

**Backend cung cấp API để:**
- Quản lý file source code
- Biên dịch (build) chương trình
- Chạy chương trình
- Chỉnh sửa nội dung file

**📂 API Endpoints**
* `GET /files/` → Lấy danh sách file
* `POST /files/create` → Tạo file mới
* `GET /files/run` → Chạy chương trình
* `GET /files/{filename}` → Đọc file
* `DELETE /files/{filename}` → Xóa file
* `POST /files/edit/{filename}` → Sửa nội dung file
* `POST /files/build/{filename}` → Build (compile) file

![alt text](images/api.png)

Dưới đây là phiên bản README **ngắn gọn, rõ ràng** cho phần Docker + CI/CD:

---

## 3. 🚀 Docker & CI/CD

### 🐳 Docker

**Chạy bằng Docker Compose**

```bash
docker compose up --build test
```

---

### 📦 Dockerfile

* Base image: `python:3.11-slim`
* Cài thêm:

  * `openjdk-21`
  * `build-essential`
* Cài dependencies từ `requirements.txt`
* Run app bằng:

```bash
python run.py
```

---

### 🔄 CI/CD (GitHub Actions)

* Trigger khi push vào branch `main`
* Tự động:

  1. Checkout code
  2. Build Docker
  3. Run test (`pytest`)

```yaml
docker compose build
docker compose run --rm test
```



<p align="center">
  <a href="https://www.facebook.com/Shiba.Vo.Tien">
    <img src="https://img.shields.io/badge/Facebook-1877F2?style=for-the-badge&logo=facebook&logoColor=white" alt="Facebook"/>
  </a>
  <a href="https://www.tiktok.com/@votien_shiba">
    <img src="https://img.shields.io/badge/TikTok-000000?style=for-the-badge&logo=tiktok&logoColor=white" alt="TikTok"/>
  </a>
  <a href="https://www.facebook.com/groups/khmt.ktmt.cse.bku?locale=vi_VN">
    <img src="https://img.shields.io/badge/Facebook%20Group-4267B2?style=for-the-badge&logo=facebook&logoColor=white" alt="Facebook Group"/>
  </a>
  <a href="https://www.facebook.com/CODE.MT.BK">
    <img src="https://img.shields.io/badge/Page%20CODE.MT.BK-0057FF?style=for-the-badge&logo=facebook&logoColor=white" alt="Facebook Page"/>
  </a>
  <a href="https://github.com/VoTienBKU">
    <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub"/>
  </a>
</p>