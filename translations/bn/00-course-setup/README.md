<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-18T00:22:30+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "bn"
}
-->
# এই কোর্স শুরু করা

আমরা খুবই উত্তেজিত যে আপনি এই কোর্সটি শুরু করছেন এবং জেনারেটিভ AI দিয়ে কী তৈরি করতে অনুপ্রাণিত হন তা দেখার জন্য অপেক্ষা করছি!

আপনার সফলতা নিশ্চিত করতে, এই পৃষ্ঠায় সেটআপ ধাপ, প্রযুক্তিগত প্রয়োজনীয়তা এবং সাহায্য পাওয়ার জায়গাগুলো উল্লেখ করা হয়েছে।

## সেটআপ ধাপ

এই কোর্সটি শুরু করতে, আপনাকে নিম্নলিখিত ধাপগুলো সম্পন্ন করতে হবে।

### ১. এই রিপোজিটরি ফর্ক করুন

[এই পুরো রিপোজিটরি ফর্ক করুন](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) আপনার নিজস্ব GitHub অ্যাকাউন্টে, যাতে আপনি কোড পরিবর্তন করতে পারেন এবং চ্যালেঞ্জগুলো সম্পন্ন করতে পারেন। আপনি [এই রিপোজিটরি স্টার (🌟) দিতে পারেন](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) যাতে এটি এবং সম্পর্কিত রিপোজিটরি সহজে খুঁজে পান।

### ২. একটি কোডস্পেস তৈরি করুন

কোড চালানোর সময় কোনো ডিপেনডেন্সি সমস্যা এড়ানোর জন্য, আমরা এই কোর্সটি [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst) এ চালানোর সুপারিশ করি।

আপনার ফর্কে: **Code -> Codespaces -> New on main**

![কোডস্পেস তৈরি করার বোতাম দেখানো ডায়ালগ](../../../00-course-setup/images/who-will-pay.webp)

#### ২.১ একটি সিক্রেট যোগ করুন

1. ⚙️ গিয়ার আইকন -> Command Pallete-> Codespaces : Manage user secret -> Add a new secret।  
2. নাম দিন OPENAI_API_KEY, আপনার কী পেস্ট করুন, সেভ করুন।

### ৩. এরপর কী করবেন?

| আমি করতে চাই…         | যান…                                                                 |
|---------------------|-------------------------------------------------------------------------|
| লেসন ১ শুরু করতে চাই | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)     |
| অফলাইনে কাজ করতে চাই | [`setup-local.md`](02-setup-local.md)                                   |
| একটি LLM প্রোভাইডার সেটআপ করতে চাই | [`providers.md`](03-providers.md)                                        |
| অন্যান্য শিক্ষার্থীদের সাথে দেখা করতে চাই | [আমাদের Discord-এ যোগ দিন](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)   |

## সমস্যার সমাধান

| সমস্যা                                   | সমাধান                                                             |
|-------------------------------------------|-----------------------------------------------------------------|
| কন্টেইনার বিল্ড ১০ মিনিটের বেশি সময় নিচ্ছে | **Codespaces ➜ “Rebuild Container”**                            |
| `python: command not found`               | টার্মিনাল সংযুক্ত হয়নি; **+** ➜ *bash* ক্লিক করুন                    |
| OpenAI থেকে `401 Unauthorized`            | ভুল / মেয়াদোত্তীর্ণ `OPENAI_API_KEY`                                |
| VS Code দেখাচ্ছে “Dev container mounting…”   | ব্রাউজার ট্যাব রিফ্রেশ করুন—Codespaces মাঝে মাঝে সংযোগ হারায়   |
| নোটবুক কার্নেল অনুপস্থিত                   | নোটবুক মেনু ➜ **Kernel ▸ Select Kernel ▸ Python 3**           |

   ইউনিক্স-ভিত্তিক সিস্টেম:

   ```bash
   touch .env
   ```
  
   উইন্ডোজ:

   ```cmd
   echo . > .env
   ```
  
3. **`.env` ফাইল সম্পাদনা করুন**: `.env` ফাইলটি একটি টেক্সট এডিটরে (যেমন VS Code, Notepad++ বা অন্য কোনো এডিটার) খুলুন। ফাইলটিতে নিম্নলিখিত লাইনটি যোগ করুন এবং `your_github_token_here` এর জায়গায় আপনার আসল GitHub টোকেন দিন:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```
  
4. **ফাইলটি সেভ করুন**: পরিবর্তনগুলো সেভ করুন এবং টেক্সট এডিটার বন্ধ করুন।

5. **`python-dotenv` ইনস্টল করুন**: যদি আপনি আগে ইনস্টল না করে থাকেন, তাহলে `.env` ফাইল থেকে আপনার Python অ্যাপ্লিকেশনে পরিবেশ ভেরিয়েবল লোড করার জন্য `python-dotenv` প্যাকেজটি ইনস্টল করতে হবে। এটি `pip` ব্যবহার করে ইনস্টল করতে পারেন:

   ```bash
   pip install python-dotenv
   ```
  
6. **আপনার Python স্ক্রিপ্টে পরিবেশ ভেরিয়েবল লোড করুন**: আপনার Python স্ক্রিপ্টে, `.env` ফাইল থেকে পরিবেশ ভেরিয়েবল লোড করতে `python-dotenv` প্যাকেজ ব্যবহার করুন:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```
  
এটাই! আপনি সফলভাবে একটি `.env` ফাইল তৈরি করেছেন, আপনার GitHub টোকেন যোগ করেছেন এবং এটি আপনার Python অ্যাপ্লিকেশনে লোড করেছেন।

## আপনার কম্পিউটারে লোকালভাবে চালানোর পদ্ধতি

আপনার কম্পিউটারে কোড লোকালভাবে চালানোর জন্য, আপনার [Python ইনস্টল](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst) করা থাকতে হবে।

এরপর রিপোজিটরি ব্যবহার করতে, আপনাকে এটি ক্লোন করতে হবে:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```
  
যখন সবকিছু চেক আউট হয়ে যাবে, তখন আপনি শুরু করতে পারবেন!

## ঐচ্ছিক ধাপ

### Miniconda ইনস্টল করা

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) হলো [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python এবং কিছু প্যাকেজ ইনস্টল করার জন্য একটি হালকা ইনস্টলার।  
Conda নিজেই একটি প্যাকেজ ম্যানেজার, যা বিভিন্ন Python [**ভার্চুয়াল এনভায়রনমেন্ট**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) এবং প্যাকেজ সেটআপ এবং পরিবর্তন করা সহজ করে তোলে। এটি এমন প্যাকেজ ইনস্টল করার জন্যও সুবিধাজনক যা `pip` এর মাধ্যমে পাওয়া যায় না।

[MiniConda ইনস্টলেশন গাইড](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst) অনুসরণ করে এটি সেটআপ করুন।

Miniconda ইনস্টল করার পরে, আপনাকে [রিপোজিটরি](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) ক্লোন করতে হবে (যদি আপনি আগে না করে থাকেন)।

এরপর, আপনাকে একটি ভার্চুয়াল এনভায়রনমেন্ট তৈরি করতে হবে। Conda ব্যবহার করে এটি করতে, একটি নতুন এনভায়রনমেন্ট ফাইল (_environment.yml_) তৈরি করুন। যদি আপনি Codespaces ব্যবহার করে থাকেন, তাহলে এটি `.devcontainer` ডিরেক্টরির মধ্যে তৈরি করুন, অর্থাৎ `.devcontainer/environment.yml`।

আপনার এনভায়রনমেন্ট ফাইলটি নিচের স্নিপেট দিয়ে পূরণ করুন:

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
  
যদি আপনি conda ব্যবহার করে কোনো ত্রুটি পান, তাহলে আপনি ম্যানুয়ালি Microsoft AI লাইব্রেরি ইনস্টল করতে পারেন নিম্নলিখিত কমান্ড ব্যবহার করে:

```
conda install -c microsoft azure-ai-ml
```
  
এনভায়রনমেন্ট ফাইলটি আমাদের প্রয়োজনীয় ডিপেনডেন্সি নির্ধারণ করে। `<environment-name>` হলো আপনার Conda এনভায়রনমেন্টের জন্য পছন্দের নাম এবং `<python-version>` হলো আপনার পছন্দের Python সংস্করণ, যেমন `3` হলো Python-এর সর্বশেষ প্রধান সংস্করণ।

এটি সম্পন্ন করার পরে, আপনি আপনার Conda এনভায়রনমেন্ট তৈরি করতে পারেন নিচের কমান্ডগুলো চালিয়ে:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```
  
যদি কোনো সমস্যা হয়, [Conda এনভায়রনমেন্ট গাইড](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst) দেখুন।

### Python সাপোর্ট এক্সটেনশন সহ Visual Studio Code ব্যবহার করা

আমরা এই কোর্সের জন্য [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) এডিটর ব্যবহার করার সুপারিশ করি, যেখানে [Python সাপোর্ট এক্সটেনশন](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) ইনস্টল করা আছে। তবে এটি একটি সুপারিশ, বাধ্যতামূলক নয়।

> **নোট**: কোর্স রিপোজিটরি VS Code-এ খুললে, আপনি প্রজেক্টটি একটি কন্টেইনারে সেটআপ করার অপশন পাবেন। কারণ কোর্স রিপোজিটরিতে একটি [বিশেষ `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) ডিরেক্টরি রয়েছে। এটি পরে বিস্তারিত আলোচনা করা হবে।

> **নোট**: রিপোজিটরি ক্লোন এবং VS Code-এ ডিরেক্টরি খুললে, এটি স্বয়ংক্রিয়ভাবে আপনাকে একটি Python সাপোর্ট এক্সটেনশন ইনস্টল করার পরামর্শ দেবে।

> **নোট**: যদি VS Code আপনাকে রিপোজিটরি একটি কন্টেইনারে পুনরায় খুলতে বলে, এই অনুরোধটি প্রত্যাখ্যান করুন যাতে লোকালভাবে ইনস্টল করা Python সংস্করণ ব্যবহার করতে পারেন।

### ব্রাউজারে Jupyter ব্যবহার করা

আপনি [Jupyter পরিবেশ](https://jupyter.org?WT.mc_id=academic-105485-koreyst) ব্যবহার করে ব্রাউজারেই প্রজেক্টে কাজ করতে পারেন। ক্লাসিক Jupyter এবং [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) উন্নত ডেভেলপমেন্ট পরিবেশ প্রদান করে, যেমন অটো-কমপ্লিশন, কোড হাইলাইটিং ইত্যাদি।

লোকালভাবে Jupyter শুরু করতে, টার্মিনাল/কমান্ড লাইনে যান, কোর্স ডিরেক্টরিতে নেভিগেট করুন এবং চালান:

```bash
jupyter notebook
```
  
অথবা

```bash
jupyterhub
```
  
এটি একটি Jupyter ইনস্ট্যান্স শুরু করবে এবং এটি অ্যাক্সেস করার URL কমান্ড লাইনে দেখানো হবে।

URL-এ প্রবেশ করলে, আপনি কোর্সের আউটলাইন দেখতে পাবেন এবং যেকোনো `*.ipynb` ফাইল নেভিগেট করতে পারবেন। যেমন, `08-building-search-applications/python/oai-solution.ipynb`।

### কন্টেইনারে চালানো

আপনার কম্পিউটারে বা Codespace-এ সবকিছু সেটআপ করার বিকল্প হিসেবে আপনি একটি [কন্টেইনার](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>) ব্যবহার করতে পারেন। কোর্স রিপোজিটরির বিশেষ `.devcontainer` ফোল্ডারটি VS Code-কে প্রজেক্টটি একটি কন্টেইনারে সেটআপ করার সুযোগ দেয়। Codespaces-এর বাইরে, এটি Docker ইনস্টল করার প্রয়োজন হবে এবং এটি কিছুটা জটিল হতে পারে, তাই আমরা এটি শুধুমাত্র অভিজ্ঞদের জন্য সুপারিশ করি যারা কন্টেইনার নিয়ে কাজ করেছেন।

GitHub Codespaces ব্যবহার করার সময় আপনার API কী নিরাপদ রাখার সেরা উপায় হলো Codespace Secrets ব্যবহার করা। [Codespaces সিক্রেট ম্যানেজমেন্ট](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst) গাইডটি অনুসরণ করুন আরও জানতে।

## লেসন এবং প্রযুক্তিগত প্রয়োজনীয়তা

এই কোর্সে ৬টি ধারণাগত লেসন এবং ৬টি কোডিং লেসন রয়েছে।

কোডিং লেসনের জন্য, আমরা Azure OpenAI Service ব্যবহার করছি। এই কোড চালানোর জন্য আপনাকে Azure OpenAI সার্ভিস এবং একটি API কী প্রয়োজন হবে। [এই আবেদনপত্র পূরণ করে](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst) অ্যাক্সেসের জন্য আবেদন করতে পারেন।

আপনার আবেদন প্রক্রিয়া সম্পন্ন হওয়ার অপেক্ষায় থাকাকালীন, প্রতিটি কোডিং লেসনে একটি `README.md` ফাইল অন্তর্ভুক্ত রয়েছে যেখানে আপনি কোড এবং আউটপুট দেখতে পারবেন।

## প্রথমবার Azure OpenAI সার্ভিস ব্যবহার করা

যদি এটি আপনার প্রথমবার Azure OpenAI সার্ভিস ব্যবহার হয়, অনুগ্রহ করে [Azure OpenAI সার্ভিস রিসোর্স তৈরি এবং ডিপ্লয় করার গাইড](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst) অনুসরণ করুন।

## প্রথমবার OpenAI API ব্যবহার করা

যদি এটি আপনার প্রথমবার OpenAI API ব্যবহার হয়, অনুগ্রহ করে [ইন্টারফেস তৈরি এবং ব্যবহার করার গাইড](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst) অনুসরণ করুন।

## অন্যান্য শিক্ষার্থীদের সাথে দেখা করুন

আমরা আমাদের অফিসিয়াল [AI Community Discord সার্ভার](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) এ অন্যান্য শিক্ষার্থীদের সাথে দেখা করার জন্য চ্যানেল তৈরি করেছি। এটি জেনারেটিভ AI-তে দক্ষতা অর্জন করতে ইচ্ছুক উদ্যোক্তা, নির্মাতা, শিক্ষার্থী এবং অন্যদের সাথে নেটওয়ার্ক করার একটি চমৎকার উপায়।

[![ডিসকর্ড চ্যানেলে যোগ দিন](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

প্রজেক্ট টিমও এই Discord সার্ভারে থাকবে শিক্ষার্থীদের সাহায্য করার জন্য।

## অবদান রাখুন

এই কোর্সটি একটি ওপেন-সোর্স উদ্যোগ। যদি আপনি উন্নতির জায়গা বা সমস্যা দেখতে পান, অনুগ্রহ করে একটি [Pull Request তৈরি করুন](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) অথবা একটি [GitHub issue লগ করুন](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst)।

প্রজেক্ট টিম সব অবদান ট্র্যাক করবে। ওপেন সোর্সে অবদান রাখা জেনারেটিভ AI-তে আপনার ক্যারিয়ার গড়ার একটি অসাধারণ উপায়।

বেশিরভাগ অবদান রাখার জন্য আপনাকে একটি Contributor License Agreement (CLA) সম্মত হতে হবে, যা নিশ্চিত করে যে আপনার অবদান ব্যবহারের অধিকার আমাদের রয়েছে। বিস্তারিত জানতে [CLA, Contributor License Agreement ওয়েবসাইট](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst) দেখুন।

গুরুত্বপূর্ণ: এই রিপোজিটরিতে টেক্সট অনুবাদ করার সময়, অনুগ্রহ করে নিশ্চিত করুন যে আপনি মেশিন অনুবাদ ব্যবহার করছেন না। আমরা কমিউনিটির মাধ্যমে অনুবাদ যাচাই করব, তাই অনুগ্রহ করে শুধুমাত্র সেই ভাষায় অনুবাদ করার জন্য স্বেচ্ছাসেবক হন যেখানে আপনি দক্ষ।

যখন আপনি একটি পুল রিকোয়েস্ট জমা দেবেন, একটি CLA-বট স্বয়ংক্রিয়ভাবে নির্ধারণ করবে যে আপনাকে CLA প্রদান করতে হবে কিনা এবং PR যথাযথভাবে সাজাবে (যেমন, লেবেল, মন্তব্য)। বট দ্বারা প্রদত্ত নির্দেশাবলী অনুসরণ করুন। আপনাকে এটি শুধুমাত্র একবার করতে হবে সমস্ত রিপোজিটরির জন্য যা আমাদের CLA ব্যবহার করে।

এই প্রজেক্টটি [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst) গ্রহণ করেছে। আরও তথ্যের জন্য Code of Conduct FAQ পড়ুন অথবা [Email opencode](opencode@microsoft.com) এ অতিরিক্ত প্রশ্ন বা মন্তব্য পাঠান।

## চলুন শুরু করি
এখন যেহেতু আপনি এই কোর্স সম্পন্ন করার জন্য প্রয়োজনীয় ধাপগুলো সম্পন্ন করেছেন, চলুন শুরু করি [জেনারেটিভ এআই এবং এলএলএমস সম্পর্কে পরিচিতি](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst) দিয়ে।

---

**অস্বীকৃতি**:  
এই নথিটি AI অনুবাদ পরিষেবা [Co-op Translator](https://github.com/Azure/co-op-translator) ব্যবহার করে অনুবাদ করা হয়েছে। আমরা যথাসাধ্য সঠিকতা নিশ্চিত করার চেষ্টা করি, তবে অনুগ্রহ করে মনে রাখবেন যে স্বয়ংক্রিয় অনুবাদে ত্রুটি বা অসঙ্গতি থাকতে পারে। মূল ভাষায় থাকা নথিটিকে প্রামাণিক উৎস হিসেবে বিবেচনা করা উচিত। গুরুত্বপূর্ণ তথ্যের জন্য, পেশাদার মানব অনুবাদ সুপারিশ করা হয়। এই অনুবাদ ব্যবহারের ফলে কোনো ভুল বোঝাবুঝি বা ভুল ব্যাখ্যা হলে আমরা দায়বদ্ধ থাকব না।