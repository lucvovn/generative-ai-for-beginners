<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-18T01:19:21+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "sr"
}
-->
# Почетак курса

Веома смо узбуђени што започињете овај курс и радујемо се да видимо шта ћете инспирисани Генеративном вештачком интелигенцијом створити!

Да бисмо осигурали ваш успех, на овој страници су наведени кораци за подешавање, технички захтеви и где можете добити помоћ ако је потребно.

## Кораци за подешавање

Да бисте започели са овим курсом, потребно је да завршите следеће кораке.

### 1. Форкујте овај репозиторијум

[Форкујте цео репозиторијум](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) на свој GitHub налог како бисте могли да мењате код и завршите изазове. Такође можете [означити овај репозиторијум звездицом (🌟)](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) како бисте га лакше пронашли, као и повезане репозиторијуме.

### 2. Креирајте Codespace

Да бисте избегли проблеме са зависностима приликом покретања кода, препоручујемо да овај курс покренете у [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst).

У вашем форку: **Code -> Codespaces -> New on main**

![Дијалог који приказује дугмад за креирање Codespace-а](../../../00-course-setup/images/who-will-pay.webp)

#### 2.1 Додајте тајну

1. ⚙️ Икона зупчаника -> Command Pallete -> Codespaces : Manage user secret -> Add a new secret.
2. Назовите OPENAI_API_KEY, налепите ваш кључ, Сачувајте.

### 3. Шта је следеће?

| Желим да…           | Идите на…                                                               |
|---------------------|-------------------------------------------------------------------------|
| Започнем лекцију 1  | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)     |
| Радим офлајн        | [`setup-local.md`](02-setup-local.md)                                   |
| Подесим LLM провајдера | [`providers.md`](03-providers.md)                                        |
| Упознам друге учеснике | [Придружите се нашем Discord-у](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)   |

## Решавање проблема

| Симптом                                   | Решавање проблема                                              |
|-------------------------------------------|-----------------------------------------------------------------|
| Изградња контејнера траје > 10 минута     | **Codespaces ➜ “Rebuild Container”**                            |
| `python: command not found`               | Терминал није повезан; кликните **+** ➜ *bash*                  |
| `401 Unauthorized` од OpenAI              | Погрешан / истекао `OPENAI_API_KEY`                             |
| VS Code приказује “Dev container mounting…” | Освежите картицу прегледача—Codespaces понекад губи везу         |
| Недостаје језгро за Notebook              | Мени Notebook ➜ **Kernel ▸ Select Kernel ▸ Python 3**           |

   Unix-базирани системи:

   ```bash
   touch .env
   ```

   Windows:

   ```cmd
   echo . > .env
   ```

3. **Измените `.env` датотеку**: Отворите `.env` датотеку у текст едитору (нпр. VS Code, Notepad++ или било ком другом едитору). Додајте следећи ред у датотеку, замењујући `your_github_token_here` са вашим стварним GitHub токеном:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```

4. **Сачувајте датотеку**: Сачувајте измене и затворите текст едитор.

5. **Инсталирајте `python-dotenv`**: Ако већ нисте, потребно је да инсталирате пакет `python-dotenv` како бисте учитали променљиве окружења из `.env` датотеке у вашу Python апликацију. Можете га инсталирати помоћу `pip`:

   ```bash
   pip install python-dotenv
   ```

6. **Учитајте променљиве окружења у ваш Python скрипт**: У вашем Python скрипту, користите пакет `python-dotenv` за учитавање променљивих окружења из `.env` датотеке:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```

То је то! Успешно сте креирали `.env` датотеку, додали ваш GitHub токен и учитали га у вашу Python апликацију.

## Како покренути локално на вашем рачунару

Да бисте покренули код локално на вашем рачунару, потребно је да имате неку верзију [Python-а инсталирану](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst).

Да бисте користили репозиторијум, потребно је да га клонирате:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

Када све преузмете, можете почети!

## Опциони кораци

### Инсталирање Miniconda

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) је лагани инсталер за инсталирање [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python-а, као и неколико пакета.
Conda је менаџер пакета који олакшава подешавање и пребацивање између различитих Python [**виртуелних окружења**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) и пакета. Такође је користан за инсталирање пакета који нису доступни преко `pip`.

Можете пратити [упутство за инсталацију MiniConda](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst) да бисте га подесили.

Са инсталираним Miniconda, потребно је да клонирате [репозиторијум](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) (ако то већ нисте урадили).

Затим, потребно је да креирате виртуелно окружење. Да бисте то урадили помоћу Conda, креирајте нову датотеку окружења (_environment.yml_). Ако пратите курс користећи Codespaces, креирајте ову датотеку унутар директоријума `.devcontainer`, дакле `.devcontainer/environment.yml`.

Попуните вашу датотеку окружења следећим кодом:

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

Ако наиђете на грешке приликом коришћења conda, можете ручно инсталирати Microsoft AI Libraries користећи следећу команду у терминалу.

```
conda install -c microsoft azure-ai-ml
```

Датотека окружења специфицира потребне зависности. `<environment-name>` се односи на име које желите да користите за ваше Conda окружење, а `<python-version>` је верзија Python-а коју желите да користите, на пример, `3` је најновија главна верзија Python-а.

Када то завршите, можете креирати ваше Conda окружење покретањем следећих команди у командној линији/терминалу:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

Погледајте [упутство за Conda окружења](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst) ако наиђете на било какве проблеме.

### Коришћење Visual Studio Code-а са екстензијом за Python

Препоручујемо коришћење [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) едитора са инсталираном [екстензијом за Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) за овај курс. Међутим, ово је више препорука, а не обавезан услов.

> **Напомена**: Отварањем репозиторијума курса у VS Code-у, имате опцију да подесите пројекат унутар контејнера. Ово је могуће захваљујући [посебном `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) директоријуму који се налази унутар репозиторијума курса. Више о овоме касније.

> **Напомена**: Када клонирате и отворите директоријум у VS Code-у, он ће аутоматски предложити да инсталирате екстензију за Python.

> **Напомена**: Ако вам VS Code предложи да поново отворите репозиторијум у контејнеру, одбијте овај захтев како бисте користили локално инсталирану верзију Python-а.

### Коришћење Jupyter-а у прегледачу

Такође можете радити на пројекту користећи [Jupyter окружење](https://jupyter.org?WT.mc_id=academic-105485-koreyst) директно у вашем прегледачу. Класични Jupyter и [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) пружају веома пријатно окружење за развој са функцијама као што су аутоматско довршавање, истицање кода, итд.

Да бисте покренули Jupyter локално, идите до терминала/командне линије, навигирајте до директоријума курса и извршите:

```bash
jupyter notebook
```

или

```bash
jupyterhub
```

Ово ће покренути Jupyter инстанцу, а URL за приступ ће бити приказан у прозору командне линије.

Када приступите URL-у, требало би да видите преглед курса и да можете да навигирате до било које `*.ipynb` датотеке. На пример, `08-building-search-applications/python/oai-solution.ipynb`.

### Покретање у контејнеру

Алтернатива подешавању свега на вашем рачунару или Codespace-у је коришћење [контејнера](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>). Посебан `.devcontainer` директоријум унутар репозиторијума курса омогућава VS Code-у да подеси пројекат унутар контејнера. Изван Codespaces-а, ово ће захтевати инсталацију Docker-а, и искрено, укључује мало више посла, па ово препоручујемо само онима који имају искуства са радом у контејнерима.

Један од најбољих начина да чувате своје API кључеве безбедним приликом коришћења GitHub Codespaces-а је коришћење тајни Codespace-а. Молимо вас да пратите [упутство за управљање тајнама Codespace-а](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst) да бисте сазнали више о овоме.

## Лекције и технички захтеви

Курс има 6 концептуалних лекција и 6 лекција програмирања.

За лекције програмирања користимо Azure OpenAI Service. Потребан вам је приступ Azure OpenAI сервису и API кључ да бисте покренули овај код. Можете се пријавити за приступ [попуњавањем ове пријаве](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst).

Док чекате да ваша пријава буде обрађена, свака лекција програмирања такође укључује `README.md` датотеку где можете видети код и резултате.

## Први пут коришћење Azure OpenAI сервиса

Ако први пут радите са Azure OpenAI сервисом, молимо вас да пратите ово упутство о томе како [креирати и поставити ресурс Azure OpenAI сервиса.](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst)

## Први пут коришћење OpenAI API-ја

Ако први пут радите са OpenAI API-јем, молимо вас да пратите упутство о томе како [креирати и користити интерфејс.](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst)

## Упознајте друге учеснике

Креирали смо канале на нашем званичном [AI Community Discord серверу](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) за упознавање других учесника. Ово је одличан начин да се повежете са другим предузетницима, програмерима, студентима и свима који желе да унапреде своје знање о Генеративној вештачкој интелигенцији.

[![Придружите се Discord каналу](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

Пројектни тим ће такође бити на овом Discord серверу како би помогао учесницима.

## Допринос

Овај курс је иницијатива отвореног кода. Ако видите области за побољшање или проблеме, молимо вас да креирате [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) или пријавите [GitHub проблем](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst).

Пројектни тим ће пратити све доприносе. Допринос отвореном коду је невероватан начин да изградите своју каријеру у области Генеративне вештачке интелигенције.

Већина доприноса захтева да се сложите са Уговором о лиценци за допринос (CLA) којим изјављујете да имате право и заправо дајете нам права да користимо ваш допринос. За детаље, посетите [CLA, веб-сајт Уговора о лиценци за допринос](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst).

Важно: приликом превођења текста у овом репозиторијуму, молимо вас да не користите машински превод. Проверићемо преводе преко заједнице, па вас молимо да волонтирате за преводе само на језике које добро познајете.

Када пошаљете Pull Request, CLA-бот ће аутоматски утврдити да ли је потребно да доставите CLA и означити PR на одговарајући начин (нпр. етикета, коментар). Само следите упутства која вам бот пружа. Ово ћете морати да урадите само једном за све репозиторијуме који користе наш CLA.

Овај пројекат је усвојио [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst). За више информација прочитајте FAQ о Кодексу понашања или контактирајте [Email opencode](opencode@microsoft.com) за додатна питања или коментаре.

## Хајде да почнемо
Сада када сте завршили потребне кораке за завршетак овог курса, хајде да започнемо упознавањем са [уводом у генеративну вештачку интелигенцију и LLM-ове](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst).

---

**Одрицање од одговорности**:  
Овај документ је преведен помоћу услуге за превођење вештачке интелигенције [Co-op Translator](https://github.com/Azure/co-op-translator). Иако настојимо да обезбедимо тачност, молимо вас да имате у виду да аутоматски преводи могу садржати грешке или нетачности. Оригинални документ на његовом изворном језику треба сматрати ауторитативним извором. За критичне информације препоручује се професионални превод од стране људи. Не преузимамо одговорност за било каква погрешна тумачења или неспоразуме који могу настати услед коришћења овог превода.