# Портфоліо

Простий статичний сайт-портфоліо (HTML/CSS, без збірки) для розміщення на GitHub Pages.

## Структура

```
index.html                          — головна сторінка з переліком проєктів
style.css                           — стилі
telegram-worker/worker.js           — Cloudflare Worker: приймає заявку з форми і пересилає в Telegram
telegram-worker/README.md           — інструкція з налаштування Worker'а
cases/ai-reels-creator.html         — кейс: AI Reels Creator
cases/dr-macaron.html               — кейс: Dr. Macaron
cases/englishgo.html                — кейс: EnglishGo
cases/flight-dream.html             — кейс: Flight Dream
cases/sensoryiq.html                — кейс: sensoryIQ (дитячий центр розвитку)
cases/cleaning-service.html         — кейс: клінінгова служба
cases/pip-orchard.html              — кейс: Pip's Orchard (дитячий сайт)
assets/screenshots/                 — скріншоти проєктів
```

## Як опублікувати на GitHub Pages

Архів `portfolio-git-ready.zip` вже містить готовий git-репозиторій (гілка `main`, перший коміт зроблено) — залишилось тільки прив'язати його до GitHub і запушити.

1. Розпакуйте архів і відкрийте термінал у цій папці.
2. Створіть новий **порожній** репозиторій на GitHub (без README, без .gitignore — щоб не було конфліктів), наприклад `portfolio`.
3. Виконайте в терміналі (замініть `ваш-нік` на свій GitHub-нікнейм):
   ```
   git remote add origin https://github.com/ваш-нік/portfolio.git
   git push -u origin main
   ```
4. У репозиторії на GitHub відкрийте **Settings → Pages**.
5. У розділі **Source** оберіть branch `main` і папку `/ (root)`, натисніть **Save**.
6. Через 1-2 хвилини сайт буде доступний за адресою:
   `https://ваш-нік.github.io/portfolio/`

**Якщо немає git на комп'ютері** — простіше через веб-інтерфейс: у порожньому репозиторії GitHub натисніть "uploading an existing file" і перетягніть усі файли з розпакованої папки (окрім `.git`), потім повторіть кроки 4-6.

## Форма «Обговорити проєкт» / «Написати»

На головній сторінці кнопки «Обговорити проєкт» (хіро-блок) і «Написати» (футер) відкривають форму
з полями Ім'я, Телефон (з перевіркою формату) і коментар. Форма надсилає дані на невеликий
Cloudflare Worker, який пересилає заявку в Telegram — повна інструкція в `telegram-worker/README.md`.

**Чому не напряму з сайту:** токен Telegram-бота небезпечно тримати у відкритому коді сайту (його
побачить будь-хто, хто відкриє "Перегляд коду сторінки"). Тому токен зберігається окремо — у
змінних середовища Cloudflare — і ніколи не потрапляє у файли сайту.

**Щоб форма запрацювала, виконайте кроки з `telegram-worker/README.md`** — там детально розписано,
як створити бота через @BotFather, задеплоїти Worker на Cloudflare (безкоштовно) і вставити
отриманий URL `TELEGRAM_ENDPOINT` у `index.html`.

## Що потрібно доробити перед публікацією

- [ ] Виконати налаштування форми з `telegram-worker/README.md` і оновити `TELEGRAM_ENDPOINT` в `index.html`.
- [ ] За бажанням — додати більше проєктів у секцію `.projects` в `index.html` (копіюйте блок `.project-card`).

## Поточні проєкти в портфоліо

1. AI Reels Creator — лендінг AI-контент студії
2. Dr. Macaron — сайт кондитерської
3. EnglishGo — курс англійської
4. Pip's Orchard — інтерактивний сайт для вивчення англійської дітьми
5. Flight Dream — польоти на повітряній кулі
6. sensoryIQ — дитячий центр розвитку
7. Клінінгова служба — прибирання квартир та офісів
