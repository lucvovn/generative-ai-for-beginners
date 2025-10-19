<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-18T00:27:12+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "mr"
}
-->
# या कोर्ससह सुरुवात करा

आम्ही खूप उत्सुक आहोत की तुम्ही हा कोर्स सुरू कराल आणि जनरेटिव्ह AI सह तुम्ही काय तयार करण्यासाठी प्रेरित व्हाल ते पाहू!

तुमच्या यशासाठी, या पृष्ठावर सेटअप चरण, तांत्रिक आवश्यकता आणि आवश्यक असल्यास मदत कुठे मिळवायची याची माहिती दिली आहे.

## सेटअप चरण

हा कोर्स सुरू करण्यासाठी, तुम्हाला खालील चरण पूर्ण करणे आवश्यक आहे.

### 1. या रिपॉझिटरीला फोर्क करा

[ही संपूर्ण रिपॉझिटरी फोर्क करा](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) तुमच्या स्वतःच्या GitHub खात्यावर, जेणेकरून तुम्ही कोड बदलू शकता आणि आव्हाने पूर्ण करू शकता. तुम्ही [या रिपॉझिटरीला स्टार (🌟)](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) देखील देऊ शकता, जेणेकरून ती आणि संबंधित रिपॉझिटरी सहज सापडतील.

### 2. कोडस्पेस तयार करा

कोड चालवताना कोणत्याही डिपेंडन्सी समस्यांना टाळण्यासाठी, आम्ही हा कोर्स [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst) मध्ये चालवण्याची शिफारस करतो.

तुमच्या फोर्कमध्ये: **Code -> Codespaces -> New on main**

![कोडस्पेस तयार करण्यासाठी बटणांचे डायलॉग](../../../00-course-setup/images/who-will-pay.webp)

#### 2.1 एक गुपित जोडा

1. ⚙️ गियर आयकॉन -> कमांड पॅलेट -> Codespaces : Manage user secret -> Add a new secret.  
2. नाव OPENAI_API_KEY, तुमची की पेस्ट करा, सेव्ह करा.

### 3. पुढे काय?

| मला करायचे आहे…       | जा…                                                                 |
|---------------------|---------------------------------------------------------------------|
| पहिला धडा सुरू करा | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md) |
| ऑफलाइन काम करा     | [`setup-local.md`](02-setup-local.md)                               |
| LLM प्रदाता सेटअप करा | [`providers.md`](03-providers.md)                                  |
| इतर शिकणाऱ्यांना भेटा | [आमच्या डिस्कॉर्डमध्ये सामील व्हा](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) |

## समस्या सोडवणे

| लक्षण                                   | उपाय                                                         |
|-----------------------------------------|-------------------------------------------------------------|
| कंटेनर बिल्ड 10 मिनिटांपेक्षा जास्त वेळ घेत आहे | **Codespaces ➜ “Rebuild Container”**                        |
| `python: command not found`             | टर्मिनल जोडलेले नाही; **+** वर क्लिक करा ➜ *bash*          |
| OpenAI कडून `401 Unauthorized`         | चुकीचा / कालबाह्य `OPENAI_API_KEY`                         |
| VS Code “Dev container mounting…” दाखवतो | ब्राउझर टॅब रीफ्रेश करा—कधी कधी Codespaces कनेक्शन गमावतो |
| नोटबुक कर्नल गायब                     | नोटबुक मेनू ➜ **Kernel ▸ Select Kernel ▸ Python 3**         |

   युनिक्स-आधारित प्रणाली:

   ```bash
   touch .env
   ```
  
   विंडोज:

   ```cmd
   echo . > .env
   ```
  
3. **`.env` फाइल संपादित करा**: `.env` फाइल टेक्स्ट एडिटरमध्ये उघडा (उदा., VS Code, Notepad++, किंवा इतर कोणताही एडिटर). खालील ओळ फाइलमध्ये जोडा, `your_github_token_here` तुमच्या वास्तविक GitHub टोकनने बदला:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```
  
4. **फाइल सेव्ह करा**: बदल सेव्ह करा आणि टेक्स्ट एडिटर बंद करा.

5. **`python-dotenv` इंस्टॉल करा**: जर तुम्ही आधीच केले नसेल, तर तुम्हाला `.env` फाइलमधून तुमच्या Python अॅप्लिकेशनमध्ये पर्यावरणीय व्हेरिएबल्स लोड करण्यासाठी `python-dotenv` पॅकेज इंस्टॉल करावे लागेल. तुम्ही ते `pip` वापरून इंस्टॉल करू शकता:

   ```bash
   pip install python-dotenv
   ```
  
6. **तुमच्या Python स्क्रिप्टमध्ये पर्यावरणीय व्हेरिएबल्स लोड करा**: तुमच्या Python स्क्रिप्टमध्ये, `.env` फाइलमधून पर्यावरणीय व्हेरिएबल्स लोड करण्यासाठी `python-dotenv` पॅकेज वापरा:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```
  
बस्स! तुम्ही यशस्वीरित्या `.env` फाइल तयार केली आहे, तुमचे GitHub टोकन जोडले आहे आणि ते तुमच्या Python अॅप्लिकेशनमध्ये लोड केले आहे.

## तुमच्या संगणकावर स्थानिकरित्या चालवणे

कोड तुमच्या संगणकावर स्थानिकरित्या चालवण्यासाठी, तुम्हाला [Python ची काही आवृत्ती इंस्टॉल केलेली](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst) असणे आवश्यक आहे.

त्यानंतर रिपॉझिटरी वापरण्यासाठी, तुम्हाला ती क्लोन करावी लागेल:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```
  
सर्व काही तपासल्यानंतर, तुम्ही सुरुवात करू शकता!

## पर्यायी चरण

### मिनिकोंडा इंस्टॉल करणे

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) हे [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python, तसेच काही पॅकेजेस इंस्टॉल करण्यासाठी एक हलके इंस्टॉलर आहे.  
Conda स्वतः एक पॅकेज मॅनेजर आहे, ज्यामुळे वेगवेगळ्या Python [**व्हर्च्युअल एन्व्हायर्नमेंट्स**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) आणि पॅकेजेस सेटअप करणे आणि स्विच करणे सोपे होते. हे `pip` द्वारे उपलब्ध नसलेल्या पॅकेजेस इंस्टॉल करण्यासाठी देखील उपयुक्त आहे.

[MiniConda इंस्टॉलेशन गाइड](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst) अनुसरण करून ते सेटअप करा.

Miniconda इंस्टॉल केल्यानंतर, तुम्हाला [रिपॉझिटरी](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) क्लोन करावी लागेल (जर तुम्ही आधीच केले नसेल तर).

यानंतर, तुम्हाला एक व्हर्च्युअल एन्व्हायर्नमेंट तयार करावे लागेल. Conda सह हे करण्यासाठी, नवीन एन्व्हायर्नमेंट फाइल (_environment.yml_) तयार करा. जर तुम्ही Codespaces वापरत असाल, तर `.devcontainer` डिरेक्टरीमध्ये हे तयार करा, म्हणजे `.devcontainer/environment.yml`.

तुमच्या एन्व्हायर्नमेंट फाइलमध्ये खालील स्निपेट भरा:

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
  
जर तुम्हाला Conda वापरताना त्रुटी आढळल्या तर तुम्ही टर्मिनलमध्ये खालील कमांड वापरून Microsoft AI Libraries मॅन्युअली इंस्टॉल करू शकता.

```
conda install -c microsoft azure-ai-ml
```
  
एन्व्हायर्नमेंट फाइल आवश्यक डिपेंडन्सी निर्दिष्ट करते. `<environment-name>` म्हणजे तुम्ही Conda एन्व्हायर्नमेंटसाठी वापरू इच्छित असलेले नाव आणि `<python-version>` म्हणजे तुम्ही वापरू इच्छित असलेली Python ची आवृत्ती, उदाहरणार्थ, `3` ही Python ची नवीनतम मुख्य आवृत्ती आहे.

हे पूर्ण झाल्यावर, तुम्ही तुमचे Conda एन्व्हायर्नमेंट तयार करण्यासाठी खालील कमांड्स तुमच्या कमांड लाइन/टर्मिनलमध्ये चालवू शकता:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```
  
जर तुम्हाला कोणत्याही समस्यांना सामोरे जावे लागले तर [Conda एन्व्हायर्नमेंट्स गाइड](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst) पहा.

### Python सपोर्ट एक्सटेंशनसह Visual Studio Code वापरणे

आम्ही या कोर्ससाठी [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) एडिटर Python सपोर्ट एक्सटेंशनसह वापरण्याची शिफारस करतो. तथापि, ही फक्त शिफारस आहे, अनिवार्य आवश्यकता नाही.

> **टीप**: VS Code मध्ये कोर्स रिपॉझिटरी उघडून, तुम्हाला प्रोजेक्ट कंटेनरमध्ये सेटअप करण्याचा पर्याय मिळतो. हे कोर्स रिपॉझिटरीमध्ये असलेल्या [विशेष `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) डिरेक्टरीमुळे आहे. याबद्दल नंतर अधिक माहिती मिळेल.

> **टीप**: एकदा तुम्ही रिपॉझिटरी क्लोन करून VS Code मध्ये उघडल्यावर, ते तुम्हाला आपोआप Python सपोर्ट एक्सटेंशन इंस्टॉल करण्याचा सल्ला देईल.

> **टीप**: जर VS Code तुम्हाला रिपॉझिटरी कंटेनरमध्ये पुन्हा उघडण्याचा सल्ला देत असेल, तर स्थानिकरित्या इंस्टॉल केलेल्या Python आवृत्तीचा वापर करण्यासाठी हा विनंती नाकारावा.

### ब्राउझरमध्ये Jupyter वापरणे

तुम्ही [Jupyter एन्व्हायर्नमेंट](https://jupyter.org?WT.mc_id=academic-105485-koreyst) ब्राउझरमध्ये वापरून प्रोजेक्टवर काम करू शकता. क्लासिक Jupyter आणि [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) ऑटो-कम्प्लिशन, कोड हायलाइटिंग इत्यादी वैशिष्ट्यांसह एक सुखद विकास वातावरण प्रदान करतात.

Jupyter स्थानिकरित्या सुरू करण्यासाठी, टर्मिनल/कमांड लाइनवर जा, कोर्स डिरेक्टरीमध्ये जा आणि खालील कमांड चालवा:

```bash
jupyter notebook
```
  
किंवा

```bash
jupyterhub
```
  
यामुळे Jupyter सुरू होईल आणि त्याचा ऍक्सेस करण्यासाठी URL कमांड लाइन विंडोमध्ये दाखवला जाईल.

एकदा तुम्ही URL ऍक्सेस केल्यावर, तुम्हाला कोर्सचे स्वरूप दिसेल आणि तुम्ही कोणत्याही `*.ipynb` फाइलवर जाऊ शकता. उदाहरणार्थ, `08-building-search-applications/python/oai-solution.ipynb`.

### कंटेनरमध्ये चालवणे

तुमच्या संगणकावर किंवा Codespace वर सर्व काही सेटअप करण्याचा पर्याय म्हणजे [कंटेनर](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>) वापरणे. कोर्स रिपॉझिटरीमधील विशेष `.devcontainer` फोल्डरमुळे VS Code प्रोजेक्ट कंटेनरमध्ये सेटअप करणे शक्य होते. Codespaces बाहेर, यासाठी Docker इंस्टॉल करणे आवश्यक आहे, आणि प्रामाणिकपणे सांगायचे तर, यासाठी थोडेसे काम करावे लागते, त्यामुळे आम्ही हे फक्त कंटेनर कामकाजाचा अनुभव असलेल्या लोकांसाठी शिफारस करतो.

GitHub Codespaces वापरताना तुमच्या API की सुरक्षित ठेवण्याचा सर्वोत्तम मार्ग म्हणजे Codespace Secrets वापरणे. कृपया [Codespaces secrets management](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst) मार्गदर्शक अनुसरण करा.

## धडे आणि तांत्रिक आवश्यकता

या कोर्समध्ये 6 संकल्पना धडे आणि 6 कोडिंग धडे आहेत.

कोडिंग धड्यांसाठी, आम्ही Azure OpenAI Service वापरत आहोत. तुम्हाला Azure OpenAI सेवा आणि API कीची आवश्यकता असेल. तुम्ही [ही अर्ज प्रक्रिया पूर्ण करून](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst) ऍक्सेससाठी अर्ज करू शकता.

तुमचा अर्ज प्रक्रिया होईपर्यंत, प्रत्येक कोडिंग धड्यात `README.md` फाइल समाविष्ट आहे जिथे तुम्ही कोड आणि आउटपुट पाहू शकता.

## प्रथमच Azure OpenAI सेवा वापरणे

जर तुम्ही प्रथमच Azure OpenAI सेवा वापरत असाल, तर कृपया [Azure OpenAI सेवा संसाधन तयार आणि तैनात कसे करावे](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst) या मार्गदर्शकाचे अनुसरण करा.

## प्रथमच OpenAI API वापरणे

जर तुम्ही प्रथमच OpenAI API वापरत असाल, तर कृपया [इंटरफेस तयार आणि वापरण्याबद्दल मार्गदर्शक](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst) अनुसरण करा.

## इतर शिकणाऱ्यांना भेटा

आम्ही आमच्या अधिकृत [AI Community Discord सर्व्हर](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) मध्ये इतर शिकणाऱ्यांना भेटण्यासाठी चॅनेल तयार केले आहेत. जनरेटिव्ह AI मध्ये स्तर उंचावण्याचा विचार करणाऱ्या उद्योजक, निर्माते, विद्यार्थी आणि कोणत्याही समान विचारसरणीच्या लोकांशी नेटवर्किंग करण्याचा हा एक उत्तम मार्ग आहे.

[![डिस्कॉर्ड चॅनेलमध्ये सामील व्हा](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

प्रोजेक्ट टीम देखील या डिस्कॉर्ड सर्व्हरवर शिकणाऱ्यांना मदत करण्यासाठी असेल.

## योगदान द्या

हा कोर्स एक ओपन-सोर्स उपक्रम आहे. जर तुम्हाला सुधारणा करण्याचे क्षेत्र किंवा समस्या दिसत असतील, तर कृपया [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) तयार करा किंवा [GitHub issue](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst) लॉग करा.

प्रोजेक्ट टीम सर्व योगदानांचे ट्रॅकिंग करेल. ओपन सोर्समध्ये योगदान देणे हे जनरेटिव्ह AI मध्ये तुमचे करिअर घडवण्याचा एक अद्भुत मार्ग आहे.

बहुतेक योगदानांसाठी तुम्हाला Contributor License Agreement (CLA) सहमत होण्याची आवश्यकता आहे, ज्यामध्ये तुम्हाला अधिकार आहेत आणि प्रत्यक्षात तुम्ही आम्हाला तुमचे योगदान वापरण्याचे अधिकार देत आहात. तपशीलांसाठी, [CLA, Contributor License Agreement वेबसाइट](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst) भेट द्या.

महत्त्वाचे: या रिपॉझिटरीमधील मजकूर अनुवाद करताना, कृपया मशीन अनुवाद वापरू नका याची खात्री करा. आम्ही समुदायाद्वारे अनुवाद सत्यापित करू, त्यामुळे कृपया फक्त त्या भाषांमध्ये अनुवादासाठी स्वयंसेवा करा ज्यामध्ये तुम्ही प्रवीण आहात.

तुम्ही Pull Request सबमिट केल्यावर, CLA-बॉट आपोआप ठरवेल की तुम्हाला CLA प्रदान करणे आवश्यक आहे का आणि PR योग्यरित्या सजवेल (उदा., लेबल, टिप्पणी). बॉटद्वारे प्रदान केलेल्या सूचनांचे अनुसरण करा. तुम्हाला आमच्या CLA वापरणाऱ्या सर्व रिपॉझिटरीमध्ये हे फक्त एकदाच करावे लागेल.

या प्रोजेक्टने [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst) स्वीकारले आहे. अधिक माहितीसाठी Code of Conduct FAQ वाचा किंवा [Email opencode](opencode@microsoft.com) वर कोणतेही अतिरिक्त प्रश्न किंवा टिप्पण्या पाठवा.

## चला सुरुवात करू!
आता तुम्ही या कोर्ससाठी आवश्यक टप्पे पूर्ण केले आहेत, चला सुरुवात करूया [जनरेटिव्ह AI आणि LLMs ची ओळख](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst) मिळवून.

---

**अस्वीकरण**:  
हा दस्तऐवज AI भाषांतर सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) वापरून भाषांतरित करण्यात आला आहे. आम्ही अचूकतेसाठी प्रयत्नशील असलो तरी, कृपयास लक्षात ठेवा की स्वयंचलित भाषांतरांमध्ये त्रुटी किंवा अचूकतेचा अभाव असू शकतो. मूळ भाषेतील दस्तऐवज हा अधिकृत स्रोत मानला जावा. महत्त्वाच्या माहितीसाठी व्यावसायिक मानवी भाषांतराची शिफारस केली जाते. या भाषांतराचा वापर करून उद्भवलेल्या कोणत्याही गैरसमज किंवा चुकीच्या अर्थासाठी आम्ही जबाबदार नाही.