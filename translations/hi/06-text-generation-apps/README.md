<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "df027997f1448323d6159b78a1b669bf",
  "translation_date": "2025-10-18T00:09:19+00:00",
  "source_file": "06-text-generation-apps/README.md",
  "language_code": "hi"
}
-->
# टेक्स्ट जनरेशन एप्लिकेशन बनाना

[![टेक्स्ट जनरेशन एप्लिकेशन बनाना](../../../translated_images/06-lesson-banner.a5c629f990a636c852353c5533f1a6a218ece579005e91f96339d508d9cf8f47.hi.png)](https://youtu.be/0Y5Luf5sRQA?si=t_xVg0clnAI4oUFZ)

> _(ऊपर दी गई छवि पर क्लिक करें इस पाठ का वीडियो देखने के लिए)_

अब तक आपने इस पाठ्यक्रम में देखा है कि प्रॉम्प्ट जैसे मुख्य अवधारणाएं और "प्रॉम्प्ट इंजीनियरिंग" नामक एक पूरी विधा मौजूद है। कई उपकरण जैसे ChatGPT, Office 365, Microsoft Power Platform और अन्य, आपको प्रॉम्प्ट का उपयोग करके कुछ हासिल करने में मदद करते हैं।

यदि आप अपने ऐप में ऐसा अनुभव जोड़ना चाहते हैं, तो आपको प्रॉम्प्ट, कंप्लीशन और एक लाइब्रेरी चुनने जैसी अवधारणाओं को समझना होगा। यही आप इस अध्याय में सीखेंगे।

## परिचय

इस अध्याय में, आप:

- openai लाइब्रेरी और इसकी मुख्य अवधारणाओं के बारे में जानेंगे।
- openai का उपयोग करके एक टेक्स्ट जनरेशन ऐप बनाएंगे।
- प्रॉम्प्ट, टेम्परेचर और टोकन जैसी अवधारणाओं का उपयोग करके टेक्स्ट जनरेशन ऐप बनाना समझेंगे।

## सीखने के लक्ष्य

इस पाठ के अंत में, आप:

- समझा पाएंगे कि टेक्स्ट जनरेशन ऐप क्या है।
- openai का उपयोग करके एक टेक्स्ट जनरेशन ऐप बना पाएंगे।
- अपने ऐप को अधिक या कम टोकन का उपयोग करने और टेम्परेचर बदलने के लिए कॉन्फ़िगर कर पाएंगे, ताकि आउटपुट में विविधता हो।

## टेक्स्ट जनरेशन ऐप क्या है?

आमतौर पर जब आप एक ऐप बनाते हैं, तो उसमें निम्नलिखित प्रकार का इंटरफ़ेस होता है:

- कमांड-आधारित। कंसोल ऐप्स आमतौर पर ऐसे ऐप्स होते हैं जहां आप एक कमांड टाइप करते हैं और यह एक कार्य करता है। उदाहरण के लिए, `git` एक कमांड-आधारित ऐप है।
- यूजर इंटरफेस (UI)। कुछ ऐप्स में ग्राफिकल यूजर इंटरफेस (GUIs) होते हैं जहां आप बटन क्लिक करते हैं, टेक्स्ट इनपुट करते हैं, विकल्प चुनते हैं और अधिक।

### कंसोल और UI ऐप्स की सीमाएं

इसे एक कमांड-आधारित ऐप से तुलना करें जहां आप एक कमांड टाइप करते हैं:

- **यह सीमित है**। आप कोई भी कमांड टाइप नहीं कर सकते, केवल वही जो ऐप समर्थन करता है।
- **भाषा विशिष्ट**। कुछ ऐप्स कई भाषाओं का समर्थन करते हैं, लेकिन डिफ़ॉल्ट रूप से ऐप एक विशिष्ट भाषा के लिए बनाया गया है, भले ही आप अधिक भाषा समर्थन जोड़ सकें।

### टेक्स्ट जनरेशन ऐप्स के लाभ

तो टेक्स्ट जनरेशन ऐप कैसे अलग है?

एक टेक्स्ट जनरेशन ऐप में, आपके पास अधिक लचीलापन होता है, आप केवल एक सेट कमांड या एक विशिष्ट इनपुट भाषा तक सीमित नहीं होते। इसके बजाय, आप ऐप के साथ प्राकृतिक भाषा का उपयोग करके बातचीत कर सकते हैं। एक और लाभ यह है कि आप पहले से ही एक डेटा स्रोत के साथ बातचीत कर रहे हैं जिसे जानकारी के विशाल संग्रह पर प्रशिक्षित किया गया है, जबकि एक पारंपरिक ऐप केवल डेटाबेस में मौजूद जानकारी तक सीमित हो सकता है।

### टेक्स्ट जनरेशन ऐप के साथ क्या बनाया जा सकता है?

आप कई चीजें बना सकते हैं। उदाहरण के लिए:

- **एक चैटबॉट**। एक चैटबॉट जो आपके कंपनी और उसके उत्पादों जैसे विषयों के बारे में सवालों के जवाब देता है।
- **सहायक**। LLMs टेक्स्ट को सारांशित करने, टेक्स्ट से अंतर्दृष्टि प्राप्त करने, रिज्यूमे जैसे टेक्स्ट बनाने और अधिक में उत्कृष्ट हैं।
- **कोड सहायक**। जिस भाषा मॉडल का आप उपयोग करते हैं, उसके आधार पर आप एक कोड सहायक बना सकते हैं जो आपको कोड लिखने में मदद करता है। उदाहरण के लिए, आप GitHub Copilot और ChatGPT जैसे उत्पादों का उपयोग कोड लिखने में मदद के लिए कर सकते हैं।

## मैं कैसे शुरू कर सकता हूं?

खैर, आपको LLM के साथ एकीकृत करने का तरीका खोजना होगा, जो आमतौर पर निम्नलिखित दो दृष्टिकोणों को शामिल करता है:

- API का उपयोग करें। यहां आप अपने प्रॉम्प्ट के साथ वेब अनुरोध बना रहे हैं और वापस जनरेट किया गया टेक्स्ट प्राप्त कर रहे हैं।
- लाइब्रेरी का उपयोग करें। लाइब्रेरी API कॉल्स को संक्षेप में प्रस्तुत करने और उन्हें उपयोग में आसान बनाने में मदद करती हैं।

## लाइब्रेरी/SDKs

LLMs के साथ काम करने के लिए कुछ प्रसिद्ध लाइब्रेरी हैं जैसे:

- **openai**, यह लाइब्रेरी आपके मॉडल से कनेक्ट करना और प्रॉम्प्ट भेजना आसान बनाती है।

फिर कुछ उच्च स्तर पर काम करने वाली लाइब्रेरी हैं जैसे:

- **Langchain**। Langchain बहुत प्रसिद्ध है और Python का समर्थन करता है।
- **Semantic Kernel**। Semantic Kernel Microsoft द्वारा बनाई गई एक लाइब्रेरी है जो C#, Python और Java भाषाओं का समर्थन करती है।

## openai का उपयोग करके पहला ऐप

आइए देखें कि हम अपना पहला ऐप कैसे बना सकते हैं, हमें कौन सी लाइब्रेरी चाहिए, कितना काम करना होगा आदि।

### openai इंस्टॉल करें

OpenAI या Azure OpenAI के साथ इंटरैक्ट करने के लिए कई लाइब्रेरी उपलब्ध हैं। C#, Python, JavaScript, Java और अन्य जैसे कई प्रोग्रामिंग भाषाओं का उपयोग करना संभव है। हमने `openai` Python लाइब्रेरी का उपयोग करने का चयन किया है, इसलिए हम इसे इंस्टॉल करने के लिए `pip` का उपयोग करेंगे।

```bash
pip install openai
```

### एक संसाधन बनाएं

आपको निम्नलिखित चरणों को पूरा करना होगा:

- Azure पर एक खाता बनाएं [https://azure.microsoft.com/free/](https://azure.microsoft.com/free/?WT.mc_id=academic-105485-koreyst)।
- Azure OpenAI तक पहुंच प्राप्त करें। [https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai](https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai?WT.mc_id=academic-105485-koreyst) पर जाएं और पहुंच के लिए आवेदन करें।

  > [!NOTE]
  > लिखने के समय, आपको Azure OpenAI तक पहुंच के लिए आवेदन करना होगा।

- Python इंस्टॉल करें <https://www.python.org/>
- Azure OpenAI Service संसाधन बनाएं। इस गाइड को देखें कि [संसाधन कैसे बनाएं](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal?WT.mc_id=academic-105485-koreyst)।

### API कुंजी और एंडपॉइंट का पता लगाएं

इस बिंदु पर, आपको अपनी `openai` लाइब्रेरी को बताना होगा कि कौन सी API कुंजी का उपयोग करना है। अपनी API कुंजी खोजने के लिए, Azure OpenAI संसाधन के "Keys and Endpoint" अनुभाग में जाएं और "Key 1" मान को कॉपी करें।

![Azure पोर्टल में Keys और Endpoint संसाधन ब्लेड](https://learn.microsoft.com/azure/ai-services/openai/media/quickstarts/endpoint.png?WT.mc_id=academic-105485-koreyst)

अब जब आपने यह जानकारी कॉपी कर ली है, तो आइए लाइब्रेरी को इसका उपयोग करने का निर्देश दें।

> [!NOTE]
> अपनी API कुंजी को अपने कोड से अलग रखना उचित है। आप ऐसा पर्यावरण चर का उपयोग करके कर सकते हैं।
>
> - पर्यावरण चर `OPENAI_API_KEY` को अपनी API कुंजी पर सेट करें।
>   `export OPENAI_API_KEY='sk-...'`

### Azure कॉन्फ़िगरेशन सेटअप करें

यदि आप Azure OpenAI का उपयोग कर रहे हैं, तो यहां बताया गया है कि कॉन्फ़िगरेशन कैसे सेट करें:

```python
openai.api_type = 'azure'
openai.api_key = os.environ["OPENAI_API_KEY"]
openai.api_version = '2023-05-15'
openai.api_base = os.getenv("API_BASE")
```

ऊपर हम निम्नलिखित सेट कर रहे हैं:

- `api_type` को `azure` पर सेट कर रहे हैं। यह लाइब्रेरी को बताता है कि Azure OpenAI का उपयोग करें और OpenAI का नहीं।
- `api_key`, यह आपकी Azure पोर्टल में पाई जाने वाली API कुंजी है।
- `api_version`, यह उस API का संस्करण है जिसे आप उपयोग करना चाहते हैं। लिखने के समय, नवीनतम संस्करण `2023-05-15` है।
- `api_base`, यह API का एंडपॉइंट है। आप इसे Azure पोर्टल में अपनी API कुंजी के बगल में पा सकते हैं।

> [!NOTE] > `os.getenv` एक फ़ंक्शन है जो पर्यावरण चर को पढ़ता है। आप इसका उपयोग `OPENAI_API_KEY` और `API_BASE` जैसे पर्यावरण चर को पढ़ने के लिए कर सकते हैं। इन पर्यावरण चर को अपने टर्मिनल में सेट करें या `dotenv` जैसी लाइब्रेरी का उपयोग करें।

## टेक्स्ट जनरेट करें

टेक्स्ट जनरेट करने का तरीका `Completion` क्लास का उपयोग करना है। यहां एक उदाहरण है:

```python
prompt = "Complete the following: Once upon a time there was a"

completion = openai.Completion.create(model="davinci-002", prompt=prompt)
print(completion.choices[0].text)
```

ऊपर दिए गए कोड में, हम एक कंप्लीशन ऑब्जेक्ट बनाते हैं और उस मॉडल को पास करते हैं जिसे हम उपयोग करना चाहते हैं और प्रॉम्प्ट। फिर हम जनरेट किया गया टेक्स्ट प्रिंट करते हैं।

### चैट कंप्लीशन

अब तक, आपने देखा है कि हम टेक्स्ट जनरेट करने के लिए `Completion` का उपयोग कर रहे हैं। लेकिन एक और क्लास है जिसे `ChatCompletion` कहा जाता है जो चैटबॉट्स के लिए अधिक उपयुक्त है। इसे उपयोग करने का एक उदाहरण यहां दिया गया है:

```python
import openai

openai.api_key = "sk-..."

completion = openai.ChatCompletion.create(model="gpt-3.5-turbo", messages=[{"role": "user", "content": "Hello world"}])
print(completion.choices[0].message.content)
```

इस कार्यक्षमता के बारे में अधिक जानकारी अगले अध्याय में।

## अभ्यास - अपना पहला टेक्स्ट जनरेशन ऐप

अब जब हमने openai को सेटअप और कॉन्फ़िगर करना सीख लिया है, तो अपना पहला टेक्स्ट जनरेशन ऐप बनाने का समय है। अपना ऐप बनाने के लिए, निम्नलिखित चरणों का पालन करें:

1. एक वर्चुअल एनवायरनमेंट बनाएं और openai इंस्टॉल करें:

   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install openai
   ```

   > [!NOTE]
   > यदि आप Windows का उपयोग कर रहे हैं तो `venv\Scripts\activate` टाइप करें, `source venv/bin/activate` के बजाय।

   > [!NOTE]
   > अपनी Azure OpenAI कुंजी का पता लगाने के लिए [https://portal.azure.com/](https://portal.azure.com/?WT.mc_id=academic-105485-koreyst) पर जाएं और `Open AI` खोजें, फिर `Open AI resource` चुनें और फिर `Keys and Endpoint` चुनें और `Key 1` मान को कॉपी करें।

1. एक _app.py_ फ़ाइल बनाएं और उसमें निम्नलिखित कोड डालें:

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
   > यदि आप Azure OpenAI का उपयोग कर रहे हैं, तो आपको `api_type` को `azure` पर सेट करना होगा और `api_key` को अपनी Azure OpenAI कुंजी पर सेट करना होगा।

   आपको निम्नलिखित जैसा आउटपुट दिखाई देगा:

   ```output
    very unhappy _____.

   Once upon a time there was a very unhappy mermaid.
   ```

## विभिन्न प्रकार के प्रॉम्प्ट, विभिन्न कार्यों के लिए

अब आपने देखा कि प्रॉम्प्ट का उपयोग करके टेक्स्ट कैसे जनरेट किया जाता है। आपके पास एक प्रोग्राम भी है जिसे आप संशोधित और बदल सकते हैं ताकि विभिन्न प्रकार के टेक्स्ट जनरेट किए जा सकें।

प्रॉम्प्ट का उपयोग विभिन्न प्रकार के कार्यों के लिए किया जा सकता है। उदाहरण के लिए:

- **एक प्रकार का टेक्स्ट जनरेट करें**। उदाहरण के लिए, आप एक कविता, क्विज़ के लिए प्रश्न आदि जनरेट कर सकते हैं।
- **जानकारी खोजें**। आप प्रॉम्प्ट का उपयोग जानकारी खोजने के लिए कर सकते हैं जैसे 'वेब डेवलपमेंट में CORS का क्या मतलब है?'।
- **कोड जनरेट करें**। आप प्रॉम्प्ट का उपयोग कोड जनरेट करने के लिए कर सकते हैं, उदाहरण के लिए ईमेल को मान्य करने के लिए उपयोग किए जाने वाले एक नियमित अभिव्यक्ति को विकसित करना या क्यों न एक पूरा प्रोग्राम जनरेट करें, जैसे कि एक वेब ऐप?

## एक अधिक व्यावहारिक उपयोग मामला: एक रेसिपी जनरेटर

कल्पना करें कि आपके पास घर पर सामग्री है और आप कुछ पकाना चाहते हैं। इसके लिए, आपको एक रेसिपी की आवश्यकता है। रेसिपी खोजने का एक तरीका सर्च इंजन का उपयोग करना है या आप इसके लिए एक LLM का उपयोग कर सकते हैं।

आप ऐसा प्रॉम्प्ट लिख सकते हैं:

> "मुझे निम्नलिखित सामग्री के साथ एक डिश के लिए 5 रेसिपी दिखाएं: चिकन, आलू और गाजर। प्रत्येक रेसिपी के लिए, उपयोग की गई सभी सामग्री सूचीबद्ध करें।"

ऊपर दिए गए प्रॉम्प्ट के अनुसार, आपको निम्नलिखित जैसा उत्तर मिल सकता है:

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

यह परिणाम शानदार है, मुझे पता है कि क्या पकाना है। इस बिंदु पर, उपयोगी सुधार क्या हो सकते हैं:

- ऐसी सामग्री को फ़िल्टर करना जो मुझे पसंद नहीं है या जिससे मुझे एलर्जी है।
- एक शॉपिंग सूची तैयार करना, यदि मेरे पास घर पर सभी सामग्री नहीं है।

उपरोक्त मामलों के लिए, आइए एक अतिरिक्त प्रॉम्प्ट जोड़ें:

> "कृपया लहसुन वाली रेसिपी को हटा दें क्योंकि मुझे एलर्जी है और इसे किसी और चीज़ से बदलें। साथ ही, कृपया रेसिपी के लिए एक शॉपिंग सूची तैयार करें, यह मानते हुए कि मेरे पास घर पर चिकन, आलू और गाजर हैं।"

अब आपके पास एक नया परिणाम है, अर्थात्:

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

यह आपकी पांच रेसिपी हैं, जिनमें लहसुन का उल्लेख नहीं है और आपके पास घर पर जो सामग्री है उसे ध्यान में रखते हुए एक शॉपिंग सूची भी है।

## अभ्यास - एक रेसिपी जनरेटर बनाएं

अब जब हमने एक परिदृश्य को खेला है, तो आइए प्रदर्शित परिदृश्य से मेल खाने के लिए कोड लिखें। ऐसा करने के लिए, निम्नलिखित चरणों का पालन करें:

1. मौजूदा _app.py_ फ़ाइल का उपयोग प्रारंभिक बिंदु के रूप में करें।
1. `prompt` वेरिएबल का पता लगाएं और उसके कोड को निम्नलिखित में बदलें:

   ```python
   prompt = "Show me 5 recipes for a dish with the following ingredients: chicken, potatoes, and carrots. Per recipe, list all the ingredients used"
   ```

   यदि आप अब कोड चलाते हैं, तो आपको निम्नलिखित जैसा आउटपुट दिखाई देना चाहिए:

   ```output
   -Chicken Stew with Potatoes and Carrots: 3 tablespoons oil, 1 onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 1/2 cups chicken broth, 1/2 cup dry white wine, 2 tablespoons chopped fresh parsley, 2 tablespoons unsalted butter, 1 1/2 pounds boneless, skinless chicken thighs, cut into 1-inch pieces
   -Oven-Roasted Chicken with Potatoes and Carrots: 3 tablespoons extra-virgin olive oil, 1 tablespoon Dijon mustard, 1 tablespoon chopped fresh rosemary, 1 tablespoon chopped fresh thyme, 4 cloves garlic, minced, 1 1/2 pounds small red potatoes, quartered, 1 1/2 pounds carrots, quartered lengthwise, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 (4-pound) whole chicken
   -Chicken, Potato, and Carrot Casserole: cooking spray, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and shredded, 1 potato, peeled and shredded, 1/2 teaspoon dried thyme leaves, 1/4 teaspoon salt, 1/4 teaspoon black pepper, 2 cups fat-free, low-sodium chicken broth, 1 cup frozen peas, 1/4 cup all-purpose flour, 1 cup 2% reduced-fat milk, 1/4 cup grated Parmesan cheese

   -One Pot Chicken and Potato Dinner: 2 tablespoons olive oil, 1 pound boneless, skinless chicken thighs, cut into 1-inch pieces, 1 large onion, chopped, 3 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 2 cups chicken broth, 1/2 cup dry white wine

   -Chicken, Potato, and Carrot Curry: 1 tablespoon vegetable oil, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 teaspoon ground coriander, 1 teaspoon ground cumin, 1/2 teaspoon ground turmeric, 1/2 teaspoon ground ginger, 1/4 teaspoon cayenne pepper, 2 cups chicken broth, 1/2 cup dry white wine, 1 (15-ounce) can chickpeas, drained and rinsed, 1/2 cup raisins, 1/2 cup chopped fresh cilantro
   ```

   > नोट, आपका LLM गैर-निर्धारित है, इसलिए हो सकता है कि हर बार जब आप प्रोग्राम चलाएं तो आपको अलग-अलग परिणाम मिलें।

   शानदार, आइए देखें कि हम चीजों को कैसे सुधार सकते हैं। चीजों को सुधारने के लिए, हम यह सुनिश्चित करना चाहते हैं कि कोड लचीला हो, ताकि सामग्री और रेसिपी की संख्या को बेहतर और बदला जा सके।

1. आइए कोड को निम्नलिखित तरीके से बदलें:

   ```python
   no_recipes = input("No of recipes (for example, 5): ")

   ingredients = input("List of ingredients (for example, chicken, potatoes, and carrots): ")

   # interpolate the number of recipes into the prompt an ingredients
   prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used"
   ```

   कोड का परीक्षण करने पर, यह कुछ इस तरह दिख सकता है:

   ```output
   No of recipes (for example, 5): 3
   List of ingredients (for example, chicken, potatoes, and carrots): milk,strawberries

   -Strawberry milk shake: milk, strawberries, sugar, vanilla extract, ice cubes
   -Strawberry shortcake: milk, flour, baking powder, sugar, salt, unsalted butter, strawberries, whipped cream
   -Strawberry milk: milk, strawberries, sugar, vanilla extract
   ```

### फ़िल्टर और शॉपिंग सूची जोड़कर सुधार करें

अब हमारे पास एक काम करने वाला ऐप है जो रेसिपी जनरेट करने में सक्षम है और यह लचीला है क्योंकि यह उपयोगकर्ता से इनपुट पर निर्भर करता है, रेसिपी की संख्या और उपयोग की गई सामग्री दोनों पर।

इसे और बेहतर बनाने के लिए, हम निम्नलिखित जोड़ना चाहते हैं:

- **सामग्री को फ़िल्टर करें**। हम उन सामग्रियों को फ़िल्टर करना चाहते हैं जो हमें पसंद नहीं हैं या जिनसे हमें एलर्जी है। इस बदलाव को पूरा करने के लिए, हम अपने मौजूदा प्रॉम्प्ट को संपादित कर सकते हैं और इसके अंत में एक फ़िल्टर शर्त जोड़ सकते हैं, जैसे:

  ```python
  filter = input("Filter (for example, vegetarian, vegan, or gluten-free): ")

  prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used, no {filter}"
  ```

  ऊपर, हमने प्रॉम्प्ट के अंत में `{filter}` जोड़ा है और हम उपयोगकर्ता से फ़िल्टर मान भी प्राप्त कर रहे हैं।

  प्रोग्राम चलाने का एक उदाहरण इनपुट अब कुछ इस तरह दिख सकता है:

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

  जैसा कि आप देख सकते हैं, दूध वाली कोई भी रेसिपी फ़िल्टर कर दी गई है। लेकिन, यदि आपको लैक्टोज से एलर्जी है, तो आप उन रेसिपी को भी फ़िल्टर करना चाह सकते हैं जिनमें चीज़ है, इसलिए स्पष्ट होना आवश्यक है।

- **एक शॉपिंग सूची तैयार करें**। हम एक शॉपिंग सूची तैयार करना चाहते हैं, यह मानते हुए कि हमारे पास घर पर क्या है।

  इस कार्यक्षमता के लिए, हम या तो सब कुछ एक प्रॉम्प्ट में हल करने की कोशिश कर सकते हैं या इसे दो प्रॉम्प्ट में विभाजित कर सकते हैं। आइए बाद वाले दृष्टिकोण को आजमाएं। यहां हम एक अतिरिक्त प्रॉम्प्ट जोड़ने का सुझाव दे रहे हैं, लेकिन इसके काम करने के लिए, हमें पहले प्रॉम्प्ट के परिणाम को दूसरे प्रॉम्प्ट के संदर्भ के रूप में जोड़ना होगा।

  कोड के उस भाग का पता लगाएं जो पहले प्रॉम्प्ट के परिणाम को प्रिंट करता है और उसके नीचे निम्नलिखित कोड जोड़ें:
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

  निम्नलिखित पर ध्यान दें:

  1. हम एक नया प्रॉम्प्ट बना रहे हैं, जिसमें पहले प्रॉम्प्ट के परिणाम को नए प्रॉम्प्ट में जोड़ रहे हैं:

     ```python
     new_prompt = f"{old_prompt_result} {prompt}"
     ```

  1. हम एक नया अनुरोध करते हैं, लेकिन पहले प्रॉम्प्ट में पूछे गए टोकन की संख्या को ध्यान में रखते हुए, इस बार हम `max_tokens` को 1200 कहते हैं।

     ```python
     completion = openai.Completion.create(engine=deployment_name, prompt=new_prompt, max_tokens=1200)
     ```

     इस कोड को चलाने पर, हम निम्नलिखित आउटपुट पर पहुंचते हैं:

     ```output
     No of recipes (for example, 5): 2
     List of ingredients (for example, chicken, potatoes, and carrots): apple,flour
     Filter (for example, vegetarian, vegan, or gluten-free): sugar


     -Apple and flour pancakes: 1 cup flour, 1/2 tsp baking powder, 1/2 tsp baking soda, 1/4 tsp salt, 1 tbsp sugar, 1 egg, 1 cup buttermilk or sour milk, 1/4 cup melted butter, 1 Granny Smith apple, peeled and grated
     -Apple fritters: 1-1/2 cups flour, 1 tsp baking powder, 1/4 tsp salt, 1/4 tsp baking soda, 1/4 tsp nutmeg, 1/4 tsp cinnamon, 1/4 tsp allspice, 1/4 cup sugar, 1/4 cup vegetable shortening, 1/4 cup milk, 1 egg, 2 cups shredded, peeled apples
     Shopping list:
     -Flour, baking powder, baking soda, salt, sugar, egg, buttermilk, butter, apple, nutmeg, cinnamon, allspice
     ```

## अपनी सेटअप को बेहतर बनाएं

अब तक हमारे पास ऐसा कोड है जो काम करता है, लेकिन कुछ सुधार हैं जो हमें चीजों को और बेहतर बनाने के लिए करने चाहिए। कुछ चीजें जो हमें करनी चाहिए:

- **कोड से सीक्रेट्स को अलग करें**, जैसे API कुंजी। सीक्रेट्स को कोड में नहीं होना चाहिए और उन्हें सुरक्षित स्थान पर संग्रहीत किया जाना चाहिए। सीक्रेट्स को कोड से अलग करने के लिए, हम पर्यावरणीय वेरिएबल्स और `python-dotenv` जैसी लाइब्रेरी का उपयोग कर सकते हैं ताकि उन्हें एक फाइल से लोड किया जा सके। कोड में यह इस प्रकार दिखेगा:

  1. एक `.env` फाइल बनाएं जिसमें निम्नलिखित सामग्री हो:

     ```bash
     OPENAI_API_KEY=sk-...
     ```

     > ध्यान दें, Azure के लिए, आपको निम्नलिखित पर्यावरणीय वेरिएबल्स सेट करने की आवश्यकता है:

     ```bash
     OPENAI_API_TYPE=azure
     OPENAI_API_VERSION=2023-05-15
     OPENAI_API_BASE=<replace>
     ```

     कोड में, आप पर्यावरणीय वेरिएबल्स को इस प्रकार लोड करेंगे:

     ```python
     from dotenv import load_dotenv

     load_dotenv()

     openai.api_key = os.environ["OPENAI_API_KEY"]
     ```

- **टोकन लंबाई पर एक विचार**। हमें यह विचार करना चाहिए कि हमें उस टेक्स्ट को उत्पन्न करने के लिए कितने टोकन की आवश्यकता है जिसे हम चाहते हैं। टोकन पैसे खर्च करते हैं, इसलिए जहां संभव हो, हमें उपयोग किए गए टोकन की संख्या के साथ आर्थिक रूप से व्यवहार करना चाहिए। उदाहरण के लिए, क्या हम प्रॉम्प्ट को इस प्रकार लिख सकते हैं कि हम कम टोकन का उपयोग कर सकें?

  उपयोग किए गए टोकन को बदलने के लिए, आप `max_tokens` पैरामीटर का उपयोग कर सकते हैं। उदाहरण के लिए, यदि आप 100 टोकन का उपयोग करना चाहते हैं, तो आप ऐसा करेंगे:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, max_tokens=100)
  ```

- **टेम्परेचर के साथ प्रयोग करना**। टेम्परेचर एक ऐसा पैरामीटर है जिसे हमने अब तक उल्लेख नहीं किया है, लेकिन यह हमारे प्रोग्राम के प्रदर्शन के लिए एक महत्वपूर्ण संदर्भ है। टेम्परेचर का मान जितना अधिक होगा, आउटपुट उतना ही अधिक रैंडम होगा। इसके विपरीत, टेम्परेचर का मान जितना कम होगा, आउटपुट उतना ही अधिक अनुमानित होगा। विचार करें कि आप अपने आउटपुट में विविधता चाहते हैं या नहीं।

  टेम्परेचर को बदलने के लिए, आप `temperature` पैरामीटर का उपयोग कर सकते हैं। उदाहरण के लिए, यदि आप 0.5 का टेम्परेचर उपयोग करना चाहते हैं, तो आप ऐसा करेंगे:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, temperature=0.5)
  ```

  > ध्यान दें, 1.0 के करीब होने पर आउटपुट अधिक विविध होगा।

## असाइनमेंट

इस असाइनमेंट के लिए, आप क्या बनाना चाहते हैं, यह चुन सकते हैं।

यहां कुछ सुझाव दिए गए हैं:

- रेसिपी जनरेटर ऐप को और बेहतर बनाने के लिए उसमें बदलाव करें। टेम्परेचर मान और प्रॉम्प्ट्स के साथ प्रयोग करें और देखें कि आप क्या बना सकते हैं।
- एक "स्टडी बडी" बनाएं। यह ऐप किसी विषय के बारे में सवालों के जवाब देने में सक्षम होना चाहिए, उदाहरण के लिए, Python। आप ऐसे प्रॉम्प्ट्स का उपयोग कर सकते हैं जैसे "Python में एक निश्चित विषय क्या है?", या आप ऐसा प्रॉम्प्ट दे सकते हैं जो कहे, मुझे किसी निश्चित विषय के लिए कोड दिखाएं आदि।
- इतिहास बॉट, इतिहास को जीवंत बनाएं, बॉट को एक निश्चित ऐतिहासिक चरित्र की भूमिका निभाने का निर्देश दें और उसके जीवन और समय के बारे में सवाल पूछें।

## समाधान

### स्टडी बडी

नीचे एक प्रारंभिक प्रॉम्प्ट दिया गया है, देखें कि आप इसे कैसे उपयोग कर सकते हैं और अपनी पसंद के अनुसार इसे बदल सकते हैं।

```text
- "You're an expert on the Python language

    Suggest a beginner lesson for Python in the following format:

    Format:
    - concepts:
    - brief explanation of the lesson:
    - exercise in code with solutions"
```

### इतिहास बॉट

यहां कुछ प्रॉम्प्ट्स दिए गए हैं जिन्हें आप उपयोग कर सकते हैं:

```text
- "You are Abe Lincoln, tell me about yourself in 3 sentences, and respond using grammar and words like Abe would have used"
- "You are Abe Lincoln, respond using grammar and words like Abe would have used:

   Tell me about your greatest accomplishments, in 300 words"
```

## ज्ञान जांच

टेम्परेचर की अवधारणा क्या करती है?

1. यह नियंत्रित करता है कि आउटपुट कितना रैंडम है।
1. यह नियंत्रित करता है कि प्रतिक्रिया कितनी बड़ी है।
1. यह नियंत्रित करता है कि कितने टोकन उपयोग किए गए हैं।

## 🚀 चुनौती

असाइनमेंट पर काम करते समय, टेम्परेचर को बदलने का प्रयास करें, इसे 0, 0.5, और 1 पर सेट करने का प्रयास करें। याद रखें कि 0 सबसे कम विविध है और 1 सबसे अधिक है। कौन सा मान आपके ऐप के लिए सबसे अच्छा काम करता है?

## शानदार काम! अपनी सीख जारी रखें

इस पाठ को पूरा करने के बाद, हमारे [Generative AI Learning collection](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst) को देखें ताकि आप अपनी जनरेटिव AI ज्ञान को और बढ़ा सकें!

पाठ 7 पर जाएं जहां हम देखेंगे कि [चैट एप्लिकेशन कैसे बनाएं](../07-building-chat-applications/README.md?WT.mc_id=academic-105485-koreyst)!

---

**अस्वीकरण**:  
यह दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) का उपयोग करके अनुवादित किया गया है। जबकि हम सटीकता के लिए प्रयास करते हैं, कृपया ध्यान दें कि स्वचालित अनुवाद में त्रुटियां या अशुद्धियां हो सकती हैं। मूल भाषा में दस्तावेज़ को आधिकारिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए, पेशेवर मानव अनुवाद की सिफारिश की जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम उत्तरदायी नहीं हैं।