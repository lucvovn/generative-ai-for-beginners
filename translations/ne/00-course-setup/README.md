<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-18T00:30:22+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "ne"
}
-->
# यो कोर्स सुरु गर्दै

हामी तपाईंलाई यो कोर्स सुरु गर्न र Generative AI सँग के निर्माण गर्न प्रेरित हुनुहुन्छ भनेर हेर्नको लागि धेरै उत्साहित छौं!

तपाईंको सफलताको सुनिश्चित गर्न, यो पृष्ठले सेटअप चरणहरू, प्राविधिक आवश्यकताहरू, र आवश्यक परेमा सहयोग कहाँ प्राप्त गर्ने बारेमा जानकारी दिन्छ।

## सेटअप चरणहरू

यो कोर्स लिन सुरु गर्न, तपाईंले निम्न चरणहरू पूरा गर्न आवश्यक छ।

### १. यो रिपोजिटरी फोर्क गर्नुहोस्

[यो सम्पूर्ण रिपोजिटरी फोर्क गर्नुहोस्](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) आफ्नो GitHub खातामा ताकि तपाईं कोड परिवर्तन गर्न सक्नुहुन्छ र चुनौतीहरू पूरा गर्न सक्नुहुन्छ। तपाईं [यो रिपोजिटरीलाई स्टार (🌟)](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) पनि गर्न सक्नुहुन्छ ताकि यसलाई र सम्बन्धित रिपोजिटरीहरू सजिलै भेट्न सक्नुहुन्छ।

### २. कोडस्पेस सिर्जना गर्नुहोस्

कोड चलाउँदा कुनै निर्भरता समस्या नहोस् भनेर सुनिश्चित गर्न, हामी यो कोर्स [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst) मा चलाउन सिफारिस गर्छौं।

तपाईंको फोर्कमा: **Code -> Codespaces -> New on main**

![कोडस्पेस सिर्जना गर्नका लागि बटनहरू देखाउने संवाद](../../../00-course-setup/images/who-will-pay.webp)

#### २.१ गोप्य जानकारी थप्नुहोस्

1. ⚙️ गियर आइकन -> Command Pallete-> Codespaces : Manage user secret -> Add a new secret.
2. नाम OPENAI_API_KEY राख्नुहोस्, आफ्नो key पेस्ट गर्नुहोस्, Save गर्नुहोस्।

### ३. अब के गर्ने?

| म चाहन्छु...          | जानुहोस्…                                                                  |
|---------------------|-------------------------------------------------------------------------|
| पाठ १ सुरु गर्नुहोस्      | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)     |
| अफलाइन काम गर्नुहोस्        | [`setup-local.md`](02-setup-local.md)                                   |
| LLM प्रदायक सेटअप गर्नुहोस् | [`providers.md`](03-providers.md)                                        |
| अन्य सिक्नेहरूसँग भेट्नुहोस् | [हाम्रो Discord मा सामेल हुनुहोस्](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)   |

## समस्या समाधान

| लक्षण                                   | समाधान                                                             |
|-------------------------------------------|-----------------------------------------------------------------|
| कन्टेनर निर्माण १० मिनेट भन्दा बढी समय लाग्यो            | **Codespaces ➜ “Rebuild Container”**                            |
| `python: command not found`               | टर्मिनल जडान भएन; **+** क्लिक गर्नुहोस् ➜ *bash*                    |
| OpenAI बाट `401 Unauthorized`            | गलत / समाप्त भएको `OPENAI_API_KEY`                                |
| VS Code ले “Dev container mounting…” देखाउँछ   | ब्राउजर ट्याब रिफ्रेस गर्नुहोस्—कहिलेकाहीं Codespaces जडान गुमाउँछ   |
| नोटबुक कर्नेल हराइरहेको छ                   | नोटबुक मेनु ➜ **Kernel ▸ Select Kernel ▸ Python 3**           |

   Unix-आधारित प्रणालीहरू:

   ```bash
   touch .env
   ```

   Windows:

   ```cmd
   echo . > .env
   ```

3. **`.env` फाइल सम्पादन गर्नुहोस्**: `.env` फाइललाई कुनै पनि टेक्स्ट एडिटर (जस्तै, VS Code, Notepad++, वा अन्य) मा खोल्नुहोस्। फाइलमा निम्न लाइन थप्नुहोस्, `your_github_token_here` लाई आफ्नो वास्तविक GitHub टोकनले बदल्नुहोस्:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```

4. **फाइल सुरक्षित गर्नुहोस्**: परिवर्तनहरू सुरक्षित गर्नुहोस् र टेक्स्ट एडिटर बन्द गर्नुहोस्।

5. **`python-dotenv` स्थापना गर्नुहोस्**: यदि तपाईंले पहिले नै स्थापना गर्नुभएको छैन भने, `.env` फाइलबाट वातावरणीय चरहरू लोड गर्न `python-dotenv` प्याकेज स्थापना गर्न आवश्यक छ। तपाईं यसलाई `pip` प्रयोग गरेर स्थापना गर्न सक्नुहुन्छ:

   ```bash
   pip install python-dotenv
   ```

6. **तपाईंको Python स्क्रिप्टमा वातावरणीय चरहरू लोड गर्नुहोस्**: तपाईंको Python स्क्रिप्टमा, `.env` फाइलबाट वातावरणीय चरहरू लोड गर्न `python-dotenv` प्याकेज प्रयोग गर्नुहोस्:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```

यति नै! तपाईंले सफलतापूर्वक `.env` फाइल सिर्जना गर्नुभयो, आफ्नो GitHub टोकन थप्नुभयो, र यसलाई आफ्नो Python एप्लिकेसनमा लोड गर्नुभयो।

## आफ्नो कम्प्युटरमा स्थानीय रूपमा कसरी चलाउने

कोडलाई आफ्नो कम्प्युटरमा स्थानीय रूपमा चलाउन, तपाईंलाई [Python](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst) को कुनै संस्करण स्थापना गर्न आवश्यक छ।

त्यसपछि रिपोजिटरी प्रयोग गर्न, तपाईंले यसलाई क्लोन गर्न आवश्यक छ:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

सबै कुरा जाँच गरेपछि, तपाईं सुरु गर्न सक्नुहुन्छ!

## वैकल्पिक चरणहरू

### Miniconda स्थापना गर्दै

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python, साथै केही प्याकेजहरू स्थापना गर्नको लागि हल्का इन्स्टलर हो। Conda आफैं एक प्याकेज म्यानेजर हो, जसले विभिन्न Python [**भर्चुअल वातावरणहरू**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) र प्याकेजहरू सेटअप गर्न र स्विच गर्न सजिलो बनाउँछ। यसले `pip` मार्फत उपलब्ध नभएका प्याकेजहरू स्थापना गर्न पनि मद्दत गर्दछ।

[MiniConda स्थापना गाइड](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst) पालना गरेर यसलाई सेटअप गर्नुहोस्।

Miniconda स्थापना गरेपछि, तपाईंले [रिपोजिटरी](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) क्लोन गर्न आवश्यक छ (यदि तपाईंले पहिले नै क्लोन गर्नुभएको छैन भने)।

त्यसपछि, तपाईंले भर्चुअल वातावरण सिर्जना गर्न आवश्यक छ। Conda प्रयोग गरेर यो गर्न, नयाँ वातावरण फाइल (_environment.yml_) सिर्जना गर्नुहोस्। यदि तपाईं Codespaces प्रयोग गर्दै हुनुहुन्छ भने, यसलाई `.devcontainer` निर्देशिकामा सिर्जना गर्नुहोस्, यसरी `.devcontainer/environment.yml`।

तपाईंको वातावरण फाइललाई तलको स्निपेटले भर्नुहोस्:

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

यदि तपाईंलाई conda प्रयोग गर्दा त्रुटिहरू आइपर्छ भने, तपाईंले म्यानुअली Microsoft AI Libraries निम्न कमाण्ड प्रयोग गरेर टर्मिनलमा स्थापना गर्न सक्नुहुन्छ।

```
conda install -c microsoft azure-ai-ml
```

वातावरण फाइलले हामीलाई आवश्यक निर्भरता निर्दिष्ट गर्दछ। `<environment-name>` ले तपाईंको Conda वातावरणको लागि प्रयोग गर्न चाहेको नामलाई जनाउँछ, र `<python-version>` ले तपाईं प्रयोग गर्न चाहेको Python को संस्करणलाई जनाउँछ, उदाहरणका लागि, `3` Python को पछिल्लो प्रमुख संस्करण हो।

त्यसपछि, तपाईं आफ्नो Conda वातावरण सिर्जना गर्न सक्नुहुन्छ तलका कमाण्डहरू चलाएर:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

यदि तपाईंलाई कुनै समस्या आउँछ भने [Conda वातावरण गाइड](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst) हेर्नुहोस्।

### Python समर्थन विस्तारसहित Visual Studio Code प्रयोग गर्दै

हामी यो कोर्सको लागि [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) एडिटर प्रयोग गर्न सिफारिस गर्छौं, जसमा [Python समर्थन विस्तार](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) स्थापना गरिएको छ। यद्यपि, यो सिफारिस मात्र हो, अनिवार्य आवश्यकता होइन।

> **नोट**: VS Code मा कोर्स रिपोजिटरी खोल्दा, तपाईंले परियोजना कन्टेनर भित्र सेटअप गर्ने विकल्प पाउनुहुन्छ। यो कोर्स रिपोजिटरी भित्र रहेको [विशेष `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) निर्देशिकाको कारण हो। यसबारे पछि थप जानकारी।

> **नोट**: जब तपाईं रिपोजिटरी क्लोन गरेर VS Code मा खोल्नुहुन्छ, यसले स्वचालित रूपमा तपाईंलाई Python समर्थन विस्तार स्थापना गर्न सुझाव दिनेछ।

> **नोट**: यदि VS Code ले रिपोजिटरीलाई कन्टेनरमा पुन: खोल्न सुझाव दिन्छ भने, स्थानीय रूपमा स्थापना गरिएको Python संस्करण प्रयोग गर्न यो अनुरोध अस्वीकार गर्नुहोस्।

### ब्राउजरमा Jupyter प्रयोग गर्दै

तपाईं [Jupyter environment](https://jupyter.org?WT.mc_id=academic-105485-koreyst) प्रयोग गरेर पनि परियोजनामा काम गर्न सक्नुहुन्छ। क्लासिक Jupyter र [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) ले स्वत: पूर्णता, कोड हाइलाइटिङ जस्ता सुविधाहरू सहित एक रमाइलो विकास वातावरण प्रदान गर्दछ।

Jupyter स्थानीय रूपमा सुरु गर्न, टर्मिनल/कमाण्ड लाइनमा जानुहोस्, कोर्स निर्देशिकामा नेभिगेट गर्नुहोस्, र निम्न कमाण्ड कार्यान्वयन गर्नुहोस्:

```bash
jupyter notebook
```

वा

```bash
jupyterhub
```

यसले Jupyter इन्स्टेन्स सुरु गर्नेछ र यसलाई पहुँच गर्न URL कमाण्ड लाइन विन्डोमा देखाइनेछ।

एकपटक तपाईंले URL पहुँच गर्नुभयो भने, तपाईंले कोर्सको रूपरेखा देख्नुहुनेछ र कुनै पनि `*.ipynb` फाइलमा नेभिगेट गर्न सक्नुहुनेछ। उदाहरणका लागि, `08-building-search-applications/python/oai-solution.ipynb`।

### कन्टेनरमा चलाउँदै

तपाईंको कम्प्युटर वा Codespace मा सबै सेटअप गर्ने विकल्पको सट्टा, तपाईं [कन्टेनर](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>) प्रयोग गर्न सक्नुहुन्छ। कोर्स रिपोजिटरी भित्रको विशेष `.devcontainer` फोल्डरले VS Code लाई परियोजना कन्टेनर भित्र सेटअप गर्न सम्भव बनाउँछ। Codespaces बाहिर, यसले Docker स्थापना आवश्यक छ, र यो वास्तवमा केही काम समावेश गर्दछ, त्यसैले हामी यो केवल कन्टेनरसँग काम गर्ने अनुभव भएका व्यक्तिहरूलाई सिफारिस गर्छौं।

GitHub Codespaces प्रयोग गर्दा तपाईंको API key सुरक्षित राख्नको लागि उत्तम तरिकाहरू मध्ये एक Codespace Secrets प्रयोग गर्नु हो। कृपया [Codespaces गोप्य व्यवस्थापन](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst) गाइड पालना गर्नुहोस्।

## पाठहरू र प्राविधिक आवश्यकताहरू

यो कोर्समा ६ अवधारणात्मक पाठहरू र ६ कोडिङ पाठहरू छन्।

कोडिङ पाठहरूको लागि, हामी Azure OpenAI सेवा प्रयोग गर्दैछौं। तपाईंलाई Azure OpenAI सेवा र API key को पहुँच आवश्यक छ। तपाईं [यो आवेदन पूरा गरेर](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst) पहुँचको लागि आवेदन दिन सक्नुहुन्छ।

जब तपाईंको आवेदन प्रक्रिया भइरहेको छ, प्रत्येक कोडिङ पाठमा `README.md` फाइल समावेश गरिएको छ जहाँ तपाईं कोड र आउटपुटहरू हेर्न सक्नुहुन्छ।

## Azure OpenAI सेवा पहिलो पटक प्रयोग गर्दै

यदि यो तपाईंको पहिलो पटक Azure OpenAI सेवा प्रयोग गर्दै हुनुहुन्छ भने, कृपया [Azure OpenAI सेवा स्रोत सिर्जना र परिनियोजन गर्ने](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst) गाइड पालना गर्नुहोस्।

## OpenAI API पहिलो पटक प्रयोग गर्दै

यदि यो तपाईंको पहिलो पटक OpenAI API प्रयोग गर्दै हुनुहुन्छ भने, कृपया [इन्टरफेस सिर्जना र प्रयोग गर्ने](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst) गाइड पालना गर्नुहोस्।

## अन्य सिक्नेहरूसँग भेट्नुहोस्

हामीले हाम्रो आधिकारिक [AI Community Discord server](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) मा अन्य सिक्नेहरूसँग भेट्नका लागि च्यानलहरू सिर्जना गरेका छौं। यो समान सोच भएका उद्यमीहरू, निर्माणकर्ताहरू, विद्यार्थीहरू, र Generative AI मा स्तर उकास्न खोजिरहेका व्यक्तिहरूसँग नेटवर्क गर्नको लागि उत्कृष्ट तरिका हो।

[![डिस्कोर्ड च्यानलमा सामेल हुनुहोस्](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

परियोजना टोली पनि यस Discord सर्भरमा सिक्नेहरूलाई मद्दत गर्न उपलब्ध हुनेछ।

## योगदान गर्नुहोस्

यो कोर्स एक खुला-स्रोत पहल हो। यदि तपाईंले सुधारका क्षेत्रहरू वा समस्याहरू देख्नुभयो भने, कृपया [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) सिर्जना गर्नुहोस् वा [GitHub समस्या](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst) लग गर्नुहोस्।

परियोजना टोलीले सबै योगदानहरू ट्र्याक गर्नेछ। खुला स्रोतमा योगदान गर्नु Generative AI मा आफ्नो करियर निर्माण गर्ने अद्भुत तरिका हो।

धेरैजसो योगदानहरूलाई Contributor License Agreement (CLA) मा सहमत हुन आवश्यक छ जसले घोषणा गर्दछ कि तपाईंलाई अधिकार छ र वास्तवमा हामीलाई तपाईंको योगदान प्रयोग गर्न अधिकार दिनुहुन्छ। थप जानकारीको लागि [CLA, Contributor License Agreement वेबसाइट](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst) हेर्नुहोस्।

जब तपाईंले pull request पेश गर्नुहुन्छ, CLA-bot ले स्वचालित रूपमा निर्धारण गर्नेछ कि तपाईंलाई CLA प्रदान गर्न आवश्यक छ कि छैन र PR लाई उपयुक्त रूपमा सजाउनेछ (जस्तै, लेबल, टिप्पणी)। तपाईंले केवल बोटले प्रदान गरेको निर्देशनहरू पालना गर्नुपर्नेछ। तपाईंले यो केवल एक पटक गर्नुपर्नेछ सबै रिपोजिटरीहरूमा हाम्रो CLA प्रयोग गर्दै।

यो परियोजनाले [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst) अपनाएको छ। थप जानकारीको लागि Code of Conduct FAQ पढ्नुहोस् वा [Email opencode](opencode@microsoft.com) मा थप प्रश्न वा टिप्पणीहरूका लागि सम्पर्क गर्नुहोस्।

## सुरु गरौं
अब तपाईंले यो पाठ्यक्रम पूरा गर्न आवश्यक चरणहरू पूरा गर्नुभएको छ, आउनुहोस् [Generative AI र LLMs को परिचय](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst) प्राप्त गरेर सुरु गरौं।

---

**अस्वीकरण**:  
यो दस्तावेज AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) प्रयोग गरेर अनुवाद गरिएको छ। हामी शुद्धताको लागि प्रयास गर्छौं, तर कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादमा त्रुटिहरू वा अशुद्धताहरू हुन सक्छ। यसको मूल भाषा मा रहेको मूल दस्तावेजलाई आधिकारिक स्रोत मानिनुपर्छ। महत्वपूर्ण जानकारीको लागि, व्यावसायिक मानव अनुवाद सिफारिस गरिन्छ। यस अनुवादको प्रयोगबाट उत्पन्न हुने कुनै पनि गलतफहमी वा गलत व्याख्याको लागि हामी जिम्मेवार हुनेछैनौं।