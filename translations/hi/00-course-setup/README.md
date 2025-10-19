<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-18T00:12:59+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "hi"
}
-->
# इस कोर्स की शुरुआत करें

हम बहुत उत्साहित हैं कि आप इस कोर्स को शुरू कर रहे हैं और देख रहे हैं कि आप जनरेटिव एआई के साथ क्या निर्माण करने के लिए प्रेरित होते हैं!

आपकी सफलता सुनिश्चित करने के लिए, इस पेज में सेटअप चरण, तकनीकी आवश्यकताएं और यदि आवश्यक हो तो मदद कहां से प्राप्त करें, इसके बारे में जानकारी दी गई है।

## सेटअप चरण

इस कोर्स को शुरू करने के लिए, आपको निम्नलिखित चरण पूरे करने होंगे।

### 1. इस रिपॉजिटरी को फोर्क करें

[इस पूरी रिपॉजिटरी को फोर्क करें](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) अपने GitHub अकाउंट में ताकि आप कोड में बदलाव कर सकें और चुनौतियों को पूरा कर सकें। आप इस रिपॉजिटरी को [स्टार (🌟)](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) भी कर सकते हैं ताकि इसे और संबंधित रिपॉजिटरी को आसानी से ढूंढ सकें।

### 2. एक कोडस्पेस बनाएं

कोड चलाते समय किसी भी डिपेंडेंसी समस्या से बचने के लिए, हम इस कोर्स को [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst) में चलाने की सलाह देते हैं।

अपने फोर्क में: **Code -> Codespaces -> New on main**

![कोडस्पेस बनाने के लिए बटन दिखाने वाला डायलॉग](../../../00-course-setup/images/who-will-pay.webp)

#### 2.1 एक सीक्रेट जोड़ें

1. ⚙️ गियर आइकन -> कमांड पैलेट -> Codespaces : Manage user secret -> Add a new secret.
2. नाम OPENAI_API_KEY, अपनी कुंजी पेस्ट करें, सेव करें।

### 3. आगे क्या?

| मैं करना चाहता हूँ…  | जाएं…                                                                  |
|---------------------|-------------------------------------------------------------------------|
| लेसन 1 शुरू करें    | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)     |
| ऑफलाइन काम करें     | [`setup-local.md`](02-setup-local.md)                                   |
| एक LLM प्रोवाइडर सेटअप करें | [`providers.md`](03-providers.md)                                        |
| अन्य शिक्षार्थियों से मिलें | [हमारे डिस्कॉर्ड से जुड़ें](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)   |

## समस्या निवारण

| समस्या                                   | समाधान                                                             |
|-------------------------------------------|-----------------------------------------------------------------|
| कंटेनर निर्माण > 10 मिनट तक अटका हुआ है  | **Codespaces ➜ “Rebuild Container”**                            |
| `python: command not found`               | टर्मिनल अटैच नहीं हुआ; **+** ➜ *bash* पर क्लिक करें             |
| OpenAI से `401 Unauthorized`              | गलत / समाप्त `OPENAI_API_KEY`                                    |
| VS Code दिखाता है “Dev container mounting…” | ब्राउज़र टैब को रिफ्रेश करें—कभी-कभी Codespaces कनेक्शन खो देता है |
| नोटबुक कर्नेल गायब                       | नोटबुक मेनू ➜ **Kernel ▸ Select Kernel ▸ Python 3**             |

   Unix-आधारित सिस्टम:

   ```bash
   touch .env
   ```

   Windows:

   ```cmd
   echo . > .env
   ```

3. **`.env` फ़ाइल संपादित करें**: `.env` फ़ाइल को किसी टेक्स्ट एडिटर (जैसे VS Code, Notepad++, या कोई अन्य एडिटर) में खोलें। फ़ाइल में निम्नलिखित लाइन जोड़ें, और `your_github_token_here` को अपने वास्तविक GitHub टोकन से बदलें:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```

4. **फ़ाइल सेव करें**: बदलाव को सेव करें और टेक्स्ट एडिटर बंद करें।

5. **`python-dotenv` इंस्टॉल करें**: यदि आपने पहले से नहीं किया है, तो आपको `.env` फ़ाइल से अपने Python एप्लिकेशन में पर्यावरण वेरिएबल्स लोड करने के लिए `python-dotenv` पैकेज इंस्टॉल करना होगा। इसे `pip` का उपयोग करके इंस्टॉल करें:

   ```bash
   pip install python-dotenv
   ```

6. **अपने Python स्क्रिप्ट में पर्यावरण वेरिएबल्स लोड करें**: अपने Python स्क्रिप्ट में, `.env` फ़ाइल से पर्यावरण वेरिएबल्स लोड करने के लिए `python-dotenv` पैकेज का उपयोग करें:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```

बस इतना ही! आपने सफलतापूर्वक `.env` फ़ाइल बनाई, अपना GitHub टोकन जोड़ा, और इसे अपने Python एप्लिकेशन में लोड किया।

## अपने कंप्यूटर पर लोकल रूप से कैसे चलाएं

कोड को अपने कंप्यूटर पर लोकल रूप से चलाने के लिए, आपको [Python का कोई संस्करण इंस्टॉल](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst) करना होगा।

इसके बाद रिपॉजिटरी का उपयोग करने के लिए, आपको इसे क्लोन करना होगा:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

एक बार जब आपके पास सब कुछ चेक आउट हो जाए, तो आप शुरू कर सकते हैं!

## वैकल्पिक चरण

### मिनिकोंडा इंस्टॉल करना

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python, और कुछ पैकेज इंस्टॉल करने के लिए एक हल्का इंस्टॉलर है।  
Conda खुद एक पैकेज मैनेजर है, जो विभिन्न Python [**वर्चुअल एनवायरनमेंट्स**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) और पैकेजों को सेटअप और स्विच करना आसान बनाता है। यह उन पैकेजों को इंस्टॉल करने में भी मदद करता है जो `pip` के माध्यम से उपलब्ध नहीं हैं।

आप [MiniConda इंस्टॉलेशन गाइड](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst) का पालन करके इसे सेटअप कर सकते हैं।

Miniconda इंस्टॉल करने के बाद, आपको [रिपॉजिटरी](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) को क्लोन करना होगा (यदि आपने पहले से नहीं किया है)।

इसके बाद, आपको एक वर्चुअल एनवायरनमेंट बनाना होगा। Conda के साथ ऐसा करने के लिए, एक नया एनवायरनमेंट फ़ाइल (_environment.yml_) बनाएं। यदि आप Codespaces का उपयोग कर रहे हैं, तो इसे `.devcontainer` डायरेक्टरी के अंदर बनाएं, यानी `.devcontainer/environment.yml`।

अपनी एनवायरनमेंट फ़ाइल को नीचे दिए गए स्निपेट से भरें:

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

यदि आपको conda का उपयोग करते समय त्रुटियां मिलती हैं, तो आप निम्नलिखित कमांड का उपयोग करके Microsoft AI Libraries को मैन्युअल रूप से इंस्टॉल कर सकते हैं:

```
conda install -c microsoft azure-ai-ml
```

एनवायरनमेंट फ़ाइल उन डिपेंडेंसी को निर्दिष्ट करती है जिनकी हमें आवश्यकता है। `<environment-name>` उस नाम को संदर्भित करता है जिसे आप अपने Conda एनवायरनमेंट के लिए उपयोग करना चाहते हैं, और `<python-version>` वह संस्करण है जिसे आप उपयोग करना चाहते हैं, उदाहरण के लिए, `3` Python का नवीनतम प्रमुख संस्करण है।

इसके बाद, आप अपने Conda एनवायरनमेंट को निम्नलिखित कमांड्स को अपने कमांड लाइन/टर्मिनल में चलाकर बना सकते हैं:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

यदि आपको कोई समस्या होती है, तो [Conda एनवायरनमेंट्स गाइड](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst) देखें।

### Python सपोर्ट एक्सटेंशन के साथ Visual Studio Code का उपयोग करना

हम इस कोर्स के लिए [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) एडिटर का उपयोग करने की सलाह देते हैं, जिसमें [Python सपोर्ट एक्सटेंशन](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) इंस्टॉल हो। हालांकि, यह केवल एक सिफारिश है और अनिवार्य आवश्यकता नहीं है।

> **नोट**: कोर्स रिपॉजिटरी को VS Code में खोलने पर, आपके पास प्रोजेक्ट को एक कंटेनर के अंदर सेटअप करने का विकल्प होता है। ऐसा इसलिए है क्योंकि कोर्स रिपॉजिटरी में [विशेष `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) डायरेक्टरी है। इसके बारे में बाद में और जानकारी दी जाएगी।

> **नोट**: जब आप रिपॉजिटरी को क्लोन और VS Code में खोलते हैं, तो यह स्वचालित रूप से आपको Python सपोर्ट एक्सटेंशन इंस्टॉल करने का सुझाव देगा।

> **नोट**: यदि VS Code आपको रिपॉजिटरी को कंटेनर में फिर से खोलने का सुझाव देता है, तो इस अनुरोध को अस्वीकार करें ताकि आप लोकल इंस्टॉल किए गए Python संस्करण का उपयोग कर सकें।

### ब्राउज़र में Jupyter का उपयोग करना

आप [Jupyter एनवायरनमेंट](https://jupyter.org?WT.mc_id=academic-105485-koreyst) का उपयोग करके ब्राउज़र में प्रोजेक्ट पर काम कर सकते हैं। क्लासिक Jupyter और [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) एक सुखद डेवलपमेंट एनवायरनमेंट प्रदान करते हैं जिसमें ऑटो-कम्प्लीशन, कोड हाइलाइटिंग आदि जैसी सुविधाएं होती हैं।

Jupyter को लोकल रूप से शुरू करने के लिए, टर्मिनल/कमांड लाइन पर जाएं, कोर्स डायरेक्टरी पर नेविगेट करें और निम्नलिखित कमांड चलाएं:

```bash
jupyter notebook
```

या

```bash
jupyterhub
```

यह एक Jupyter इंस्टेंस शुरू करेगा और इसे एक्सेस करने के लिए URL कमांड लाइन विंडो में दिखाया जाएगा।

एक बार जब आप URL तक पहुंच जाते हैं, तो आपको कोर्स का आउटलाइन दिखाई देगा और आप किसी भी `*.ipynb` फ़ाइल पर नेविगेट कर सकते हैं। उदाहरण के लिए, `08-building-search-applications/python/oai-solution.ipynb`।

### कंटेनर में चलाना

अपने कंप्यूटर या Codespace पर सब कुछ सेटअप करने का एक विकल्प [कंटेनर](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>) का उपयोग करना है। कोर्स रिपॉजिटरी में विशेष `.devcontainer` फ़ोल्डर VS Code को प्रोजेक्ट को एक कंटेनर में सेटअप करने की अनुमति देता है। Codespaces के बाहर, इसके लिए Docker इंस्टॉलेशन की आवश्यकता होगी, और यह काफी काम शामिल करता है, इसलिए हम इसे केवल उन लोगों को सलाह देते हैं जिन्हें कंटेनर के साथ काम करने का अनुभव है।

GitHub Codespaces का उपयोग करते समय अपने API कुंजियों को सुरक्षित रखने के सर्वोत्तम तरीकों में से एक Codespace Secrets का उपयोग करना है। कृपया [Codespaces सीक्रेट्स मैनेजमेंट](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst) गाइड का पालन करें ताकि इसके बारे में अधिक जानकारी प्राप्त की जा सके।

## पाठ और तकनीकी आवश्यकताएं

इस कोर्स में 6 कॉन्सेप्ट लेसन और 6 कोडिंग लेसन हैं।

कोडिंग लेसन के लिए, हम Azure OpenAI Service का उपयोग कर रहे हैं। इस कोड को चलाने के लिए आपको Azure OpenAI सेवा और एक API कुंजी की आवश्यकता होगी। आप [इस आवेदन को पूरा करके](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst) एक्सेस प्राप्त करने के लिए आवेदन कर सकते हैं।

जब तक आपका आवेदन प्रक्रिया में है, प्रत्येक कोडिंग लेसन में एक `README.md` फ़ाइल भी शामिल है जहां आप कोड और आउटपुट देख सकते हैं।

## पहली बार Azure OpenAI सेवा का उपयोग करना

यदि यह पहली बार है जब आप Azure OpenAI सेवा के साथ काम कर रहे हैं, तो कृपया इस गाइड का पालन करें कि [Azure OpenAI सेवा संसाधन कैसे बनाएं और तैनात करें।](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst)

## पहली बार OpenAI API का उपयोग करना

यदि यह पहली बार है जब आप OpenAI API के साथ काम कर रहे हैं, तो कृपया इस गाइड का पालन करें कि [इंटरफ़ेस कैसे बनाएं और उपयोग करें।](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst)

## अन्य शिक्षार्थियों से मिलें

हमने हमारे आधिकारिक [AI Community Discord सर्वर](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) में अन्य शिक्षार्थियों से मिलने के लिए चैनल बनाए हैं। यह समान विचारधारा वाले उद्यमियों, निर्माताओं, छात्रों और जनरेटिव एआई में स्तर बढ़ाने के इच्छुक किसी भी व्यक्ति के साथ नेटवर्क बनाने का एक शानदार तरीका है।

[![डिस्कॉर्ड चैनल से जुड़ें](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

प्रोजेक्ट टीम भी इस Discord सर्वर पर शिक्षार्थियों की मदद करने के लिए उपलब्ध होगी।

## योगदान करें

यह कोर्स एक ओपन-सोर्स पहल है। यदि आप सुधार के क्षेत्र या मुद्दे देखते हैं, तो कृपया एक [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) बनाएं या एक [GitHub issue](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst) लॉग करें।

प्रोजेक्ट टीम सभी योगदानों को ट्रैक करेगी। ओपन-सोर्स में योगदान करना जनरेटिव एआई में अपने करियर को बनाने का एक अद्भुत तरीका है।

अधिकांश योगदानों के लिए आपको एक Contributor License Agreement (CLA) से सहमत होना होगा, जिसमें यह घोषित करना होगा कि आपके पास अधिकार हैं और वास्तव में, हमें आपके योगदान का उपयोग करने का अधिकार प्रदान करते हैं। विवरण के लिए [CLA, Contributor License Agreement वेबसाइट](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst) पर जाएं।

महत्वपूर्ण: इस रिपॉजिटरी में टेक्स्ट का अनुवाद करते समय, कृपया सुनिश्चित करें कि आप मशीन अनुवाद का उपयोग नहीं करते हैं। हम समुदाय के माध्यम से अनुवादों को सत्यापित करेंगे, इसलिए कृपया केवल उन भाषाओं में अनुवाद के लिए स्वयंसेवा करें जिनमें आप कुशल हैं।

जब आप एक पुल अनुरोध सबमिट करते हैं, तो एक CLA-बॉट स्वचालित रूप से निर्धारित करेगा कि क्या आपको CLA प्रदान करने की आवश्यकता है और PR को उपयुक्त रूप से सजाएगा (जैसे, लेबल, टिप्पणी)। कृपया बॉट द्वारा प्रदान किए गए निर्देशों का पालन करें। आपको यह केवल एक बार सभी रिपॉजिटरी के लिए करना होगा जो हमारे CLA का उपयोग करते हैं।

इस प्रोजेक्ट ने [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst) को अपनाया है। अधिक जानकारी के लिए Code of Conduct FAQ पढ़ें या [Email opencode](opencode@microsoft.com) पर किसी भी अतिरिक्त प्रश्न या टिप्पणियों के साथ संपर्क करें।

## चलिए शुरू करते हैं!
अब जब आपने इस कोर्स को पूरा करने के लिए आवश्यक चरण पूरे कर लिए हैं, तो चलिए शुरू करते हैं और [जनरेटिव AI और LLMs का परिचय](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst) प्राप्त करते हैं।

---

**अस्वीकरण**:  
यह दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) का उपयोग करके अनुवादित किया गया है। जबकि हम सटीकता के लिए प्रयास करते हैं, कृपया ध्यान दें कि स्वचालित अनुवाद में त्रुटियां या अशुद्धियां हो सकती हैं। मूल भाषा में दस्तावेज़ को आधिकारिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए, पेशेवर मानव अनुवाद की सिफारिश की जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम जिम्मेदार नहीं हैं।