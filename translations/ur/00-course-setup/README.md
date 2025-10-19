<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-17T23:18:22+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "ur"
}
-->
# اس کورس کے ساتھ شروعات کریں

ہم بہت خوش ہیں کہ آپ اس کورس کو شروع کر رہے ہیں اور دیکھیں گے کہ آپ جنریٹو اے آئی کے ساتھ کیا تخلیق کرنے کی تحریک حاصل کرتے ہیں!

آپ کی کامیابی کو یقینی بنانے کے لیے، اس صفحے میں سیٹ اپ کے مراحل، تکنیکی ضروریات، اور مدد حاصل کرنے کے طریقے بیان کیے گئے ہیں۔

## سیٹ اپ کے مراحل

اس کورس کو شروع کرنے کے لیے، آپ کو درج ذیل مراحل مکمل کرنے کی ضرورت ہوگی۔

### 1. اس ریپو کو فورک کریں

[اس پورے ریپو کو فورک کریں](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) اپنے GitHub اکاؤنٹ پر تاکہ آپ کوڈ میں تبدیلیاں کر سکیں اور چیلنجز مکمل کر سکیں۔ آپ اس ریپو کو [اسٹار (🌟)](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) بھی کر سکتے ہیں تاکہ اسے اور متعلقہ ریپوز کو آسانی سے تلاش کر سکیں۔

### 2. ایک کوڈ اسپیس بنائیں

کوڈ چلانے کے دوران کسی بھی ڈپینڈنسی مسائل سے بچنے کے لیے، ہم تجویز کرتے ہیں کہ آپ اس کورس کو [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst) میں چلائیں۔

اپنے فورک میں: **Code -> Codespaces -> New on main**

![ڈائیلاگ جو کوڈ اسپیس بنانے کے بٹن دکھا رہا ہے](../../../00-course-setup/images/who-will-pay.webp)

#### 2.1 ایک سیکریٹ شامل کریں

1. ⚙️ گیئر آئیکن -> کمانڈ پیلیٹ -> Codespaces : Manage user secret -> ایک نیا سیکریٹ شامل کریں۔
2. نام OPENAI_API_KEY، اپنی کلید پیسٹ کریں، محفوظ کریں۔

### 3. آگے کیا ہے؟

| میں یہ کرنا چاہتا ہوں… | جائیں…                                                                 |
|-----------------------|------------------------------------------------------------------------|
| سبق 1 شروع کریں       | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)   |
| آف لائن کام کریں      | [`setup-local.md`](02-setup-local.md)                                 |
| ایک LLM فراہم کنندہ سیٹ اپ کریں | [`providers.md`](03-providers.md)                                      |
| دوسرے سیکھنے والوں سے ملیں | [ہمارے Discord میں شامل ہوں](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) |

## مسائل کا حل

| علامت                                    | حل                                                              |
|------------------------------------------|-----------------------------------------------------------------|
| کنٹینر بلڈ > 10 منٹ تک رکا ہوا ہے         | **Codespaces ➜ “Rebuild Container”**                            |
| `python: command not found`              | ٹرمینل منسلک نہیں ہوا؛ **+** ➜ *bash* پر کلک کریں               |
| OpenAI سے `401 Unauthorized`             | غلط / ختم شدہ `OPENAI_API_KEY`                                 |
| VS Code "Dev container mounting…" دکھاتا ہے | براؤزر ٹیب کو ریفریش کریں—Codespaces کبھی کبھار کنکشن کھو دیتا ہے |
| نوٹ بک کرنل غائب ہے                      | نوٹ بک مینو ➜ **Kernel ▸ Select Kernel ▸ Python 3**             |

   یونکس پر مبنی سسٹمز:

   ```bash
   touch .env
   ```

   ونڈوز:

   ```cmd
   echo . > .env
   ```

3. **`.env` فائل میں ترمیم کریں**: `.env` فائل کو کسی ٹیکسٹ ایڈیٹر (جیسے VS Code، Notepad++، یا کوئی اور ایڈیٹر) میں کھولیں۔ فائل میں درج ذیل لائن شامل کریں، `your_github_token_here` کو اپنے اصل GitHub ٹوکن سے تبدیل کریں:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```

4. **فائل محفوظ کریں**: تبدیلیاں محفوظ کریں اور ٹیکسٹ ایڈیٹر بند کریں۔

5. **`python-dotenv` انسٹال کریں**: اگر آپ نے پہلے سے انسٹال نہیں کیا ہے، تو آپ کو `.env` فائل سے اپنے Python ایپلیکیشن میں ماحولیات کے متغیرات لوڈ کرنے کے لیے `python-dotenv` پیکیج انسٹال کرنا ہوگا۔ آپ اسے `pip` کے ذریعے انسٹال کر سکتے ہیں:

   ```bash
   pip install python-dotenv
   ```

6. **اپنے Python اسکرپٹ میں ماحولیات کے متغیرات لوڈ کریں**: اپنے Python اسکرپٹ میں، `.env` فائل سے ماحولیات کے متغیرات لوڈ کرنے کے لیے `python-dotenv` پیکیج استعمال کریں:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```

یہی ہے! آپ نے کامیابی سے `.env` فائل بنائی، اپنا GitHub ٹوکن شامل کیا، اور اسے اپنے Python ایپلیکیشن میں لوڈ کیا۔

## اپنے کمپیوٹر پر مقامی طور پر چلانے کا طریقہ

کوڈ کو اپنے کمپیوٹر پر مقامی طور پر چلانے کے لیے، آپ کو [Python کا کوئی ورژن انسٹال](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst) کرنا ہوگا۔

پھر ریپوزٹری استعمال کرنے کے لیے، آپ کو اسے کلون کرنا ہوگا:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

جب آپ کے پاس سب کچھ چیک آؤٹ ہو جائے، تو آپ شروع کر سکتے ہیں!

## اختیاری مراحل

### Miniconda انسٹال کرنا

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst)، Python، اور کچھ پیکیجز انسٹال کرنے کے لیے ایک ہلکا پھلکا انسٹالر ہے۔
Conda خود ایک پیکیج مینیجر ہے، جو مختلف Python [**ورچوئل ماحولیات**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) اور پیکیجز کو سیٹ اپ اور سوئچ کرنا آسان بناتا ہے۔ یہ ان پیکیجز کو انسٹال کرنے میں بھی مددگار ثابت ہوتا ہے جو `pip` کے ذریعے دستیاب نہیں ہیں۔

آپ [MiniConda انسٹالیشن گائیڈ](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst) کی پیروی کر کے اسے سیٹ اپ کر سکتے ہیں۔

Miniconda انسٹال کرنے کے بعد، آپ کو [ریپوزٹری](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) کلون کرنے کی ضرورت ہوگی (اگر آپ نے پہلے سے نہیں کیا ہے)

اس کے بعد، آپ کو ایک ورچوئل ماحول بنانا ہوگا۔ Conda کے ساتھ ایسا کرنے کے لیے، آگے بڑھیں اور ایک نیا ماحول فائل (_environment.yml_) بنائیں۔ اگر آپ Codespaces استعمال کر رہے ہیں، تو اسے `.devcontainer` ڈائریکٹری میں بنائیں، یعنی `.devcontainer/environment.yml`۔

اپنے ماحول فائل کو نیچے دیے گئے اسنیپٹ سے بھر دیں:

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

اگر آپ کو conda استعمال کرتے وقت غلطیاں ملتی ہیں تو آپ مائیکروسافٹ AI لائبریریوں کو دستی طور پر درج ذیل کمانڈ کے ذریعے انسٹال کر سکتے ہیں:

```
conda install -c microsoft azure-ai-ml
```

ماحول فائل ان ڈپینڈنسیز کو بیان کرتی ہے جن کی ہمیں ضرورت ہے۔ `<environment-name>` اس نام کی طرف اشارہ کرتا ہے جسے آپ اپنے Conda ماحول کے لیے استعمال کرنا چاہتے ہیں، اور `<python-version>` Python کے اس ورژن کی طرف اشارہ کرتا ہے جسے آپ استعمال کرنا چاہتے ہیں، مثال کے طور پر، `3` Python کا تازہ ترین بڑا ورژن ہے۔

یہ مکمل ہونے کے بعد، آپ اپنے Conda ماحول کو کمانڈ لائن/ٹرمینل میں درج ذیل کمانڈز چلا کر بنا سکتے ہیں:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

اگر آپ کو کسی مسئلے کا سامنا ہو تو [Conda ماحولیات گائیڈ](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst) کا حوالہ دیں۔

### Python سپورٹ ایکسٹینشن کے ساتھ Visual Studio Code کا استعمال

ہم تجویز کرتے ہیں کہ اس کورس کے لیے [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) ایڈیٹر کا استعمال کریں جس میں [Python سپورٹ ایکسٹینشن](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) انسٹال ہو۔ تاہم، یہ صرف ایک تجویز ہے اور کوئی حتمی ضرورت نہیں۔

> **نوٹ**: کورس ریپوزٹری کو VS Code میں کھول کر، آپ کے پاس پروجیکٹ کو کنٹینر کے اندر سیٹ اپ کرنے کا آپشن ہوگا۔ یہ کورس ریپوزٹری میں موجود [خاص `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) ڈائریکٹری کی وجہ سے ہے۔ اس پر مزید بعد میں۔

> **نوٹ**: جب آپ ریپوزٹری کو کلون کریں اور اسے VS Code میں کھولیں، تو یہ خود بخود آپ کو Python سپورٹ ایکسٹینشن انسٹال کرنے کی تجویز دے گا۔

> **نوٹ**: اگر VS Code آپ کو ریپوزٹری کو کنٹینر میں دوبارہ کھولنے کی تجویز دے، تو اس درخواست کو مسترد کریں تاکہ Python کے مقامی طور پر انسٹال شدہ ورژن کو استعمال کیا جا سکے۔

### براؤزر میں Jupyter کا استعمال

آپ پروجیکٹ پر [Jupyter ماحول](https://jupyter.org?WT.mc_id=academic-105485-koreyst) کو براہ راست اپنے براؤزر میں استعمال کرتے ہوئے بھی کام کر سکتے ہیں۔ کلاسک Jupyter اور [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) دونوں ایک خوشگوار ترقیاتی ماحول فراہم کرتے ہیں جس میں آٹو کمپلیشن، کوڈ ہائی لائٹنگ، وغیرہ جیسی خصوصیات شامل ہیں۔

Jupyter کو مقامی طور پر شروع کرنے کے لیے، ٹرمینل/کمانڈ لائن پر جائیں، کورس ڈائریکٹری پر جائیں، اور درج ذیل کمانڈ چلائیں:

```bash
jupyter notebook
```

یا

```bash
jupyterhub
```

یہ Jupyter انسٹینس شروع کرے گا اور URL کمانڈ لائن ونڈو میں دکھایا جائے گا۔

جب آپ URL تک رسائی حاصل کریں گے، تو آپ کورس کا خاکہ دیکھ سکیں گے اور کسی بھی `*.ipynb` فائل پر جا سکیں گے۔ مثال کے طور پر، `08-building-search-applications/python/oai-solution.ipynb`۔

### کنٹینر میں چلانا

اپنے کمپیوٹر یا Codespace پر سب کچھ سیٹ اپ کرنے کا ایک متبادل طریقہ یہ ہے کہ [کنٹینر](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>) استعمال کریں۔ کورس ریپوزٹری کے اندر موجود خاص `.devcontainer` فولڈر VS Code کو پروجیکٹ کو کنٹینر کے اندر سیٹ اپ کرنے کے قابل بناتا ہے۔ Codespaces کے باہر، اس کے لیے Docker کی انسٹالیشن کی ضرورت ہوگی، اور یہ کافی کام شامل کرتا ہے، لہذا ہم اسے صرف ان لوگوں کے لیے تجویز کرتے ہیں جنہیں کنٹینرز کے ساتھ کام کرنے کا تجربہ ہے۔

GitHub Codespaces استعمال کرتے وقت اپنے API کیز کو محفوظ رکھنے کے بہترین طریقوں میں سے ایک Codespace Secrets کا استعمال ہے۔ براہ کرم [Codespaces سیکریٹس مینجمنٹ](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst) گائیڈ کو فالو کریں تاکہ مزید معلومات حاصل کی جا سکیں۔

## اسباق اور تکنیکی ضروریات

کورس میں 6 تصوراتی اسباق اور 6 کوڈنگ اسباق شامل ہیں۔

کوڈنگ اسباق کے لیے، ہم Azure OpenAI Service استعمال کر رہے ہیں۔ آپ کو Azure OpenAI سروس تک رسائی اور اس کوڈ کو چلانے کے لیے ایک API کلید کی ضرورت ہوگی۔ آپ [یہ درخواست مکمل کر کے](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst) رسائی حاصل کرنے کے لیے درخواست دے سکتے ہیں۔

جب تک آپ کی درخواست پر کارروائی ہو رہی ہو، ہر کوڈنگ سبق میں ایک `README.md` فائل بھی شامل ہے جہاں آپ کوڈ اور آؤٹ پٹس دیکھ سکتے ہیں۔

## پہلی بار Azure OpenAI سروس کا استعمال

اگر یہ آپ کا پہلی بار Azure OpenAI سروس کے ساتھ کام ہے، تو براہ کرم اس گائیڈ کو فالو کریں کہ [Azure OpenAI سروس ریسورس کیسے بنائیں اور ڈیپلائے کریں۔](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst)

## پہلی بار OpenAI API کا استعمال

اگر یہ آپ کا پہلی بار OpenAI API کے ساتھ کام ہے، تو براہ کرم اس گائیڈ کو فالو کریں کہ [انٹرفیس کیسے بنائیں اور استعمال کریں۔](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst)

## دوسرے سیکھنے والوں سے ملیں

ہم نے اپنے آفیشل [AI کمیونٹی Discord سرور](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) میں دوسرے سیکھنے والوں سے ملنے کے لیے چینلز بنائے ہیں۔ یہ جنریٹو اے آئی میں مہارت حاصل کرنے کے خواہشمند دیگر ہم خیال کاروباری افراد، بلڈرز، طلباء، اور کسی بھی شخص کے ساتھ نیٹ ورک بنانے کا ایک بہترین طریقہ ہے۔

[![ڈسکارڈ چینل میں شامل ہوں](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

پروجیکٹ ٹیم بھی اس Discord سرور پر موجود ہوگی تاکہ کسی بھی سیکھنے والے کی مدد کی جا سکے۔

## تعاون کریں

یہ کورس ایک اوپن سورس اقدام ہے۔ اگر آپ کو بہتری کے مواقع یا مسائل نظر آئیں، تو براہ کرم ایک [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) بنائیں یا ایک [GitHub مسئلہ](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst) لاگ کریں۔

پروجیکٹ ٹیم تمام تعاون کو ٹریک کرے گی۔ اوپن سورس میں تعاون کرنا جنریٹو اے آئی میں اپنے کیریئر کو بنانے کا ایک حیرت انگیز طریقہ ہے۔

زیادہ تر تعاون کے لیے آپ کو ایک Contributor License Agreement (CLA) پر اتفاق کرنا ہوگا جس میں یہ اعلان کیا جائے گا کہ آپ کے پاس اپنے تعاون کے حقوق دینے کا حق ہے اور آپ واقعی ایسا کرتے ہیں۔ تفصیلات کے لیے [CLA، Contributor License Agreement ویب سائٹ](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst) دیکھیں۔

اہم: اس ریپو میں متن کا ترجمہ کرتے وقت، براہ کرم مشین ترجمہ استعمال نہ کریں۔ ہم کمیونٹی کے ذریعے ترجمے کی تصدیق کریں گے، لہذا براہ کرم صرف ان زبانوں میں ترجمے کے لیے رضاکار بنیں جن میں آپ ماہر ہیں۔

جب آپ ایک Pull Request جمع کراتے ہیں، تو CLA-bot خود بخود یہ طے کرے گا کہ آیا آپ کو CLA فراہم کرنے کی ضرورت ہے اور PR کو مناسب طریقے سے سجائے گا (جیسے، لیبل، تبصرہ)۔ بس بوٹ کی فراہم کردہ ہدایات پر عمل کریں۔ آپ کو یہ صرف ایک بار تمام ریپوزٹریز میں کرنا ہوگا جو ہمارے CLA استعمال کرتے ہیں۔

اس پروجیکٹ نے [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst) کو اپنایا ہے۔ مزید معلومات کے لیے Code of Conduct FAQ پڑھیں یا [Email opencode](opencode@microsoft.com) پر کسی بھی اضافی سوالات یا تبصروں کے ساتھ رابطہ کریں۔

## شروع کریں
اب جب کہ آپ نے اس کورس کو مکمل کرنے کے لیے ضروری مراحل مکمل کر لیے ہیں، آئیے شروع کرتے ہیں اور [جنریٹو AI اور LLMs کا تعارف](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst) حاصل کرتے ہیں۔

---

**ڈسکلیمر**:  
یہ دستاویز AI ترجمہ سروس [Co-op Translator](https://github.com/Azure/co-op-translator) کا استعمال کرتے ہوئے ترجمہ کی گئی ہے۔ ہم درستگی کے لیے کوشش کرتے ہیں، لیکن براہ کرم آگاہ رہیں کہ خودکار ترجمے میں غلطیاں یا غیر درستیاں ہو سکتی ہیں۔ اصل دستاویز کو اس کی اصل زبان میں مستند ذریعہ سمجھا جانا چاہیے۔ اہم معلومات کے لیے، پیشہ ور انسانی ترجمہ کی سفارش کی جاتی ہے۔ ہم اس ترجمے کے استعمال سے پیدا ہونے والی کسی بھی غلط فہمی یا غلط تشریح کے ذمہ دار نہیں ہیں۔