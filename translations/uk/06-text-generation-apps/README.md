<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "df027997f1448323d6159b78a1b669bf",
  "translation_date": "2025-10-18T02:10:42+00:00",
  "source_file": "06-text-generation-apps/README.md",
  "language_code": "uk"
}
-->
# Створення додатків для генерації тексту

[![Створення додатків для генерації тексту](../../../translated_images/06-lesson-banner.a5c629f990a636c852353c5533f1a6a218ece579005e91f96339d508d9cf8f47.uk.png)](https://youtu.be/0Y5Luf5sRQA?si=t_xVg0clnAI4oUFZ)

> _(Натисніть на зображення вище, щоб переглянути відео цього уроку)_

У цьому курсі ви вже ознайомилися з основними концепціями, такими як підказки, і навіть з цілою дисципліною, яка називається "інженерія підказок". Багато інструментів, з якими ви можете взаємодіяти, як-от ChatGPT, Office 365, Microsoft Power Platform та інші, дозволяють використовувати підказки для виконання завдань.

Щоб додати такий досвід у ваш додаток, вам потрібно зрозуміти концепції, такі як підказки, завершення, і вибрати бібліотеку для роботи. Саме це ви навчитеся робити в цьому розділі.

## Вступ

У цьому розділі ви:

- Дізнаєтеся про бібліотеку openai та її основні концепції.
- Створите додаток для генерації тексту за допомогою openai.
- Зрозумієте, як використовувати концепції, такі як підказка, температура та токени, для створення додатка для генерації тексту.

## Цілі навчання

Наприкінці цього уроку ви зможете:

- Пояснити, що таке додаток для генерації тексту.
- Створити додаток для генерації тексту за допомогою openai.
- Налаштувати ваш додаток для використання більшої або меншої кількості токенів, а також змінити температуру для отримання різноманітних результатів.

## Що таке додаток для генерації тексту?

Зазвичай, коли ви створюєте додаток, він має якийсь інтерфейс, наприклад:

- Командний. Консольні додатки — це типові додатки, де ви вводите команду, і вона виконує завдання. Наприклад, `git` — це командний додаток.
- Графічний інтерфейс користувача (UI). Деякі додатки мають графічний інтерфейс, де ви натискаєте кнопки, вводите текст, вибираєте опції тощо.

### Обмеження консольних і UI-додатків

Порівняйте це з командним додатком, де ви вводите команду:

- **Це обмежено**. Ви не можете просто вводити будь-яку команду, лише ті, які підтримує додаток.
- **Мовна специфікація**. Деякі додатки підтримують багато мов, але за замовчуванням додаток створений для конкретної мови, навіть якщо можна додати підтримку інших мов.

### Переваги додатків для генерації тексту

Чим же відрізняється додаток для генерації тексту?

У додатку для генерації тексту у вас більше гнучкості, ви не обмежені набором команд або конкретною мовою введення. Натомість ви можете використовувати природну мову для взаємодії з додатком. Ще одна перевага полягає в тому, що ви вже взаємодієте з джерелом даних, яке було навчено на великому корпусі інформації, тоді як традиційний додаток може бути обмежений тим, що є в базі даних.

### Що можна створити за допомогою додатка для генерації тексту?

Є багато речей, які можна створити. Наприклад:

- **Чат-бот**. Чат-бот, який відповідає на запитання про теми, як-от ваша компанія та її продукти, може бути хорошим варіантом.
- **Помічник**. LLM чудово справляються з такими завданнями, як узагальнення тексту, отримання інсайтів із тексту, створення тексту, як-от резюме, тощо.
- **Асистент програмування**. Залежно від мовної моделі, яку ви використовуєте, ви можете створити асистента програмування, який допоможе вам писати код. Наприклад, ви можете використовувати продукт, як-от GitHub Copilot, а також ChatGPT для допомоги у написанні коду.

## Як почати?

Вам потрібно знайти спосіб інтеграції з LLM, що зазвичай передбачає два підходи:

- Використовувати API. Тут ви створюєте веб-запити з вашою підказкою і отримуєте згенерований текст у відповідь.
- Використовувати бібліотеку. Бібліотеки допомагають інкапсулювати виклики API і роблять їх простішими у використанні.

## Бібліотеки/SDK

Існує кілька добре відомих бібліотек для роботи з LLM, таких як:

- **openai**, ця бібліотека дозволяє легко підключитися до вашої моделі і надсилати підказки.

Також є бібліотеки, які працюють на більш високому рівні, такі як:

- **Langchain**. Langchain добре відомий і підтримує Python.
- **Semantic Kernel**. Semantic Kernel — це бібліотека від Microsoft, яка підтримує мови C#, Python і Java.

## Перший додаток за допомогою openai

Давайте подивимося, як ми можемо створити наш перший додаток, які бібліотеки нам потрібні, скільки потрібно зробити тощо.

### Встановлення openai

Існує багато бібліотек для взаємодії з OpenAI або Azure OpenAI. Можна використовувати різні мови програмування, такі як C#, Python, JavaScript, Java тощо. Ми вибрали бібліотеку Python `openai`, тому будемо використовувати `pip` для її встановлення.

```bash
pip install openai
```

### Створення ресурсу

Вам потрібно виконати наступні кроки:

- Створити обліковий запис на Azure [https://azure.microsoft.com/free/](https://azure.microsoft.com/free/?WT.mc_id=academic-105485-koreyst).
- Отримати доступ до Azure OpenAI. Перейдіть за посиланням [https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai](https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai?WT.mc_id=academic-105485-koreyst) і подайте запит на доступ.

  > [!NOTE]
  > На момент написання, вам потрібно подати заявку на доступ до Azure OpenAI.

- Встановити Python <https://www.python.org/>
- Створити ресурс Azure OpenAI Service. Дивіться цей посібник, як [створити ресурс](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal?WT.mc_id=academic-105485-koreyst).

### Знайдіть ключ API та кінцеву точку

На цьому етапі вам потрібно повідомити вашій бібліотеці `openai`, який ключ API використовувати. Щоб знайти ваш ключ API, перейдіть до розділу "Keys and Endpoint" вашого ресурсу Azure OpenAI і скопіюйте значення "Key 1".

![Keys and Endpoint resource blade in Azure Portal](https://learn.microsoft.com/azure/ai-services/openai/media/quickstarts/endpoint.png?WT.mc_id=academic-105485-koreyst)

Тепер, коли ви скопіювали цю інформацію, давайте налаштуємо бібліотеки для її використання.

> [!NOTE]
> Варто відокремити ваш ключ API від вашого коду. Ви можете зробити це, використовуючи змінні середовища.
>
> - Встановіть змінну середовища `OPENAI_API_KEY` на ваш ключ API.
>   `export OPENAI_API_KEY='sk-...'`

### Налаштування конфігурації Azure

Якщо ви використовуєте Azure OpenAI, ось як налаштувати конфігурацію:

```python
openai.api_type = 'azure'
openai.api_key = os.environ["OPENAI_API_KEY"]
openai.api_version = '2023-05-15'
openai.api_base = os.getenv("API_BASE")
```

Тут ми налаштовуємо наступне:

- `api_type` на `azure`. Це повідомляє бібліотеці використовувати Azure OpenAI, а не OpenAI.
- `api_key`, це ваш ключ API, знайдений у порталі Azure.
- `api_version`, це версія API, яку ви хочете використовувати. На момент написання остання версія — `2023-05-15`.
- `api_base`, це кінцева точка API. Ви можете знайти її в порталі Azure поруч із вашим ключем API.

> [!NOTE] > `os.getenv` — це функція, яка читає змінні середовища. Ви можете використовувати її для читання змінних середовища, таких як `OPENAI_API_KEY` і `API_BASE`. Встановіть ці змінні середовища у вашому терміналі або за допомогою бібліотеки, як-от `dotenv`.

## Генерація тексту

Спосіб генерації тексту — це використання класу `Completion`. Ось приклад:

```python
prompt = "Complete the following: Once upon a time there was a"

completion = openai.Completion.create(model="davinci-002", prompt=prompt)
print(completion.choices[0].text)
```

У наведеному вище коді ми створюємо об'єкт завершення і передаємо модель, яку хочемо використовувати, і підказку. Потім ми друкуємо згенерований текст.

### Завершення чату

До цього моменту ви бачили, як ми використовували `Completion` для генерації тексту. Але є ще один клас під назвою `ChatCompletion`, який більше підходить для чат-ботів. Ось приклад його використання:

```python
import openai

openai.api_key = "sk-..."

completion = openai.ChatCompletion.create(model="gpt-3.5-turbo", messages=[{"role": "user", "content": "Hello world"}])
print(completion.choices[0].message.content)
```

Більше про цю функціональність у наступному розділі.

## Вправа - ваш перший додаток для генерації тексту

Тепер, коли ми дізналися, як налаштувати і конфігурувати openai, настав час створити ваш перший додаток для генерації тексту. Щоб створити ваш додаток, виконайте наступні кроки:

1. Створіть віртуальне середовище і встановіть openai:

   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install openai
   ```

   > [!NOTE]
   > Якщо ви використовуєте Windows, введіть `venv\Scripts\activate` замість `source venv/bin/activate`.

   > [!NOTE]
   > Знайдіть ваш ключ Azure OpenAI, перейшовши за посиланням [https://portal.azure.com/](https://portal.azure.com/?WT.mc_id=academic-105485-koreyst), знайдіть `Open AI` і виберіть `Open AI resource`, потім виберіть `Keys and Endpoint` і скопіюйте значення `Key 1`.

1. Створіть файл _app.py_ і додайте до нього наступний код:

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
   > Якщо ви використовуєте Azure OpenAI, вам потрібно встановити `api_type` на `azure` і встановити `api_key` на ваш ключ Azure OpenAI.

   Ви повинні побачити вихідні дані, схожі на наступні:

   ```output
    very unhappy _____.

   Once upon a time there was a very unhappy mermaid.
   ```

## Різні типи підказок для різних завдань

Тепер ви бачили, як генерувати текст за допомогою підказки. У вас навіть є програма, яку ви можете змінювати і налаштовувати для генерації різних типів тексту.

Підказки можуть використовуватися для різних завдань. Наприклад:

- **Генерація типу тексту**. Наприклад, ви можете створити вірш, запитання для вікторини тощо.
- **Пошук інформації**. Ви можете використовувати підказки для пошуку інформації, як-от наступний приклад: "Що означає CORS у веб-розробці?".
- **Генерація коду**. Ви можете використовувати підказки для створення коду, наприклад, розробки регулярного виразу для перевірки електронних адрес або навіть створення цілої програми, як-от веб-додатка.

## Більш практичний приклад: генератор рецептів

Уявіть, що у вас є інгредієнти вдома, і ви хочете щось приготувати. Для цього вам потрібен рецепт. Один із способів знайти рецепти — це використати пошукову систему, або ви можете скористатися LLM.

Ви могли б написати підказку, як-от:

> "Покажіть мені 5 рецептів для страви з наступними інгредієнтами: курка, картопля і морква. Для кожного рецепту вкажіть всі використані інгредієнти."

З огляду на наведену вище підказку, ви можете отримати відповідь, схожу на:

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

Цей результат чудовий, я знаю, що готувати. На цьому етапі корисними покращеннями можуть бути:

- Фільтрація інгредієнтів, які мені не подобаються або на які у мене алергія.
- Складання списку покупок, якщо у мене немає всіх інгредієнтів вдома.

Для наведених вище випадків давайте додамо додаткову підказку:

> "Будь ласка, видаліть рецепти з часником, оскільки у мене алергія, і замініть його на щось інше. Також складіть список покупок для рецептів, враховуючи, що у мене вже є курка, картопля і морква вдома."

Тепер у вас є новий результат, а саме:

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

Ось ваші п'ять рецептів, без згадки про часник, і у вас також є список покупок, враховуючи те, що у вас вже є вдома.

## Вправа - створення генератора рецептів

Тепер, коли ми розіграли сценарій, давайте напишемо код, який відповідає продемонстрованому сценарію. Для цього виконайте наступні кроки:

1. Використовуйте існуючий файл _app.py_ як відправну точку.
1. Знайдіть змінну `prompt` і змініть її код на наступний:

   ```python
   prompt = "Show me 5 recipes for a dish with the following ingredients: chicken, potatoes, and carrots. Per recipe, list all the ingredients used"
   ```

   Якщо ви зараз запустите код, ви повинні побачити вихідні дані, схожі на:

   ```output
   -Chicken Stew with Potatoes and Carrots: 3 tablespoons oil, 1 onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 1/2 cups chicken broth, 1/2 cup dry white wine, 2 tablespoons chopped fresh parsley, 2 tablespoons unsalted butter, 1 1/2 pounds boneless, skinless chicken thighs, cut into 1-inch pieces
   -Oven-Roasted Chicken with Potatoes and Carrots: 3 tablespoons extra-virgin olive oil, 1 tablespoon Dijon mustard, 1 tablespoon chopped fresh rosemary, 1 tablespoon chopped fresh thyme, 4 cloves garlic, minced, 1 1/2 pounds small red potatoes, quartered, 1 1/2 pounds carrots, quartered lengthwise, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 (4-pound) whole chicken
   -Chicken, Potato, and Carrot Casserole: cooking spray, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and shredded, 1 potato, peeled and shredded, 1/2 teaspoon dried thyme leaves, 1/4 teaspoon salt, 1/4 teaspoon black pepper, 2 cups fat-free, low-sodium chicken broth, 1 cup frozen peas, 1/4 cup all-purpose flour, 1 cup 2% reduced-fat milk, 1/4 cup grated Parmesan cheese

   -One Pot Chicken and Potato Dinner: 2 tablespoons olive oil, 1 pound boneless, skinless chicken thighs, cut into 1-inch pieces, 1 large onion, chopped, 3 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 2 cups chicken broth, 1/2 cup dry white wine

   -Chicken, Potato, and Carrot Curry: 1 tablespoon vegetable oil, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 teaspoon ground coriander, 1 teaspoon ground cumin, 1/2 teaspoon ground turmeric, 1/2 teaspoon ground ginger, 1/4 teaspoon cayenne pepper, 2 cups chicken broth, 1/2 cup dry white wine, 1 (15-ounce) can chickpeas, drained and rinsed, 1/2 cup raisins, 1/2 cup chopped fresh cilantro
   ```

   > ЗАУВАЖЕННЯ, ваш LLM є недетермінованим, тому ви можете отримувати різні результати кожного разу, коли запускаєте програму.

   Чудово, давайте подивимося, як ми можемо покращити речі. Щоб покращити речі, ми хочемо переконатися, що код є гнучким, щоб інгредієнти і кількість рецептів можна було змінювати.

1. Давайте змінимо код наступним чином:

   ```python
   no_recipes = input("No of recipes (for example, 5): ")

   ingredients = input("List of ingredients (for example, chicken, potatoes, and carrots): ")

   # interpolate the number of recipes into the prompt an ingredients
   prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used"
   ```

   Тестовий запуск коду може виглядати так:

   ```output
   No of recipes (for example, 5): 3
   List of ingredients (for example, chicken, potatoes, and carrots): milk,strawberries

   -Strawberry milk shake: milk, strawberries, sugar, vanilla extract, ice cubes
   -Strawberry shortcake: milk, flour, baking powder, sugar, salt, unsalted butter, strawberries, whipped cream
   -Strawberry milk: milk, strawberries, sugar, vanilla extract
   ```

### Покращення шляхом додавання фільтра і списку покупок

Тепер у нас є робочий додаток, здатний створювати рецепти, і він гнучкий, оскільки залежить від введених користувачем даних, як щодо кількості рецептів, так і щодо використаних інгредієнтів.

Щоб ще більше покращити його, ми хочемо додати наступне:

- **Фільтрація інгредієнтів**. Ми хочемо мати можливість фільтрувати інгредієнти, які нам не подобаються або на які у нас алергія. Для реалізації цієї зміни ми можемо відредагувати нашу існуючу підказку і додати умову фільтрації в її кінець, як-от:

  ```python
  filter = input("Filter (for example, vegetarian, vegan, or gluten-free): ")

  prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used, no {filter}"
  ```

  Вище ми додаємо `{filter}` до кінця підказки і також захоплюємо значення фільтра від користувача.

  Приклад введення для запуску програми тепер може виглядати так:

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

  Як ви бачите, будь-які рецепти з молоком були відфільтровані. Але якщо у вас непереносимість лактози, ви можете захотіти відфільтрувати рецепти з сиром також, тому потрібно бути чітким.

- **Складання списку покупок**. Ми хочемо скласти список покупок, враховуючи те, що у нас вже є вдома.

  Для цієї функціональності ми могли б спробувати вирішити все в одній підказці або розділити її на дві підказки. Давайте спробуємо другий підхід. Тут ми пропонуємо додати додаткову підказку, але для цього нам потрібно додати результат першої підказки як контекст до другої підказки.

  Знайдіть частину коду, яка друкує результат першої підказки, і додайте наступний код нижче:
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

  Зверніть увагу на наступне:

  1. Ми створюємо новий запит, додаючи результат з першого запиту до нового запиту:

     ```python
     new_prompt = f"{old_prompt_result} {prompt}"
     ```

  1. Ми робимо новий запит, але також враховуємо кількість токенів, які ми запросили в першому запиті, тому цього разу ми вказуємо `max_tokens` як 1200.

     ```python
     completion = openai.Completion.create(engine=deployment_name, prompt=new_prompt, max_tokens=1200)
     ```

     Використовуючи цей код, ми отримуємо наступний результат:

     ```output
     No of recipes (for example, 5): 2
     List of ingredients (for example, chicken, potatoes, and carrots): apple,flour
     Filter (for example, vegetarian, vegan, or gluten-free): sugar


     -Apple and flour pancakes: 1 cup flour, 1/2 tsp baking powder, 1/2 tsp baking soda, 1/4 tsp salt, 1 tbsp sugar, 1 egg, 1 cup buttermilk or sour milk, 1/4 cup melted butter, 1 Granny Smith apple, peeled and grated
     -Apple fritters: 1-1/2 cups flour, 1 tsp baking powder, 1/4 tsp salt, 1/4 tsp baking soda, 1/4 tsp nutmeg, 1/4 tsp cinnamon, 1/4 tsp allspice, 1/4 cup sugar, 1/4 cup vegetable shortening, 1/4 cup milk, 1 egg, 2 cups shredded, peeled apples
     Shopping list:
     -Flour, baking powder, baking soda, salt, sugar, egg, buttermilk, butter, apple, nutmeg, cinnamon, allspice
     ```

## Покращення вашої конфігурації

Те, що ми маємо зараз, працює, але є кілька налаштувань, які ми повинні зробити, щоб покращити роботу. Деякі з них:

- **Відокремлення секретів від коду**, наприклад, API-ключа. Секрети не повинні бути в коді і мають зберігатися в безпечному місці. Щоб відокремити секрети від коду, ми можемо використовувати змінні середовища та бібліотеки, такі як `python-dotenv`, щоб завантажувати їх із файлу. Ось як це виглядає в коді:

  1. Створіть файл `.env` з наступним вмістом:

     ```bash
     OPENAI_API_KEY=sk-...
     ```

     > Зверніть увагу, для Azure потрібно встановити наступні змінні середовища:

     ```bash
     OPENAI_API_TYPE=azure
     OPENAI_API_VERSION=2023-05-15
     OPENAI_API_BASE=<replace>
     ```

     У коді ви завантажите змінні середовища таким чином:

     ```python
     from dotenv import load_dotenv

     load_dotenv()

     openai.api_key = os.environ["OPENAI_API_KEY"]
     ```

- **Слово про довжину токенів**. Ми повинні враховувати, скільки токенів нам потрібно для генерації тексту, який ми хочемо. Токени коштують грошей, тому, де це можливо, ми повинні намагатися економити кількість використаних токенів. Наприклад, чи можемо ми сформулювати запит так, щоб використовувати менше токенів?

  Щоб змінити кількість токенів, ви можете використовувати параметр `max_tokens`. Наприклад, якщо ви хочете використовувати 100 токенів, ви зробите так:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, max_tokens=100)
  ```

- **Експериментування з температурою**. Температура — це те, про що ми ще не згадували, але це важливий контекст для того, як працює наша програма. Чим вище значення температури, тим більш випадковим буде результат. І навпаки, чим нижче значення температури, тим передбачуванішим буде результат. Подумайте, чи потрібна вам варіативність у результатах.

  Щоб змінити температуру, ви можете використовувати параметр `temperature`. Наприклад, якщо ви хочете використовувати температуру 0.5, ви зробите так:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, temperature=0.5)
  ```

  > Зверніть увагу, чим ближче до 1.0, тим більш варіативним буде результат.

## Завдання

Для цього завдання ви можете обрати, що саме створювати.

Ось кілька пропозицій:

- Покращіть додаток-генератор рецептів. Експериментуйте зі значеннями температури та запитами, щоб побачити, що ви можете створити.
- Створіть "навчального помічника". Цей додаток повинен відповідати на запитання з певної теми, наприклад, Python. Ви можете використовувати запити на кшталт "Що таке певна тема в Python?" або "Покажи мені код для певної теми" тощо.
- Історичний бот, який оживляє історію. Інструктуйте бота грати роль певного історичного персонажа та задавайте йому запитання про його життя та часи.

## Рішення

### Навчальний помічник

Нижче наведено стартовий запит, подивіться, як ви можете його використати та налаштувати на свій смак.

```text
- "You're an expert on the Python language

    Suggest a beginner lesson for Python in the following format:

    Format:
    - concepts:
    - brief explanation of the lesson:
    - exercise in code with solutions"
```

### Історичний бот

Ось кілька запитів, які ви можете використовувати:

```text
- "You are Abe Lincoln, tell me about yourself in 3 sentences, and respond using grammar and words like Abe would have used"
- "You are Abe Lincoln, respond using grammar and words like Abe would have used:

   Tell me about your greatest accomplishments, in 300 words"
```

## Перевірка знань

Що робить концепція температури?

1. Контролює, наскільки випадковим є результат.
1. Контролює, наскільки великим є відповідь.
1. Контролює, скільки токенів використовується.

## 🚀 Виклик

Працюючи над завданням, спробуйте змінювати температуру, встановлюючи її на 0, 0.5 і 1. Пам'ятайте, що 0 — це найменша варіативність, а 1 — найбільша. Яке значення найкраще підходить для вашого додатка?

## Чудова робота! Продовжуйте навчання

Після завершення цього уроку ознайомтеся з нашою [колекцією навчальних матеріалів з генеративного ШІ](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst), щоб продовжити вдосконалювати свої знання про генеративний ШІ!

Перейдіть до Уроку 7, де ми розглянемо, як [створювати чат-додатки](../07-building-chat-applications/README.md?WT.mc_id=academic-105485-koreyst)!

---

**Відмова від відповідальності**:  
Цей документ був перекладений за допомогою сервісу автоматичного перекладу [Co-op Translator](https://github.com/Azure/co-op-translator). Хоча ми прагнемо до точності, будь ласка, майте на увазі, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ на його рідній мові слід вважати авторитетним джерелом. Для критичної інформації рекомендується професійний людський переклад. Ми не несемо відповідальності за будь-які непорозуміння або неправильні тлумачення, що виникають внаслідок використання цього перекладу.