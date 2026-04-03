# 📦 pip-tools — напоминалка (VS Code)

## 🧠 Идея

Работаем **не с requirements.txt напрямую**, а через:

* `requirements.in` → список зависимостей (чистый, ручной)
* `requirements.txt` → сгенерированный файл (НЕ редактировать)

---

## ⚙️ Установка

```bash
pip install pip-tools
```

---

## 📁 Структура

```
project/
│
├── requirements.in
├── requirements.txt
└── venv/
```

---

## ✍️ Добавление зависимостей

Редактируешь `requirements.in`:

```txt
requests
numpy
pandas
```

---

## 🔄 Генерация requirements.txt

```bash
pip-compile
```

или явно:

```bash
pip-compile requirements.in
```

📌 Что делает:

* фиксирует версии
* подтягивает все зависимости

---

## ⬆️ Обновление зависимостей

Обновить всё:

```bash
pip-compile --upgrade
```

Обновить конкретный пакет:

```bash
pip-compile --upgrade-package requests
```

---

## 📥 Установка зависимостей

```bash
pip-sync
```

📌 Важно:

* синхронизирует окружение строго под `requirements.txt`
* удаляет лишние пакеты

---

## 🧪 Работа в VS Code

### 1. Активируй venv

```bash
# Windows
venv\Scripts\activate

# Mac/Linux
source venv/bin/activate
```

### 2. Выбери интерпретатор

* `Ctrl + Shift + P`
* `Python: Select Interpreter`
* выбрать `venv`

---

## 🚨 Правила (иначе сломаешь себе жизнь)

* ❌ Не редактируй `requirements.txt`
* ✅ Всегда меняй `requirements.in`
* ✅ После изменений → `pip-compile`
* ✅ Для установки → `pip-sync`

---

## 💡 Быстрый цикл работы

```bash
# добавил пакет в requirements.in
pip-compile
pip-sync
```

---

## 🧯 Типичные проблемы

**Пакет не обновляется**
→ забыл `--upgrade`

**Конфликты зависимостей**
→ попробуй:

```bash
pip-compile --upgrade
```

**Окружение сломалось**
→ пересоздай venv и снова:

```bash
pip-sync
```

---

## 🧩 Минимальный набор команд

```bash
pip-compile
pip-compile --upgrade
pip-sync
```

---

Запомни:
👉 `requirements.in` — ты пишешь
👉 `requirements.txt` — машина пишет
👉 `pip-sync` — приводит всё в порядок`