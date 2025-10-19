<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "df027997f1448323d6159b78a1b669bf",
  "translation_date": "2025-10-17T23:02:22+00:00",
  "source_file": "06-text-generation-apps/README.md",
  "language_code": "ru"
}
-->
# Создание приложений для генерации текста

[![Создание приложений для генерации текста](../../../translated_images/06-lesson-banner.a5c629f990a636c852353c5533f1a6a218ece579005e91f96339d508d9cf8f47.ru.png)](https://youtu.be/0Y5Luf5sRQA?si=t_xVg0clnAI4oUFZ)

> _(Нажмите на изображение выше, чтобы посмотреть видео урока)_

В рамках этой программы обучения вы уже познакомились с основными концепциями, такими как подсказки, и даже с целой дисциплиной, называемой "инженерия подсказок". Многие инструменты, с которыми вы можете взаимодействовать, такие как ChatGPT, Office 365, Microsoft Power Platform и другие, позволяют использовать подсказки для выполнения задач.

Чтобы добавить подобный функционал в приложение, вам нужно понять такие концепции, как подсказки, завершения, и выбрать библиотеку для работы. Именно этому вы научитесь в этой главе.

## Введение

В этой главе вы:

- Узнаете о библиотеке openai и её основных концепциях.
- Создадите приложение для генерации текста с использованием openai.
- Поймёте, как использовать такие концепции, как подсказка, температура и токены, чтобы создать приложение для генерации текста.

## Цели обучения

К концу урока вы сможете:

- Объяснить, что такое приложение для генерации текста.
- Создать приложение для генерации текста с использованием openai.
- Настроить приложение для использования большего или меньшего количества токенов, а также изменить температуру для получения разнообразных результатов.

## Что такое приложение для генерации текста?

Обычно, когда вы создаёте приложение, оно имеет какой-то интерфейс, например:

- Командный. Консольные приложения — это типичные приложения, где вы вводите команду, и она выполняет задачу. Например, `git` — это командное приложение.
- Пользовательский интерфейс (UI). Некоторые приложения имеют графический пользовательский интерфейс (GUI), где вы нажимаете кнопки, вводите текст, выбираете опции и многое другое.

### Ограничения консольных и UI приложений

Сравните это с командным приложением, где вы вводите команду:

- **Ограничения**. Вы не можете просто ввести любую команду, только те, которые поддерживает приложение.
- **Языковая специфика**. Некоторые приложения поддерживают множество языков, но по умолчанию приложение создаётся для конкретного языка, даже если можно добавить поддержку других языков.

### Преимущества приложений для генерации текста

Чем же приложение для генерации текста отличается?

В приложении для генерации текста у вас больше гибкости, вы не ограничены набором команд или конкретным языком ввода. Вместо этого вы можете использовать естественный язык для взаимодействия с приложением. Ещё одно преимущество — вы уже взаимодействуете с источником данных, который обучен на огромном корпусе информации, тогда как традиционное приложение может быть ограничено данными в базе.

### Что можно создать с помощью приложения для генерации текста?

Есть множество вещей, которые можно создать. Например:

- **Чат-бот**. Чат-бот, отвечающий на вопросы по темам, таким как ваша компания и её продукты, может быть хорошим вариантом.
- **Помощник**. LLMs отлично справляются с задачами, такими как резюмирование текста, получение инсайтов из текста, создание текстов, например, резюме, и многое другое.
- **Ассистент по программированию**. В зависимости от используемой языковой модели, вы можете создать ассистента по программированию, который поможет вам писать код. Например, вы можете использовать продукт, такой как GitHub Copilot, а также ChatGPT для помощи в написании кода.

## Как начать?

Вам нужно найти способ интеграции с LLM, что обычно включает два подхода:

- Использовать API. Здесь вы создаёте веб-запросы с вашей подсказкой и получаете сгенерированный текст.
- Использовать библиотеку. Библиотеки помогают инкапсулировать вызовы API и делают их проще в использовании.

## Библиотеки/SDK

Существует несколько известных библиотек для работы с LLM, таких как:

- **openai**, эта библиотека упрощает подключение к вашей модели и отправку подсказок.

Также есть библиотеки, работающие на более высоком уровне, например:

- **Langchain**. Langchain хорошо известен и поддерживает Python.
- **Semantic Kernel**. Semantic Kernel — это библиотека от Microsoft, поддерживающая языки C#, Python и Java.

## Первое приложение с использованием openai

Давайте посмотрим, как мы можем создать наше первое приложение, какие библиотеки нам нужны, сколько потребуется и так далее.

### Установка openai

Существует множество библиотек для взаимодействия с OpenAI или Azure OpenAI. Можно использовать различные языки программирования, такие как C#, Python, JavaScript, Java и другие. Мы выбрали библиотеку `openai` для Python, поэтому будем использовать `pip` для её установки.

```bash
pip install openai
```

### Создание ресурса

Вам нужно выполнить следующие шаги:

- Создать аккаунт на Azure [https://azure.microsoft.com/free/](https://azure.microsoft.com/free/?WT.mc_id=academic-105485-koreyst).
- Получить доступ к Azure OpenAI. Перейдите по ссылке [https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai](https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai?WT.mc_id=academic-105485-koreyst) и запросите доступ.

  > [!NOTE]
  > На момент написания требуется подать заявку на доступ к Azure OpenAI.

- Установить Python <https://www.python.org/>
- Создать ресурс Azure OpenAI Service. Ознакомьтесь с этим руководством о том, как [создать ресурс](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal?WT.mc_id=academic-105485-koreyst).

### Найти ключ API и конечную точку

На этом этапе вам нужно указать библиотеке `openai`, какой ключ API использовать. Чтобы найти ваш ключ API, перейдите в раздел "Keys and Endpoint" вашего ресурса Azure OpenAI и скопируйте значение "Key 1".

![Раздел Keys and Endpoint в Azure Portal](https://learn.microsoft.com/azure/ai-services/openai/media/quickstarts/endpoint.png?WT.mc_id=academic-105485-koreyst)

Теперь, когда у вас есть эта информация, давайте настроим библиотеки для её использования.

> [!NOTE]
> Стоит отделить ваш ключ API от кода. Вы можете сделать это, используя переменные окружения.
>
> - Установите переменную окружения `OPENAI_API_KEY` в значение вашего ключа API.
>   `export OPENAI_API_KEY='sk-...'`

### Настройка конфигурации Azure

Если вы используете Azure OpenAI, вот как настроить конфигурацию:

```python
openai.api_type = 'azure'
openai.api_key = os.environ["OPENAI_API_KEY"]
openai.api_version = '2023-05-15'
openai.api_base = os.getenv("API_BASE")
```

Здесь мы устанавливаем следующее:

- `api_type` в значение `azure`. Это указывает библиотеке использовать Azure OpenAI, а не OpenAI.
- `api_key`, это ваш ключ API, найденный в Azure Portal.
- `api_version`, это версия API, которую вы хотите использовать. На момент написания последняя версия — `2023-05-15`.
- `api_base`, это конечная точка API. Вы можете найти её в Azure Portal рядом с вашим ключом API.

> [!NOTE] > `os.getenv` — это функция, которая считывает переменные окружения. Вы можете использовать её для чтения переменных окружения, таких как `OPENAI_API_KEY` и `API_BASE`. Установите эти переменные окружения в вашем терминале или с помощью библиотеки, такой как `dotenv`.

## Генерация текста

Для генерации текста используется класс `Completion`. Вот пример:

```python
prompt = "Complete the following: Once upon a time there was a"

completion = openai.Completion.create(model="davinci-002", prompt=prompt)
print(completion.choices[0].text)
```

В приведённом выше коде мы создаём объект завершения и передаём модель, которую хотим использовать, и подсказку. Затем мы выводим сгенерированный текст.

### Завершения для чата

До сих пор вы видели, как мы использовали `Completion` для генерации текста. Но есть другой класс, называемый `ChatCompletion`, который больше подходит для чат-ботов. Вот пример его использования:

```python
import openai

openai.api_key = "sk-..."

completion = openai.ChatCompletion.create(model="gpt-3.5-turbo", messages=[{"role": "user", "content": "Hello world"}])
print(completion.choices[0].message.content)
```

Подробнее об этой функциональности в следующей главе.

## Упражнение — ваше первое приложение для генерации текста

Теперь, когда мы узнали, как настроить и сконфигурировать openai, пришло время создать ваше первое приложение для генерации текста. Чтобы создать приложение, выполните следующие шаги:

1. Создайте виртуальное окружение и установите openai:

   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install openai
   ```

   > [!NOTE]
   > Если вы используете Windows, введите `venv\Scripts\activate` вместо `source venv/bin/activate`.

   > [!NOTE]
   > Найдите ваш ключ Azure OpenAI, перейдя по ссылке [https://portal.azure.com/](https://portal.azure.com/?WT.mc_id=academic-105485-koreyst), найдите `Open AI`, выберите ресурс `Open AI` и затем выберите `Keys and Endpoint`, скопируйте значение `Key 1`.

1. Создайте файл _app.py_ и добавьте в него следующий код:

   ```python
   import openai

   openai.api_key = "<replace this value with your open ai key or Azure OpenAI key>"

   openai.api_type = 'azure'
   openai.api_version = '2023-05-15'
   openai.api_base = "<endpoint found in Azure Portal where your API key is>"
   deployment_name = "<deployment name>"

   # add your completion code
   prompt = "Complete the following: Once upon a time there was a"
   messages = [{"role": "user", "content": prompt}]

   # make completion
   completion = openai.chat.completions.create(model=deployment_name, messages=messages)

   # print response
   print(completion.choices[0].message.content)
   ```

   > [!NOTE]
   > Если вы используете Azure OpenAI, вам нужно установить `api_type` в значение `azure` и установить `api_key` в значение вашего ключа Azure OpenAI.

   Вы должны увидеть вывод, похожий на следующий:

   ```output
    very unhappy _____.

   Once upon a time there was a very unhappy mermaid.
   ```

## Разные типы подсказок для разных задач

Теперь вы видели, как генерировать текст с помощью подсказки. У вас даже есть работающая программа, которую вы можете модифицировать и изменять для генерации различных типов текста.

Подсказки могут использоваться для выполнения самых разных задач. Например:

- **Генерация текста определённого типа**. Например, вы можете сгенерировать стихотворение, вопросы для викторины и т.д.
- **Поиск информации**. Вы можете использовать подсказки для поиска информации, например, 'Что означает CORS в веб-разработке?'.
- **Генерация кода**. Вы можете использовать подсказки для генерации кода, например, разработки регулярного выражения для проверки email или даже создания целой программы, например, веб-приложения.

## Более практическое применение: генератор рецептов

Представьте, что у вас дома есть ингредиенты, и вы хотите что-то приготовить. Для этого вам нужен рецепт. Один из способов найти рецепты — использовать поисковую систему, или вы можете воспользоваться LLM.

Вы можете написать такую подсказку:

> "Покажи мне 5 рецептов блюда с следующими ингредиентами: курица, картофель и морковь. Для каждого рецепта перечисли все используемые ингредиенты."

Согласно этой подсказке, вы можете получить ответ, похожий на:

```output
1. Roasted Chicken and Vegetables:
Ingredients:
- 4 chicken thighs
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 2 tablespoons olive oil
- 2 cloves garlic, minced
- 1 teaspoon dried thyme
- 1 teaspoon dried oregano
- Salt and pepper, to taste

2. Chicken and Potato Stew:
Ingredients:
- 2 tablespoons olive oil
- 1 onion, diced
- 2 cloves garlic, minced
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 teaspoon dried oregano
- 1 teaspoon dried thyme
- 1 cup chicken broth
- Salt and pepper, to taste

3. Chicken and Potato Bake:
Ingredients:
- 2 tablespoons olive oil
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 onion, diced
- 2 cloves garlic, minced
- 1 teaspoon dried oregano
- 1 teaspoon dried thyme
- 1 cup chicken broth
- Salt and pepper, to taste

4. Chicken and Potato Soup:
Ingredients:
- 2 tablespoons olive oil
- 1 onion, diced
- 2 cloves garlic, minced
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 teaspoon dried oregano
- 1 teaspoon dried thyme
- 4 cups chicken broth
- Salt and pepper, to taste

5. Chicken and Potato Hash:
Ingredients:
- 2 tablespoons olive oil
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 onion, diced
- 2 cloves garlic, minced
- 1 teaspoon dried oregano
```

Этот результат отличный, теперь я знаю, что готовить. На этом этапе полезными улучшениями могут быть:

- Исключение ингредиентов, которые мне не нравятся или на которые у меня аллергия.
- Создание списка покупок, если у меня нет всех ингредиентов дома.

Для этих случаев давайте добавим дополнительную подсказку:

> "Пожалуйста, убери рецепты с чесноком, так как у меня аллергия, и замени его чем-то другим. Также создай список покупок для рецептов, учитывая, что у меня уже есть курица, картофель и морковь."

Теперь у вас есть новый результат, а именно:

```output
1. Roasted Chicken and Vegetables:
Ingredients:
- 4 chicken thighs
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 2 tablespoons olive oil
- 1 teaspoon dried thyme
- 1 teaspoon dried oregano
- Salt and pepper, to taste

2. Chicken and Potato Stew:
Ingredients:
- 2 tablespoons olive oil
- 1 onion, diced
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 teaspoon dried oregano
- 1 teaspoon dried thyme
- 1 cup chicken broth
- Salt and pepper, to taste

3. Chicken and Potato Bake:
Ingredients:
- 2 tablespoons olive oil
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 onion, diced
- 1 teaspoon dried oregano
- 1 teaspoon dried thyme
- 1 cup chicken broth
- Salt and pepper, to taste

4. Chicken and Potato Soup:
Ingredients:
- 2 tablespoons olive oil
- 1 onion, diced
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 teaspoon dried oregano
- 1 teaspoon dried thyme
- 4 cups chicken broth
- Salt and pepper, to taste

5. Chicken and Potato Hash:
Ingredients:
- 2 tablespoons olive oil
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 onion, diced
- 1 teaspoon dried oregano

Shopping List:
- Olive oil
- Onion
- Thyme
- Oregano
- Salt
- Pepper
```

Вот ваши пять рецептов, без упоминания чеснока, и также у вас есть список покупок, учитывающий то, что у вас уже есть дома.

## Упражнение — создание генератора рецептов

Теперь, когда мы рассмотрели сценарий, давайте напишем код, соответствующий продемонстрированному сценарию. Для этого выполните следующие шаги:

1. Используйте существующий файл _app.py_ в качестве отправной точки.
1. Найдите переменную `prompt` и измените её код на следующий:

   ```python
   prompt = "Show me 5 recipes for a dish with the following ingredients: chicken, potatoes, and carrots. Per recipe, list all the ingredients used"
   ```

   Если вы теперь запустите код, вы должны увидеть вывод, похожий на:

   ```output
   -Chicken Stew with Potatoes and Carrots: 3 tablespoons oil, 1 onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 1/2 cups chicken broth, 1/2 cup dry white wine, 2 tablespoons chopped fresh parsley, 2 tablespoons unsalted butter, 1 1/2 pounds boneless, skinless chicken thighs, cut into 1-inch pieces
   -Oven-Roasted Chicken with Potatoes and Carrots: 3 tablespoons extra-virgin olive oil, 1 tablespoon Dijon mustard, 1 tablespoon chopped fresh rosemary, 1 tablespoon chopped fresh thyme, 4 cloves garlic, minced, 1 1/2 pounds small red potatoes, quartered, 1 1/2 pounds carrots, quartered lengthwise, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 (4-pound) whole chicken
   -Chicken, Potato, and Carrot Casserole: cooking spray, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and shredded, 1 potato, peeled and shredded, 1/2 teaspoon dried thyme leaves, 1/4 teaspoon salt, 1/4 teaspoon black pepper, 2 cups fat-free, low-sodium chicken broth, 1 cup frozen peas, 1/4 cup all-purpose flour, 1 cup 2% reduced-fat milk, 1/4 cup grated Parmesan cheese

   -One Pot Chicken and Potato Dinner: 2 tablespoons olive oil, 1 pound boneless, skinless chicken thighs, cut into 1-inch pieces, 1 large onion, chopped, 3 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 2 cups chicken broth, 1/2 cup dry white wine

   -Chicken, Potato, and Carrot Curry: 1 tablespoon vegetable oil, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 teaspoon ground coriander, 1 teaspoon ground cumin, 1/2 teaspoon ground turmeric, 1/2 teaspoon ground ginger, 1/4 teaspoon cayenne pepper, 2 cups chicken broth, 1/2 cup dry white wine, 1 (15-ounce) can chickpeas, drained and rinsed, 1/2 cup raisins, 1/2 cup chopped fresh cilantro
   ```

   > NOTE, ваш LLM является недетерминированным, поэтому каждый раз при запуске программы вы можете получать разные результаты.

   Отлично, давайте посмотрим, как можно улучшить программу. Чтобы улучшить её, мы хотим убедиться, что код гибкий, чтобы ингредиенты и количество рецептов можно было изменять.

1. Давайте изменим код следующим образом:

   ```python
   no_recipes = input("No of recipes (for example, 5): ")

   ingredients = input("List of ingredients (for example, chicken, potatoes, and carrots): ")

   # interpolate the number of recipes into the prompt an ingredients
   prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used"
   ```

   Тестовый запуск кода может выглядеть так:

   ```output
   No of recipes (for example, 5): 3
   List of ingredients (for example, chicken, potatoes, and carrots): milk,strawberries

   -Strawberry milk shake: milk, strawberries, sugar, vanilla extract, ice cubes
   -Strawberry shortcake: milk, flour, baking powder, sugar, salt, unsalted butter, strawberries, whipped cream
   -Strawberry milk: milk, strawberries, sugar, vanilla extract
   ```

### Улучшение с добавлением фильтра и списка покупок

Теперь у нас есть рабочее приложение, способное создавать рецепты, и оно гибкое, так как зависит от ввода пользователя, как по количеству рецептов, так и по используемым ингредиентам.

Чтобы ещё больше улучшить его, мы хотим добавить следующее:

- **Исключение ингредиентов**. Мы хотим иметь возможность исключать ингредиенты, которые нам не нравятся или на которые у нас аллергия. Чтобы реализовать это изменение, мы можем отредактировать существующую подсказку и добавить условие фильтра в её конец, например:

  ```python
  filter = input("Filter (for example, vegetarian, vegan, or gluten-free): ")

  prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used, no {filter}"
  ```

  В приведённом выше примере мы добавляем `{filter}` в конец подсказки и также захватываем значение фильтра от пользователя.

  Пример ввода при запуске программы теперь может выглядеть так:

  ```output
  No of recipes (for example, 5): 3
  List of ingredients (for example, chicken, potatoes, and carrots): onion,milk
  Filter (for example, vegetarian, vegan, or gluten-free): no milk

  1. French Onion Soup

  Ingredients:

  -1 large onion, sliced
  -3 cups beef broth
  -1 cup milk
  -6 slices french bread
  -1/4 cup shredded Parmesan cheese
  -1 tablespoon butter
  -1 teaspoon dried thyme
  -1/4 teaspoon salt
  -1/4 teaspoon black pepper

  Instructions:

  1. In a large pot, sauté onions in butter until golden brown.
  2. Add beef broth, milk, thyme, salt, and pepper. Bring to a boil.
  3. Reduce heat and simmer for 10 minutes.
  4. Place french bread slices on soup bowls.
  5. Ladle soup over bread.
  6. Sprinkle with Parmesan cheese.

  2. Onion and Potato Soup

  Ingredients:

  -1 large onion, chopped
  -2 cups potatoes, diced
  -3 cups vegetable broth
  -1 cup milk
  -1/4 teaspoon black pepper

  Instructions:

  1. In a large pot, sauté onions in butter until golden brown.
  2. Add potatoes, vegetable broth, milk, and pepper. Bring to a boil.
  3. Reduce heat and simmer for 10 minutes.
  4. Serve hot.

  3. Creamy Onion Soup

  Ingredients:

  -1 large onion, chopped
  -3 cups vegetable broth
  -1 cup milk
  -1/4 teaspoon black pepper
  -1/4 cup all-purpose flour
  -1/2 cup shredded Parmesan cheese

  Instructions:

  1. In a large pot, sauté onions in butter until golden brown.
  2. Add vegetable broth, milk, and pepper. Bring to a boil.
  3. Reduce heat and simmer for 10 minutes.
  4. In a small bowl, whisk together flour and Parmesan cheese until smooth.
  5. Add to soup and simmer for an additional 5 minutes, or until soup has thickened.
  ```

  Как видите, любые рецепты с молоком были исключены. Но если у вас непереносимость лактозы, вы можете захотеть исключить рецепты с сыром, поэтому важно быть точным.

- **Создание списка покупок**. Мы хотим создать список покупок, учитывая то, что у нас уже есть дома.

  Для этой функции мы могли бы попытаться решить всё в одной подсказке или разделить её на две. Давайте попробуем второй подход. Здесь мы предлагаем добавить дополнительную подсказку, но для этого нам нужно добавить результат первой подсказки как контекст ко второй. 

  Найдите часть кода, которая выводит результат первой подсказки, и добавьте следующий код ниже:
  ```python
  old_prompt_result = completion.choices[0].message.content
  prompt = "Produce a shopping list for the generated recipes and please don't include ingredients that I already have."

  new_prompt = f"{old_prompt_result} {prompt}"
  messages = [{"role": "user", "content": new_prompt}]
  completion = openai.Completion.create(engine=deployment_name, messages=messages, max_tokens=1200)

  # print response
  print("Shopping list:")
  print(completion.choices[0].message.content)
  ```

  Обратите внимание на следующее:

  1. Мы создаем новый запрос, добавляя результат из первого запроса к новому запросу:

     ```python
     new_prompt = f"{old_prompt_result} {prompt}"
     ```

  1. Мы делаем новый запрос, но также учитываем количество токенов, которые мы запросили в первом запросе, поэтому на этот раз мы указываем `max_tokens` как 1200.

     ```python
     completion = openai.Completion.create(engine=deployment_name, prompt=new_prompt, max_tokens=1200)
     ```

     Запустив этот код, мы получаем следующий результат:

     ```output
     No of recipes (for example, 5): 2
     List of ingredients (for example, chicken, potatoes, and carrots): apple,flour
     Filter (for example, vegetarian, vegan, or gluten-free): sugar


     -Apple and flour pancakes: 1 cup flour, 1/2 tsp baking powder, 1/2 tsp baking soda, 1/4 tsp salt, 1 tbsp sugar, 1 egg, 1 cup buttermilk or sour milk, 1/4 cup melted butter, 1 Granny Smith apple, peeled and grated
     -Apple fritters: 1-1/2 cups flour, 1 tsp baking powder, 1/4 tsp salt, 1/4 tsp baking soda, 1/4 tsp nutmeg, 1/4 tsp cinnamon, 1/4 tsp allspice, 1/4 cup sugar, 1/4 cup vegetable shortening, 1/4 cup milk, 1 egg, 2 cups shredded, peeled apples
     Shopping list:
     -Flour, baking powder, baking soda, salt, sugar, egg, buttermilk, butter, apple, nutmeg, cinnamon, allspice
     ```

## Улучшите вашу настройку

На данный момент у нас есть рабочий код, но есть несколько улучшений, которые стоит внести, чтобы сделать его еще лучше. Вот что можно сделать:

- **Отделите секреты от кода**, например, API-ключ. Секреты не должны находиться в коде, их следует хранить в безопасном месте. Чтобы отделить секреты от кода, можно использовать переменные окружения и библиотеки, такие как `python-dotenv`, чтобы загружать их из файла. Вот как это может выглядеть в коде:

  1. Создайте файл `.env` со следующим содержимым:

     ```bash
     OPENAI_API_KEY=sk-...
     ```

     > Обратите внимание, для Azure необходимо установить следующие переменные окружения:

     ```bash
     OPENAI_API_TYPE=azure
     OPENAI_API_VERSION=2023-05-15
     OPENAI_API_BASE=<replace>
     ```

     В коде вы можете загрузить переменные окружения следующим образом:

     ```python
     from dotenv import load_dotenv

     load_dotenv()

     openai.api_key = os.environ["OPENAI_API_KEY"]
     ```

- **Несколько слов о длине токенов**. Мы должны учитывать, сколько токенов нам нужно для генерации текста, который мы хотим получить. Токены стоят денег, поэтому, где это возможно, мы должны стараться экономить на их количестве. Например, можно ли сформулировать запрос так, чтобы использовать меньше токенов?

  Чтобы изменить количество используемых токенов, можно использовать параметр `max_tokens`. Например, если вы хотите использовать 100 токенов, вы можете сделать так:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, max_tokens=100)
  ```

- **Эксперименты с температурой**. Температура — это то, о чем мы пока не упоминали, но это важный параметр, влияющий на работу программы. Чем выше значение температуры, тем более случайным будет результат. Напротив, чем ниже значение температуры, тем более предсказуемым будет результат. Подумайте, хотите ли вы вариативности в вашем результате или нет.

  Чтобы изменить температуру, можно использовать параметр `temperature`. Например, если вы хотите установить температуру 0.5, вы можете сделать так:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, temperature=0.5)
  ```

  > Обратите внимание, чем ближе к 1.0, тем более разнообразным будет результат.

## Задание

Для этого задания вы можете выбрать, что именно хотите создать.

Вот несколько предложений:

- Улучшите приложение для генерации рецептов. Попробуйте поиграть со значениями температуры и формулировками запросов, чтобы увидеть, что у вас получится.
- Создайте "учебного помощника". Это приложение должно уметь отвечать на вопросы по какой-либо теме, например, Python. Вы можете использовать запросы вроде "Что такое определенная тема в Python?" или запросы, которые требуют показать код для определенной темы и т.д.
- Исторический бот, оживите историю, попросите бота сыграть роль определенного исторического персонажа и задавайте ему вопросы о его жизни и времени.

## Решение

### Учебный помощник

Ниже приведен начальный запрос, посмотрите, как вы можете его использовать и настроить по своему усмотрению.

```text
- "You're an expert on the Python language

    Suggest a beginner lesson for Python in the following format:

    Format:
    - concepts:
    - brief explanation of the lesson:
    - exercise in code with solutions"
```

### Исторический бот

Вот несколько запросов, которые вы можете использовать:

```text
- "You are Abe Lincoln, tell me about yourself in 3 sentences, and respond using grammar and words like Abe would have used"
- "You are Abe Lincoln, respond using grammar and words like Abe would have used:

   Tell me about your greatest accomplishments, in 300 words"
```

## Проверка знаний

Что делает параметр температуры?

1. Он контролирует, насколько случайным будет результат.
1. Он контролирует, насколько большим будет ответ.
1. Он контролирует, сколько токенов будет использовано.

## 🚀 Вызов

Работая над заданием, попробуйте варьировать температуру, установите ее на 0, 0.5 и 1. Помните, что 0 — это наименее вариативный результат, а 1 — наиболее. Какое значение лучше всего подходит для вашего приложения?

## Отличная работа! Продолжайте обучение

После завершения этого урока ознакомьтесь с нашей [коллекцией обучения генеративному ИИ](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst), чтобы продолжить углублять свои знания о генеративном ИИ!

Перейдите к уроку 7, где мы рассмотрим, как [создавать чат-приложения](../07-building-chat-applications/README.md?WT.mc_id=academic-105485-koreyst)!

---

**Отказ от ответственности**:  
Этот документ был переведен с использованием сервиса автоматического перевода [Co-op Translator](https://github.com/Azure/co-op-translator). Хотя мы стремимся к точности, пожалуйста, учитывайте, что автоматические переводы могут содержать ошибки или неточности. Оригинальный документ на его родном языке следует считать авторитетным источником. Для получения критически важной информации рекомендуется профессиональный перевод человеком. Мы не несем ответственности за любые недоразумения или неправильные интерпретации, возникающие в результате использования данного перевода.