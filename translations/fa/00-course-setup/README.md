<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-17T23:09:44+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "fa"
}
-->
# شروع به کار با این دوره

ما بسیار هیجان‌زده‌ایم که شما این دوره را شروع کنید و ببینید با هوش مصنوعی تولیدی چه چیزهایی می‌توانید بسازید!

برای موفقیت شما، این صفحه مراحل راه‌اندازی، نیازمندی‌های فنی و راه‌های دریافت کمک در صورت نیاز را توضیح می‌دهد.

## مراحل راه‌اندازی

برای شروع این دوره، باید مراحل زیر را انجام دهید.

### 1. فورک کردن این مخزن

[این مخزن را به طور کامل فورک کنید](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) تا بتوانید کدها را تغییر دهید و چالش‌ها را کامل کنید. همچنین می‌توانید [این مخزن را ستاره‌دار کنید (🌟)](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) تا دسترسی به آن و مخازن مرتبط آسان‌تر شود.

### 2. ایجاد یک Codespace

برای جلوگیری از مشکلات وابستگی هنگام اجرای کد، توصیه می‌کنیم این دوره را در یک [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst) اجرا کنید.

در فورک خود: **Code -> Codespaces -> New on main**

![دیالوگ نمایش دکمه‌ها برای ایجاد یک Codespace](../../../00-course-setup/images/who-will-pay.webp)

#### 2.1 افزودن یک secret

1. ⚙️ آیکون چرخ‌دنده -> Command Pallete -> Codespaces : Manage user secret -> Add a new secret.
2. نام OPENAI_API_KEY، کلید خود را وارد کنید، ذخیره کنید.

### 3. مرحله بعدی چیست؟

| من می‌خواهم…         | برو به…                                                                 |
|---------------------|-------------------------------------------------------------------------|
| شروع درس اول        | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)     |
| کار به صورت آفلاین  | [`setup-local.md`](02-setup-local.md)                                   |
| راه‌اندازی یک ارائه‌دهنده LLM | [`providers.md`](03-providers.md)                                        |
| ملاقات با دیگر یادگیرندگان | [به دیسکورد ما بپیوندید](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)   |

## رفع مشکلات

| مشکل                                   | راه‌حل                                                             |
|---------------------------------------|-----------------------------------------------------------------|
| ساخت کانتینر بیش از ۱۰ دقیقه طول می‌کشد | **Codespaces ➜ “Rebuild Container”**                            |
| `python: command not found`           | ترمینال متصل نشده؛ روی **+** کلیک کنید ➜ *bash*                    |
| `401 Unauthorized` از OpenAI          | کلید `OPENAI_API_KEY` اشتباه یا منقضی شده است                     |
| VS Code نشان می‌دهد “Dev container mounting…” | تب مرورگر را تازه کنید—گاهی اوقات Codespaces اتصال را از دست می‌دهد   |
| هسته نوت‌بوک گم شده است               | منوی نوت‌بوک ➜ **Kernel ▸ Select Kernel ▸ Python 3**           |

   سیستم‌های مبتنی بر یونیکس:

   ```bash
   touch .env
   ```

   ویندوز:

   ```cmd
   echo . > .env
   ```

3. **ویرایش فایل `.env`**: فایل `.env` را در یک ویرایشگر متن (مانند VS Code، Notepad++ یا هر ویرایشگر دیگر) باز کنید. خط زیر را به فایل اضافه کنید و `your_github_token_here` را با توکن واقعی گیت‌هاب خود جایگزین کنید:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```

4. **ذخیره فایل**: تغییرات را ذخیره کنید و ویرایشگر متن را ببندید.

5. **نصب `python-dotenv`**: اگر قبلاً این کار را انجام نداده‌اید، باید بسته `python-dotenv` را برای بارگذاری متغیرهای محیطی از فایل `.env` به برنامه پایتون خود نصب کنید. می‌توانید آن را با استفاده از `pip` نصب کنید:

   ```bash
   pip install python-dotenv
   ```

6. **بارگذاری متغیرهای محیطی در اسکریپت پایتون خود**: در اسکریپت پایتون خود، از بسته `python-dotenv` برای بارگذاری متغیرهای محیطی از فایل `.env` استفاده کنید:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```

همین! شما با موفقیت یک فایل `.env` ایجاد کرده‌اید، توکن گیت‌هاب خود را اضافه کرده‌اید و آن را در برنامه پایتون خود بارگذاری کرده‌اید.

## نحوه اجرای محلی روی کامپیوتر شما

برای اجرای کد به صورت محلی روی کامپیوتر خود، باید نسخه‌ای از [پایتون نصب شده](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst) داشته باشید.

سپس برای استفاده از مخزن، باید آن را کلون کنید:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

پس از اینکه همه چیز را بررسی کردید، می‌توانید شروع کنید!

## مراحل اختیاری

### نصب Miniconda

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) یک نصب‌کننده سبک برای نصب [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst)، پایتون و چند بسته دیگر است.
Conda خود یک مدیر بسته است که راه‌اندازی و جابجایی بین محیط‌های [**مجازی پایتون**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) و بسته‌ها را آسان می‌کند. همچنین برای نصب بسته‌هایی که از طریق `pip` در دسترس نیستند، مفید است.

می‌توانید راهنمای نصب [MiniConda](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst) را دنبال کنید تا آن را راه‌اندازی کنید.

با نصب Miniconda، باید [مخزن](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) را کلون کنید (اگر قبلاً این کار را نکرده‌اید).

سپس باید یک محیط مجازی ایجاد کنید. برای انجام این کار با Conda، یک فایل محیط جدید (_environment.yml_) ایجاد کنید. اگر از Codespaces استفاده می‌کنید، این فایل را در دایرکتوری `.devcontainer` ایجاد کنید، بنابراین `.devcontainer/environment.yml`.

فایل محیط خود را با قطعه کد زیر پر کنید:

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

اگر با استفاده از conda خطاهایی دریافت کردید، می‌توانید کتابخانه‌های هوش مصنوعی مایکروسافت را به صورت دستی با استفاده از دستور زیر در ترمینال نصب کنید.

```
conda install -c microsoft azure-ai-ml
```

فایل محیط وابستگی‌هایی که نیاز داریم را مشخص می‌کند. `<environment-name>` به نامی که می‌خواهید برای محیط Conda خود استفاده کنید اشاره دارد و `<python-version>` نسخه پایتونی است که می‌خواهید استفاده کنید، برای مثال، `3` آخرین نسخه اصلی پایتون است.

با انجام این کار، می‌توانید محیط Conda خود را با اجرای دستورات زیر در خط فرمان/ترمینال ایجاد کنید:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

اگر با مشکلی مواجه شدید، به [راهنمای محیط‌های Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst) مراجعه کنید.

### استفاده از Visual Studio Code با افزونه پشتیبانی پایتون

ما توصیه می‌کنیم از ویرایشگر [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) با افزونه [پشتیبانی پایتون](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) برای این دوره استفاده کنید. البته این فقط یک توصیه است و الزام نیست.

> **توجه**: با باز کردن مخزن دوره در VS Code، این امکان را دارید که پروژه را در یک کانتینر تنظیم کنید. این به دلیل دایرکتوری [خاص `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) موجود در مخزن دوره است. اطلاعات بیشتر در این مورد بعداً ارائه خواهد شد.

> **توجه**: پس از کلون کردن و باز کردن دایرکتوری در VS Code، به طور خودکار به شما پیشنهاد می‌شود که افزونه پشتیبانی پایتون را نصب کنید.

> **توجه**: اگر VS Code پیشنهاد داد که مخزن را در یک کانتینر باز کنید، این درخواست را رد کنید تا از نسخه محلی نصب شده پایتون استفاده کنید.

### استفاده از Jupyter در مرورگر

شما همچنین می‌توانید روی پروژه با استفاده از محیط [Jupyter](https://jupyter.org?WT.mc_id=academic-105485-koreyst) در مرورگر خود کار کنید. هم Jupyter کلاسیک و هم [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) محیط توسعه دلپذیری با ویژگی‌هایی مانند تکمیل خودکار، برجسته‌سازی کد و غیره ارائه می‌دهند.

برای شروع Jupyter به صورت محلی، به ترمینال/خط فرمان بروید، به دایرکتوری دوره بروید و اجرا کنید:

```bash
jupyter notebook
```

یا

```bash
jupyterhub
```

این کار یک نمونه Jupyter را شروع می‌کند و URL برای دسترسی به آن در پنجره خط فرمان نمایش داده می‌شود.

پس از دسترسی به URL، باید طرح کلی دوره را مشاهده کنید و بتوانید به هر فایل `*.ipynb` دسترسی پیدا کنید. برای مثال، `08-building-search-applications/python/oai-solution.ipynb`.

### اجرا در یک کانتینر

یک جایگزین برای تنظیم همه چیز روی کامپیوتر یا Codespace شما استفاده از یک [کانتینر](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>) است. دایرکتوری خاص `.devcontainer` در مخزن دوره این امکان را فراهم می‌کند که VS Code پروژه را در یک کانتینر تنظیم کند. خارج از Codespaces، این نیاز به نصب Docker دارد و به طور کلی کمی کار می‌برد، بنابراین ما این روش را فقط به کسانی که تجربه کار با کانتینرها دارند توصیه می‌کنیم.

یکی از بهترین راه‌ها برای حفظ امنیت کلیدهای API شما هنگام استفاده از GitHub Codespaces استفاده از Secrets Codespace است. لطفاً راهنمای [مدیریت Secrets Codespaces](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst) را دنبال کنید تا اطلاعات بیشتری در این مورد کسب کنید.

## درس‌ها و نیازمندی‌های فنی

این دوره شامل ۶ درس مفهومی و ۶ درس کدنویسی است.

برای درس‌های کدنویسی، ما از سرویس Azure OpenAI استفاده می‌کنیم. برای اجرای این کد، شما نیاز به دسترسی به سرویس Azure OpenAI و یک کلید API دارید. می‌توانید با [تکمیل این درخواست](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst) برای دسترسی اقدام کنید.

در حالی که منتظر پردازش درخواست خود هستید، هر درس کدنویسی همچنین شامل یک فایل `README.md` است که می‌توانید کد و خروجی‌ها را مشاهده کنید.

## استفاده از سرویس Azure OpenAI برای اولین بار

اگر این اولین بار است که با سرویس Azure OpenAI کار می‌کنید، لطفاً این راهنما را دنبال کنید تا [یک منبع سرویس Azure OpenAI ایجاد و مستقر کنید.](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst)

## استفاده از API OpenAI برای اولین بار

اگر این اولین بار است که با API OpenAI کار می‌کنید، لطفاً راهنمای [ایجاد و استفاده از رابط کاربری](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst) را دنبال کنید.

## ملاقات با دیگر یادگیرندگان

ما کانال‌هایی در سرور رسمی [دیسکورد جامعه هوش مصنوعی](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) برای ملاقات با دیگر یادگیرندگان ایجاد کرده‌ایم. این یک راه عالی برای شبکه‌سازی با کارآفرینان، سازندگان، دانشجویان و هر کسی است که به دنبال پیشرفت در هوش مصنوعی تولیدی است.

[![به کانال دیسکورد بپیوندید](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

تیم پروژه نیز در این سرور دیسکورد حضور خواهد داشت تا به یادگیرندگان کمک کند.

## مشارکت

این دوره یک ابتکار منبع باز است. اگر مناطقی برای بهبود یا مشکلاتی مشاهده کردید، لطفاً یک [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) ایجاد کنید یا یک [مشکل گیت‌هاب](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst) ثبت کنید.

تیم پروژه تمام مشارکت‌ها را پیگیری خواهد کرد. مشارکت در منبع باز یک راه فوق‌العاده برای ساختن حرفه خود در زمینه هوش مصنوعی تولیدی است.

بیشتر مشارکت‌ها نیاز به توافق‌نامه مجوز مشارکت‌کننده (CLA) دارند که اعلام می‌کند شما حق دارید و واقعاً به ما اجازه می‌دهید از مشارکت شما استفاده کنیم. برای جزئیات، به [وب‌سایت توافق‌نامه مجوز مشارکت‌کننده CLA](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst) مراجعه کنید.

مهم: هنگام ترجمه متن در این مخزن، لطفاً مطمئن شوید که از ترجمه ماشینی استفاده نمی‌کنید. ما ترجمه‌ها را از طریق جامعه بررسی خواهیم کرد، بنابراین لطفاً فقط برای ترجمه به زبان‌هایی که در آن‌ها مهارت دارید داوطلب شوید.

وقتی یک درخواست pull ارسال می‌کنید، یک ربات CLA به طور خودکار تعیین می‌کند که آیا نیاز به ارائه CLA دارید یا خیر و PR را به طور مناسب تزئین می‌کند (مانند برچسب، نظر). فقط دستورالعمل‌های ارائه شده توسط ربات را دنبال کنید. شما فقط یک بار نیاز به انجام این کار دارید برای تمام مخازن استفاده‌کننده از CLA ما.

این پروژه [کد رفتار منبع باز مایکروسافت](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst) را پذیرفته است. برای اطلاعات بیشتر، بخش سوالات متداول کد رفتار را بخوانید یا با [ایمیل opencode](opencode@microsoft.com) برای سوالات یا نظرات اضافی تماس بگیرید.

## بیایید شروع کنیم
حالا که مراحل لازم برای تکمیل این دوره را انجام داده‌اید، بیایید با [معرفی هوش مصنوعی مولد و مدل‌های زبانی بزرگ (LLMs)](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst) شروع کنیم.

---

**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما تلاش می‌کنیم دقت را حفظ کنیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است شامل خطاها یا نادرستی‌ها باشند. سند اصلی به زبان اصلی آن باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما مسئولیتی در قبال سوء تفاهم‌ها یا تفسیرهای نادرست ناشی از استفاده از این ترجمه نداریم.