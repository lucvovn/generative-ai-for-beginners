<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "df027997f1448323d6159b78a1b669bf",
  "translation_date": "2025-10-18T00:26:28+00:00",
  "source_file": "06-text-generation-apps/README.md",
  "language_code": "mr"
}
-->
# टेक्स्ट जनरेशन अ‍ॅप्लिकेशन्स तयार करणे

[![टेक्स्ट जनरेशन अ‍ॅप्लिकेशन्स तयार करणे](../../../translated_images/06-lesson-banner.a5c629f990a636c852353c5533f1a6a218ece579005e91f96339d508d9cf8f47.mr.png)](https://youtu.be/0Y5Luf5sRQA?si=t_xVg0clnAI4oUFZ)

> _(वरील प्रतिमेवर क्लिक करून या धड्याचा व्हिडिओ पहा)_

या अभ्यासक्रमाद्वारे तुम्ही आतापर्यंत पाहिले आहे की प्रॉम्प्ट्ससारख्या मुख्य संकल्पना आणि "प्रॉम्प्ट इंजिनिअरिंग" नावाचा एक संपूर्ण शिस्त आहे. तुम्ही ज्या अनेक साधनांशी संवाद साधू शकता जसे की ChatGPT, Office 365, Microsoft Power Platform आणि बरेच काही, तुम्हाला काहीतरी साध्य करण्यासाठी प्रॉम्प्ट्स वापरण्यास समर्थन देतात.

तुम्हाला अ‍ॅपमध्ये अशी अनुभव जोडायची असल्यास, तुम्हाला प्रॉम्प्ट्स, पूर्णता आणि काम करण्यासाठी लायब्ररी निवडण्यासारख्या संकल्पनांचा अभ्यास करणे आवश्यक आहे. तुम्ही या अध्यायात नेमके हेच शिकाल.

## परिचय

या अध्यायात, तुम्ही:

- openai लायब्ररी आणि त्याच्या मुख्य संकल्पनांबद्दल शिकाल.
- openai वापरून एक टेक्स्ट जनरेशन अ‍ॅप तयार कराल.
- प्रॉम्प्ट, तापमान आणि टोकन्ससारख्या संकल्पनांचा वापर करून टेक्स्ट जनरेशन अ‍ॅप कसे तयार करायचे ते समजून घ्याल.

## शिकण्याची उद्दिष्टे

या धड्याच्या शेवटी, तुम्ही:

- टेक्स्ट जनरेशन अ‍ॅप म्हणजे काय ते स्पष्ट करू शकाल.
- openai वापरून टेक्स्ट जनरेशन अ‍ॅप तयार करू शकाल.
- तुमच्या अ‍ॅपला अधिक किंवा कमी टोकन्स वापरण्यासाठी आणि विविध आउटपुटसाठी तापमान बदलण्यासाठी कॉन्फिगर करू शकाल.

## टेक्स्ट जनरेशन अ‍ॅप म्हणजे काय?

सामान्यतः जेव्हा तुम्ही अ‍ॅप तयार करता तेव्हा त्यामध्ये खालीलप्रमाणे काही प्रकारचे इंटरफेस असते:

- कमांड-आधारित. कन्सोल अ‍ॅप्स हे सामान्यतः अ‍ॅप्स असतात जिथे तुम्ही कमांड टाइप करता आणि ते कार्य पूर्ण करते. उदाहरणार्थ, `git` हे एक कमांड-आधारित अ‍ॅप आहे.
- युजर इंटरफेस (UI). काही अ‍ॅप्समध्ये ग्राफिकल युजर इंटरफेस (GUIs) असतात जिथे तुम्ही बटणे क्लिक करता, टेक्स्ट इनपुट करता, पर्याय निवडता आणि बरेच काही करता.

### कन्सोल आणि UI अ‍ॅप्स मर्यादित आहेत

तुम्ही टाइप केलेल्या कमांड-आधारित अ‍ॅपशी तुलना करा:

- **हे मर्यादित आहे**. तुम्ही कोणताही कमांड टाइप करू शकत नाही, फक्त अ‍ॅप समर्थन देतो तेच टाइप करू शकता.
- **भाषा विशिष्ट**. काही अ‍ॅप्स अनेक भाषांना समर्थन देतात, परंतु डीफॉल्टनुसार अ‍ॅप विशिष्ट भाषेसाठी तयार केले जाते, जरी तुम्ही अधिक भाषा समर्थन जोडू शकत असाल.

### टेक्स्ट जनरेशन अ‍ॅप्सचे फायदे

तर टेक्स्ट जनरेशन अ‍ॅप कसे वेगळे आहे?

टेक्स्ट जनरेशन अ‍ॅपमध्ये तुम्हाला अधिक लवचिकता मिळते, तुम्ही कमांड्सच्या सेट किंवा विशिष्ट इनपुट भाषेपुरते मर्यादित नसता. त्याऐवजी, तुम्ही अ‍ॅपशी संवाद साधण्यासाठी नैसर्गिक भाषा वापरू शकता. आणखी एक फायदा म्हणजे तुम्ही आधीच माहितीच्या विस्तृत संग्रहावर प्रशिक्षित केलेल्या डेटासोर्सशी संवाद साधत आहात, तर पारंपरिक अ‍ॅप डेटाबेसमध्ये मर्यादित असू शकतो.

### टेक्स्ट जनरेशन अ‍ॅपसह मी काय तयार करू शकतो?

तुम्ही अनेक गोष्टी तयार करू शकता. उदाहरणार्थ:

- **चॅटबॉट**. तुमच्या कंपनी आणि तिच्या उत्पादनांबद्दल प्रश्नांची उत्तरे देणारा चॅटबॉट एक चांगला पर्याय असू शकतो.
- **मदतनीस**. LLMs टेक्स्टचे सारांश तयार करणे, टेक्स्टमधून अंतर्दृष्टी मिळवणे, रेझ्युमे तयार करणे यासारख्या गोष्टींमध्ये उत्कृष्ट आहेत.
- **कोड सहाय्यक**. तुम्ही वापरत असलेल्या भाषा मॉडेलवर अवलंबून, तुम्ही कोड लिहिण्यास मदत करणारा कोड सहाय्यक तयार करू शकता. उदाहरणार्थ, तुम्ही GitHub Copilot तसेच ChatGPT सारख्या उत्पादनांचा वापर करून कोड लिहू शकता.

## मी कसे सुरुवात करू शकतो?

ठीक आहे, तुम्हाला LLM सह एकत्रित होण्याचा मार्ग शोधणे आवश्यक आहे ज्यामध्ये सामान्यतः खालील दोन पद्धतींचा समावेश असतो:

- API वापरा. येथे तुम्ही तुमच्या प्रॉम्प्टसह वेब विनंत्या तयार करत आहात आणि परत तयार केलेला टेक्स्ट मिळवत आहात.
- लायब्ररी वापरा. लायब्ररी API कॉल्स कॅप्सूल करण्यात मदत करतात आणि त्यांचा वापर सुलभ करतात.

## लायब्ररी/SDKs

LLMs सोबत काम करण्यासाठी काही प्रसिद्ध लायब्ररी आहेत जसे की:

- **openai**, ही लायब्ररी तुमच्या मॉडेलशी कनेक्ट होणे आणि प्रॉम्प्ट्स पाठवणे सोपे करते.

त्यानंतर उच्च स्तरावर कार्य करणाऱ्या लायब्ररी आहेत जसे की:

- **Langchain**. Langchain चांगले ओळखले जाते आणि Python ला समर्थन देते.
- **Semantic Kernel**. Semantic Kernel ही Microsoft ची लायब्ररी आहे जी C#, Python आणि Java भाषांना समर्थन देते.

## openai वापरून पहिला अ‍ॅप

चला पाहूया की आपण आपला पहिला अ‍ॅप कसा तयार करू शकतो, कोणत्या लायब्ररीची आवश्यकता आहे, किती आवश्यक आहे वगैरे.

### openai इंस्टॉल करा

OpenAI किंवा Azure OpenAI सोबत संवाद साधण्यासाठी अनेक लायब्ररी उपलब्ध आहेत. C#, Python, JavaScript, Java आणि इतर अनेक प्रोग्रामिंग भाषा वापरणे शक्य आहे. आम्ही `openai` Python लायब्ररी वापरण्यास निवडले आहे, त्यामुळे आम्ही ती `pip` वापरून इंस्टॉल करू.

```bash
pip install openai
```

### संसाधन तयार करा

तुम्हाला खालील चरण पूर्ण करणे आवश्यक आहे:

- Azure वर खाते तयार करा [https://azure.microsoft.com/free/](https://azure.microsoft.com/free/?WT.mc_id=academic-105485-koreyst).
- Azure OpenAI साठी प्रवेश मिळवा. [https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai](https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai?WT.mc_id=academic-105485-koreyst) येथे जा आणि प्रवेशासाठी अर्ज करा.

  > [!NOTE]
  > लेखनाच्या वेळी, तुम्हाला Azure OpenAI साठी प्रवेशासाठी अर्ज करणे आवश्यक आहे.

- Python इंस्टॉल करा <https://www.python.org/>
- Azure OpenAI सेवा संसाधन तयार केले आहे. [संसाधन तयार करण्यासाठी मार्गदर्शक](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal?WT.mc_id=academic-105485-koreyst) पहा.

### API की आणि एंडपॉइंट शोधा

या टप्प्यावर, तुम्हाला तुमच्या `openai` लायब्ररीला कोणती API की वापरायची ते सांगणे आवश्यक आहे. तुमची API की शोधण्यासाठी, Azure OpenAI संसाधनाच्या "Keys and Endpoint" विभागात जा आणि "Key 1" मूल्य कॉपी करा.

![Azure पोर्टलमधील Keys and Endpoint संसाधन ब्लेड](https://learn.microsoft.com/azure/ai-services/openai/media/quickstarts/endpoint.png?WT.mc_id=academic-105485-koreyst)

आता तुमच्याकडे ही माहिती कॉपी केली आहे, चला लायब्ररींना ती वापरण्यास सांगूया.

> [!NOTE]
> तुमची API की तुमच्या कोडपासून वेगळी ठेवणे योग्य आहे. तुम्ही पर्यावरणीय व्हेरिएबल्स वापरून हे करू शकता.
>
> - पर्यावरणीय व्हेरिएबल `OPENAI_API_KEY` तुमच्या API की वर सेट करा.
>   `export OPENAI_API_KEY='sk-...'`

### Azure कॉन्फिगरेशन सेटअप करा

जर तुम्ही Azure OpenAI वापरत असाल, तर कॉन्फिगरेशन कसे सेटअप करायचे ते येथे आहे:

```python
openai.api_type = 'azure'
openai.api_key = os.environ["OPENAI_API_KEY"]
openai.api_version = '2023-05-15'
openai.api_base = os.getenv("API_BASE")
```

वरील सेटअपमध्ये आम्ही खालील गोष्टी सेट करत आहोत:

- `api_type` `azure` वर सेट केले आहे. हे लायब्ररीला OpenAI ऐवजी Azure OpenAI वापरण्यास सांगते.
- `api_key`, ही तुमची Azure पोर्टलमध्ये सापडलेली API की आहे.
- `api_version`, ही तुम्हाला वापरायची असलेली API ची आवृत्ती आहे. लेखनाच्या वेळी, नवीनतम आवृत्ती `2023-05-15` आहे.
- `api_base`, हा API चा एंडपॉइंट आहे. तुम्ही तुमच्या API कीच्या शेजारी Azure पोर्टलमध्ये ते शोधू शकता.

> [!NOTE] > `os.getenv` ही एक फंक्शन आहे जी पर्यावरणीय व्हेरिएबल्स वाचते. तुम्ही `OPENAI_API_KEY` आणि `API_BASE` सारख्या पर्यावरणीय व्हेरिएबल्स वाचण्यासाठी याचा वापर करू शकता. तुमच्या टर्मिनलमध्ये किंवा `dotenv` सारख्या लायब्ररीचा वापर करून हे पर्यावरणीय व्हेरिएबल्स सेट करा.

## टेक्स्ट तयार करा

टेक्स्ट तयार करण्याचा मार्ग म्हणजे `Completion` वर्ग वापरणे. येथे एक उदाहरण आहे:

```python
prompt = "Complete the following: Once upon a time there was a"

completion = openai.Completion.create(model="davinci-002", prompt=prompt)
print(completion.choices[0].text)
```

वरील कोडमध्ये, आम्ही एक पूर्णता ऑब्जेक्ट तयार करतो आणि आम्हाला वापरायचे मॉडेल आणि प्रॉम्प्ट पास करतो. नंतर आम्ही तयार केलेला टेक्स्ट प्रिंट करतो.

### चॅट पूर्णता

आतापर्यंत, तुम्ही पाहिले आहे की आम्ही टेक्स्ट तयार करण्यासाठी `Completion` वापरत आहोत. परंतु एक वर्ग आहे ज्याला `ChatCompletion` म्हणतात जो चॅटबॉट्ससाठी अधिक योग्य आहे. येथे त्याचा वापर करण्याचे एक उदाहरण आहे:

```python
import openai

openai.api_key = "sk-..."

completion = openai.ChatCompletion.create(model="gpt-3.5-turbo", messages=[{"role": "user", "content": "Hello world"}])
print(completion.choices[0].message.content)
```

या कार्यक्षमतेबद्दल पुढील अध्यायात अधिक माहिती.

## व्यायाम - तुमचा पहिला टेक्स्ट जनरेशन अ‍ॅप

आता आपण openai सेट अप आणि कॉन्फिगर कसे करायचे ते शिकलो आहोत, आता तुमचा पहिला टेक्स्ट जनरेशन अ‍ॅप तयार करण्याची वेळ आली आहे. तुमचा अ‍ॅप तयार करण्यासाठी, खालील चरणांचे अनुसरण करा:

1. एक वर्च्युअल वातावरण तयार करा आणि openai इंस्टॉल करा:

   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install openai
   ```

   > [!NOTE]
   > जर तुम्ही Windows वापरत असाल तर `venv\Scripts\activate` ऐवजी `source venv/bin/activate` टाइप करा.

   > [!NOTE]
   > तुमची Azure OpenAI की शोधा [https://portal.azure.com/](https://portal.azure.com/?WT.mc_id=academic-105485-koreyst) वर जा आणि `Open AI` शोधा आणि `Open AI resource` निवडा आणि नंतर `Keys and Endpoint` निवडा आणि `Key 1` मूल्य कॉपी करा.

1. _app.py_ फाइल तयार करा आणि त्यामध्ये खालील कोड द्या:

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
   > जर तुम्ही Azure OpenAI वापरत असाल, तर तुम्हाला `api_type` `azure` वर सेट करणे आवश्यक आहे आणि `api_key` तुमच्या Azure OpenAI कीवर सेट करणे आवश्यक आहे.

   तुम्हाला खालीलप्रमाणे आउटपुट दिसेल:

   ```output
    very unhappy _____.

   Once upon a time there was a very unhappy mermaid.
   ```

## वेगवेगळ्या गोष्टींसाठी वेगवेगळ्या प्रकारचे प्रॉम्प्ट्स

आता तुम्ही पाहिले आहे की प्रॉम्प्ट वापरून टेक्स्ट कसे तयार करायचे. तुमच्याकडे एक प्रोग्राम देखील चालू आहे ज्यामध्ये तुम्ही बदल करू शकता आणि वेगवेगळ्या प्रकारचा टेक्स्ट तयार करू शकता.

प्रॉम्प्ट्स सर्व प्रकारच्या कार्यांसाठी वापरले जाऊ शकतात. उदाहरणार्थ:

- **टेक्स्ट तयार करा**. उदाहरणार्थ, तुम्ही कविता, क्विझसाठी प्रश्न इत्यादी तयार करू शकता.
- **माहिती शोधा**. तुम्ही 'वेब डेव्हलपमेंटमध्ये CORS म्हणजे काय?' यासारख्या माहिती शोधण्यासाठी प्रॉम्प्ट्स वापरू शकता.
- **कोड तयार करा**. तुम्ही कोड तयार करण्यासाठी प्रॉम्प्ट्स वापरू शकता, उदाहरणार्थ ईमेल्स सत्यापित करण्यासाठी वापरले जाणारे नियमित अभिव्यक्ती विकसित करणे किंवा संपूर्ण प्रोग्राम तयार करणे, जसे की वेब अ‍ॅप?

## एक अधिक व्यावहारिक उपयोग: रेसिपी जनरेटर

कल्पना करा की तुमच्याकडे घरी साहित्य आहे आणि तुम्हाला काहीतरी शिजवायचे आहे. त्यासाठी तुम्हाला रेसिपीची आवश्यकता आहे. रेसिपी शोधण्याचा एक मार्ग म्हणजे सर्च इंजिन वापरणे किंवा तुम्ही LLM वापरू शकता.

तुम्ही असा प्रॉम्प्ट लिहू शकता:

> "चिकन, बटाटे आणि गाजर या साहित्यांसह डिशसाठी 5 रेसिपी दाखवा. प्रत्येक रेसिपीसाठी, वापरलेली सर्व सामग्री सूचीबद्ध करा"

वरील प्रॉम्प्ट दिल्यानंतर, तुम्हाला खालीलप्रमाणे प्रतिसाद मिळू शकतो:

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

हे परिणाम उत्कृष्ट आहे, मला काय शिजवायचे आहे ते माहित आहे. या टप्प्यावर, उपयुक्त सुधारणा काय असू शकतात:

- मला आवडत नाही किंवा ज्यामुळे मला अ‍ॅलर्जी आहे अशा घटकांना फिल्टर करणे.
- जर माझ्याकडे घरी सर्व साहित्य नसेल तर खरेदी यादी तयार करणे.

वरील प्रकरणांसाठी, चला एक अतिरिक्त प्रॉम्प्ट जोडूया:

> "कृपया लसूण असलेल्या रेसिपी काढा कारण मला अ‍ॅलर्जी आहे आणि त्याऐवजी काहीतरी वेगळे बदला. तसेच, कृपया रेसिपीसाठी खरेदी यादी तयार करा, विचार करा की माझ्याकडे आधीच चिकन, बटाटे आणि गाजर आहेत."

आता तुम्हाला एक नवीन परिणाम मिळेल, म्हणजे:

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

ही तुमची पाच रेसिपी आहेत, ज्यामध्ये लसूणचा उल्लेख नाही आणि तुमच्याकडे घरी आधीच असलेल्या गोष्टी विचारात घेऊन तुम्हाला खरेदी यादी देखील मिळाली आहे.

## व्यायाम - रेसिपी जनरेटर तयार करा

आता आपण एक परिदृश्य खेळले आहे, चला प्रदर्शित केलेल्या परिदृश्याशी जुळणारा कोड लिहूया. असे करण्यासाठी, खालील चरणांचे अनुसरण करा:

1. विद्यमान _app.py_ फाइल प्रारंभ बिंदू म्हणून वापरा
1. `prompt` व्हेरिएबल शोधा आणि त्याचा कोड खालीलप्रमाणे बदला:

   ```python
   prompt = "Show me 5 recipes for a dish with the following ingredients: chicken, potatoes, and carrots. Per recipe, list all the ingredients used"
   ```

   जर तुम्ही आता कोड चालवला तर तुम्हाला खालीलप्रमाणे आउटपुट दिसेल:

   ```output
   -Chicken Stew with Potatoes and Carrots: 3 tablespoons oil, 1 onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 1/2 cups chicken broth, 1/2 cup dry white wine, 2 tablespoons chopped fresh parsley, 2 tablespoons unsalted butter, 1 1/2 pounds boneless, skinless chicken thighs, cut into 1-inch pieces
   -Oven-Roasted Chicken with Potatoes and Carrots: 3 tablespoons extra-virgin olive oil, 1 tablespoon Dijon mustard, 1 tablespoon chopped fresh rosemary, 1 tablespoon chopped fresh thyme, 4 cloves garlic, minced, 1 1/2 pounds small red potatoes, quartered, 1 1/2 pounds carrots, quartered lengthwise, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 (4-pound) whole chicken
   -Chicken, Potato, and Carrot Casserole: cooking spray, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and shredded, 1 potato, peeled and shredded, 1/2 teaspoon dried thyme leaves, 1/4 teaspoon salt, 1/4 teaspoon black pepper, 2 cups fat-free, low-sodium chicken broth, 1 cup frozen peas, 1/4 cup all-purpose flour, 1 cup 2% reduced-fat milk, 1/4 cup grated Parmesan cheese

   -One Pot Chicken and Potato Dinner: 2 tablespoons olive oil, 1 pound boneless, skinless chicken thighs, cut into 1-inch pieces, 1 large onion, chopped, 3 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 2 cups chicken broth, 1/2 cup dry white wine

   -Chicken, Potato, and Carrot Curry: 1 tablespoon vegetable oil, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 teaspoon ground coriander, 1 teaspoon ground cumin, 1/2 teaspoon ground turmeric, 1/2 teaspoon ground ginger, 1/4 teaspoon cayenne pepper, 2 cups chicken broth, 1/2 cup dry white wine, 1 (15-ounce) can chickpeas, drained and rinsed, 1/2 cup raisins, 1/2 cup chopped fresh cilantro
   ```

   > NOTE, तुमचा LLM अनिश्चित आहे, त्यामुळे तुम्हाला प्रत्येक वेळी प्रोग्राम चालवताना वेगवेगळे परिणाम मिळू शकतात.

   छान, चला पाहूया की आपण गोष्टी कशा सुधारू शकतो. गोष्टी सुधारण्यासाठी, आम्हाला खात्री करायची आहे की कोड लवचिक आहे, त्यामुळे साहित्य आणि रेसिपींची संख्या सुधारली जाऊ शकते आणि बदलली जाऊ शकते.

1. चला कोड खालीलप्रमाणे बदलूया:

   ```python
   no_recipes = input("No of recipes (for example, 5): ")

   ingredients = input("List of ingredients (for example, chicken, potatoes, and carrots): ")

   # interpolate the number of recipes into the prompt an ingredients
   prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used"
   ```

   कोडची चाचणी घेतल्यावर, असे दिसू शकते:

   ```output
   No of recipes (for example, 5): 3
   List of ingredients (for example, chicken, potatoes, and carrots): milk,strawberries

   -Strawberry milk shake: milk, strawberries, sugar, vanilla extract, ice cubes
   -Strawberry shortcake: milk, flour, baking powder, sugar, salt, unsalted butter, strawberries, whipped cream
   -Strawberry milk: milk, strawberries, sugar, vanilla extract
   ```

### फिल्टर आणि खरेदी यादी जोडून सुधारणा करा

आता आमच्याकडे रेसिपी तयार करण्यास सक्षम असलेला कार्यरत अ‍ॅप आहे आणि तो लवचिक आहे कारण तो वापरकर्त्याच्या इनपुटवर अवलंबून आहे, रेसिपींच्या संख्येवर तसेच वापरलेल्या साहित्यावर.

याला पुढे सुधारण्यासाठी, आम्हाला खालील गोष्टी जोडायच्या आहेत:

- **साहित्य फिल्टर करा**. आम्हाला असे साहित्य फिल्टर करायचे आहे जे आम्हाला आवडत नाही किंवा ज्यामुळे आम्हाला अ‍ॅलर्जी आहे. हे बदल साध्य करण्यासाठी, आम्ही आमच्या विद्यमान प्रॉम्प्टमध्ये संपादन करू शकतो आणि त्याच्या शेवटी फिल्टर अट जोडू शकतो:

  ```python
  filter = input("Filter (for example, vegetarian, vegan, or gluten-free): ")

  prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used, no {filter}"
  ```

  वरील, आम्ही प्रॉम्प्टच्या शेवटी `{filter}` जोडतो आणि आम्ही वापरकर्त्यापासून फिल्टर मूल्य देखील कॅप्चर करतो.

  प्रोग्राम चालवण्याचा एक उदाहरण इनपुट आता असे दिसू शकतो:

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

  तुम्ही पाहू शकता, दूध असलेल्या कोणत्याही रेसिपी फिल्टर केल्या गेल्या
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

  खालील गोष्टी लक्षात घ्या:

  1. आम्ही नवीन प्रॉम्प्ट तयार करत आहोत, ज्यामध्ये पहिल्या प्रॉम्प्टचा परिणाम नवीन प्रॉम्प्टमध्ये जोडत आहोत:

     ```python
     new_prompt = f"{old_prompt_result} {prompt}"
     ```

  1. आम्ही नवीन विनंती करतो, परंतु पहिल्या प्रॉम्प्टमध्ये विचारलेल्या टोकन्सच्या संख्येचा विचार करून, यावेळी आम्ही `max_tokens` 1200 म्हणतो.

     ```python
     completion = openai.Completion.create(engine=deployment_name, prompt=new_prompt, max_tokens=1200)
     ```

     हा कोड वापरून पाहिल्यानंतर, आम्हाला खालील आउटपुट मिळते:

     ```output
     No of recipes (for example, 5): 2
     List of ingredients (for example, chicken, potatoes, and carrots): apple,flour
     Filter (for example, vegetarian, vegan, or gluten-free): sugar


     -Apple and flour pancakes: 1 cup flour, 1/2 tsp baking powder, 1/2 tsp baking soda, 1/4 tsp salt, 1 tbsp sugar, 1 egg, 1 cup buttermilk or sour milk, 1/4 cup melted butter, 1 Granny Smith apple, peeled and grated
     -Apple fritters: 1-1/2 cups flour, 1 tsp baking powder, 1/4 tsp salt, 1/4 tsp baking soda, 1/4 tsp nutmeg, 1/4 tsp cinnamon, 1/4 tsp allspice, 1/4 cup sugar, 1/4 cup vegetable shortening, 1/4 cup milk, 1 egg, 2 cups shredded, peeled apples
     Shopping list:
     -Flour, baking powder, baking soda, salt, sugar, egg, buttermilk, butter, apple, nutmeg, cinnamon, allspice
     ```

## तुमची सेटअप सुधारित करा

आत्तापर्यंत आपल्याकडे कार्यरत कोड आहे, परंतु गोष्टी अधिक चांगल्या प्रकारे सुधारण्यासाठी काही बदल करणे आवश्यक आहे. आपल्याला करावयाच्या काही गोष्टी:

- **गुपिते कोडपासून वेगळी करा**, जसे की API की. गुपिते कोडमध्ये असू नयेत आणि सुरक्षित ठिकाणी संग्रहित केली पाहिजेत. गुपिते कोडपासून वेगळी करण्यासाठी, आपण पर्यावरणीय व्हेरिएबल्स आणि `python-dotenv` सारख्या लायब्ररी वापरू शकता जेणेकरून ती फाइलमधून लोड करता येईल. कोडमध्ये हे कसे दिसेल:

  1. खालील सामग्रीसह `.env` फाइल तयार करा:

     ```bash
     OPENAI_API_KEY=sk-...
     ```

     > लक्षात ठेवा, Azure साठी, आपल्याला खालील पर्यावरणीय व्हेरिएबल्स सेट करणे आवश्यक आहे:

     ```bash
     OPENAI_API_TYPE=azure
     OPENAI_API_VERSION=2023-05-15
     OPENAI_API_BASE=<replace>
     ```

     कोडमध्ये, आपण पर्यावरणीय व्हेरिएबल्स खालीलप्रमाणे लोड करू शकता:

     ```python
     from dotenv import load_dotenv

     load_dotenv()

     openai.api_key = os.environ["OPENAI_API_KEY"]
     ```

- **टोकन लांबीबद्दल एक शब्द**. आपल्याला हवे असलेले मजकूर तयार करण्यासाठी किती टोकन्स आवश्यक आहेत याचा विचार करणे आवश्यक आहे. टोकन्ससाठी पैसे लागतात, त्यामुळे शक्य असल्यास, आपण वापरलेल्या टोकन्सची संख्या कमी करण्याचा प्रयत्न करावा. उदाहरणार्थ, आपण प्रॉम्प्ट कसे मांडू शकतो जेणेकरून कमी टोकन्स वापरता येतील?

  वापरलेले टोकन्स बदलण्यासाठी, आपण `max_tokens` पॅरामीटर वापरू शकता. उदाहरणार्थ, जर आपण 100 टोकन्स वापरू इच्छित असाल, तर आपण असे करू शकता:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, max_tokens=100)
  ```

- **तापमानासह प्रयोग करणे**. तापमान ही एक गोष्ट आहे जी आपण अद्याप उल्लेख केलेली नाही परंतु आपल्या प्रोग्रामच्या कार्यक्षमतेसाठी महत्त्वाची आहे. तापमान मूल्य जितके जास्त असेल तितके आउटपुट अधिक अनियमित असेल. उलट, तापमान मूल्य जितके कमी असेल तितके आउटपुट अधिक अंदाजे असेल. आपल्या आउटपुटमध्ये विविधता हवी आहे की नाही याचा विचार करा.

  तापमान बदलण्यासाठी, आपण `temperature` पॅरामीटर वापरू शकता. उदाहरणार्थ, जर आपण 0.5 तापमान वापरू इच्छित असाल, तर आपण असे करू शकता:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, temperature=0.5)
  ```

  > लक्षात ठेवा, 1.0 च्या जवळ असलेले आउटपुट अधिक विविध असेल.

## असाइनमेंट

या असाइनमेंटसाठी, आपण काय तयार करायचे ते निवडू शकता.

काही सुचवण्या येथे दिल्या आहेत:

- रेसिपी जनरेटर अॅप अधिक सुधारण्यासाठी बदल करा. तापमान मूल्ये आणि प्रॉम्प्ट्ससह प्रयोग करा आणि आपण काय तयार करू शकता ते पहा.
- "स्टडी बडी" तयार करा. हे अॅप एखाद्या विषयाबद्दल प्रश्नांची उत्तरे देऊ शकेल, उदाहरणार्थ Python, आपण असे प्रॉम्प्ट्स ठेवू शकता "Python मधील विशिष्ट विषय काय आहे?", किंवा आपण असे प्रॉम्प्ट ठेवू शकता ज्यामध्ये म्हटले आहे, मला विशिष्ट विषयासाठी कोड दाखवा इत्यादी.
- इतिहास बॉट, इतिहास जिवंत करा, बॉटला एखाद्या ऐतिहासिक पात्राची भूमिका बजावण्याचे निर्देश द्या आणि त्याच्या जीवन आणि काळाबद्दल प्रश्न विचारा.

## समाधान

### स्टडी बडी

खाली एक स्टार्टर प्रॉम्प्ट आहे, पहा आपण ते कसे वापरू शकता आणि आपल्या आवडीनुसार बदलू शकता.

```text
- "You're an expert on the Python language

    Suggest a beginner lesson for Python in the following format:

    Format:
    - concepts:
    - brief explanation of the lesson:
    - exercise in code with solutions"
```

### इतिहास बॉट

येथे काही प्रॉम्प्ट्स आहेत जे आपण वापरू शकता:

```text
- "You are Abe Lincoln, tell me about yourself in 3 sentences, and respond using grammar and words like Abe would have used"
- "You are Abe Lincoln, respond using grammar and words like Abe would have used:

   Tell me about your greatest accomplishments, in 300 words"
```

## ज्ञान तपासणी

तापमान संकल्पना काय करते?

1. ते आउटपुट किती अनियमित आहे हे नियंत्रित करते.
1. ते प्रतिसाद किती मोठा आहे हे नियंत्रित करते.
1. ते किती टोकन्स वापरले जातात हे नियंत्रित करते.

## 🚀 आव्हान

असाइनमेंटवर काम करताना, तापमान बदलण्याचा प्रयत्न करा, ते 0, 0.5, आणि 1 वर सेट करण्याचा प्रयत्न करा. लक्षात ठेवा की 0 हे सर्वात कमी विविध आहे आणि 1 हे सर्वात जास्त आहे. कोणते मूल्य आपल्या अॅपसाठी सर्वात चांगले कार्य करते?

## उत्तम काम! तुमचे शिक्षण सुरू ठेवा

हे धडा पूर्ण केल्यानंतर, आमच्या [Generative AI Learning collection](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst) वर जा आणि आपल्या जनरेटिव्ह AI ज्ञानाचा स्तर वाढवा!

धडा 7 वर जा जिथे आपण [चॅट अॅप्लिकेशन्स तयार करणे](../07-building-chat-applications/README.md?WT.mc_id=academic-105485-koreyst) कसे करायचे ते पाहू!

---

**अस्वीकरण**:  
हा दस्तऐवज AI भाषांतर सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) वापरून भाषांतरित करण्यात आला आहे. आम्ही अचूकतेसाठी प्रयत्नशील असलो तरी, कृपयास लक्षात ठेवा की स्वयंचलित भाषांतरे त्रुटी किंवा अचूकतेच्या अभावासह असू शकतात. मूळ भाषेतील दस्तऐवज हा अधिकृत स्रोत मानला जावा. महत्त्वाच्या माहितीसाठी, व्यावसायिक मानवी भाषांतराची शिफारस केली जाते. या भाषांतराचा वापर करून उद्भवलेल्या कोणत्याही गैरसमज किंवा चुकीच्या अर्थासाठी आम्ही जबाबदार राहणार नाही.