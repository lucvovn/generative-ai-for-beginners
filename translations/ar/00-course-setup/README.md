<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-17T23:05:20+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "ar"
}
-->
# البدء في هذه الدورة

نحن متحمسون جدًا لبدء هذه الدورة ورؤية ما ستلهمك لبنائه باستخدام الذكاء الاصطناعي التوليدي!

لضمان نجاحك، توضح هذه الصفحة خطوات الإعداد والمتطلبات التقنية وأماكن الحصول على المساعدة إذا لزم الأمر.

## خطوات الإعداد

لبدء هذه الدورة، ستحتاج إلى إكمال الخطوات التالية.

### 1. نسخ هذا المستودع

[قم بنسخ هذا المستودع بالكامل](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) إلى حساب GitHub الخاص بك لتتمكن من تعديل أي كود وإكمال التحديات. يمكنك أيضًا [إضافة نجمة (🌟) لهذا المستودع](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) لتسهيل العثور عليه وعلى المستودعات ذات الصلة.

### 2. إنشاء مساحة عمل برمجية

لتجنب أي مشاكل تتعلق بالاعتماديات عند تشغيل الكود، نوصي بتشغيل هذه الدورة في [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst).

في النسخة الخاصة بك: **Code -> Codespaces -> New on main**

![نافذة تظهر أزرار لإنشاء مساحة عمل برمجية](../../../00-course-setup/images/who-will-pay.webp)

#### 2.1 إضافة مفتاح سري

1. ⚙️ أيقونة الترس -> Command Pallete -> Codespaces : Manage user secret -> Add a new secret.
2. اسم OPENAI_API_KEY، قم بلصق المفتاح الخاص بك، ثم احفظ.

### 3. ماذا بعد؟

| أريد أن...          | انتقل إلى...                                                             |
|---------------------|-------------------------------------------------------------------------|
| بدء الدرس الأول      | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)     |
| العمل دون اتصال     | [`setup-local.md`](02-setup-local.md)                                   |
| إعداد مزود LLM      | [`providers.md`](03-providers.md)                                        |
| لقاء متعلمين آخرين  | [انضم إلى Discord الخاص بنا](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)   |

## استكشاف الأخطاء وإصلاحها

| العرض                                   | الحل                                                             |
|-------------------------------------------|-----------------------------------------------------------------|
| بناء الحاوية متوقف > 10 دقائق            | **Codespaces ➜ “Rebuild Container”**                            |
| `python: command not found`               | لم يتم إرفاق الطرفية؛ انقر **+** ➜ *bash*                    |
| `401 Unauthorized` من OpenAI            | مفتاح `OPENAI_API_KEY` خاطئ / منتهي الصلاحية                                |
| VS Code يظهر “Dev container mounting…”   | قم بتحديث علامة التبويب في المتصفح—أحيانًا تفقد Codespaces الاتصال   |
| نواة دفتر الملاحظات مفقودة                   | قائمة دفتر الملاحظات ➜ **Kernel ▸ Select Kernel ▸ Python 3**           |

   أنظمة Unix:

   ```bash
   touch .env
   ```

   Windows:

   ```cmd
   echo . > .env
   ```

3. **تعديل ملف `.env`**: افتح ملف `.env` في محرر نصوص (مثل VS Code، Notepad++، أو أي محرر آخر). أضف السطر التالي إلى الملف، مع استبدال `your_github_token_here` برمز GitHub الخاص بك:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```

4. **احفظ الملف**: احفظ التغييرات وأغلق محرر النصوص.

5. **تثبيت `python-dotenv`**: إذا لم تقم بذلك بالفعل، ستحتاج إلى تثبيت حزمة `python-dotenv` لتحميل متغيرات البيئة من ملف `.env` إلى تطبيق Python الخاص بك. يمكنك تثبيتها باستخدام `pip`:

   ```bash
   pip install python-dotenv
   ```

6. **تحميل متغيرات البيئة في سكريبت Python الخاص بك**: في سكريبت Python الخاص بك، استخدم حزمة `python-dotenv` لتحميل متغيرات البيئة من ملف `.env`:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```

هذا كل شيء! لقد أنشأت بنجاح ملف `.env`، وأضفت رمز GitHub الخاص بك، وقمت بتحميله في تطبيق Python الخاص بك.

## كيفية التشغيل محليًا على جهاز الكمبيوتر الخاص بك

لتشغيل الكود محليًا على جهاز الكمبيوتر الخاص بك، ستحتاج إلى تثبيت نسخة من [Python](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst).

ثم لاستخدام المستودع، تحتاج إلى نسخه:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

بمجرد أن يتم التحقق من كل شيء، يمكنك البدء!

## خطوات اختيارية

### تثبيت Miniconda

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) هو مثبت خفيف لتثبيت [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst)، Python، وبعض الحزم.
Conda نفسها هي مدير حزم، يسهل إعداد والتبديل بين [**البيئات الافتراضية**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) المختلفة لـ Python والحزم. كما أنها مفيدة لتثبيت الحزم التي لا تتوفر عبر `pip`.

يمكنك اتباع [دليل تثبيت MiniConda](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst) لإعدادها.

مع تثبيت Miniconda، تحتاج إلى نسخ [المستودع](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) (إذا لم تقم بذلك بالفعل).

بعد ذلك، تحتاج إلى إنشاء بيئة افتراضية. للقيام بذلك باستخدام Conda، قم بإنشاء ملف بيئة جديد (_environment.yml_). إذا كنت تتابع باستخدام Codespaces، قم بإنشاء هذا داخل دليل `.devcontainer`، وبالتالي `.devcontainer/environment.yml`.

قم بملء ملف البيئة الخاص بك بالمقتطف أدناه:

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

إذا واجهت أخطاء أثناء استخدام conda، يمكنك تثبيت مكتبات Microsoft AI يدويًا باستخدام الأمر التالي في الطرفية.

```
conda install -c microsoft azure-ai-ml
```

يحدد ملف البيئة التبعيات التي نحتاجها. `<environment-name>` يشير إلى الاسم الذي ترغب في استخدامه لبيئة Conda الخاصة بك، و `<python-version>` هو إصدار Python الذي ترغب في استخدامه، على سبيل المثال، `3` هو أحدث إصدار رئيسي من Python.

بعد ذلك، يمكنك إنشاء بيئة Conda الخاصة بك عن طريق تشغيل الأوامر أدناه في سطر الأوامر/الطرفية

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

راجع [دليل بيئات Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst) إذا واجهت أي مشاكل.

### استخدام Visual Studio Code مع ملحق دعم Python

نوصي باستخدام محرر [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) مع [ملحق دعم Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) المثبت لهذه الدورة. ومع ذلك، هذا مجرد توصية وليس شرطًا أساسيًا.

> **ملاحظة**: عند فتح مستودع الدورة في VS Code، لديك خيار إعداد المشروع داخل حاوية. هذا بسبب [الدليل الخاص `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) الموجود داخل مستودع الدورة. المزيد عن هذا لاحقًا.

> **ملاحظة**: بمجرد نسخ وفتح الدليل في VS Code، سيقترح تلقائيًا تثبيت ملحق دعم Python.

> **ملاحظة**: إذا اقترح VS Code إعادة فتح المستودع في حاوية، قم برفض هذا الطلب لاستخدام النسخة المثبتة محليًا من Python.

### استخدام Jupyter في المتصفح

يمكنك أيضًا العمل على المشروع باستخدام [بيئة Jupyter](https://jupyter.org?WT.mc_id=academic-105485-koreyst) مباشرة داخل المتصفح. يوفر كل من Jupyter الكلاسيكي و [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) بيئة تطوير ممتعة مع ميزات مثل الإكمال التلقائي، تمييز الكود، وغيرها.

لبدء Jupyter محليًا، توجه إلى الطرفية/سطر الأوامر، وانتقل إلى دليل الدورة، وقم بتنفيذ:

```bash
jupyter notebook
```

أو

```bash
jupyterhub
```

سيبدأ هذا تشغيل Jupyter وستظهر عنوان URL للوصول إليه داخل نافذة سطر الأوامر.

بمجرد الوصول إلى عنوان URL، يجب أن ترى مخطط الدورة وتتمكن من التنقل إلى أي ملف `*.ipynb`. على سبيل المثال، `08-building-search-applications/python/oai-solution.ipynb`.

### التشغيل داخل حاوية

بديل لإعداد كل شيء على جهاز الكمبيوتر الخاص بك أو Codespace هو استخدام [حاوية](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>). يجعل الدليل الخاص `.devcontainer` داخل مستودع الدورة من الممكن لـ VS Code إعداد المشروع داخل حاوية. خارج Codespaces، سيتطلب ذلك تثبيت Docker، وبصراحة، يتطلب بعض العمل، لذا نوصي بهذا فقط لأولئك الذين لديهم خبرة في العمل مع الحاويات.

واحدة من أفضل الطرق للحفاظ على أمان مفاتيح API الخاصة بك عند استخدام GitHub Codespaces هي استخدام أسرار Codespace. يرجى اتباع [دليل إدارة أسرار Codespaces](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst) لمعرفة المزيد عن هذا.

## الدروس والمتطلبات التقنية

تتضمن الدورة 6 دروس مفاهيمية و6 دروس برمجية.

بالنسبة للدروس البرمجية، نستخدم خدمة Azure OpenAI. ستحتاج إلى الوصول إلى خدمة Azure OpenAI ومفتاح API لتشغيل هذا الكود. يمكنك التقديم للحصول على الوصول عن طريق [إكمال هذا الطلب](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst).

أثناء انتظار معالجة طلبك، يتضمن كل درس برمجي أيضًا ملف `README.md` حيث يمكنك عرض الكود والمخرجات.

## استخدام خدمة Azure OpenAI لأول مرة

إذا كانت هذه هي المرة الأولى التي تعمل فيها مع خدمة Azure OpenAI، يرجى اتباع هذا الدليل حول كيفية [إنشاء ونشر مورد خدمة Azure OpenAI.](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst)

## استخدام واجهة برمجة التطبيقات OpenAI لأول مرة

إذا كانت هذه هي المرة الأولى التي تعمل فيها مع واجهة برمجة التطبيقات OpenAI، يرجى اتباع الدليل حول كيفية [إنشاء واستخدام الواجهة.](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst)

## لقاء متعلمين آخرين

لقد أنشأنا قنوات في [خادم Discord الرسمي لمجتمع الذكاء الاصطناعي](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) للقاء متعلمين آخرين. هذه طريقة رائعة للتواصل مع رواد الأعمال، والمطورين، والطلاب، وأي شخص يتطلع إلى تحسين مهاراته في الذكاء الاصطناعي التوليدي.

[![انضم إلى قناة Discord](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

سيكون فريق المشروع أيضًا على هذا الخادم Discord لمساعدة أي متعلمين.

## المساهمة

هذه الدورة هي مبادرة مفتوحة المصدر. إذا رأيت مجالات للتحسين أو مشاكل، يرجى إنشاء [طلب سحب](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) أو تسجيل [مشكلة على GitHub](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst).

سيقوم فريق المشروع بتتبع جميع المساهمات. المساهمة في المصادر المفتوحة هي طريقة رائعة لبناء حياتك المهنية في الذكاء الاصطناعي التوليدي.

تتطلب معظم المساهمات منك الموافقة على اتفاقية ترخيص المساهم (CLA) التي تعلن أنك لديك الحق في، وتقوم فعليًا، بمنحنا حقوق استخدام مساهمتك. لمزيد من التفاصيل، قم بزيارة [موقع CLA، اتفاقية ترخيص المساهم](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst).

هام: عند ترجمة النص في هذا المستودع، يرجى التأكد من أنك لا تستخدم الترجمة الآلية. سنقوم بالتحقق من الترجمات عبر المجتمع، لذا يرجى التطوع للترجمات فقط في اللغات التي تتقنها.

عندما تقدم طلب سحب، سيحدد CLA-bot تلقائيًا ما إذا كنت بحاجة إلى تقديم CLA ويقوم بتزيين الطلب بشكل مناسب (مثل وضع علامة أو تعليق). ما عليك سوى اتباع التعليمات المقدمة من الروبوت. ستحتاج إلى القيام بذلك مرة واحدة فقط عبر جميع المستودعات التي تستخدم CLA الخاص بنا.

اعتمد هذا المشروع [مدونة قواعد السلوك المفتوحة المصدر من Microsoft](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst). لمزيد من المعلومات، اقرأ الأسئلة الشائعة حول مدونة قواعد السلوك أو اتصل بـ [Email opencode](opencode@microsoft.com) لأي أسئلة أو تعليقات إضافية.

## لنبدأ
الآن بعد أن أكملت الخطوات اللازمة لإتمام هذه الدورة، دعنا نبدأ بالحصول على [مقدمة عن الذكاء الاصطناعي التوليدي ونماذج اللغة الكبيرة](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst).

---

**إخلاء المسؤولية**:  
تم ترجمة هذا المستند باستخدام خدمة الترجمة بالذكاء الاصطناعي [Co-op Translator](https://github.com/Azure/co-op-translator). بينما نسعى لتحقيق الدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار المستند الأصلي بلغته الأصلية المصدر الرسمي. للحصول على معلومات حاسمة، يُوصى بالترجمة البشرية الاحترافية. نحن غير مسؤولين عن أي سوء فهم أو تفسيرات خاطئة تنشأ عن استخدام هذه الترجمة.