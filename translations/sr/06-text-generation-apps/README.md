<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "df027997f1448323d6159b78a1b669bf",
  "translation_date": "2025-10-18T01:16:14+00:00",
  "source_file": "06-text-generation-apps/README.md",
  "language_code": "sr"
}
-->
# Изградња апликација за генерисање текста

[![Изградња апликација за генерисање текста](../../../translated_images/06-lesson-banner.a5c629f990a636c852353c5533f1a6a218ece579005e91f96339d508d9cf8f47.sr.png)](https://youtu.be/0Y5Luf5sRQA?si=t_xVg0clnAI4oUFZ)

> _(Кликните на слику изнад да бисте погледали видео лекцију)_

До сада сте кроз овај курс видели да постоје основни концепти као што су упити и чак цела дисциплина која се зове "инжењеринг упита". Многи алати са којима можете да комуницирате, као што су ChatGPT, Office 365, Microsoft Power Platform и други, подржавају коришћење упита за постизање одређених циљева.

Да бисте додали такво искуство у апликацију, потребно је да разумете концепте као што су упити, завршетци и да изаберете библиотеку са којом ћете радити. Управо то ћете научити у овом поглављу.

## Увод

У овом поглављу ћете:

- Научити о библиотеци openai и њеним основним концептима.
- Направити апликацију за генерисање текста користећи openai.
- Разумети како да користите концепте као што су упит, температура и токени за изградњу апликације за генерисање текста.

## Циљеви учења

На крају ове лекције, моћи ћете да:

- Објасните шта је апликација за генерисање текста.
- Направите апликацију за генерисање текста користећи openai.
- Конфигуришете своју апликацију да користи више или мање токена, као и да промените температуру за разноврснији излаз.

## Шта је апликација за генерисање текста?

Обично када правите апликацију, она има неку врсту интерфејса као што су следећи:

- Командни интерфејс. Конзолне апликације су типичне апликације где уносите команду и она извршава задатак. На пример, `git` је апликација заснована на командама.
- Кориснички интерфејс (UI). Неке апликације имају графичке корисничке интерфејсе (GUI) где кликнете на дугмад, уносите текст, бирате опције и више.

### Ограничења конзолних и UI апликација

Упоредите то са апликацијом заснованом на командама где уносите команду:

- **Ограничено је**. Не можете уносити било коју команду, већ само оне које апликација подржава.
- **Језички специфично**. Неке апликације подржавају многе језике, али подразумевано апликација је направљена за одређени језик, чак и ако можете додати подршку за више језика.

### Предности апликација за генерисање текста

Како се апликација за генерисање текста разликује?

У апликацији за генерисање текста имате више флексибилности, нисте ограничени на скуп команди или одређени језик уноса. Уместо тога, можете користити природни језик за интеракцију са апликацијом. Још једна предност је што већ комуницирате са извором података који је обучен на огромном корпусу информација, док је традиционална апликација можда ограничена на оно што се налази у бази података.

### Шта могу да направим са апликацијом за генерисање текста?

Постоји много ствари које можете направити. На пример:

- **Четбот**. Четбот који одговара на питања о темама, као што су ваша компанија и њени производи, може бити добар избор.
- **Помоћник**. LLM-ови су одлични у стварима као што су сумирање текста, добијање увида из текста, производња текста као што су биографије и више.
- **Асистент за код**. У зависности од модела језика који користите, можете направити асистента за код који вам помаже да пишете код. На пример, можете користити производ као што је GitHub Copilot, као и ChatGPT, да вам помогну у писању кода.

## Како могу да започнем?

Потребно је да пронађете начин за интеграцију са LLM, што обично подразумева следећа два приступа:

- Коришћење API-ја. Овде конструишете веб захтеве са вашим упитом и добијате генерисани текст назад.
- Коришћење библиотеке. Библиотеке помажу у инкапсулацији API позива и чине их лакшим за коришћење.

## Библиотеке/SDK-ови

Постоји неколико добро познатих библиотека за рад са LLM-овима као што су:

- **openai**, ова библиотека олакшава повезивање са вашим моделом и слање упита.

Затим постоје библиотеке које раде на вишем нивоу као што су:

- **Langchain**. Langchain је добро познат и подржава Python.
- **Semantic Kernel**. Semantic Kernel је библиотека компаније Microsoft која подржава језике C#, Python и Java.

## Прва апликација користећи openai

Хајде да видимо како можемо направити нашу прву апликацију, које библиотеке су нам потребне, колико је потребно и тако даље.

### Инсталирајте openai

Постоји много библиотека за интеракцију са OpenAI или Azure OpenAI. Могуће је користити бројне програмске језике као што су C#, Python, JavaScript, Java и више. Ми смо изабрали да користимо Python библиотеку `openai`, па ћемо користити `pip` за њену инсталацију.

```bash
pip install openai
```

### Направите ресурс

Потребно је да извршите следеће кораке:

- Направите налог на Azure [https://azure.microsoft.com/free/](https://azure.microsoft.com/free/?WT.mc_id=academic-105485-koreyst).
- Остварите приступ Azure OpenAI. Идите на [https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai](https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai?WT.mc_id=academic-105485-koreyst) и затражите приступ.

  > [!NOTE]
  > У време писања, потребно је да се пријавите за приступ Azure OpenAI.

- Инсталирајте Python <https://www.python.org/>
- Направите Azure OpenAI Service ресурс. Погледајте овај водич за [прављење ресурса](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal?WT.mc_id=academic-105485-koreyst).

### Лоцирајте API кључ и крајњу тачку

У овом тренутку, потребно је да кажете вашој `openai` библиотеци који API кључ да користи. Да бисте пронашли ваш API кључ, идите на секцију "Keys and Endpoint" вашег Azure OpenAI ресурса и копирајте вредност "Key 1".

![Keys and Endpoint ресурс у Azure порталу](https://learn.microsoft.com/azure/ai-services/openai/media/quickstarts/endpoint.png?WT.mc_id=academic-105485-koreyst)

Сада када сте копирали ову информацију, хајде да упутимо библиотеке да је користе.

> [!NOTE]
> Вреди раздвојити ваш API кључ од вашег кода. То можете учинити коришћењем променљивих окружења.
>
> - Поставите променљиву окружења `OPENAI_API_KEY` на ваш API кључ.
>   `export OPENAI_API_KEY='sk-...'`

### Конфигурација Azure

Ако користите Azure OpenAI, ево како да подесите конфигурацију:

```python
openai.api_type = 'azure'
openai.api_key = os.environ["OPENAI_API_KEY"]
openai.api_version = '2023-05-15'
openai.api_base = os.getenv("API_BASE")
```

Горе постављамо следеће:

- `api_type` на `azure`. Ово говори библиотеци да користи Azure OpenAI, а не OpenAI.
- `api_key`, ово је ваш API кључ који се налази у Azure порталу.
- `api_version`, ово је верзија API-ја коју желите да користите. У време писања, најновија верзија је `2023-05-15`.
- `api_base`, ово је крајња тачка API-ја. Можете је пронаћи у Azure порталу поред вашег API кључа.

> [!NOTE] > `os.getenv` је функција која чита променљиве окружења. Можете је користити за читање променљивих окружења као што су `OPENAI_API_KEY` и `API_BASE`. Поставите ове променљиве окружења у вашем терминалу или користећи библиотеку као што је `dotenv`.

## Генерисање текста

Начин за генерисање текста је коришћење класе `Completion`. Ево примера:

```python
prompt = "Complete the following: Once upon a time there was a"

completion = openai.Completion.create(model="davinci-002", prompt=prompt)
print(completion.choices[0].text)
```

У горњем коду, креирамо објекат завршетка и прослеђујемо модел који желимо да користимо и упит. Затим штампамо генерисани текст.

### Завршетак чета

До сада сте видели како користимо `Completion` за генерисање текста. Али постоји још једна класа која се зове `ChatCompletion` и која је више прилагођена четботовима. Ево примера њеног коришћења:

```python
import openai

openai.api_key = "sk-..."

completion = openai.ChatCompletion.create(model="gpt-3.5-turbo", messages=[{"role": "user", "content": "Hello world"}])
print(completion.choices[0].message.content)
```

Више о овој функционалности у наредном поглављу.

## Вежба - ваша прва апликација за генерисање текста

Сада када смо научили како да подесимо и конфигуришемо openai, време је да направимо вашу прву апликацију за генерисање текста. Да бисте направили своју апликацију, следите ове кораке:

1. Направите виртуелно окружење и инсталирајте openai:

   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install openai
   ```

   > [!NOTE]
   > Ако користите Windows, уместо `source venv/bin/activate` унесите `venv\Scripts\activate`.

   > [!NOTE]
   > Лоцирајте ваш Azure OpenAI кључ тако што ћете отићи на [https://portal.azure.com/](https://portal.azure.com/?WT.mc_id=academic-105485-koreyst), потражити `Open AI` и изабрати `Open AI ресурс`, а затим изабрати `Keys and Endpoint` и копирати вредност `Key 1`.

1. Направите датотеку _app.py_ и унесите следећи код:

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
   > Ако користите Azure OpenAI, потребно је да поставите `api_type` на `azure` и да поставите `api_key` на ваш Azure OpenAI кључ.

   Требало би да видите излаз који изгледа овако:

   ```output
    very unhappy _____.

   Once upon a time there was a very unhappy mermaid.
   ```

## Различите врсте упита за различите ствари

Сада сте видели како да генеришете текст користећи упит. Чак имате програм који ради и који можете модификовати и мењати да генерише различите врсте текста.

Упити се могу користити за све врсте задатака. На пример:

- **Генерисање врсте текста**. На пример, можете генерисати песму, питања за квиз итд.
- **Проналажење информација**. Можете користити упите за тражење информација као што је следећи пример 'Шта значи CORS у веб развоју?'.
- **Генерисање кода**. Можете користити упите за генерисање кода, на пример развој регуларног израза који се користи за валидацију е-поште или зашто не генерисати цео програм, као што је веб апликација?

## Практичнији пример: генератор рецепата

Замислите да имате састојке код куће и желите да скувате нешто. За то вам је потребан рецепт. Један од начина да пронађете рецепте је да користите претраживач или можете користити LLM за то.

Могли бисте написати упит овако:

> "Прикажи ми 5 рецепата за јело са следећим састојцима: пилетина, кромпир и шаргарепа. За сваки рецепт, наведите све коришћене састојке."

С обзиром на горњи упит, могли бисте добити одговор сличан овоме:

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

Овај резултат је одличан, знам шта да скувам. У овом тренутку, корисна побољшања би могла бити:

- Филтрирање састојака које не волим или на које сам алергичан.
- Израда списка за куповину, у случају да немам све састојке код куће.

За горе наведене случајеве, хајде да додамо додатни упит:

> "Молим те уклони рецепте са белим луком јер сам алергичан и замени га нечим другим. Такође, молим те направи списак за куповину за рецепте, узимајући у обзир да већ имам пилетину, кромпир и шаргарепу код куће."

Сада имате нови резултат, наиме:

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

То су ваших пет рецепата, без помена белог лука, а такође имате и списак за куповину узимајући у обзир оно што већ имате код куће.

## Вежба - направите генератор рецепата

Сада када смо разрадили сценарио, хајде да напишемо код који одговара демонстрираном сценарију. Да бисмо то урадили, следите ове кораке:

1. Користите постојећу датотеку _app.py_ као почетну тачку.
1. Лоцирајте променљиву `prompt` и промените њен код на следећи начин:

   ```python
   prompt = "Show me 5 recipes for a dish with the following ingredients: chicken, potatoes, and carrots. Per recipe, list all the ingredients used"
   ```

   Ако сада покренете код, требало би да видите излаз сличан:

   ```output
   -Chicken Stew with Potatoes and Carrots: 3 tablespoons oil, 1 onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 1/2 cups chicken broth, 1/2 cup dry white wine, 2 tablespoons chopped fresh parsley, 2 tablespoons unsalted butter, 1 1/2 pounds boneless, skinless chicken thighs, cut into 1-inch pieces
   -Oven-Roasted Chicken with Potatoes and Carrots: 3 tablespoons extra-virgin olive oil, 1 tablespoon Dijon mustard, 1 tablespoon chopped fresh rosemary, 1 tablespoon chopped fresh thyme, 4 cloves garlic, minced, 1 1/2 pounds small red potatoes, quartered, 1 1/2 pounds carrots, quartered lengthwise, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 (4-pound) whole chicken
   -Chicken, Potato, and Carrot Casserole: cooking spray, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and shredded, 1 potato, peeled and shredded, 1/2 teaspoon dried thyme leaves, 1/4 teaspoon salt, 1/4 teaspoon black pepper, 2 cups fat-free, low-sodium chicken broth, 1 cup frozen peas, 1/4 cup all-purpose flour, 1 cup 2% reduced-fat milk, 1/4 cup grated Parmesan cheese

   -One Pot Chicken and Potato Dinner: 2 tablespoons olive oil, 1 pound boneless, skinless chicken thighs, cut into 1-inch pieces, 1 large onion, chopped, 3 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 2 cups chicken broth, 1/2 cup dry white wine

   -Chicken, Potato, and Carrot Curry: 1 tablespoon vegetable oil, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 teaspoon ground coriander, 1 teaspoon ground cumin, 1/2 teaspoon ground turmeric, 1/2 teaspoon ground ginger, 1/4 teaspoon cayenne pepper, 2 cups chicken broth, 1/2 cup dry white wine, 1 (15-ounce) can chickpeas, drained and rinsed, 1/2 cup raisins, 1/2 cup chopped fresh cilantro
   ```

   > NOTE, ваш LLM је недетерминистички, тако да можете добити различите резултате сваки пут када покренете програм.

   Одлично, хајде да видимо како можемо побољшати ствари. Да бисмо побољшали ствари, желимо да осигурамо да је код флексибилан, тако да се састојци и број рецепата могу побољшати и променити.

1. Хајде да променимо код на следећи начин:

   ```python
   no_recipes = input("No of recipes (for example, 5): ")

   ingredients = input("List of ingredients (for example, chicken, potatoes, and carrots): ")

   # interpolate the number of recipes into the prompt an ingredients
   prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used"
   ```

   Тестирање кода могло би изгледати овако:

   ```output
   No of recipes (for example, 5): 3
   List of ingredients (for example, chicken, potatoes, and carrots): milk,strawberries

   -Strawberry milk shake: milk, strawberries, sugar, vanilla extract, ice cubes
   -Strawberry shortcake: milk, flour, baking powder, sugar, salt, unsalted butter, strawberries, whipped cream
   -Strawberry milk: milk, strawberries, sugar, vanilla extract
   ```

### Побољшање додавањем филтера и списка за куповину

Сада имамо функционалну апликацију способну за производњу рецепата и она је флексибилна јер се ослања на уносе корисника, како у броју рецепата, тако и у коришћеним састојцима.

Даље побољшање које желимо да додамо је следеће:

- **Филтрирање састојака**. Желимо да будемо у могућности да филтрирамо састојке које не волимо или на које смо алергични. Да бисмо постигли ову промену, можемо уредити наш постојећи упит и додати услов за филтрирање на крај овако:

  ```python
  filter = input("Filter (for example, vegetarian, vegan, or gluten-free): ")

  prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used, no {filter}"
  ```

  Горе, додали смо `{filter}` на крај упита и такође смо ухватили вредност филтера од корисника.

  Пример уноса приликом покретања програма сада може изгледати овако:

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

  Као што видите, сви рецепти са млеком су филтрирани. Али, ако сте нетолерантни на лактозу, можда желите да филтрирате рецепте са сиром, тако да је потребно бити јасан.

- **Израда списка за куповину**. Желимо да направимо списак за куповину, узимајући у обзир оно што већ имамо код куће.

  За ову функционалност, могли бисмо покушати да решимо све у једном упиту или бисмо могли да га поделимо на два упита. Хајде да пробамо други приступ. Овде предлажемо додавање додатног упита, али да би то функционисало, потребно је да додамо резултат првог упита као контекст другом упиту.

  Лоцирајте део у
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

  Обратите пажњу на следеће:

  1. Конструишемо нови упит додавањем резултата из првог упита новом упиту:

     ```python
     new_prompt = f"{old_prompt_result} {prompt}"
     ```

  1. Правимо нови захтев, али узимајући у обзир број токена који смо тражили у првом упиту, па овог пута кажемо да је `max_tokens` 1200.

     ```python
     completion = openai.Completion.create(engine=deployment_name, prompt=new_prompt, max_tokens=1200)
     ```

     Испробавајући овај код, сада долазимо до следећег резултата:

     ```output
     No of recipes (for example, 5): 2
     List of ingredients (for example, chicken, potatoes, and carrots): apple,flour
     Filter (for example, vegetarian, vegan, or gluten-free): sugar


     -Apple and flour pancakes: 1 cup flour, 1/2 tsp baking powder, 1/2 tsp baking soda, 1/4 tsp salt, 1 tbsp sugar, 1 egg, 1 cup buttermilk or sour milk, 1/4 cup melted butter, 1 Granny Smith apple, peeled and grated
     -Apple fritters: 1-1/2 cups flour, 1 tsp baking powder, 1/4 tsp salt, 1/4 tsp baking soda, 1/4 tsp nutmeg, 1/4 tsp cinnamon, 1/4 tsp allspice, 1/4 cup sugar, 1/4 cup vegetable shortening, 1/4 cup milk, 1 egg, 2 cups shredded, peeled apples
     Shopping list:
     -Flour, baking powder, baking soda, salt, sugar, egg, buttermilk, butter, apple, nutmeg, cinnamon, allspice
     ```

## Побољшајте своје подешавање

Оно што имамо до сада је код који ради, али постоје неке измене које би требало да урадимо како бисмо додатно побољшали ствари. Неке од ствари које би требало да урадимо су:

- **Одвојите тајне од кода**, као што је API кључ. Тајне не припадају коду и треба их чувати на сигурном месту. Да бисмо одвојили тајне од кода, можемо користити променљиве окружења и библиотеке као што је `python-dotenv` за учитавање из датотеке. Ево како би то изгледало у коду:

  1. Направите `.env` датотеку са следећим садржајем:

     ```bash
     OPENAI_API_KEY=sk-...
     ```

     > Напомена, за Azure, потребно је да подесите следеће променљиве окружења:

     ```bash
     OPENAI_API_TYPE=azure
     OPENAI_API_VERSION=2023-05-15
     OPENAI_API_BASE=<replace>
     ```

     У коду, променљиве окружења бисте учитали на следећи начин:

     ```python
     from dotenv import load_dotenv

     load_dotenv()

     openai.api_key = os.environ["OPENAI_API_KEY"]
     ```

- **Реч о дужини токена**. Требало би да размислимо о томе колико нам је токена потребно за генерисање текста који желимо. Токени коштају, па где год је могуће, требало би да покушамо да будемо економични са бројем токена које користимо. На пример, можемо ли формулисати упит тако да користимо мање токена?

  Да бисте променили број коришћених токена, можете користити параметар `max_tokens`. На пример, ако желите да користите 100 токена, урадили бисте:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, max_tokens=100)
  ```

- **Експериментисање са температуром**. Температура је нешто што до сада нисмо споменули, али је важан контекст за то како наш програм функционише. Што је већа вредност температуре, то ће излаз бити насумичнији. Супротно томе, што је вредност температуре нижа, то ће излаз бити предвидљивији. Размислите да ли желите варијацију у вашем излазу или не.

  Да бисте променили температуру, можете користити параметар `temperature`. На пример, ако желите да користите температуру од 0.5, урадили бисте:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, temperature=0.5)
  ```

  > Напомена, што је ближе 1.0, то је излаз разноврснији.

## Задатак

За овај задатак, можете изабрати шта желите да направите.

Ево неких предлога:

- Унапредите апликацију за генерисање рецепата. Експериментишите са вредностима температуре и упитима да видите шта можете да постигнете.
- Направите "другара за учење". Ова апликација би требало да може да одговара на питања о одређеној теми, на пример Python. Могли бисте да имате упите као што су "Шта је одређена тема у Python-у?", или можете имати упит који каже, покажи ми код за одређену тему итд.
- Историјски бот, оживите историју, упутите бота да игра улогу одређеног историјског лика и постављајте му питања о његовом животу и времену.

## Решење

### Другар за учење

Испод је почетни упит, видите како можете да га користите и прилагодите својим потребама.

```text
- "You're an expert on the Python language

    Suggest a beginner lesson for Python in the following format:

    Format:
    - concepts:
    - brief explanation of the lesson:
    - exercise in code with solutions"
```

### Историјски бот

Ево неких упита које бисте могли да користите:

```text
- "You are Abe Lincoln, tell me about yourself in 3 sentences, and respond using grammar and words like Abe would have used"
- "You are Abe Lincoln, respond using grammar and words like Abe would have used:

   Tell me about your greatest accomplishments, in 300 words"
```

## Провера знања

Шта ради концепт температуре?

1. Контролише колико је излаз насумичан.
1. Контролише колико је одговор велики.
1. Контролише колико токена се користи.

## 🚀 Изазов

Док радите на задатку, покушајте да варирате температуру, пробајте да је поставите на 0, 0.5 и 1. Запамтите да је 0 најмање разноврсно, а 1 најразноврсније. Која вредност најбоље функционише за вашу апликацију?

## Одличан рад! Наставите са учењем

Након што завршите ову лекцију, погледајте нашу [Збирку за учење о генеративној вештачкој интелигенцији](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst) да наставите са унапређењем знања о генеративној вештачкој интелигенцији!

Прелазите на лекцију 7 где ћемо погледати како да [направимо апликације за ћаскање](../07-building-chat-applications/README.md?WT.mc_id=academic-105485-koreyst)!

---

**Одрицање од одговорности**:  
Овај документ је преведен помоћу услуге за превођење вештачке интелигенције [Co-op Translator](https://github.com/Azure/co-op-translator). Иако настојимо да обезбедимо тачност, молимо вас да имате у виду да аутоматски преводи могу садржати грешке или нетачности. Оригинални документ на изворном језику треба сматрати меродавним извором. За критичне информације препоручује се професионални превод од стране људи. Не преузимамо одговорност за било каква погрешна тумачења или неспоразуме који могу настати услед коришћења овог превода.