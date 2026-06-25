# Server Proxy JB Platinum

[![Version](https://img.shields.io/badge/version-1.0.0.6-blue)](https://github.com/SmartMaster35Rus/server-proxy-jb-platinum/releases)
[![Platform](https://img.shields.io/badge/platform-macOS%2014%2B-blue)](https://github.com/SmartMaster35Rus/server-proxy-jb-platinum)
[![License](https://img.shields.io/badge/license-Proprietary-red)](https://github.com/SmartMaster35Rus/server-proxy-jb-platinum)

**Локальный MITM-прокси сервер с GUI в один клик для Jailbreak и диагностики iOS-устройств.**

Запустил — подключил телефон — видишь весь трафик. Никаких терминалов, конфигов и веб-интерфейсов.

<p align="center">
  <img src="screenshot.png" alt="Server Proxy JB Platinum" width="800"/>
</p>

---

## Что умеет

- **Однокнопочный СТАРТ/СТОП** — без консоли и командной строки
- **Live-таблица трафика** — метод, статус, URL, размер, время запроса
- **Полный MITM-перехват** — HTTP + HTTPS через mitmproxy
- **Portable** — один .app, работает без установки
- **Автоопределение LAN IP** — реальный адрес сети, не VPN-интерфейс
- **Корректная версия macOS** — отображает маркетинговое имя (Sonoma, Ventura и т.д.) + build number
- **Автоочистка логов** — при выходе сервер останавливается, кэш чистится
- **RU / EN / ES** — три языка интерфейса

## Требования

| Что | Детали |
|-----|--------|
| ОС | macOS 14+ (Sonoma, Ventura, Monterey) |
| VPN | Обязательно включить любой рабочий VPN на Mac |
| mitmproxy | Установить: `pip install mitmproxy` или `brew install mitmproxy` |
| Права | Обычный запуск (права администратора не требуются) |

## Скачать

👉 **[Скачать последнюю версию](https://github.com/SmartMaster35Rus/server-proxy-jb-platinum/releases/latest)**

| Файл | Назначение |
|------|-----------|
| `server_proxy_jb_platinum_v1.0.0.6_build*.dmg` | Установщик DMG — перетащи в Applications |

## Установка mitmproxy

Прокси-сервер использует системный `mitmweb`. Перед первым запуском установите его одним из способов:

```bash
# Способ 1: через pip
pip install mitmproxy

# Способ 2: через Homebrew
brew install mitmproxy
```

Проверка установки:
```bash
mitmweb --version
```

## Как пользоваться

### 1. Запуск

1. Открой DMG → перетащи **Server Proxy JB Platinum** в **Applications**
2. Запусти приложение из Launchpad или Finder
3. Включи **VPN** на Mac
4. Нажми **СТАРТ** → подтверди что VPN включен
5. Сервер поднимется за 2-5 секунд

### 2. Настройка телефона

Открой на iPhone/iPad:

```
Настройки → Wi‑Fi → ⓘ у сети → HTTP Proxy → Вручную
```

| Поле | Значение |
|------|----------|
| Сервер | `<LAN IP>` (показан в приложении) |
| Порт | `8080` |

### 3. Установка сертификатов

Открой Safari и перейди по порядку:

1. `http://mitm.it` → iOS → установить сертификат
2. `http://tlsroot.litten.ca` → установить **ISRG Root X1**
3. `http://tlsroot.litten.ca` → установить **ISRG Root X2**

Затем: **Настройки → Основные → Об устройстве → Доверие сертификатов** → включить `mitmproxy`

### 4. Работа

Трафик с устройства появится в таблице справа в реальном времени.

> После завершения отключи HTTP-прокси в настройках Wi‑Fi телефона.

## Скриншоты

| Окно | Описание |
|------|----------|
| ![main](screenshot.png) | Главное окно с трафиком |

## Продвинутое

### Веб-интерфейс mitmweb

Если нужен полный веб-интерфейс mitmweb — открой в браузере:

```
http://127.0.0.1:8081
```

### Dashboard мониторинга

Веб-панель с устройствами и подключениями:

```
http://127.0.0.1:8090
```

### Очистка портов

Если порты 8080/8081 заняты:

```bash
lsof -ti tcp:8080          # найти процесс
kill -9 <PID>              # завершить
```

## FAQ

| Вопрос | Ответ |
|--------|-------|
| Сервер не стартует | Проверь что `mitmweb` установлен (`mitmweb --version`) |
| Нет трафика | Проверь IP и порт в настройках прокси телефона |
| Ошибка сертификата | Удали старый профиль mitmproxy в настройках телефона |
| Не видно HTTPS | Проверь что сертификат mitmproxy установлен и ему доверяют |
| Неправильный LAN IP | Отключи VPN-клиент с virtual-адаптером, используй реальный Wi-Fi IP |

## Технические детали

| Параметр | Значение |
|----------|----------|
| Прокси-порт | 8080 (HTTP/HTTPS) |
| Web-интерфейс | 8081 (mitmweb) |
| Dashboard | 8090 (мониторинг устройств) |
| Сертификат | mitm.it |
| mitmproxy | 12.x (системный) |
| Python | 3.9–3.13 |
| Framework | PyQt6 |

## Лицензия

Proprietary. All rights reserved. © SmartMaster35Rus, 2026.

---

[Сообщить об ошибке](https://github.com/SmartMaster35Rus/server-proxy-jb-platinum/issues) · [Все релизы](https://github.com/SmartMaster35Rus/server-proxy-jb-platinum/releases)
