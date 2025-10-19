<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-18T02:13:30+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "uk"
}
-->
# Початок роботи з цим курсом

Ми дуже раді, що ви починаєте цей курс, і з нетерпінням чекаємо, що надихне вас створювати за допомогою Генеративного Штучного Інтелекту!

Щоб забезпечити ваш успіх, ця сторінка містить кроки налаштування, технічні вимоги та інформацію про те, де отримати допомогу, якщо це необхідно.

## Кроки налаштування

Щоб розпочати проходження цього курсу, вам потрібно виконати наступні кроки.

### 1. Форкніть цей репозиторій

[Форкніть цей репозиторій](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) у свій обліковий запис GitHub, щоб мати можливість змінювати будь-який код і виконувати завдання. Ви також можете [додати зірочку (🌟) цьому репозиторію](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst), щоб легше знаходити його та пов’язані репозиторії.

### 2. Створіть Codespace

Щоб уникнути проблем із залежностями під час запуску коду, ми рекомендуємо проходити цей курс у [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst).

У вашому форку: **Code -> Codespaces -> New on main**

![Діалогове вікно з кнопками для створення Codespace](../../../00-course-setup/images/who-will-pay.webp)

#### 2.1 Додайте секрет

1. ⚙️ Іконка шестерні -> Command Pallete -> Codespaces : Manage user secret -> Add a new secret.
2. Назвіть OPENAI_API_KEY, вставте ваш ключ, Збережіть.

### 3. Що далі?

| Я хочу…             | Перейти до…                                                             |
|---------------------|-------------------------------------------------------------------------|
| Почати урок 1       | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)     |
| Працювати офлайн    | [`setup-local.md`](02-setup-local.md)                                   |
| Налаштувати провайдера LLM | [`providers.md`](03-providers.md)                                        |
| Познайомитися з іншими учасниками | [Приєднатися до нашого Discord](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)   |

## Вирішення проблем

| Симптом                                   | Рішення                                                         |
|-------------------------------------------|-----------------------------------------------------------------|
| Збірка контейнера триває більше 10 хвилин | **Codespaces ➜ “Rebuild Container”**                            |
| `python: command not found`               | Термінал не підключився; натисніть **+** ➜ *bash*               |
| `401 Unauthorized` від OpenAI             | Неправильний / прострочений `OPENAI_API_KEY`                    |
| VS Code показує “Dev container mounting…” | Оновіть вкладку браузера — іноді Codespaces втрачає з’єднання   |
| Відсутнє ядро для ноутбука                | Меню ноутбука ➜ **Kernel ▸ Select Kernel ▸ Python 3**           |

   Unix-подібні системи:

   ```bash
   touch .env
   ```

   Windows:

   ```cmd
   echo . > .env
   ```

3. **Редагуйте файл `.env`**: Відкрийте файл `.env` у текстовому редакторі (наприклад, VS Code, Notepad++ або будь-якому іншому редакторі). Додайте наступний рядок до файлу, замінивши `your_github_token_here` на ваш фактичний токен GitHub:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```

4. **Збережіть файл**: Збережіть зміни та закрийте текстовий редактор.

5. **Встановіть `python-dotenv`**: Якщо ви ще цього не зробили, вам потрібно встановити пакет `python-dotenv`, щоб завантажити змінні середовища з файлу `.env` у ваш додаток Python. Ви можете встановити його за допомогою `pip`:

   ```bash
   pip install python-dotenv
   ```

6. **Завантажте змінні середовища у вашому Python-скрипті**: У вашому Python-скрипті використовуйте пакет `python-dotenv`, щоб завантажити змінні середовища з файлу `.env`:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```

Ось і все! Ви успішно створили файл `.env`, додали ваш GitHub токен і завантажили його у ваш Python-додаток.

## Як запустити локально на вашому комп'ютері

Щоб запустити код локально на вашому комп'ютері, вам потрібно мати встановлену якусь версію [Python](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst).

Щоб використовувати репозиторій, вам потрібно його клонувати:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

Як тільки ви все завантажите, можете починати!

## Додаткові кроки

### Встановлення Miniconda

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) — це легкий інсталятор для встановлення [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python, а також кількох пакетів.
Conda — це менеджер пакетів, який полегшує налаштування та перемикання між різними Python [**віртуальними середовищами**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) і пакетами. Він також зручний для встановлення пакетів, які недоступні через `pip`.

Ви можете скористатися [інструкцією з встановлення MiniConda](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst), щоб налаштувати його.

Після встановлення Miniconda вам потрібно клонувати [репозиторій](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) (якщо ви ще цього не зробили).

Далі вам потрібно створити віртуальне середовище. Щоб зробити це за допомогою Conda, створіть новий файл середовища (_environment.yml_). Якщо ви працюєте в Codespaces, створіть цей файл у каталозі `.devcontainer`, тобто `.devcontainer/environment.yml`.

Заповніть ваш файл середовища наступним фрагментом:

```yml
name: <environment-name>
channels:
  - defaults
  - microsoft
dependencies:
  - python=<python-version>
  - openai
  - python-dotenv
  - pip
  - pip:
      - azure-ai-ml
```

Якщо ви отримуєте помилки при використанні conda, ви можете вручну встановити бібліотеки Microsoft AI за допомогою наступної команди в терміналі.

```
conda install -c microsoft azure-ai-ml
```

Файл середовища визначає необхідні залежності. `<environment-name>` відноситься до назви, яку ви хочете використовувати для вашого середовища Conda, а `<python-version>` — це версія Python, яку ви хочете використовувати, наприклад, `3` — остання основна версія Python.

Після цього ви можете створити своє середовище Conda, виконавши наступні команди в командному рядку/терміналі:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

Зверніться до [довідника з середовищ Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst), якщо у вас виникнуть проблеми.

### Використання Visual Studio Code з розширенням підтримки Python

Ми рекомендуємо використовувати редактор [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) з встановленим [розширенням підтримки Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) для цього курсу. Однак це лише рекомендація, а не обов'язкова вимога.

> **Примітка**: Відкривши репозиторій курсу у VS Code, ви маєте можливість налаштувати проект у контейнері. Це можливо завдяки спеціальному каталогу [`.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst), який знаходиться в репозиторії курсу. Детальніше про це пізніше.

> **Примітка**: Після клонування та відкриття каталогу у VS Code, програма автоматично запропонує вам встановити розширення підтримки Python.

> **Примітка**: Якщо VS Code пропонує вам повторно відкрити репозиторій у контейнері, відхиліть цей запит, щоб використовувати локально встановлену версію Python.

### Використання Jupyter у браузері

Ви також можете працювати над проектом, використовуючи [середовище Jupyter](https://jupyter.org?WT.mc_id=academic-105485-koreyst) прямо у вашому браузері. Як класичний Jupyter, так і [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) забезпечують досить приємне середовище розробки з такими функціями, як автозаповнення, підсвічування коду тощо.

Щоб запустити Jupyter локально, перейдіть до терміналу/командного рядка, перейдіть до каталогу курсу та виконайте:

```bash
jupyter notebook
```

або

```bash
jupyterhub
```

Це запустить екземпляр Jupyter, і URL для доступу до нього буде показаний у вікні командного рядка.

Після доступу до URL ви повинні побачити структуру курсу та зможете перейти до будь-якого файлу `*.ipynb`. Наприклад, `08-building-search-applications/python/oai-solution.ipynb`.

### Запуск у контейнері

Альтернативою налаштуванню всього на вашому комп'ютері або в Codespace є використання [контейнера](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>). Спеціальна папка `.devcontainer` у репозиторії курсу дозволяє VS Code налаштувати проект у контейнері. За межами Codespaces це потребуватиме встановлення Docker, і, чесно кажучи, це вимагає трохи зусиль, тому ми рекомендуємо це лише тим, хто має досвід роботи з контейнерами.

Один із найкращих способів зберегти ваші API-ключі в безпеці під час використання GitHub Codespaces — це використання секретів Codespace. Будь ласка, дотримуйтесь [інструкції з управління секретами Codespaces](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst), щоб дізнатися більше про це.

## Уроки та технічні вимоги

Курс складається з 6 концептуальних уроків і 6 уроків програмування.

Для уроків програмування ми використовуємо службу Azure OpenAI. Вам знадобиться доступ до служби Azure OpenAI та ключ API, щоб запустити цей код. Ви можете подати заявку на доступ, [заповнивши цю форму](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst).

Поки ваша заявка обробляється, кожен урок програмування також містить файл `README.md`, де ви можете переглянути код і результати.

## Використання служби Azure OpenAI вперше

Якщо ви вперше працюєте зі службою Azure OpenAI, будь ласка, дотримуйтесь цієї інструкції, як [створити та розгорнути ресурс служби Azure OpenAI.](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst)

## Використання API OpenAI вперше

Якщо ви вперше працюєте з API OpenAI, будь ласка, дотримуйтесь інструкції, як [створити та використовувати інтерфейс.](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst)

## Познайомтеся з іншими учасниками

Ми створили канали на нашому офіційному [Discord сервері AI Community](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) для знайомства з іншими учасниками. Це чудовий спосіб налагодити зв’язки з іншими підприємцями, розробниками, студентами та всіма, хто хоче розвиватися в Генеративному Штучному Інтелекті.

[![Приєднатися до Discord каналу](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

Команда проекту також буде на цьому Discord сервері, щоб допомогти учасникам.

## Внесок

Цей курс є ініціативою з відкритим кодом. Якщо ви бачите області для покращення або проблеми, будь ласка, створіть [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) або зареєструйте [GitHub issue](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst).

Команда проекту буде відстежувати всі внески. Внесок у відкритий код — це чудовий спосіб побудувати вашу кар’єру в Генеративному Штучному Інтелекті.

Більшість внесків вимагають від вас погодження з Угодою про ліцензію для учасників (CLA), яка підтверджує, що ви маєте право і фактично надаєте нам права на використання вашого внеску. Для деталей відвідайте [веб-сайт CLA, Contributor License Agreement](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst).

Важливо: перекладаючи текст у цьому репозиторії, будь ласка, переконайтеся, що ви не використовуєте машинний переклад. Ми перевіримо переклади через спільноту, тому, будь ласка, беріть участь у перекладах лише мовами, якими ви володієте.

Коли ви надсилаєте pull request, CLA-bot автоматично визначить, чи потрібно вам надати CLA, і відповідно позначить PR (наприклад, міткою, коментарем). Просто дотримуйтесь інструкцій, наданих ботом. Вам потрібно буде зробити це лише один раз для всіх репозиторіїв, які використовують наш CLA.

Цей проект прийняв [Кодекс поведінки Microsoft Open Source](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst). Для отримання додаткової інформації прочитайте FAQ Кодексу поведінки або зв’яжіться з [Email opencode](opencode@microsoft.com) з будь-якими додатковими запитаннями або коментарями.

## Почнемо!
Тепер, коли ви завершили необхідні кроки для проходження цього курсу, давайте розпочнемо з [вступу до Генеративного ШІ та LLM](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst).

---

**Відмова від відповідальності**:  
Цей документ був перекладений за допомогою сервісу автоматичного перекладу [Co-op Translator](https://github.com/Azure/co-op-translator). Хоча ми прагнемо до точності, будь ласка, майте на увазі, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ на його рідній мові слід вважати авторитетним джерелом. Для критичної інформації рекомендується професійний людський переклад. Ми не несемо відповідальності за будь-які непорозуміння або неправильні тлумачення, що виникають внаслідок використання цього перекладу.