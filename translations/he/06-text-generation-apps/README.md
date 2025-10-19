<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "df027997f1448323d6159b78a1b669bf",
  "translation_date": "2025-10-17T20:00:07+00:00",
  "source_file": "06-text-generation-apps/README.md",
  "language_code": "he"
}
-->
# בניית יישומי יצירת טקסט

[![בניית יישומי יצירת טקסט](../../../translated_images/06-lesson-banner.a5c629f990a636c852353c5533f1a6a218ece579005e91f96339d508d9cf8f47.he.png)](https://youtu.be/0Y5Luf5sRQA?si=t_xVg0clnAI4oUFZ)

> _(לחצו על התמונה למעלה לצפייה בסרטון של השיעור הזה)_

עד כה ראיתם דרך תוכנית הלימודים הזו שישנם מושגים מרכזיים כמו הנחיות ואפילו תחום שלם שנקרא "הנדסת הנחיות". כלים רבים שתוכלו לתקשר איתם כמו ChatGPT, Office 365, Microsoft Power Platform ועוד, תומכים בשימוש בהנחיות כדי להשיג משהו.

כדי להוסיף חוויה כזו ליישום, עליכם להבין מושגים כמו הנחיות, השלמות ולבחור ספרייה לעבוד איתה. בדיוק את זה תלמדו בפרק הזה.

## מבוא

בפרק הזה תלמדו:

- על ספריית openai והמושגים המרכזיים שלה.
- כיצד לבנות יישום יצירת טקסט באמצעות openai.
- להבין כיצד להשתמש במושגים כמו הנחיה, טמפרטורה וטוקנים כדי לבנות יישום יצירת טקסט.

## מטרות למידה

בסוף השיעור הזה תוכלו:

- להסביר מהו יישום יצירת טקסט.
- לבנות יישום יצירת טקסט באמצעות openai.
- להגדיר את היישום שלכם לשימוש ביותר או פחות טוקנים וגם לשנות את הטמפרטורה, לתוצאה מגוונת.

## מהו יישום יצירת טקסט?

בדרך כלל כשאתם בונים יישום יש לו סוג כלשהו של ממשק כמו הבא:

- מבוסס פקודות. יישומי קונסולה הם יישומים טיפוסיים שבהם אתם מקלידים פקודה והיא מבצעת משימה. לדוגמה, `git` הוא יישום מבוסס פקודות.
- ממשק משתמש (UI). ישנם יישומים עם ממשקי משתמש גרפיים (GUIs) שבהם אתם לוחצים על כפתורים, מזינים טקסט, בוחרים אפשרויות ועוד.

### יישומי קונסולה ו-UI מוגבלים

השוו את זה ליישום מבוסס פקודות שבו אתם מקלידים פקודה:

- **זה מוגבל**. אתם לא יכולים פשוט להקליד כל פקודה, רק את אלו שהיישום תומך בהן.
- **תלוי שפה**. יש יישומים שתומכים בשפות רבות, אבל כברירת מחדל היישום נבנה לשפה מסוימת, גם אם ניתן להוסיף תמיכה בשפות נוספות.

### יתרונות של יישומי יצירת טקסט

אז איך יישום יצירת טקסט שונה?

ביישום יצירת טקסט, יש לכם יותר גמישות, אתם לא מוגבלים למערכת פקודות או לשפת קלט מסוימת. במקום זאת, אתם יכולים להשתמש בשפה טבעית כדי לתקשר עם היישום. יתרון נוסף הוא שאתם כבר מתקשרים עם מקור נתונים שאומן על מאגר מידע רחב, בעוד שיישום מסורתי עשוי להיות מוגבל למה שיש בבסיס הנתונים.

### מה אפשר לבנות עם יישום יצירת טקסט?

יש הרבה דברים שאפשר לבנות. לדוגמה:

- **צ'אטבוט**. צ'אטבוט שעונה על שאלות בנושאים כמו החברה שלכם והמוצרים שלה יכול להיות מתאים.
- **עוזר**. מודלים שפתיים גדולים (LLMs) מצוינים בדברים כמו סיכום טקסט, הפקת תובנות מטקסט, יצירת טקסט כמו קורות חיים ועוד.
- **עוזר קוד**. בהתאם למודל השפה שבו אתם משתמשים, תוכלו לבנות עוזר קוד שיעזור לכם לכתוב קוד. לדוגמה, תוכלו להשתמש במוצר כמו GitHub Copilot וגם ב-ChatGPT כדי לעזור לכם לכתוב קוד.

## איך מתחילים?

ובכן, עליכם למצוא דרך להשתלב עם מודל שפה גדול (LLM), מה שבדרך כלל כרוך בשתי גישות:

- שימוש ב-API. כאן אתם בונים בקשות רשת עם ההנחיה שלכם ומקבלים טקסט שנוצר בחזרה.
- שימוש בספרייה. ספריות עוזרות לעטוף את קריאות ה-API ולהפוך אותן לקלות יותר לשימוש.

## ספריות/SDKs

ישנן כמה ספריות ידועות לעבודה עם מודלים שפתיים גדולים כמו:

- **openai**, ספרייה זו מקלה על החיבור למודל שלכם ושליחת הנחיות.

ואז יש ספריות שפועלות ברמה גבוהה יותר כמו:

- **Langchain**. Langchain ידועה ותומכת ב-Python.
- **Semantic Kernel**. Semantic Kernel היא ספרייה של Microsoft שתומכת בשפות C#, Python ו-Java.

## יישום ראשון באמצעות openai

בואו נראה איך אפשר לבנות את היישום הראשון שלנו, אילו ספריות נדרשות, כמה נדרש ועוד.

### התקנת openai

ישנן ספריות רבות שם בחוץ לתקשורת עם OpenAI או Azure OpenAI. ניתן להשתמש בשפות תכנות רבות כמו C#, Python, JavaScript, Java ועוד. בחרנו להשתמש בספריית Python `openai`, ולכן נשתמש ב-`pip` כדי להתקין אותה.

```bash
pip install openai
```

### יצירת משאב

עליכם לבצע את השלבים הבאים:

- ליצור חשבון ב-Azure [https://azure.microsoft.com/free/](https://azure.microsoft.com/free/?WT.mc_id=academic-105485-koreyst).
- לקבל גישה ל-Azure OpenAI. עברו ל-[https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai](https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai?WT.mc_id=academic-105485-koreyst) ובקשו גישה.

  > [!NOTE]
  > נכון לזמן הכתיבה, עליכם להגיש בקשה לגישה ל-Azure OpenAI.

- התקינו Python <https://www.python.org/>
- צרו משאב שירות Azure OpenAI. ראו מדריך זה כיצד [ליצור משאב](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal?WT.mc_id=academic-105485-koreyst).

### איתור מפתח API ונקודת קצה

בשלב זה, עליכם להגדיר לספריית `openai` שלכם איזה מפתח API להשתמש. כדי למצוא את מפתח ה-API שלכם, עברו לקטע "Keys and Endpoint" במשאב Azure OpenAI שלכם והעתיקו את הערך "Key 1".

![Keys and Endpoint resource blade in Azure Portal](https://learn.microsoft.com/azure/ai-services/openai/media/quickstarts/endpoint.png?WT.mc_id=academic-105485-koreyst)

עכשיו שיש לכם את המידע הזה, בואו ננחה את הספריות להשתמש בו.

> [!NOTE]
> כדאי להפריד את מפתח ה-API שלכם מהקוד. ניתן לעשות זאת באמצעות משתני סביבה.
>
> - הגדירו את משתנה הסביבה `OPENAI_API_KEY` למפתח ה-API שלכם.
>   `export OPENAI_API_KEY='sk-...'`

### הגדרת תצורה Azure

אם אתם משתמשים ב-Azure OpenAI, כך תגדירו תצורה:

```python
openai.api_type = 'azure'
openai.api_key = os.environ["OPENAI_API_KEY"]
openai.api_version = '2023-05-15'
openai.api_base = os.getenv("API_BASE")
```

למעלה אנחנו מגדירים את הדברים הבאים:

- `api_type` ל-`azure`. זה אומר לספרייה להשתמש ב-Azure OpenAI ולא ב-OpenAI.
- `api_key`, זהו מפתח ה-API שלכם שנמצא בפורטל Azure.
- `api_version`, זו גרסת ה-API שאתם רוצים להשתמש בה. נכון לזמן הכתיבה, הגרסה האחרונה היא `2023-05-15`.
- `api_base`, זו נקודת הקצה של ה-API. ניתן למצוא אותה בפורטל Azure ליד מפתח ה-API שלכם.

> [!NOTE] > `os.getenv` היא פונקציה שקוראת משתני סביבה. ניתן להשתמש בה כדי לקרוא משתני סביבה כמו `OPENAI_API_KEY` ו-`API_BASE`. הגדירו את משתני הסביבה האלה בטרמינל שלכם או באמצעות ספרייה כמו `dotenv`.

## יצירת טקסט

הדרך ליצור טקסט היא להשתמש במחלקה `Completion`. הנה דוגמה:

```python
prompt = "Complete the following: Once upon a time there was a"

completion = openai.Completion.create(model="davinci-002", prompt=prompt)
print(completion.choices[0].text)
```

בקוד למעלה, אנחנו יוצרים אובייקט השלמה ומעבירים את המודל שאנחנו רוצים להשתמש בו ואת ההנחיה. לאחר מכן אנחנו מדפיסים את הטקסט שנוצר.

### השלמות צ'אט

עד כה, ראיתם איך אנחנו משתמשים ב-`Completion` כדי ליצור טקסט. אבל יש מחלקה נוספת שנקראת `ChatCompletion` שמתאימה יותר לצ'אטבוטים. הנה דוגמה לשימוש בה:

```python
import openai

openai.api_key = "sk-..."

completion = openai.ChatCompletion.create(model="gpt-3.5-turbo", messages=[{"role": "user", "content": "Hello world"}])
print(completion.choices[0].message.content)
```

עוד על פונקציונליות זו בפרק הבא.

## תרגיל - יישום יצירת הטקסט הראשון שלכם

עכשיו שלמדנו איך להגדיר ולתצורת openai, הגיע הזמן לבנות את יישום יצירת הטקסט הראשון שלכם. כדי לבנות את היישום שלכם, בצעו את השלבים הבאים:

1. צרו סביבה וירטואלית והתקינו openai:

   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install openai
   ```

   > [!NOTE]
   > אם אתם משתמשים ב-Windows הקלידו `venv\Scripts\activate` במקום `source venv/bin/activate`.

   > [!NOTE]
   > מצאו את מפתח Azure OpenAI שלכם על ידי מעבר ל-[https://portal.azure.com/](https://portal.azure.com/?WT.mc_id=academic-105485-koreyst) וחיפוש `Open AI`, בחרו את `Open AI resource` ואז בחרו `Keys and Endpoint` והעתיקו את הערך `Key 1`.

1. צרו קובץ _app.py_ ותנו לו את הקוד הבא:

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
   > אם אתם משתמשים ב-Azure OpenAI, עליכם להגדיר את `api_type` ל-`azure` ולהגדיר את `api_key` למפתח Azure OpenAI שלכם.

   אתם אמורים לראות פלט כמו הבא:

   ```output
    very unhappy _____.

   Once upon a time there was a very unhappy mermaid.
   ```

## סוגים שונים של הנחיות, לדברים שונים

עכשיו ראיתם איך ליצור טקסט באמצעות הנחיה. יש לכם אפילו תוכנית פועלת שתוכלו לשנות ולהתאים כדי ליצור סוגים שונים של טקסט.

ניתן להשתמש בהנחיות לכל מיני משימות. לדוגמה:

- **יצירת סוג טקסט**. לדוגמה, ניתן ליצור שיר, שאלות לחידון וכו'.
- **חיפוש מידע**. ניתן להשתמש בהנחיות לחיפוש מידע כמו הדוגמה הבאה 'מה המשמעות של CORS בפיתוח אתרים?'.
- **יצירת קוד**. ניתן להשתמש בהנחיות ליצירת קוד, לדוגמה פיתוח ביטוי רגולרי המשמש לאימות אימיילים או אפילו יצירת תוכנית שלמה, כמו יישום אינטרנט.

## שימוש מעשי יותר: מחולל מתכונים

דמיינו שיש לכם מרכיבים בבית ואתם רוצים לבשל משהו. לשם כך, אתם צריכים מתכון. דרך למצוא מתכונים היא להשתמש במנוע חיפוש או שתוכלו להשתמש במודל שפה גדול (LLM) לשם כך.

תוכלו לכתוב הנחיה כמו כך:

> "הראה לי 5 מתכונים למנה עם המרכיבים הבאים: עוף, תפוחי אדמה וגזר. עבור כל מתכון, רשום את כל המרכיבים המשמשים"

בהתחשב בהנחיה לעיל, ייתכן שתקבלו תגובה דומה ל:

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

תוצאה זו נהדרת, אני יודע מה לבשל. בשלב זה, מה שיכול להיות שיפורים שימושיים הם:

- סינון מרכיבים שאני לא אוהב או שאליהם אני אלרגי.
- יצירת רשימת קניות, במקרה שאין לי את כל המרכיבים בבית.

למקרים לעיל, בואו נוסיף הנחיה נוספת:

> "אנא הסר מתכונים עם שום כי אני אלרגי והחלף אותו במשהו אחר. כמו כן, אנא צור רשימת קניות עבור המתכונים, בהתחשב בכך שכבר יש לי עוף, תפוחי אדמה וגזר בבית."

עכשיו יש לכם תוצאה חדשה, כלומר:

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

אלו חמשת המתכונים שלכם, ללא שום מוזכר וגם יש לכם רשימת קניות בהתחשב במה שכבר יש לכם בבית.

## תרגיל - בניית מחולל מתכונים

עכשיו ששיחקנו תרחיש, בואו נכתוב קוד שיתאים לתרחיש שהודגם. כדי לעשות זאת, בצעו את השלבים הבאים:

1. השתמשו בקובץ _app.py_ הקיים כנקודת התחלה
1. מצאו את המשתנה `prompt` ושנו את הקוד שלו ל:

   ```python
   prompt = "Show me 5 recipes for a dish with the following ingredients: chicken, potatoes, and carrots. Per recipe, list all the ingredients used"
   ```

   אם עכשיו תפעילו את הקוד, אתם אמורים לראות פלט דומה ל:

   ```output
   -Chicken Stew with Potatoes and Carrots: 3 tablespoons oil, 1 onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 1/2 cups chicken broth, 1/2 cup dry white wine, 2 tablespoons chopped fresh parsley, 2 tablespoons unsalted butter, 1 1/2 pounds boneless, skinless chicken thighs, cut into 1-inch pieces
   -Oven-Roasted Chicken with Potatoes and Carrots: 3 tablespoons extra-virgin olive oil, 1 tablespoon Dijon mustard, 1 tablespoon chopped fresh rosemary, 1 tablespoon chopped fresh thyme, 4 cloves garlic, minced, 1 1/2 pounds small red potatoes, quartered, 1 1/2 pounds carrots, quartered lengthwise, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 (4-pound) whole chicken
   -Chicken, Potato, and Carrot Casserole: cooking spray, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and shredded, 1 potato, peeled and shredded, 1/2 teaspoon dried thyme leaves, 1/4 teaspoon salt, 1/4 teaspoon black pepper, 2 cups fat-free, low-sodium chicken broth, 1 cup frozen peas, 1/4 cup all-purpose flour, 1 cup 2% reduced-fat milk, 1/4 cup grated Parmesan cheese

   -One Pot Chicken and Potato Dinner: 2 tablespoons olive oil, 1 pound boneless, skinless chicken thighs, cut into 1-inch pieces, 1 large onion, chopped, 3 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 2 cups chicken broth, 1/2 cup dry white wine

   -Chicken, Potato, and Carrot Curry: 1 tablespoon vegetable oil, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 teaspoon ground coriander, 1 teaspoon ground cumin, 1/2 teaspoon ground turmeric, 1/2 teaspoon ground ginger, 1/4 teaspoon cayenne pepper, 2 cups chicken broth, 1/2 cup dry white wine, 1 (15-ounce) can chickpeas, drained and rinsed, 1/2 cup raisins, 1/2 cup chopped fresh cilantro
   ```

   > שימו לב, המודל השפתי שלכם הוא לא דטרמיניסטי, כך שייתכן שתקבלו תוצאות שונות בכל פעם שתפעילו את התוכנית.

   נהדר, בואו נראה איך אפשר לשפר דברים. כדי לשפר דברים, אנחנו רוצים לוודא שהקוד גמיש, כך שניתן לשפר ולשנות את המרכיבים ואת מספר המתכונים.

1. בואו נשנה את הקוד בדרך הבאה:

   ```python
   no_recipes = input("No of recipes (for example, 5): ")

   ingredients = input("List of ingredients (for example, chicken, potatoes, and carrots): ")

   # interpolate the number of recipes into the prompt an ingredients
   prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used"
   ```

   הפעלת הקוד לבדיקה יכולה להיראות כך:

   ```output
   No of recipes (for example, 5): 3
   List of ingredients (for example, chicken, potatoes, and carrots): milk,strawberries

   -Strawberry milk shake: milk, strawberries, sugar, vanilla extract, ice cubes
   -Strawberry shortcake: milk, flour, baking powder, sugar, salt, unsalted butter, strawberries, whipped cream
   -Strawberry milk: milk, strawberries, sugar, vanilla extract
   ```

### שיפור על ידי הוספת סינון ורשימת קניות

עכשיו יש לנו יישום עובד שמסוגל לייצר מתכונים והוא גמיש מכיוון שהוא מסתמך על קלטים מהמשתמש, הן על מספר המתכונים והן על המרכיבים המשמשים.

כדי לשפר אותו עוד יותר, אנחנו רוצים להוסיף את הדברים הבאים:

- **סינון מרכיבים**. אנחנו רוצים להיות מסוגלים לסנן מרכיבים שאנחנו לא אוהבים או שאליהם אנחנו אלרגיים. כדי לבצע שינוי זה, נוכל לערוך את ההנחיה הקיימת שלנו ולהוסיף תנאי סינון בסופה כמו כך:

  ```python
  filter = input("Filter (for example, vegetarian, vegan, or gluten-free): ")

  prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used, no {filter}"
  ```

  למעלה, אנחנו מוסיפים `{filter}` לסוף ההנחיה ואנחנו גם לוכדים את ערך הסינון מהמשתמש.

  דוגמה לקלט של הפעלת התוכנית יכולה להיראות כך:

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

  כפי שאתם רואים, כל מתכון עם חלב בו סונן החוצה. אבל, אם אתם רגישים ללקטוז, ייתכן שתרצו לסנן גם מתכונים עם גבינה בהם, כך שיש צורך להיות ברורים.

- **יצירת רשימת קניות**. אנחנו רוצים ליצור רשימת קניות, בהתחשב במה שכבר יש לנו בבית.

  עבור פונקציונליות זו, נוכל לנסות לפתור הכל בהנחיה אחת או שנוכל לחלק אותה לשתי הנחיות. בואו ננסה את הגישה השנייה. כאן אנחנו מציעים להוסיף הנחיה נוספת, אבל כדי שזה יעבוד, אנחנו צריכים להוסיף את תוצאת ההנחיה הראשונה כקונטקסט להנחיה השנייה.

  מצאו את החלק בקוד שמדפיס את התוצאה מההנחיה הראשונה והוסיפו את הקוד הבא מתחת:
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

  שימו לב לנקודות הבאות:

  1. אנחנו יוצרים הנחיה חדשה על ידי הוספת התוצאה מההנחיה הראשונה להנחיה החדשה:

     ```python
     new_prompt = f"{old_prompt_result} {prompt}"
     ```

  1. אנחנו מבצעים בקשה חדשה, אך גם מתחשבים במספר הטוקנים שביקשנו בהנחיה הראשונה, ולכן הפעם אנחנו מציינים ש-`max_tokens` הוא 1200.

     ```python
     completion = openai.Completion.create(engine=deployment_name, prompt=new_prompt, max_tokens=1200)
     ```

     לאחר הרצת הקוד הזה, אנחנו מגיעים לתוצאה הבאה:

     ```output
     No of recipes (for example, 5): 2
     List of ingredients (for example, chicken, potatoes, and carrots): apple,flour
     Filter (for example, vegetarian, vegan, or gluten-free): sugar


     -Apple and flour pancakes: 1 cup flour, 1/2 tsp baking powder, 1/2 tsp baking soda, 1/4 tsp salt, 1 tbsp sugar, 1 egg, 1 cup buttermilk or sour milk, 1/4 cup melted butter, 1 Granny Smith apple, peeled and grated
     -Apple fritters: 1-1/2 cups flour, 1 tsp baking powder, 1/4 tsp salt, 1/4 tsp baking soda, 1/4 tsp nutmeg, 1/4 tsp cinnamon, 1/4 tsp allspice, 1/4 cup sugar, 1/4 cup vegetable shortening, 1/4 cup milk, 1 egg, 2 cups shredded, peeled apples
     Shopping list:
     -Flour, baking powder, baking soda, salt, sugar, egg, buttermilk, butter, apple, nutmeg, cinnamon, allspice
     ```

## שפרו את ההגדרות שלכם

מה שיש לנו עד כה הוא קוד שעובד, אבל יש כמה שיפורים שכדאי לבצע כדי לשפר את הדברים עוד יותר. כמה דברים שכדאי לעשות הם:

- **הפרדת סודות מהקוד**, כמו מפתח ה-API. סודות לא צריכים להיות חלק מהקוד ויש לאחסן אותם במקום מאובטח. כדי להפריד סודות מהקוד, ניתן להשתמש במשתני סביבה ובספריות כמו `python-dotenv` כדי לטעון אותם מקובץ. כך זה ייראה בקוד:

  1. צרו קובץ `.env` עם התוכן הבא:

     ```bash
     OPENAI_API_KEY=sk-...
     ```

     > שימו לב, עבור Azure, יש להגדיר את משתני הסביבה הבאים:

     ```bash
     OPENAI_API_TYPE=azure
     OPENAI_API_VERSION=2023-05-15
     OPENAI_API_BASE=<replace>
     ```

     בקוד, תטענו את משתני הסביבה כך:

     ```python
     from dotenv import load_dotenv

     load_dotenv()

     openai.api_key = os.environ["OPENAI_API_KEY"]
     ```

- **מילה על אורך הטוקנים**. כדאי לשקול כמה טוקנים אנחנו צריכים כדי ליצור את הטקסט הרצוי. טוקנים עולים כסף, ולכן כדאי להיות חסכוניים במספר הטוקנים שאנחנו משתמשים בהם. לדוגמה, האם אפשר לנסח את ההנחיה כך שנשתמש בפחות טוקנים?

  כדי לשנות את מספר הטוקנים, ניתן להשתמש בפרמטר `max_tokens`. לדוגמה, אם רוצים להשתמש ב-100 טוקנים, תעשו כך:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, max_tokens=100)
  ```

- **ניסוי עם טמפרטורה**. טמפרטורה היא משהו שלא הזכרנו עד כה אבל היא חשובה להקשר של איך התוכנית שלנו מתפקדת. ככל שערך הטמפרטורה גבוה יותר, התוצאה תהיה יותר אקראית. לעומת זאת, ככל שערך הטמפרטורה נמוך יותר, התוצאה תהיה יותר צפויה. שקלו האם אתם רוצים גיוון בתוצאה או לא.

  כדי לשנות את הטמפרטורה, ניתן להשתמש בפרמטר `temperature`. לדוגמה, אם רוצים להשתמש בטמפרטורה של 0.5, תעשו כך:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, temperature=0.5)
  ```

  > שימו לב, ככל שהערך קרוב ל-1.0, התוצאה תהיה יותר מגוונת.

## משימה

למשימה הזו, אתם יכולים לבחור מה לבנות.

הנה כמה הצעות:

- שפרו את אפליקציית יצירת המתכונים כדי לשפר אותה עוד יותר. נסו לשחק עם ערכי הטמפרטורה וההנחיות כדי לראות מה תוכלו ליצור.
- בנו "חבר ללימודים". אפליקציה זו צריכה להיות מסוגלת לענות על שאלות בנושא מסוים, לדוגמה Python. תוכלו להשתמש בהנחיות כמו "מהו נושא מסוים ב-Python?", או "הראה לי קוד לנושא מסוים" וכו'.
- בוט היסטוריה, הפכו את ההיסטוריה לחיה, הנחו את הבוט לשחק דמות היסטורית מסוימת ושאלו אותו שאלות על חייו וזמנו.

## פתרון

### חבר ללימודים

להלן הנחיה התחלתית, ראו איך תוכלו להשתמש בה ולשפר אותה לפי רצונכם.

```text
- "You're an expert on the Python language

    Suggest a beginner lesson for Python in the following format:

    Format:
    - concepts:
    - brief explanation of the lesson:
    - exercise in code with solutions"
```

### בוט היסטוריה

הנה כמה הנחיות שתוכלו להשתמש בהן:

```text
- "You are Abe Lincoln, tell me about yourself in 3 sentences, and respond using grammar and words like Abe would have used"
- "You are Abe Lincoln, respond using grammar and words like Abe would have used:

   Tell me about your greatest accomplishments, in 300 words"
```

## בדיקת ידע

מה עושה מושג הטמפרטורה?

1. הוא שולט כמה אקראית תהיה התוצאה.
1. הוא שולט כמה גדולה תהיה התשובה.
1. הוא שולט כמה טוקנים ישמשו.

## 🚀 אתגר

בעת עבודה על המשימה, נסו לשנות את הטמפרטורה, נסו להגדיר אותה ל-0, 0.5 ו-1. זכרו ש-0 הוא הכי פחות מגוון ו-1 הוא הכי מגוון. איזה ערך עובד הכי טוב עבור האפליקציה שלכם?

## עבודה מצוינת! המשיכו ללמוד

לאחר שסיימתם את השיעור הזה, בדקו את [אוסף הלמידה של AI גנרטיבי](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst) כדי להמשיך ולהעמיק את הידע שלכם ב-AI גנרטיבי!

עברו לשיעור 7 שבו נלמד איך [לבנות אפליקציות צ'אט](../07-building-chat-applications/README.md?WT.mc_id=academic-105485-koreyst)!

---

**כתב ויתור**:  
מסמך זה תורגם באמצעות שירות תרגום AI [Co-op Translator](https://github.com/Azure/co-op-translator). למרות שאנו שואפים לדיוק, יש להיות מודעים לכך שתרגומים אוטומטיים עשויים להכיל שגיאות או אי דיוקים. המסמך המקורי בשפתו המקורית צריך להיחשב כמקור סמכותי. עבור מידע קריטי, מומלץ להשתמש בתרגום מקצועי אנושי. איננו אחראים לאי הבנות או לפרשנויות שגויות הנובעות משימוש בתרגום זה.