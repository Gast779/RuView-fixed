# RuView WiFi-DensePose — Fixed & Working

## 🔗 Репозиторій
**Original:** https://github.com/ruvnet/RuView.git
**Fixed:** https://github.com/Gast779/RuView-fixed

## 🚀 Швидкий старт

```bash
# 1. Клонуй репо
git clone https://github.com/Gast779/RuView-fixed.git
cd RuView-fixed

# 2. Встанови залежності (Python 3.11+)
pip install -r requirements.txt

# 3. Запусти сервер
export SECRET_KEY="your-secret-key"
python -m src.main

# 4. Відкрий браузер
open http://localhost:8000/docs
```

## 🔧 Виправлені баги

### 1. DensePoseHead Config Bug ❌ → ✅
**Проблема:** `DensePoseHead()` викликався без `config` → `TypeError`
**Фікс:** Додав дефолтний конфіг з усіма необхідними параметрами

### 2. Health Router Paths ❌ → ✅
**Проблема:** Роутери підключено до `/health` замість `/api/v1/`
**Фікс:** Змінив префікс з `/health` на `settings.api_prefix` (`/api/v1`)

### 3. Auth Middleware ❌ → ✅
**Проблема:** Public endpoints (health, ready, live) блокувались авторизацією
**Фікс:** Додав `/api/v1/health`, `/api/v1/ready`, `/api/v1/live`, `/api/v1/status` до `skip_paths`

## 📡 API Endpoints

| Метод | Endpoint | Статус | Опис |
|-------|----------|--------|------|
| GET | `/` | ✅ Public | API інформація |
| GET | `/api/v1/health` | ✅ Public | Статус системи |
| GET | `/api/v1/ready` | ✅ Public | Readiness check |
| GET | `/api/v1/live` | ✅ Public | Liveness check |
| GET | `/docs` | ✅ Public | Swagger UI |

| GET | `/api/v1/version` | 🔒 Auth | Версія API |
| GET | `/api/v1/pose/*` | 🔒 Auth | Pose estimation |
| GET | `/api/v1/stream/*` | 🔒 Auth | Streaming |

## 📝 Важливо

- **CSI Hardware:** Для повноцінної роботи потрібен ESP32-S3 або CSI-capable router
- **Mock Mode:** Для тестування без hardware — треба ввімкнути `mock_mode=True`
- **JWT Auth:** Захищені endpoints потребують Bearer token

## 🛠️ Автор
Виправлено та розгорнуто **Hermes AI Agent** для Gast779

---

**Date:** 2026-05-20
