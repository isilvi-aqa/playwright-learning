# 📘 Roadmap: Автоматизация тестирования на Python

> Pet-проект для изучения **Python + Playwright + Pytest + SQL + Allure**
> Объекты тестирования: **SauceDemo** (UI), **JSONPlaceholder** (API), **локальная PostgreSQL** (БД)

---

## 📑 Содержание

1. [Общая информация](#-общая-информация)
2. [🔌 Настройка VS Code](#-настройка-vs-code)
3. [📁 Структура проекта](#-структура-проекта)
4. [Этап 1. Настройка окружения (День 1–2)](#%EF%B8%8F-этап-1-настройка-окружения-день-12)
5. [Этап 2. Page Object Model (День 3–5)](#-этап-2-page-object-model-день-35)
6. [Этап 3. UI-тесты (День 6–8)](#-этап-3-ui-тесты-день-68)
7. [Этап 4. API-тесты (День 9–11)](#-этап-4-api-тесты-день-911)
8. [Этап 5. Работа с БД (День 12–14)](#%EF%B8%8F-этап-5-работа-с-бд-день-1214)
9. [Этап 6. Allure и отчёты (День 15–16)](#-этап-6-allure-и-отчёты-день-1516)
10. [Этап 7. CI/CD (День 17–20)](#-этап-7-cicd-день-1720)
11. [💡 Best Practices](#-best-practices)
12. [🔧 Фикстуры с разными scope](#-фикстуры-с-разными-scope)
13. [⏳ Ожидания в Playwright](#-ожидания-в-playwright)
14. [📸 Автоматические скриншоты при падении](#-автоматические-скриншоты-при-падении)
15. [⚡ Параллельный запуск (pytest-xdist)](#-параллельный-запуск-pytest-xdist)
16. [🌍 Работа с несколькими окружениями](#-работа-с-несколькими-окружениями)
17. [🗂️ Хранение тестовых данных](#%EF%B8%8F-хранение-тестовых-данных)
18. [🏷️ Кастомные маркеры](#-кастомные-маркеры)
19. [✅ Итоговый чек-лист знаний](#-итоговый-чек-лист-знаний)
20. [▶️ Полезные команды](#%EF%B8%8F-полезные-команды)
21. [📚 Ресурсы для изучения](#-ресурсы-для-изучения)

---

## ✅ Прогресс

- [ ] **Этап 1.** Настройка окружения (День 1–2)
- [ ] **Этап 2.** Page Object Model (День 3–5)
- [ ] **Этап 3.** UI-тесты (День 6–8)
- [ ] **Этап 4.** API-тесты (День 9–11)
- [ ] **Этап 5.** Работа с БД (День 12–14)
- [ ] **Этап 6.** Allure и отчёты (День 15–16)
- [ ] **Этап 7.** CI/CD (День 17–20)

---

## 🎯 Общая информация

- 👤 Профиль: начинающий автотестировщик, на работе использует **Java + Selenide + RestAssured + Allure**
- 🎯 Цель: освоить **Python + Playwright + Pytest + SQL + Allure** в pet-проекте
- 🛠️ IDE: **VS Code** с AI-ассистентом
- 🧩 Покрытие: **UI + API + БД**
- 🐍 Python: **3.11**
- 🌐 UI-стенд: [https://www.saucedemo.com](https://www.saucedemo.com)
- 🌐 API-стенд: [https://jsonplaceholder.typicode.com](https://jsonplaceholder.typicode.com)
- 🗄️ БД: **локальная PostgreSQL** (через `docker-compose`)

---

## 🔌 Настройка VS Code

### 1. Обязательные расширения

| Расширение | ID | Описание |
|---|---|---|
| Python | `ms-python.python` | Поддержка Python, IntelliSense, отладка, запуск тестов |
| Pylance | `ms-python.vscode-pylance` | Быстрый type-checker и автодополнение |
| Playwright Test for VSCode | `ms-playwright.playwright` | Запуск/отладка Playwright-тестов, инспектор локаторов |
| GitLens | `eamodio.gitlens` | История коммитов, blame, сравнение прямо в редакторе |
| Allure (Gherkin/шаги) | `alexkrechik.cucumberautocomplete` | Подсветка шагов и Gherkin; для отчётов — `allure serve` |

> ⚠️ **Примечание по Allure**: полноценного официального расширения VS Code для просмотра Allure-отчётов нет. Для подсветки шагов Allure в коде используйте **`alexkrechik.cucumberautocomplete`** (Gherkin/шаги). Отчёты открывайте в браузере командой `allure serve allure-results`.

Установка всех обязательных расширений одной командой:

```bash
code --install-extension ms-python.python
code --install-extension ms-python.vscode-pylance
code --install-extension ms-playwright.playwright
code --install-extension eamodio.gitlens
code --install-extension alexkrechik.cucumberautocomplete
```

### 2. Рекомендуемые расширения

| Расширение | ID | Зачем нужно |
|---|---|---|
| Pytest | `LittleFoxTeam.pytest` | Удобный запуск отдельных тестов из UI |
| GitHub Copilot / Codeium | `GitHub.copilot` / `Codeium.codeium` | AI-ассистент в редакторе |
| Git Graph | `mhutchie.git-graph` | Визуализация графа коммитов |
| REST Client | `humao.rest-client` | Выполнение HTTP-запросов из `.http`-файлов (ручная проверка API) |
| SQLTools | `mtxr.sqltools` + `mtxr.sqltools-driver-pg` | Просмотр и запросы к PostgreSQL прямо из VS Code |
| Better Comments | `aaron-bond.better-comments` | Цветные комментарии (TODO, !, ? и т.д.) |
| Indent Rainbow | `oderwat.indent-rainbow` | Подсветка отступов — удобно в Python |
| Error Lens | `usernamehw.errorlens` | Ошибки линтера прямо в строке кода |
| autoDocstring | `njpwerner.autodocstring` | Автогенерация docstring |

Установка рекомендуемых:

```bash
code --install-extension LittleFoxTeam.pytest
code --install-extension GitHub.copilot
code --install-extension mhutchie.git-graph
code --install-extension humao.rest-client
code --install-extension mtxr.sqltools
code --install-extension mtxr.sqltools-driver-pg
code --install-extension aaron-bond.better-comments
code --install-extension oderwat.indent-rainbow
code --install-extension usernamehw.errorlens
code --install-extension njpwerner.autodocstring
```

### 3. Пример `.vscode/settings.json`

```json
{
  "[python]": {
    "editor.defaultFormatter": "ms-python.black-formatter",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.organizeImports": "explicit"
    }
  },
  "python.defaultInterpreterPath": "${workspaceFolder}/.venv/Scripts/python.exe",
  "python.analysis.typeCheckingMode": "basic",
  "python.testing.pytestEnabled": true,
  "python.testing.unittestEnabled": false,
  "python.testing.pytestArgs": ["tests"],
  "python.linting.enabled": true,
  "python.linting.flake8Enabled": true,
  "python.linting.flake8Args": ["--max-line-length=100"],
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000,
  "editor.tabSize": 4,
  "terminal.integrated.defaultProfile.windows": "PowerShell",
  "terminal.integrated.env.windows": {
    "PYTHONPATH": "${workspaceFolder}"
  },
  "playwright.env": {
    "BASE_URL": "https://www.saucedemo.com"
  },
  "playwright.showTrace": "afterError",
  "allure.resultsFolder": "allure-results"
}
```

### 4. Пример `.vscode/launch.json` (отладка pytest)

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Pytest: текущий файл",
      "type": "debugpy",
      "request": "launch",
      "module": "pytest",
      "args": ["${file}", "-v", "-s"],
      "console": "integratedTerminal",
      "justMyCode": false
    },
    {
      "name": "Pytest: UI-тесты",
      "type": "debugpy",
      "request": "launch",
      "module": "pytest",
      "args": ["tests/ui", "-v", "--headed"],
      "console": "integratedTerminal"
    },
    {
      "name": "Pytest: конкретный тест",
      "type": "debugpy",
      "request": "launch",
      "module": "pytest",
      "args": ["${input:testPath}", "-v", "-s"],
      "console": "integratedTerminal",
      "inputs": [
        {
          "id": "testPath",
          "type": "promptString",
          "description": "Путь к тесту (nodeid)",
          "default": "tests/ui/test_login.py::test_login_success"
        }
      ]
    }
  ]
}
```

### 5. Горячие клавиши VS Code для тестов

| Действие | Windows/Linux | Mac |
|---|---|---|
| Запустить тест (Run) | `Ctrl+; R` | `Cmd+; R` |
| Отладить тест (Debug) | `Ctrl+; D` | `Cmd+; D` |
| Перейти к тесту в файле | `Ctrl+; F` | `Cmd+; F` |
| Открыть панель Testing | `Ctrl+Shift+P` → `Testing: Focus on Test Explorer` | `Cmd+Shift+P` → `Testing` |
| Запустить все тесты | `Ctrl+; A` | `Cmd+; A` |
| Открыть терминал | `` Ctrl+` `` | `` Cmd+` `` |
| Запустить задачу | `Ctrl+Shift+B` | `Cmd+Shift+B` |

> 💡 Если сочетания не работают — установите расширение **Pytest** (`LittleFoxTeam.pytest`), оно добавляет кнопки ▶️ / 🐛 прямо над каждой тестовой функцией.

---

## 📁 Структура проекта

```text
playwrite-learning/
├── .github/
│   └── workflows/
│       └── ci.yml                      # GitHub Actions workflow
├── .vscode/
│   ├── settings.json
│   └── launch.json
├── pages/                              # Page Object Model (UI)
│   ├── __init__.py
│   ├── base_page.py                    # Базовый класс с общими методами
│   ├── login_page.py                   # Страница входа SauceDemo
│   ├── inventory_page.py               # Каталог товаров
│   ├── cart_page.py                    # Корзина
│   └── checkout_page.py                # Оформление (задание для сам. работы)
├── api/                                # API-клиент и модели
│   ├── __init__.py
│   ├── client.py                       # HTTP-клиент с Allure-шагами
│   ├── endpoints.py                    # Все эндпоинты JSONPlaceholder
│   └── models/
│       ├── __init__.py
│       ├── post.py                     # Pydantic-модель Post
│       ├── user.py                     # Pydantic-модель User
│       └── comment.py                  # Pydantic-модель Comment
├── db/                                 # Работа с БД
│   ├── __init__.py
│   ├── connection.py                   # DatabaseConnection (SQLAlchemy)
│   ├── validators.py                   # DBValidator
│   └── schema.sql                      # DDL для тестовой схемы
├── tests/
│   ├── __init__.py
│   ├── conftest.py                     # Общие фикстуры (UI + API + DB)
│   ├── ui/
│   │   ├── __init__.py
│   │   ├── test_login.py
│   │   └── test_cart.py
│   ├── api/
│   │   ├── __init__.py
│   │   ├── test_posts.py
│   │   └── test_users.py
│   └── integration/
│       ├── __init__.py
│       └── test_ui_db_integration.py
├── utils/
│   ├── __init__.py
│   ├── config.py                       # Чтение .env, класс Config
│   ├── helpers.py                      # Вспомогательные функции
│   ├── allure_helpers.py               # Кастомные аттачменты
│   └── data_loader.py                  # Загрузка JSON/YAML/Excel
├── data/
│   ├── test_data.json                  # Тестовые данные
│   ├── users.yaml                      # Данные пользователей
│   └── products.xlsx                   # Данные товаров (пример)
├── .env.example                        # Шаблон переменных окружения
├── .env                                # Локальные секреты (в .gitignore)
├── .gitignore
├── docker-compose.yml                  # PostgreSQL для тестов
├── pytest.ini                          # Конфигурация pytest
├── requirements.txt
└── PLAN.md                             # Этот файл
```

---

- [ ] ## ⚙️ Этап 1. Настройка окружения (День 1–2)

### 1.1 Установка Python и виртуального окружения

```bash
# Проверка версии Python (нужна 3.11+)
python --version

# Создание виртуального окружения
python -m venv .venv

# Активация (Windows PowerShell)
.\.venv\Scripts\Activate.ps1

# Активация (Linux/macOS)
source .venv/bin/activate
```

> Если PowerShell блокирует активацию — выполните:
> `Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned`

### 1.2 Установка зависимостей

`requirements.txt`:

```text
pytest==8.3.4
pytest-xdist==3.6.1
playwright==1.49.1
allure-pytest==2.13.5
requests==2.32.3
SQLAlchemy==2.0.36
psycopg2-binary==2.9.10
python-dotenv==1.0.1
pydantic==2.10.4
faker==33.3.1
openpyxl==3.1.5
pyyaml==6.0.2
```

```bash
pip install -r requirements.txt

# Установка браузеров Playwright
playwright install

# (опционально) Установка системных зависимостей Playwright
playwright install-deps
```

### 1.3 Файлы конфигурации

`.env.example`:

```bash
# Окружения
ENV=dev
UI_BASE_URL=https://www.saucedemo.com
API_BASE_URL=https://jsonplaceholder.typicode.com

# БД
DB_HOST=localhost
DB_PORT=5432
DB_NAME=test_db
DB_USER=postgres
DB_PASSWORD=postgres
DB_SCHEMA=public

# Playwright
HEADLESS=true
SLOW_MO=0
```

`.gitignore`:

```text
.venv/
__pycache__/
*.pyc
.env
allure-results/
allure-report/
test-results/
.playwright/
*.log
.pytest_cache/
.idea/
.vscode/launch.json
```

`pytest.ini`:

```ini
[pytest]
minversion = 8.0
testpaths = tests
python_files = test_*.py
python_classes = Test*
python_functions = test_*
addopts =
    -v
    -ra
    --strict-markers
    --tb=short
    --alluredir=allure-results
markers =
    smoke: критические smoke-тесты
    regression: регрессионные тесты
    ui: UI-тесты (Playwright)
    api: API-тесты (requests)
    db: тесты с работой БД
    integration: интеграционные тесты
    slow: медленные тесты
log_cli = true
log_cli_level = INFO
```

`docker-compose.yml` (PostgreSQL):

```yaml
version: "3.9"
services:
  postgres:
    image: postgres:16-alpine
    container_name: test_postgres
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
      POSTGRES_DB: test_db
    ports:
      - "5432:5432"
    volumes:
      - pgdata:/var/lib/postgresql/data
      - ./db/schema.sql:/docker-entrypoint-initdb.d/schema.sql
volumes:
  pgdata:
```

### 1.4 Проверка окружения

```bash
# Запуск БД
docker compose up -d

# Проверка установки
python -c "import playwright, pytest, requests, sqlalchemy, pydantic; print('OK')"
playwright --version
allure --version   # если не установлен: scoop install allure (Windows)
```

### ✅ Контрольные вопросы (Этап 1)

1. Зачем нужно виртуальное окружение и что произойдёт, если его не использовать?
2. В чём разница между `pip install playwright` и `playwright install`?
3. Зачем `--strict-markers` в `pytest.ini` и что будет без него?
4. Почему `.env` должен быть в `.gitignore`, а `.env.example` — нет?
5. Как переключиться между окружениями (dev/staging/prod), не меняя код?

### 📝 Задания для самостоятельной работы

- [ ] Создать репозиторий на GitHub, запушить структуру проекта (без `.venv` и `.env`).
- [ ] Запустить `docker compose up -d` и подключиться к БД через расширение SQLTools.

---

- [ ] ## 🏗️ Этап 2. Page Object Model (День 3–5)

### 2.1 Концепция POM

**Page Object Model** — паттерн, при котором каждая веб-страница описывается отдельным классом. Тесты работают не с локаторами напрямую, а с методами page-объектов.

**Принципы:**
- 📦 **Инкапсуляция** — локаторы и действия скрыты внутри класса страницы.
- 🔄 **Переиспользование** — методы страницы используются во множестве тестов.
- 🛠️ **Поддерживаемость** — при изменении UI правится только один файл.
- 🧪 **Читаемость** — тест выглядит как описание бизнес-шага: `login_page.login("user", "pass")`.

**Аналогия из вашего Java-стека:** POM в Python ≈ Page Object в Java/Selenide. `base_page.py` ≈ `BasePage` с `SelenideElement`, только вместо `$x()` — Playwright locators.

### 2.2 `pages/base_page.py`

```python
from typing import Self
from playwright.sync_api import Page, Locator, expect
import allure


class BasePage:
    """Базовый класс для всех page-объектов."""

    def __init__(self, page: Page) -> None:
        self.page = page

    # --- Навигация ---

    @allure.step("Открыть страницу {url}")
    def open(self, url: str) -> Self:
        self.page.goto(url)
        return self

    @allure.step("Получить текущий URL")
    def current_url(self) -> str:
        return self.page.url

    # --- Локаторы (вспомогательные методы) ---

    def locator(self, selector: str) -> Locator:
        return self.page.locator(selector)

    # --- Действия ---

    @allure.step("Кликнуть по элементу: {selector}")
    def click(self, selector: str) -> Self:
        self.page.locator(selector).click()
        return self

    @allure.step("Заполнить поле {selector} значением")
    def fill(self, selector: str, value: str) -> Self:
        self.page.locator(selector).fill(value)
        return self

    # --- Проверки ---

    @allure.step("Проверить видимость элемента: {selector}")
    def should_be_visible(self, selector: str) -> Self:
        expect(self.page.locator(selector)).to_be_visible()
        return self

    @allure.step("Проверить текст элемента: {selector} == {expected}")
    def should_have_text(self, selector: str, expected: str) -> Self:
        expect(self.page.locator(selector)).to_have_text(expected)
        return self

    # --- Скриншот ---

    def take_screenshot(self, name: str = "screenshot") -> None:
        allure.attach(
            self.page.screenshot(),
            name=name,
            attachment_type=allure.attachment_type.PNG,
        )
```

### 2.3 `pages/login_page.py`

```python
from playwright.sync_api import Page, expect
import allure
from pages.base_page import BasePage


class LoginPage(BasePage):
    """Страница входа SauceDemo."""

    # Локаторы
    USERNAME_INPUT = "#user-name"
    PASSWORD_INPUT = "#password"
    LOGIN_BUTTON = "#login-button"
    ERROR_MESSAGE = "[data-test='error']"

    def __init__(self, page: Page) -> None:
        super().__init__(page)
        self.url = "/"

    # --- Действия ---

    @allure.step("Ввести логин: {username}")
    def enter_username(self, username: str) -> "LoginPage":
        self.fill(self.USERNAME_INPUT, username)
        return self

    @allure.step("Ввести пароль")
    def enter_password(self, password: str) -> "LoginPage":
        self.fill(self.PASSWORD_INPUT, password)
        return self

    @allure.step("Нажать кнопку Login")
    def click_login(self) -> None:
        self.click(self.LOGIN_BUTTON)

    # --- Составные шаги ---

    @allure.step("Выполнить вход как {username}")
    def login(self, username: str, password: str) -> None:
        self.enter_username(username)
        self.enter_password(password)
        self.click_login()

    # --- Проверки ---

    @allure.step("Проверить сообщение об ошибке: {expected}")
    def should_show_error(self, expected: str) -> None:
        self.should_have_text(self.ERROR_MESSAGE, expected)

    @allure.step("Проверить, что вход выполнен (URL изменился)")
    def should_be_logged_in(self) -> None:
        expect(self.page).to_have_url(lambda url: "inventory" in url)
```

### 2.4 `pages/inventory_page.py`

```python
from playwright.sync_api import Page, expect
import allure
from pages.base_page import BasePage


class InventoryPage(BasePage):
    """Каталог товаров SauceDemo."""

    INVENTORY_ITEM = ".inventory_item"
    ITEM_NAME = ".inventory_item_name"
    ITEM_PRICE = ".inventory_item_price"
    ADD_TO_CART_BUTTON = "[data-test^='add-to-cart-']"
    REMOVE_BUTTON = "[data-test^='remove-']"
    SHOPPING_CART_BADGE = ".shopping_cart_badge"
    SHOPPING_CART_LINK = ".shopping_cart_link"
    SORT_DROPDOWN = "[data-test='product-sort-container']"

    def __init__(self, page: Page) -> None:
        super().__init__(page)
        self.url = "/inventory.html"

    # --- Действия ---

    @allure.step("Добавить товар '{name}' в корзину")
    def add_to_cart(self, name: str) -> "InventoryPage":
        item = self.page.locator(self.INVENTORY_ITEM).filter(has_text=name)
        item.locator(self.ADD_TO_CART_BUTTON).click()
        return self

    @allure.step("Открыть корзину")
    def go_to_cart(self) -> None:
        self.click(self.SHOPPING_CART_LINK)

    @allure.step("Выбрать сортировку: {option}")
    def sort_by(self, option: str) -> "InventoryPage":
        self.page.select_option(self.SORT_DROPDOWN, option)
        return self

    # --- Проверки ---

    @allure.step("Проверить количество товаров в каталоге: {count}")
    def should_have_items_count(self, count: int) -> None:
        expect(self.page.locator(self.INVENTORY_ITEM)).to_have_count(count)

    @allure.step("Проверить бейдж корзины: {count}")
    def should_have_cart_badge(self, count: int) -> None:
        expect(self.page.locator(self.SHOPPING_CART_BADGE)).to_have_text(str(count))

    # --- Данные ---

    def get_all_item_names(self) -> list[str]:
        return self.page.locator(self.ITEM_NAME).all_inner_texts()

    def get_all_prices(self) -> list[float]:
        prices = self.page.locator(self.ITEM_PRICE).all_inner_texts()
        return [float(p.replace("$", "")) for p in prices]
```

### 2.5 `pages/cart_page.py`

```python
from playwright.sync_api import Page, expect
import allure
from pages.base_page import BasePage


class CartPage(BasePage):
    """Корзина SauceDemo."""

    CART_ITEM = ".cart_item"
    CART_ITEM_NAME = ".inventory_item_name"
    CART_ITEM_PRICE = ".inventory_item_price"
    REMOVE_BUTTON = "[data-test^='remove-']"
    CHECKOUT_BUTTON = "#checkout"
    CONTINUE_SHOPPING_BUTTON = "#continue-shopping"

    def __init__(self, page: Page) -> None:
        super().__init__(page)
        self.url = "/cart.html"

    @allure.step("Удалить товар '{name}' из корзины")
    def remove_item(self, name: str) -> "CartPage":
        item = self.page.locator(self.CART_ITEM).filter(has_text=name)
        item.locator(self.REMOVE_BUTTON).click()
        return self

    @allure.step("Перейти к оформлению заказа")
    def click_checkout(self) -> None:
        self.click(self.CHECKOUT_BUTTON)

    @allure.step("Продолжить покупки")
    def continue_shopping(self) -> None:
        self.click(self.CONTINUE_SHOPPING_BUTTON)

    @allure.step("Проверить количество товаров в корзине: {count}")
    def should_have_items_count(self, count: int) -> None:
        expect(self.page.locator(self.CART_ITEM)).to_have_count(count)

    @allure.step("Проверить, что товар '{name}' в корзине")
    def should_contain_item(self, name: str) -> None:
        item = self.page.locator(self.CART_ITEM).filter(has_text=name)
        expect(item).to_be_visible()

    def get_item_names(self) -> list[str]:
        return self.page.locator(self.CART_ITEM_NAME).all_inner_texts()
```

### ✅ Контрольные вопросы (Этап 2)

1. Почему локаторы хранятся как константы класса, а не внутри методов?
2. В чём разница между `expect(locator).to_be_visible()` и обычным `if locator.is_visible()`?
3. Зачем методы page-объекта возвращают `self` (fluent interface)?
4. Какой паттерн в Selenide соответствует `BasePage` в этом коде?
5. Почему в `LoginPage.login()` три шага объединены в один `@allure.step`?

### 📝 Задание для самостоятельной работы (Этап 2)

- [ ] Создать `pages/checkout_page.py` для страницы оформления заказа (`/checkout-step-one.html`) со следующими методами:
  - `fill_first_name(name)`, `fill_last_name(name)`, `fill_zip(code)`
  - `click_continue()` → переход к `/checkout-step-two.html`
  - `should_show_error(expected)` — проверка ошибки валидации
  - `get_error_text()` — получение текста ошибки

---

- [ ] ## 🧪 Этап 3. UI-тесты (День 6–8)

### 3.1 Фикстуры в `tests/conftest.py`

```python
import pytest
from playwright.sync_api import Page, Playwright
from pages.login_page import LoginPage
from pages.inventory_page import InventoryPage
from pages.cart_page import CartPage
from api.client import ApiClient
from db.connection import DatabaseConnection
from utils.config import Config


# ---------- Конфигурация ----------

@pytest.fixture(scope="session")
def config() -> Config:
    return Config()


# ---------- Браузер Playwright ----------

@pytest.fixture(scope="session")
def browser_context(playwright: Playwright, config: Config):
    browser = playwright.chromium.launch(headless=config.HEADLESS)
    context = browser.new_context(
        base_url=config.UI_BASE_URL,
        viewport={"width": 1280, "height": 720},
    )
    yield context
    context.close()
    browser.close()


@pytest.fixture
def page(browser_context) -> Page:
    """Новая страница для каждого теста (scope=function)."""
    page = browser_context.new_page()
    yield page
    page.close()


# ---------- Page-объекты ----------

@pytest.fixture
def login_page(page: Page) -> LoginPage:
    return LoginPage(page)


@pytest.fixture
def inventory_page(page: Page) -> InventoryPage:
    return InventoryPage(page)


@pytest.fixture
def cart_page(page: Page) -> CartPage:
    return CartPage(page)


@pytest.fixture
def logged_in_page(page: Page, login_page: LoginPage, config: Config) -> Page:
    """Страница после успешного входа (готовый стейт)."""
    login_page.open(config.UI_BASE_URL)
    login_page.login("standard_user", "secret_sauce")
    return page


# ---------- API клиент ----------

@pytest.fixture(scope="session")
def api_client(config: Config) -> ApiClient:
    return ApiClient(base_url=config.API_BASE_URL)


# ---------- БД ----------

@pytest.fixture(scope="session")
def db(config: Config) -> DatabaseConnection:
    conn = DatabaseConnection(config)
    yield conn
    conn.close()
```

### 3.2 `tests/ui/test_login.py`

```python
import pytest
from playwright.sync_api import expect

pytestmark = pytest.mark.ui


class TestLogin:
    """Тесты страницы входа."""

    def test_login_success(self, login_page, inventory_page, config):
        """Позитивный тест: успешный вход."""
        login_page.open(config.UI_BASE_URL)
        login_page.login("standard_user", "secret_sauce")
        inventory_page.should_have_items_count(6)

    def test_login_locked_out_user(self, login_page, config):
        """Негативный тест: заблокированный пользователь."""
        login_page.open(config.UI_BASE_URL)
        login_page.login("locked_out_user", "secret_sauce")
        login_page.should_show_error(
            "Epic sadface: Sorry, this user has been locked out."
        )

    def test_login_empty_credentials(self, login_page, config):
        """Негативный тест: пустые поля."""
        login_page.open(config.UI_BASE_URL)
        login_page.click_login()
        login_page.should_show_error("Epic sadface: Username is required")

    def test_login_wrong_password(self, login_page, config):
        """Негативный тест: неверный пароль."""
        login_page.open(config.UI_BASE_URL)
        login_page.login("standard_user", "wrong_pass")
        login_page.should_show_error(
            "Epic sadface: Username and password do not match any user in this service"
        )

    @pytest.mark.parametrize(
        "username,password,should_succeed",
        [
            ("standard_user", "secret_sauce", True),
            ("problem_user", "secret_sauce", True),
            ("performance_glitch_user", "secret_sauce", True),
            ("locked_out_user", "secret_sauce", False),
            ("standard_user", "wrong", False),
        ],
        ids=["standard", "problem", "glitch", "locked", "wrong-pass"],
    )
    def test_login_parametrized(
        self, login_page, inventory_page, config,
        username, password, should_succeed
    ):
        """Параметризованный тест: разные сценарии входа."""
        login_page.open(config.UI_BASE_URL)
        login_page.login(username, password)

        if should_succeed:
            inventory_page.should_have_items_count(6)
        else:
            expect_error = login_page.locator(login_page.ERROR_MESSAGE)
            assert expect_error.is_visible()
```

### 3.3 `tests/ui/test_cart.py`

```python
import pytest

pytestmark = pytest.mark.ui


class TestCart:
    """Тесты корзины."""

    def test_add_single_item_to_cart(self, logged_in_page, inventory_page, cart_page):
        """Добавление одного товара в корзину."""
        inventory_page.add_to_cart("Sauce Labs Backpack")
        inventory_page.should_have_cart_badge(1)
        inventory_page.go_to_cart()
        cart_page.should_have_items_count(1)
        cart_page.should_contain_item("Sauce Labs Backpack")

    def test_add_multiple_items(self, logged_in_page, inventory_page, cart_page):
        """Добавление нескольких товаров."""
        items = ["Sauce Labs Backpack", "Sauce Labs Bike Light", "Sauce Labs Bolt T-Shirt"]
        for item in items:
            inventory_page.add_to_cart(item)
        inventory_page.should_have_cart_badge(len(items))
        inventory_page.go_to_cart()
        cart_page.should_have_items_count(len(items))

    def test_remove_item_from_cart(self, logged_in_page, inventory_page, cart_page):
        """Удаление товара из корзины."""
        inventory_page.add_to_cart("Sauce Labs Backpack")
        inventory_page.add_to_cart("Sauce Labs Bike Light")
        inventory_page.go_to_cart()
        cart_page.remove_item("Sauce Labs Backpack")
        cart_page.should_have_items_count(1)
        cart_page.should_contain_item("Sauce Labs Bike Light")

    def test_continue_shopping(self, logged_in_page, inventory_page, cart_page):
        """Возврат к покупкам."""
        inventory_page.add_to_cart("Sauce Labs Backpack")
        inventory_page.go_to_cart()
        cart_page.continue_shopping()
        inventory_page.should_have_cart_badge(1)
```

### ✅ Контрольные вопросы (Этап 3)

1. В чём разница между `scope="function"` и `scope="session"` у фикстуры `page`?
2. Почему `logged_in_page` использует `login_page`, а не дублирует логику входа?
3. Что делает `pytestmark = pytest.mark.ui` в начале файла?
4. Чем параметризация `@pytest.mark.parametrize` лучше создания отдельных тест-методов?
5. Зачем параметр `ids` в `parametrize`?

### 📝 Задания для самостоятельной работы (Этап 3)

- [ ] Написать `test_inventory.py` с тестами на сортировку товаров (по имени A→Z, Z→A, по цене).
- [ ] Добавить параметризованный тест на добавление всех 6 товаров в корзину.

---

- [ ] ## 🌐 Этап 4. API-тесты (День 9–11)

### 4.1 `api/endpoints.py`

```python
"""Эндпоинты JSONPlaceholder (https://jsonplaceholder.typicode.com)."""


class Endpoints:
    POSTS = "/posts"
    POST = "/posts/{post_id}"
    POST_COMMENTS = "/posts/{post_id}/comments"

    USERS = "/users"
    USER = "/users/{user_id}"
    USER_POSTS = "/users/{user_id}/posts"

    COMMENTS = "/comments"
    ALBUMS = "/albums"
    PHOTOS = "/photos"
    TODOS = "/todos"
```

### 4.2 `api/client.py`

```python
import allure
import requests
from typing import Any


class ApiClient:
    """HTTP-клиент с автоматическими Allure-шагами и аттачментами."""

    def __init__(self, base_url: str, default_timeout: int = 10) -> None:
        self.base_url = base_url.rstrip("/")
        self.session = requests.Session()
        self.session.headers.update({"Content-Type": "application/json"})
        self.timeout = default_timeout

    def _url(self, endpoint: str) -> str:
        return f"{self.base_url}{endpoint}"

    def _attach(self, response: requests.Response) -> None:
        allure.attach(
            f"REQUEST: {response.request.method} {response.request.url}\n"
            f"Body: {response.request.body}\n\n"
            f"RESPONSE: {response.status_code}\n"
            f"Body: {response.text}",
            name="HTTP Exchange",
            attachment_type=allure.attachment_type.TEXT,
        )

    @allure.step("GET {endpoint}")
    def get(self, endpoint: str, params: dict | None = None, **kwargs) -> requests.Response:
        response = self.session.get(
            self._url(endpoint), params=params, timeout=self.timeout, **kwargs
        )
        self._attach(response)
        return response

    @allure.step("POST {endpoint}")
    def post(self, endpoint: str, json: Any = None, **kwargs) -> requests.Response:
        response = self.session.post(
            self._url(endpoint), json=json, timeout=self.timeout, **kwargs
        )
        self._attach(response)
        return response

    @allure.step("PUT {endpoint}")
    def put(self, endpoint: str, json: Any = None, **kwargs) -> requests.Response:
        response = self.session.put(
            self._url(endpoint), json=json, timeout=self.timeout, **kwargs
        )
        self._attach(response)
        return response

    @allure.step("PATCH {endpoint}")
    def patch(self, endpoint: str, json: Any = None, **kwargs) -> requests.Response:
        response = self.session.patch(
            self._url(endpoint), json=json, timeout=self.timeout, **kwargs
        )
        self._attach(response)
        return response

    @allure.step("DELETE {endpoint}")
    def delete(self, endpoint: str, **kwargs) -> requests.Response:
        response = self.session.delete(self._url(endpoint), timeout=self.timeout, **kwargs)
        self._attach(response)
        return response
```

### 4.3 Pydantic-модели

`api/models/post.py`:

```python
from pydantic import BaseModel, Field


class Post(BaseModel):
    userId: int
    id: int | None = None
    title: str
    body: str


class PostCreate(BaseModel):
    """Модель для создания поста (без id)."""
    userId: int
    title: str = Field(min_length=1, max_length=200)
    body: str = Field(min_length=1)
```

`api/models/user.py`:

```python
from pydantic import BaseModel, EmailStr


class Address(BaseModel):
    street: str
    suite: str
    city: str
    zipcode: str
    geo: dict


class User(BaseModel):
    id: int
    name: str
    username: str
    email: EmailStr
    address: Address
    phone: str
    website: str
    company: dict
```

> ⚠️ Для `EmailStr` требуется `pip install pydantic[email]` (или `email-validator`).

### 4.4 `tests/api/test_posts.py`

```python
import pytest
from api.endpoints import Endpoints
from api.models.post import Post, PostCreate
from faker import Faker

pytestmark = pytest.mark.api
faker = Faker()


class TestPosts:
    """Тесты эндпоинта /posts."""

    def test_get_all_posts(self, api_client):
        """Получение всех постов."""
        response = api_client.get(Endpoints.POSTS)
        assert response.status_code == 200
        posts = [Post(**p) for p in response.json()]
        assert len(posts) == 100

    def test_get_post_by_id(self, api_client):
        """Получение конкретного поста."""
        response = api_client.get(Endpoints.POST.format(post_id=1))
        assert response.status_code == 200
        post = Post(**response.json())
        assert post.id == 1
        assert post.userId == 1

    @pytest.mark.parametrize("post_id", [1, 50, 100], ids=["first", "middle", "last"])
    def test_get_post_parametrized(self, api_client, post_id):
        response = api_client.get(Endpoints.POST.format(post_id=post_id))
        assert response.status_code == 200
        post = Post(**response.json())
        assert post.id == post_id

    def test_create_post(self, api_client):
        """Создание поста (JSONPlaceholder возвращает 201)."""
        new_post = PostCreate(
            userId=1,
            title=faker.sentence(),
            body=faker.paragraph(),
        )
        response = api_client.post(Endpoints.POSTS, json=new_post.model_dump())
        assert response.status_code == 201
        created = Post(**response.json())
        assert created.title == new_post.title
        assert created.id == 101  # JSONPlaceholder всегда возвращает id=101

    def test_update_post(self, api_client):
        """Обновление поста через PUT."""
        payload = {"userId": 1, "id": 1, "title": "updated", "body": "new body"}
        response = api_client.put(Endpoints.POST.format(post_id=1), json=payload)
        assert response.status_code == 200
        assert response.json()["title"] == "updated"

    def test_delete_post(self, api_client):
        """Удаление поста."""
        response = api_client.delete(Endpoints.POST.format(post_id=1))
        assert response.status_code == 200

    def test_get_post_comments(self, api_client):
        """Комментарии к посту."""
        response = api_client.get(Endpoints.POST_COMMENTS.format(post_id=1))
        assert response.status_code == 200
        assert len(response.json()) > 0

    def test_get_nonexistent_post(self, api_client):
        """Негативный: несуществующий пост возвращает пустой объект."""
        response = api_client.get(Endpoints.POST.format(post_id=9999))
        assert response.status_code == 404
        assert response.json() == {}
```

### 4.5 `tests/api/test_users.py`

```python
import pytest
from api.endpoints import Endpoints
from api.models.user import User

pytestmark = pytest.mark.api


class TestUsers:
    def test_get_all_users(self, api_client):
        response = api_client.get(Endpoints.USERS)
        assert response.status_code == 200
        users = [User(**u) for u in response.json()]
        assert len(users) == 10

    def test_get_user_by_id(self, api_client):
        response = api_client.get(Endpoints.USER.format(user_id=1))
        assert response.status_code == 200
        user = User(**response.json())
        assert user.username == "Bret"
        assert "@" in user.email

    def test_filter_users_by_name(self, api_client):
        """Фильтрация через query-параметры."""
        response = api_client.get(Endpoints.USERS, params={"username": "Bret"})
        assert response.status_code == 200
        assert len(response.json()) == 1
```

### ✅ Контрольные вопросы (Этап 4)

1. Зачем Pydantic-модели в API-тестах, если можно проверять `response.json()["title"]`?
2. В чём разница между `model_dump()` и `dict()` (устаревший метод)?
3. Почему `ApiClient` использует `requests.Session()`, а не `requests.get()` напрямую?
4. Что вернёт JSONPlaceholder при POST на `/posts` — реальное сохранение или заглушку?
5. Как `@allure.step` на методах клиента помогает в отчёте?

### 📝 Задания для самостоятельной работы (Этап 4)

- [ ] Написать `test_comments.py` с тестами на эндпоинт `/comments` (GET, фильтрация по `postId`).
- [ ] Добавить валидацию схемы ответа с помощью `pydantic` + `response.json()`.

---

- [ ] ## 🗄️ Этап 5. Работа с БД (День 12–14)

### 5.1 `db/schema.sql` (DDL тестовой схемы)

```sql
CREATE TABLE IF NOT EXISTS users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE IF NOT EXISTS orders (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id),
    product_name VARCHAR(200) NOT NULL,
    quantity INTEGER DEFAULT 1,
    total_price NUMERIC(10, 2) NOT NULL,
    status VARCHAR(20) DEFAULT 'created',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 5.2 `db/connection.py`

```python
from sqlalchemy import create_engine, text
from sqlalchemy.engine import Engine
import allure
from utils.config import Config


class DatabaseConnection:
    """Обёртка над SQLAlchemy для выполнения запросов с Allure-шагами."""

    def __init__(self, config: Config) -> None:
        self._engine: Engine = create_engine(
            f"postgresql+psycopg2://{config.DB_USER}:{config.DB_PASSWORD}"
            f"@{config.DB_HOST}:{config.DB_PORT}/{config.DB_NAME}",
            echo=False,
        )

    @allure.step("SQL QUERY: {query}")
    def execute_query(self, query: str, params: dict | None = None) -> list[dict]:
        """SELECT — возвращает список словарей."""
        with self._engine.connect() as conn:
            result = conn.execute(text(query), params or {})
            rows = [dict(row._mapping) for row in result]
            allure.attach(
                f"Query: {query}\nParams: {params}\nRows: {len(rows)}",
                name="SQL Result",
                attachment_type=allure.attachment_type.TEXT,
            )
            return rows

    @allure.step("SQL COMMAND: {query}")
    def execute_command(self, query: str, params: dict | None = None) -> int:
        """INSERT/UPDATE/DELETE — возвращает количество затронутых строк."""
        with self._engine.begin() as conn:
            result = conn.execute(text(query), params or {})
            allure.attach(
                f"Command: {query}\nParams: {params}\nRowcount: {result.rowcount}",
                name="SQL Command",
                attachment_type=allure.attachment_type.TEXT,
            )
            return result.rowcount

    def close(self) -> None:
        self._engine.dispose()
```

### 5.3 `db/validators.py`

```python
from db.connection import DatabaseConnection


class DBValidator:
    """Валидаторы состояния БД для тестов."""

    def __init__(self, db: DatabaseConnection) -> None:
        self.db = db

    def user_exists(self, username: str) -> bool:
        rows = self.db.execute_query(
            "SELECT 1 FROM users WHERE username = :username",
            {"username": username},
        )
        return len(rows) > 0

    def get_user_by_email(self, email: str) -> dict | None:
        rows = self.db.execute_query(
            "SELECT * FROM users WHERE email = :email",
            {"email": email},
        )
        return rows[0] if rows else None

    def get_order_count(self, user_id: int) -> int:
        rows = self.db.execute_query(
            "SELECT COUNT(*) AS cnt FROM orders WHERE user_id = :uid",
            {"uid": user_id},
        )
        return rows[0]["cnt"] if rows else 0

    def get_orders_by_user(self, user_id: int) -> list[dict]:
        return self.db.execute_query(
            "SELECT * FROM orders WHERE user_id = :uid ORDER BY created_at DESC",
            {"uid": user_id},
        )
```

### 5.4 `tests/integration/test_ui_db_integration.py`

```python
import pytest
from db.validators import DBValidator
from faker import Faker

pytestmark = [pytest.mark.integration, pytest.mark.db]
faker = Faker()


@pytest.fixture
def db_validator(db):
    return DBValidator(db)


class TestUiDbIntegration:
    """Интеграционные тесты: UI-действие → проверка в БД."""

    def test_create_user_via_api_and_verify_in_db(self, api_client, db_validator, db):
        """Создаём пользователя через API (имитация) и проверяем в БД."""
        username = faker.user_name()
        email = faker.email()

        # Предусловие: добавляем запись в БД (имитация backend-обработки UI-формы)
        db.execute_command(
            "INSERT INTO users (username, email) VALUES (:u, :e)",
            {"u": username, "e": email},
        )

        # Проверка через валидатор
        assert db_validator.user_exists(username)
        user = db_validator.get_user_by_email(email)
        assert user is not None
        assert user["username"] == username

    def test_order_lifecycle_in_db(self, db_validator, db):
        """Полный цикл заказа в БД."""
        # Создаём пользователя
        db.execute_command(
            "INSERT INTO users (username, email) VALUES (:u, :e) RETURNING id",
            {"u": faker.user_name(), "e": faker.email()},
        )
        user = db.execute_query("SELECT id FROM users ORDER BY id DESC LIMIT 1")[0]
        user_id = user["id"]

        # Создаём заказ
        db.execute_command(
            "INSERT INTO orders (user_id, product_name, total_price) "
            "VALUES (:uid, :name, :price)",
            {"uid": user_id, "name": "Sauce Labs Backpack", "price": 29.99},
        )

        assert db_validator.get_order_count(user_id) == 1

    def test_cleanup_isolated(self, db):
        """Тест демонстрирует изоляцию: данные создаются и чистятся."""
        db.execute_command(
            "INSERT INTO users (username, email) VALUES (:u, :e)",
            {"u": "temp_user", "e": "temp@test.com"},
        )
        assert db.execute_query("SELECT * FROM users WHERE username = 'temp_user'")
        db.execute_command("DELETE FROM users WHERE username = 'temp_user'")
        assert not db.execute_query("SELECT * FROM users WHERE username = 'temp_user'")
```

### ✅ Контрольные вопросы (Этап 5)

1. В чём разница между `execute_query` и `execute_command`? Зачем `begin()` во втором?
2. Почему фикстура `db` имеет `scope="session"`, а не `scope="function"`?
3. Как обеспечить изоляцию данных между тестами (транзакции / cleanup)?
4. Зачем `text()` оборачивает SQL-строки в SQLAlchemy 2.0?
5. Почему параметризованные запросы (`:username`) безопаснее, чем f-strings?

### 📝 Задания для самостоятельной работы (Этап 5)

- [ ] Добавить метод `get_order_total(user_id)` в `DBValidator` — сумма всех заказов пользователя.
- [ ] Написать тест, который через UI добавляет товар в корзину, а затем проверяет запись заказа в БД.

---

- [ ] ## ✅ Этап 6. Allure и отчёты (День 15–16)

### 6.1 Настройка Allure

Allure уже подключён через `allure-pytest` в `requirements.txt` и `--alluredir=allure-results` в `pytest.ini`.

Установка самого Allure CLI (для просмотра отчётов):

```bash
# Windows (через scoop)
scoop install allure

# macOS
brew install allure

# Проверка
allure --version
```

### 6.2 Кастомные аттачменты — `utils/allure_helpers.py`

```python
import allure
import json
from playwright.sync_api import Page


def attach_screenshot(page: Page, name: str = "Скриншот") -> None:
    """Прикрепить скриншот страницы к Allure-отчёту."""
    allure.attach(
        page.screenshot(full_page=True),
        name=name,
        attachment_type=allure.attachment_type.PNG,
    )


def attach_api_response(response, name: str = "API Response") -> None:
    """Прикрепить API-ответ в формате JSON."""
    allure.attach(
        json.dumps(response.json(), indent=2, ensure_ascii=False),
        name=name,
        attachment_type=allure.attachment_type.JSON,
    )


def attach_sql_query(query: str, result: list) -> None:
    """Прикрепить SQL-запрос и его результат."""
    allure.attach(
        f"QUERY:\n{query}\n\nRESULT:\n{json.dumps(result, indent=2, default=str)}",
        name="SQL",
        attachment_type=allure.attachment_type.TEXT,
    )


def attach_text(text: str, name: str = "Info") -> None:
    """Прикрепить произвольный текст."""
    allure.attach(text, name=name, attachment_type=allure.attachment_type.TEXT)


def attach_environment_info() -> None:
    """Создать файл environment.properties для раздела Environment в отчёте."""
    import os
    from utils.config import Config
    cfg = Config()
    env_content = (
        f"Python={os.popen('python --version').read().strip()}\n"
        f"ENV={cfg.ENV}\n"
        f"UI_BASE_URL={cfg.UI_BASE_URL}\n"
        f"API_BASE_URL={cfg.API_BASE_URL}\n"
        f"DB={cfg.DB_NAME}@{cfg.DB_HOST}:{cfg.DB_PORT}\n"
    )
    with open("allure-results/environment.properties", "w", encoding="utf-8") as f:
        f.write(env_content)
```

### 6.3 Скриншот при падении (через хук)

```python
# в conftest.py
import pytest
import allure


@pytest.hookimpl(hookwrapper=True, tryfirst=True)
def pytest_runtest_makereport(item, call):
    """Автоматический скриншот при падении UI-теста."""
    outcome = yield
    report = outcome.get_result()
    if report.when == "call" and report.failed:
        page = item.funcargs.get("page")
        if page is not None:
            allure.attach(
                page.screenshot(full_page=True),
                name="screenshot-on-failure",
                attachment_type=allure.attachment_type.PNG,
            )
            allure.attach(
                page.content(),
                name="page-html-on-failure",
                attachment_type=allure.attachment_type.HTML,
            )
```

### 6.4 Категории — `allure-results/categories.json`

```json
[
  {
    "name": "UI failures",
    "matchedStatuses": ["broken", "failed"],
    "flaky": true
  },
  {
    "name": "API failures",
    "matchedStatuses": ["failed"]
  }
]
```

### 6.5 Команды для генерации отчётов

```bash
# Запуск тестов с генерацией результатов
pytest tests/ --alluredir=allure-results

# Открыть отчёт в браузере (онлайн-режим, сервер поднимается локально)
allure serve allure-results

# Сгенерировать статичный HTML-отчёт в папку allure-report
allure generate allure-results -o allure-report --clean

# Открыть статичный отчёт
allure open allure-report

# Очистить результаты
rm -rf allure-results allure-report
```

### ✅ Контрольные вопросы (Этап 6)

1. Чем `allure serve` отличается от `allure generate` + `allure open`?
2. Зачем файл `environment.properties` и где он должен лежать?
3. Как добавить кастомную категорию для падений только UI-тестов?
4. Что делает хук `pytest_runtest_makereport` и почему с `hookwrapper=True`?
5. Почему `attachment_type=allure.attachment_type.JSON` удобнее, чем `TEXT` для API-ответов?

### 📝 Задания для самостоятельной работы (Этап 6)

- [ ] Добавить запись видео (Playwright `video="on"`) и прикреплять ссылку на него в отчёт.
- [ ] Создать `conftest`-хук, добавляющий в отчёт длительность каждого теста как текстовый аттачмент.

---

- [ ] ## 🚀 Этап 7. CI/CD (День 17–20)

### 7.1 GitHub Actions workflow — `.github/workflows/ci.yml`

```yaml
name: CI - Automated Tests

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]
  schedule:
    # Ночной прогон в 03:00 UTC
    - cron: "0 3 * * *"

jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      fail-fast: false
      matrix:
        python-version: ["3.11"]
        test-suite: [ui, api, integration]

    steps:
      - name: 📥 Checkout кода
        uses: actions/checkout@v4

      - name: 🐍 Установка Python ${{ matrix.python-version }}
        uses: actions/setup-python@v5
        with:
          python-version: ${{ matrix.python-version }}

      - name: 📦 Кэширование pip-зависимостей
        uses: actions/cache@v4
        with:
          path: ~/.cache/pip
          key: ${{ runner.os }}-pip-${{ hashFiles('requirements.txt') }}
          restore-keys: ${{ runner.os }}-pip-

      - name: 📥 Установка зависимостей
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: 🎭 Установка браузеров Playwright
        run: playwright install --with-deps chromium

      - name: 🗄️ Запуск PostgreSQL
        run: docker compose up -d postgres

      - name: ⏳ Ожидание готовности БД
        run: |
          for i in {1..30}; do
            pg_isready -h localhost -p 5432 && break
            sleep 1
          done

      - name: 🧪 Запуск тестов (${{ matrix.test-suite }})
        env:
          ENV: ci
          UI_BASE_URL: https://www.saucedemo.com
          API_BASE_URL: https://jsonplaceholder.typicode.com
          DB_HOST: localhost
          DB_PORT: 5432
          DB_NAME: test_db
          DB_USER: postgres
          DB_PASSWORD: postgres
          HEADLESS: "true"
        run: |
          pytest tests/${{ matrix.test-suite }} \
            -v \
            --alluredir=allure-results-${{ matrix.test-suite }} \
            --clean-alluredir

      - name: 📊 Генерация Allure-отчёта
        if: always()
        uses: simple-elf/allure-report-action@v1.9
        with:
          allure_results: allure-results-${{ matrix.test-suite }}
          allure_history: allure-history
          allure_report: allure-report-${{ matrix.test-suite }}
          keep_reports: 20

      - name: 🚀 Публикация отчёта на GitHub Pages
        if: always() && github.ref == 'refs/heads/main'
        uses: peaceiris/actions-gh-pages@v4
        with:
          personal_token: ${{ secrets.GITHUB_TOKEN }}
          deploy_dir: allure-history

      - name: 💀 Уведомление в Slack при падении
        if: failure()
        uses: rtCamp/action-slack-notify@v2
        env:
          SLACK_WEBHOOK: ${{ secrets.SLACK_WEBHOOK }}
          SLACK_MESSAGE: "Тесты ${{ matrix.test-suite }} упали! ${{ github.server_url }}/${{ github.repository }}/actions/runs/${{ github.run_id }}"
```

### 7.2 Кэширование и оптимизация

- **Кэш pip** — по `hashFiles('requirements.txt')`.
- **Кэш браузеров Playwright** — через `actions/cache` на `~/.cache/ms-playwright`.
- **Матричный запуск** — UI/API/integration гоняются параллельно в 3 job'ах.

### 7.3 Бейдж статуса в README

```markdown
![CI](https://github.com/<USER>/<REPO>/actions/workflows/ci.yml/badge.svg)
```

### ✅ Контрольные вопросы (Этап 7)

1. Зачем `if: always()` на шагах генерации отчёта?
2. В чём разница между `secrets.GITHUB_TOKEN` и созданным вручную `PAT`?
3. Почему `fail-fast: false` в матрице — полезно для тестов?
4. Зачем отдельная ветка `gh-pages` для истории Allure?
5. Как сделать так, чтобы ночной прогон шёл только по `develop`, а не по PR?

### 📝 Задания для самостоятельной работы (Этап 7)

- [ ] Добавить шаг линтера (`flake8`) и проверки типов (`mypy`) до запуска тестов.
- [ ] Настроить отправку Allure-ссылки в PR-комментарий через `actions/github-script`.

---

## 💡 Best Practices

### ✅ Делай

- **Один тест — одна проверка** (атомарность). Если тест проверяет и вход, и корзину, и оформление — разбей его.
- **Имена тестов описывают поведение**: `test_locked_user_cannot_login`, а не `test_login_3`.
- **Arrange-Act-Assert** структура: подготовка → действие → проверка.
- **Фикстуры для предусловий**, не для проверок. Фикстура `logged_in_page` = подготовка.
- **Параметризация** для однотипных проверок вместо копирования тестов.
- **Маркеры** для фильтрации: `@pytest.mark.smoke`, `@pytest.mark.api`.
- **Изоляция данных**: каждый тест должен работать со своими данными и чистить за собой.
- **Stable locators**: предпочитай `data-test`, `role`, `text` — не хрупкие XPath.
- **Явные ожидания** вместо `time.sleep()`.

### ❌ Избегай

- **`time.sleep()`** — главный источник «флаки». Используй `expect(locator).to_be_visible()`.
- **Хардкод URL/кредов** в тестах → только через `Config`/`.env`.
- **Зависимости между тестами**: тест Б не должен зависеть от того, что тест А прошёл.
- **Проверка нескольких независимых вещей** в одном `assert`.
- **Локаторы по классам/CSS-структуре**, которые часто меняются (`div > div:nth-child(2)`).
- **Мутация глобального состояния** (БД) без отката.
- **Игнорирование флаки-тестов** — помечай `@pytest.mark.flaky` и разбирайся.

---

## 🔧 Фикстуры с разными scope

```python
import pytest


# scope="function" (по умолчанию) — создается перед КАЖДЫМ тестом, уничтожается после.
@pytest.fixture
def db_transaction():
    print("\n[function] Начало транзакции")
    yield "tx"
    print("\n[function] Откат транзакции")


# scope="class" — один раз на весь класс тестов.
@pytest.fixture(scope="class")
def api_token():
    print("\n[class] Получение токена")
    return "Bearer super-secret"


# scope="module" — один раз на весь .py файл.
@pytest.fixture(scope="module")
def module_data():
    print("\n[module] Загрузка тяжёлых данных")
    return {"big": "dataset"}


# scope="session" — один раз на весь прогон pytest.
@pytest.fixture(scope="session")
def db_connection():
    print("\n[session] Подключение к БД")
    conn = {"connection": "open"}
    yield conn
    print("\n[session] Закрытие подключения БД")
    conn["connection"] = "closed"


# autouse=True — запускается автоматически для всех тестов.
@pytest.fixture(autouse=True)
def reset_state():
    print("\n[autouse] Сброс состояния перед тестом")
    yield
    print("\n[autouse] Очистка после теста")


class TestScopes:
    def test_a(self, db_transaction, api_token):
        assert api_token == "Bearer super-secret"

    def test_b(self, db_transaction):
        assert db_transaction == "tx"
```

**Сводка scope:**

| Scope | Когда создаётся | Когда уничтожается | Типичный use-case |
|---|---|---|---|
| `function` | Перед каждым тестом | После каждого теста | Страница браузера, транзакция БД |
| `class` | Перед первым тестом класса | После последнего теста класса | Токен авторизации для группы тестов |
| `module` | Перед первым тестом в файле | После последнего теста в файле | Тяжёлые данные, общие для файла |
| `session` | Один раз за прогон pytest | В конце прогона | Подключение к БД, запуск браузера |

---

## ⏳ Ожидания в Playwright

Playwright **по умолчанию использует автоожидание** (auto-waiting) — перед действием с локатором он ждёт, пока элемент станет actionable. Дополнительные явные проверки — через `expect()`.

### Неявные ожидания (auto-waiting)

При вызове `.click()`, `.fill()`, `.hover()` Playwright сам ждёт:
- элемент присутствует в DOM
- виден
- не перекрыт
- включён (enabled)

```python
# Эти действия автоматически ждут готовности элемента
page.locator("#login-button").click()       # подождёт кликабельности
page.locator("#user-name").fill("user")     # подождёт возможности ввода
```

### Явные ожидания (expect)

```python
from playwright.sync_api import expect

# Видимость
expect(page.locator(".error")).to_be_visible()

# Текст
expect(page.locator("h3")).to_have_text("Products")

# Количество элементов
expect(page.locator(".inventory_item")).to_have_count(6)

# URL
expect(page).to_have_url("https://www.saucedemo.com/inventory.html")
expect(page).to_have_url(lambda url: "inventory" in url)

# Атрибут
expect(page.locator("#login-button")).to_have_attribute("value", "Login")

# Состояние чекбокса
expect(page.locator("#checkbox")).to_be_checked()

# Не существует / скрыт
expect(page.locator(".removed-item")).to_have_count(0)
expect(page.locator(".modal")).to_be_hidden()
```

### Кастомные ожидания

```python
# Ждать появления с таймаутом (мс)
page.wait_for_selector(".loaded", timeout=10000)

# Ждать состояние сети idle
page.wait_for_load_state("networkidle")

# Ждать определённый запрос
page.wait_for_response("**/api/users")

# Ждать функцию-предикат
page.wait_for_function("document.title === 'Products'")
```

### ⚠️ Никогда так

```python
# ❌ Плохо — хардкод задержки
import time
time.sleep(3)

# ✅ Хорошо — умное ожидание
expect(page.locator("#loaded")).to_be_visible(timeout=10000)
```

**Сравнение с Selenide (ваш Java-стек):**

| Playwright | Selenide | Описание |
|---|---|---|
| `expect(loc).to_be_visible()` | `loc.shouldBe(visible)` | Явное ожидание видимости |
| `loc.click()` (auto-wait) | `loc.click()` (auto-wait) | Клик с автоожиданием |
| `page.wait_for_selector()` | `$(loc).should(appear)` | Ожидание появления |
| `expect(page).to_have_url()` | `webdriver().shouldHave(url())` | Проверка URL |

---

## 📸 Автоматические скриншоты при падении

### Вариант 1: Хук в `conftest.py` (рекомендуемый)

```python
import pytest
import allure


@pytest.hookimpl(hookwrapper=True, tryfirst=True)
def pytest_runtest_makereport(item, call):
    outcome = yield
    report = outcome.get_result()

    if report.when == "call" and report.failed:
        # Скриншот если есть page-фикстура
        page = item.funcargs.get("page")
        if page is not None:
            allure.attach(
                page.screenshot(full_page=True),
                name="screenshot-on-failure",
                attachment_type=allure.attachment_type.PNG,
            )
            allure.attach(
                page.content(),
                name="html-on-failure",
                attachment_type=allure.attachment_type.HTML,
            )
            # Сохранить инфо о странице
            allure.attach(
                f"URL: {page.url}\nTitle: {page.title()}",
                name="page-info",
                attachment_type=allure.attachment_type.TEXT,
            )
```

### Вариант 2: Playwright trace (для глубокой отладки)

```python
# в фикстуре browser_context
context = browser.new_context(
    trace="on-all-retries",   # сохранять trace при ретраях
    record_video_dir="test-results/videos/",
)
```

Просмотр trace:
```bash
playwright show-trace trace.zip
```

---

## ⚡ Параллельный запуск (pytest-xdist)

### Установка

```bash
pip install pytest-xdist
```

### Команды запуска

```bash
# Авто: по числу ядер CPU
pytest -n auto

# Явно: 4 воркера
pytest -n 4

# Распределение по тест-файлам (рекомендуется для UI)
pytest -n auto --dist=loadfile

# Распределение по тест-группам (для изоляции БД)
pytest -n auto --dist=loadgroup
```

### Группировка тестов (для общего состояния)

```python
import pytest

# Тесты в одной группе попадут на один воркер
@pytest.mark.xdist_group(name="db-shared")
class TestDbShared:
    def test_one(self, db): ...
    def test_two(self, db): ...
```

### ⚠️ Особенности для UI и БД

- **UI-тесты**: каждый воркер должен иметь свой `browser_context` (фикстура `function` scope обеспечивает это).
- **БД-тесты**: при параллельном запуске возможны конфликты. Решения:
  - Использовать транзакции с откатом (savepoints).
  - Создавать отдельную схему/БД на воркер: `DB_SCHEMA=test_worker_{worker_id}`.
  - Группировать тесты через `xdist_group`.

```python
# Получить ID воркера (если параллельный запуск)
import os
worker_id = os.environ.get("PYTEST_XDIST_WORKER", "gw0")
```

### Конфигурация для CI

```bash
# В GitHub Actions — ограничить воркеры, чтобы не перегружать
pytest -n 4 --dist=loadfile
```

---

## 🌍 Работа с несколькими окружениями

### Структура `.env`

```bash
# .env.dev
ENV=dev
UI_BASE_URL=https://www.saucedemo.com
API_BASE_URL=https://jsonplaceholder.typicode.com
DB_HOST=localhost
DB_PORT=5432

# .env.staging
ENV=staging
UI_BASE_URL=https://staging.saucedemo.com
API_BASE_URL=https://staging-api.example.com
DB_HOST=staging-db.internal
DB_PORT=5432

# .env.prod (read-only: только GET)
ENV=prod
UI_BASE_URL=https://www.saucedemo.com
API_BASE_URL=https://jsonplaceholder.typicode.com
READ_ONLY=true
```

### `utils/config.py`

```python
import os
from dotenv import load_dotenv


class Config:
    """Конфигурация приложения, читаемая из .env."""

    def __init__(self) -> None:
        env = os.getenv("ENV", "dev")
        load_dotenv(f".env.{env}")
        load_dotenv(override=True)  # .env перекрывает

        self.ENV: str = env
        self.UI_BASE_URL: str = os.getenv("UI_BASE_URL")
        self.API_BASE_URL: str = os.getenv("API_BASE_URL")

        self.DB_HOST: str = os.getenv("DB_HOST", "localhost")
        self.DB_PORT: int = int(os.getenv("DB_PORT", "5432"))
        self.DB_NAME: str = os.getenv("DB_NAME", "test_db")
        self.DB_USER: str = os.getenv("DB_USER", "postgres")
        self.DB_PASSWORD: str = os.getenv("DB_PASSWORD", "postgres")
        self.DB_SCHEMA: str = os.getenv("DB_SCHEMA", "public")

        self.HEADLESS: bool = os.getenv("HEADLESS", "true").lower() == "true"
        self.SLOW_MO: int = int(os.getenv("SLOW_MO", "0"))
        self.READ_ONLY: bool = os.getenv("READ_ONLY", "false").lower() == "true"


# SAUCE_USERS — тестовые пользователи SauceDemo
SAUCE_USERS = {
    "standard": ("standard_user", "secret_sauce"),
    "locked": ("locked_out_user", "secret_sauce"),
    "problem": ("problem_user", "secret_sauce"),
    "glitch": ("performance_glitch_user", "secret_sauce"),
}
```

### Переключение окружения

```bash
# Через переменную окружения
ENV=staging pytest tests/

# В CI (GitHub Actions) — через env в шаге
env:
  ENV: ci
  UI_BASE_URL: https://www.saucedemo.com
```

### Защита от записи в prod

```python
# в conftest.py
import pytest


@pytest.fixture(autouse=True)
def prevent_writes_in_prod(config, request):
    """В prod-окружении блокирует тесты, изменяющие данные."""
    if config.READ_ONLY:
        for marker in request.node.iter_markers():
            if marker.name in ("write", "create", "delete"):
                pytest.skip("Пропуск write-теста в read-only окружении")
```

---

## 🗂️ Хранение тестовых данных

### 1. JSON — `data/test_data.json`

```json
{
  "users": {
    "standard": {"username": "standard_user", "password": "secret_sauce"},
    "locked": {"username": "locked_out_user", "password": "secret_sauce"}
  },
  "products": ["Sauce Labs Backpack", "Sauce Labs Bike Light"],
  "expected_errors": {
    "locked": "Epic sadface: Sorry, this user has been locked out.",
    "empty": "Epic sadface: Username is required"
  }
}
```

### 2. YAML — `data/users.yaml`

```yaml
standard_user:
  username: standard_user
  password: secret_sauce
  expected_items: 6

locked_user:
  username: locked_out_user
  password: secret_sauce
  expected_error: "Epic sadface: Sorry, this user has been locked out."
```

### 3. Excel — `data/products.xlsx`

| name | price | in_stock |
|---|---|---|
| Sauce Labs Backpack | 29.99 | TRUE |
| Sauce Labs Bike Light | 9.99 | TRUE |

### `utils/data_loader.py`

```python
import json
import yaml
from pathlib import Path
from openpyxl import load_workbook

DATA_DIR = Path(__file__).parent.parent / "data"


def load_json(filename: str) -> dict:
    with open(DATA_DIR / filename, "r", encoding="utf-8") as f:
        return json.load(f)


def load_yaml(filename: str) -> dict:
    with open(DATA_DIR / filename, "r", encoding="utf-8") as f:
        return yaml.safe_load(f)


def load_excel(filename: str, sheet: str = "Sheet1") -> list[dict]:
    wb = load_workbook(DATA_DIR / filename, data_only=True)
    ws = wb[sheet]
    rows = list(ws.iter_rows(values_only=True))
    headers = rows[0]
    return [dict(zip(headers, row)) for row in rows[1:]]
```

### Использование в тестах

```python
from utils.data_loader import load_json, load_yaml

def test_with_json_data(login_page, config):
    data = load_json("test_data.json")
    user = data["users"]["standard"]
    login_page.open(config.UI_BASE_URL)
    login_page.login(user["username"], user["password"])

@pytest.mark.parametrize("user_key", ["standard_user", "locked_user"])
def test_with_yaml_data(login_page, config, user_key):
    data = load_yaml("users.yaml")
    user = data[user_key]
    login_page.open(config.UI_BASE_URL)
    login_page.login(user["username"], user["password"])
```

**Когда что использовать:**
- **JSON** — простые данные, конфиги, моки API.
- **YAML** — человекочитаемые данные со сложной структурой.
- **Excel** — когда данные готовят аналитики/QA вручную, без программирования.
- **Faker** — генерация случайных данных (имена, email) для уникальности.

---

## 🏷️ Кастомные маркеры

### Регистрация в `pytest.ini`

```ini
[pytest]
markers =
    smoke: критические smoke-тесты (быстрый прогон)
    regression: полные регрессионные тесты
    ui: UI-тесты (Playwright)
    api: API-тесты (requests)
    db: тесты с работой БД
    integration: интеграционные тесты
    slow: медленные тесты (>5с)
    flaky: нестабильные тесты (требуют разбора)
    write: тесты, изменяющие данные (блокируются в read-only)
```

### Применение

```python
import pytest

@pytest.mark.smoke
@pytest.mark.ui
def test_login_quick(login_page, config):
    login_page.open(config.UI_BASE_URL)
    login_page.login("standard_user", "secret_sauce")

@pytest.mark.regression
@pytest.mark.api
@pytest.mark.slow
def test_full_api_regression(api_client):
    ...

@pytest.mark.flaky
def test_unstable_sometimes_fails():
    ...
```

### Запуск по маркерам

```bash
# Только smoke
pytest -m smoke

# UI, но не slow
pytest -m "ui and not slow"

# API или DB
pytest -m "api or db"

# Все, кроме flaky
pytest -m "not flaky"

# Комбинация
pytest -m "regression and (ui or api) and not slow"
```

### Комбинирование с parametrize

```python
@pytest.mark.smoke
@pytest.mark.parametrize("browser_name", ["chromium", "firefox", "webkit"])
def test_cross_browser(browser_name, config):
    ...
```

### Динамические маркеры (автоматическое добавление)

```python
def pytest_collection_modifyitems(items):
    """Автоматически помечать тесты в папке ui/ маркером ui."""
    for item in items:
        if "tests/ui/" in str(item.fspath):
            item.add_marker(pytest.mark.ui)
        elif "tests/api/" in str(item.fspath):
            item.add_marker(pytest.mark.api)
```

---

## ✅ Итоговый чек-лист знаний

### 📚 Теория

- [ ] Понимание POM и его отличий от процедурного подхода
- [ ] Разница между `scope` фикстур (function/class/module/session)
- [ ] Auto-waiting в Playwright vs явные ожидания
- [ ] HTTP-методы и коды состояния (GET/POST/PUT/DELETE/PATCH, 2xx/4xx/5xx)
- [ ] Pydantic-валидация: `BaseModel`, `Field`, вложенные модели
- [ ] SQLAlchemy 2.0: `text()`, `connect()`, `begin()`, параметризованные запросы
- [ ] Разница между `.env`, `.env.example` и переменными окружения
- [ ] Allure: steps, attachments, categories, environment, history
- [ ] CI/CD: matrix, cache, secrets, artifacts, GitHub Pages

### 🛠️ Практика

- [ ] Развёрнуто окружение (venv, deps, docker, БД)
- [ ] Реализованы 4+ page-объекта (base + 3 страницы)
- [ ] UI-тесты: позитивные, негативные, параметризованные
- [ ] API-клиент с Allure-шагами и Pydantic-валидацией
- [ ] API-тесты: CRUD на 2+ сущностях
- [ ] DatabaseConnection + DBValidator
- [ ] Интеграционный тест UI/БД
- [ ] Автоскриншоты при падении
- [ ] Allure-отчёт с категориями и environment
- [ ] GitHub Actions: matrix, кэш, публикация отчёта
- [ ] Параллельный запуск через xdist

### 🧩 Паттерны и подходы

- [ ] Page Object Model
- [ ] Fixture injection (dependency injection в pytest)
- [ ] Builder / Fluent interface (`return self`)
- [ ] Singleton (через session-scoped фикстуры)
- [ ] Data Provider (parametrize + external data)
- [ ] Strategy (разные окружения через Config)
- [ ] Factory (создание тестовых данных через Faker)

---

## ▶️ Полезные команды

### Запуск тестов

```bash
# Все тесты
pytest

# Только UI
pytest tests/ui -m ui

# Только API
pytest tests/api -m api

# Конкретный файл
pytest tests/ui/test_login.py

# Конкретный тест
pytest tests/ui/test_login.py::TestLogin::test_login_success

# По маркеру
pytest -m "smoke and not slow"

# С подробным выводом
pytest -v -s

# Остановиться на первом падении
pytest -x

# Показать 3 самых медленных теста
pytest --durations=3
```

### Параллельность

```bash
# Авто по числу ядер
pytest -n auto

# 4 воркера, распределение по файлам
pytest -n 4 --dist=loadfile
```

### Playwright

```bash
# Установка браузеров
playwright install

# Запуск с headed-режимом
pytest tests/ui --headed

# Открыть Codegen (генератор локаторов)
playwright codegen https://www.saucedemo.com

# Просмотр trace
playwright show-trace trace.zip
```

### Allure

```bash
# Генерация результатов (если не задано в pytest.ini)
pytest --alluredir=allure-results

# Просмотр отчёта
allure serve allure-results

# Статичный отчёт
allure generate allure-results -o allure-report --clean
allure open allure-report
```

### Линтинг и типы

```bash
# Форматирование
black .
isort .

# Линтинг
flake8 .
pylint pages/ tests/

# Проверка типов
mypy pages/ api/ db/
```

### БД

```bash
# Запуск PostgreSQL
docker compose up -d

# Остановка
docker compose down

# Подключение к БД
docker exec -it test_postgres psql -U postgres -d test_db

# Применить схему
docker exec -i test_postgres psql -U postgres -d test_db < db/schema.sql
```

---

## 📚 Ресурсы для изучения

### 🐍 Python

- [Официальная документация Python](https://docs.python.org/3/)
- [Real Python](https://realpython.com/) — практические статьи
- [Python Type Hints (mypy)](https://mypy.readthedocs.io/)

### 🎭 Playwright

- [Официальная документация Playwright Python](https://playwright.dev/python/)
- [Локаторы Playwright](https://playwright.dev/python/docs/locators)

### 🧪 Pytest

- [Официальная документация pytest](https://docs.pytest.org/)
- [Pytest Fixtures (продвинутые)](https://docs.pytest.org/en/stable/how-to/fixtures.html)
- [pytest-xdist](https://pytest-xdist.readthedocs.io/)

### 🌐 API / Requests / Pydantic

- [Requests Documentation](https://docs.python-requests.org/)
- [Pydantic v2 Docs](https://docs.pydantic.dev/2.0/)
- [JSONPlaceholder](https://jsonplaceholder.typicode.com/)

### 🗄️ БД / SQLAlchemy

- [SQLAlchemy 2.0 Documentation](https://docs.sqlalchemy.org/en/20/)
- [PostgreSQL Tutorial](https://www.postgresqltutorial.com/)

### ✅ Allure

- [Allure Framework](https://allurereport.org/)
- [allure-pytest](https://pypi.org/project/allure-pytest/)

### 🚀 CI/CD

- [GitHub Actions Documentation](https://docs.github.com/actions)
- [Allure Report Action](https://github.com/marketplace/actions/allure-report-action)

### 📖 Книги

- **"Python Testing with pytest"** — Brian Okken
- **"Testing with Playwright"** — официальные гайды
- **"API Testing with Python"** — статьи на RealPython

---

> 🎯 **Совет**: двигайся строго по этапам. Не переходи к следующему, пока не закрыл все контрольные вопросы и не выполнил задание для самостоятельной работы. Используй AI-ассистента для разбора непонятных моментов, но код пиши сам — это закрепит навык.
