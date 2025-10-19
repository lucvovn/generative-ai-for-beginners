<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-17T23:02:51+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "ru"
}
-->
# Начало работы с этим курсом

Мы очень рады, что вы начинаете этот курс, и с нетерпением ждем, что вы вдохновитесь на создание чего-то удивительного с помощью генеративного ИИ!

Чтобы обеспечить ваш успех, на этой странице описаны шаги настройки, технические требования и информация о том, где можно получить помощь, если это необходимо.

## Шаги настройки

Чтобы начать прохождение курса, вам нужно выполнить следующие шаги.

### 1. Форкните этот репозиторий

[Сделайте форк этого репозитория](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) в свой аккаунт GitHub, чтобы иметь возможность изменять код и выполнять задания. Вы также можете [добавить звезду (🌟) этому репозиторию](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst), чтобы легче находить его и связанные репозитории.

### 2. Создайте Codespace

Чтобы избежать проблем с зависимостями при запуске кода, мы рекомендуем проходить этот курс в [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst).

В вашем форке: **Code -> Codespaces -> New on main**

![Диалоговое окно с кнопками для создания Codespace](../../../00-course-setup/images/who-will-pay.webp)

#### 2.1 Добавьте секрет

1. ⚙️ Значок шестеренки -> Command Palette -> Codespaces : Manage user secret -> Add a new secret.
2. Назовите его OPENAI_API_KEY, вставьте ваш ключ, сохраните.

### 3. Что дальше?

| Я хочу…             | Перейти к…                                                              |
|---------------------|-------------------------------------------------------------------------|
| Начать урок 1       | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)     |
| Работать офлайн     | [`setup-local.md`](02-setup-local.md)                                   |
| Настроить провайдера LLM | [`providers.md`](03-providers.md)                                        |
| Познакомиться с другими участниками | [Присоединиться к нашему Discord](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)   |

## Устранение неполадок

| Симптом                                   | Решение                                                         |
|-------------------------------------------|-----------------------------------------------------------------|
| Сборка контейнера занимает > 10 минут     | **Codespaces ➜ “Rebuild Container”**                            |
| `python: command not found`               | Терминал не подключен; нажмите **+** ➜ *bash*                   |
| `401 Unauthorized` от OpenAI              | Неверный / истекший `OPENAI_API_KEY`                            |
| VS Code показывает “Dev container mounting…” | Обновите вкладку браузера — иногда Codespaces теряет соединение |
| Отсутствует ядро для ноутбука             | Меню ноутбука ➜ **Kernel ▸ Select Kernel ▸ Python 3**           |

   Unix-подобные системы:

   ```bash
   touch .env
   ```

   Windows:

   ```cmd
   echo . > .env
   ```

3. **Отредактируйте файл `.env`**: Откройте файл `.env` в текстовом редакторе (например, VS Code, Notepad++ или любом другом). Добавьте следующую строку в файл, заменив `your_github_token_here` на ваш реальный токен GitHub:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```

4. **Сохраните файл**: Сохраните изменения и закройте текстовый редактор.

5. **Установите `python-dotenv`**: Если вы еще этого не сделали, вам нужно установить пакет `python-dotenv`, чтобы загружать переменные окружения из файла `.env` в ваше Python-приложение. Вы можете установить его с помощью `pip`:

   ```bash
   pip install python-dotenv
   ```

6. **Загрузите переменные окружения в ваш Python-скрипт**: В вашем Python-скрипте используйте пакет `python-dotenv`, чтобы загрузить переменные окружения из файла `.env`:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```

Готово! Вы успешно создали файл `.env`, добавили ваш GitHub-токен и загрузили его в ваше Python-приложение.

## Как запустить локально на вашем компьютере

Чтобы запустить код локально на вашем компьютере, вам нужно установить какую-либо версию [Python](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst).

Затем, чтобы использовать репозиторий, вам нужно его клонировать:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

После того как вы все скачаете, можно начинать!

## Дополнительные шаги

### Установка Miniconda

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) — это легкий установщик для установки [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python, а также некоторых пакетов.
Conda — это менеджер пакетов, который упрощает настройку и переключение между различными [**виртуальными окружениями**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) Python и пакетами. Он также полезен для установки пакетов, недоступных через `pip`.

Вы можете следовать [руководству по установке MiniConda](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst), чтобы настроить его.

После установки Miniconda вам нужно клонировать [репозиторий](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) (если вы еще этого не сделали).

Далее вам нужно создать виртуальное окружение. Чтобы сделать это с помощью Conda, создайте новый файл окружения (_environment.yml_). Если вы работаете в Codespaces, создайте его в директории `.devcontainer`, то есть `.devcontainer/environment.yml`.

Заполните ваш файл окружения следующим фрагментом:

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

Если вы столкнулись с ошибками при использовании Conda, вы можете вручную установить библиотеки Microsoft AI, используя следующую команду в терминале.

```
conda install -c microsoft azure-ai-ml
```

Файл окружения указывает необходимые зависимости. `<environment-name>` — это имя, которое вы хотите использовать для вашего окружения Conda, а `<python-version>` — версия Python, которую вы хотите использовать, например, `3` — последняя основная версия Python.

После этого вы можете создать окружение Conda, выполнив команды ниже в командной строке/терминале:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

Обратитесь к [руководству по окружениям Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst), если столкнетесь с проблемами.

### Использование Visual Studio Code с расширением поддержки Python

Мы рекомендуем использовать редактор [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) с установленным [расширением поддержки Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) для этого курса. Однако это скорее рекомендация, чем обязательное требование.

> **Примечание**: Открыв репозиторий курса в VS Code, у вас будет возможность настроить проект в контейнере. Это возможно благодаря специальной директории [`.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst), находящейся в репозитории курса. Подробнее об этом позже.

> **Примечание**: После клонирования и открытия директории в VS Code, программа автоматически предложит установить расширение поддержки Python.

> **Примечание**: Если VS Code предложит открыть репозиторий в контейнере, отклоните это предложение, чтобы использовать локально установленную версию Python.

### Использование Jupyter в браузере

Вы также можете работать над проектом, используя [среду Jupyter](https://jupyter.org?WT.mc_id=academic-105485-koreyst) прямо в вашем браузере. Как классический Jupyter, так и [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) предоставляют удобную среду разработки с такими функциями, как автодополнение, подсветка кода и т.д.

Чтобы запустить Jupyter локально, откройте терминал/командную строку, перейдите в директорию курса и выполните:

```bash
jupyter notebook
```

или

```bash
jupyterhub
```

Это запустит экземпляр Jupyter, и URL для доступа к нему будет показан в окне командной строки.

После доступа к URL вы увидите структуру курса и сможете перейти к любому файлу `*.ipynb`. Например, `08-building-search-applications/python/oai-solution.ipynb`.

### Запуск в контейнере

Альтернативой настройке всего на вашем компьютере или в Codespace является использование [контейнера](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>). Специальная папка `.devcontainer` в репозитории курса позволяет VS Code настроить проект в контейнере. Вне Codespaces это потребует установки Docker, и, честно говоря, это требует немного усилий, поэтому мы рекомендуем этот способ только тем, кто имеет опыт работы с контейнерами.

Один из лучших способов сохранить ваши API-ключи в безопасности при использовании GitHub Codespaces — это использование секретов Codespace. Пожалуйста, следуйте [руководству по управлению секретами Codespaces](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst), чтобы узнать больше.

## Уроки и технические требования

Курс включает 6 концептуальных уроков и 6 уроков по программированию.

Для уроков по программированию мы используем Azure OpenAI Service. Вам потребуется доступ к Azure OpenAI Service и API-ключ, чтобы запустить этот код. Вы можете подать заявку на доступ, [заполнив эту форму](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst).

Пока ваша заявка находится на рассмотрении, каждый урок по программированию также включает файл `README.md`, где вы можете просмотреть код и результаты.

## Использование Azure OpenAI Service впервые

Если вы впервые работаете с Azure OpenAI Service, пожалуйста, следуйте этому руководству о том, [как создать и развернуть ресурс Azure OpenAI Service.](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst)

## Использование OpenAI API впервые

Если вы впервые работаете с OpenAI API, пожалуйста, следуйте руководству о том, [как создать и использовать интерфейс.](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst)

## Познакомьтесь с другими участниками

Мы создали каналы в нашем официальном [Discord-сервере AI Community](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) для знакомства с другими участниками. Это отличный способ наладить связи с единомышленниками, предпринимателями, разработчиками, студентами и всеми, кто хочет развиваться в области генеративного ИИ.

[![Присоединиться к Discord-каналу](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

Команда проекта также будет на этом Discord-сервере, чтобы помочь участникам.

## Внесите вклад

Этот курс — инициатива с открытым исходным кодом. Если вы видите области для улучшения или проблемы, пожалуйста, создайте [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) или зарегистрируйте [GitHub issue](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst).

Команда проекта будет отслеживать все вклады. Внесение вклада в проекты с открытым исходным кодом — это удивительный способ построить карьеру в области генеративного ИИ.

Большинство вкладов требуют, чтобы вы согласились с Contributor License Agreement (CLA), заявляя, что у вас есть право и вы действительно предоставляете нам права на использование вашего вклада. Для получения подробной информации посетите [веб-сайт CLA, Contributor License Agreement](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst).

Важно: при переводе текста в этом репозитории, пожалуйста, убедитесь, что вы не используете машинный перевод. Мы будем проверять переводы через сообщество, поэтому, пожалуйста, участвуйте в переводах только на те языки, которыми вы владеете.

Когда вы отправляете pull request, CLA-бот автоматически определяет, нужно ли вам предоставить CLA, и добавляет соответствующую метку или комментарий к PR. Просто следуйте инструкциям, предоставленным ботом. Вам нужно будет сделать это только один раз для всех репозиториев, использующих наш CLA.

Этот проект принял [Кодекс поведения Microsoft Open Source](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst). Для получения дополнительной информации прочитайте FAQ по Кодексу поведения или свяжитесь с [Email opencode](opencode@microsoft.com) с любыми дополнительными вопросами или комментариями.

## Давайте начнем
Теперь, когда вы завершили необходимые шаги для прохождения этого курса, давайте начнем с [введения в генеративный ИИ и LLM](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst).

---

**Отказ от ответственности**:  
Этот документ был переведен с использованием сервиса автоматического перевода [Co-op Translator](https://github.com/Azure/co-op-translator). Хотя мы стремимся к точности, пожалуйста, учитывайте, что автоматические переводы могут содержать ошибки или неточности. Оригинальный документ на его родном языке следует считать авторитетным источником. Для получения критически важной информации рекомендуется профессиональный перевод человеком. Мы не несем ответственности за любые недоразумения или неправильные интерпретации, возникающие в результате использования данного перевода.