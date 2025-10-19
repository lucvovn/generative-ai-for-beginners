<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "49ededa179004ea998664c780fbeac39",
  "translation_date": "2025-10-11T11:42:02+00:00",
  "source_file": "00-course-setup/03-providers.md",
  "language_code": "ta"
}
-->
# LLM வழங்குநரை தேர்வு & அமைத்தல் 🔑

**பணி**கள் ஒரு அல்லது அதற்கு மேற்பட்ட பெரிய மொழி மாதிரி (LLM) சேவைகளை OpenAI, Azure அல்லது Hugging Face போன்ற ஆதரிக்கப்பட்ட சேவை வழங்குநர்களின் மூலம் அமைக்கப்படலாம். இவை _hosted endpoint_ (API) வழங்குகின்றன, இதை சரியான அனுமதி சான்றுகள் (API key அல்லது token) மூலம் நிரலாக்கமாக அணுகலாம். இந்த பாடத்தில், இந்த வழங்குநர்களைப் பற்றி விவாதிக்கிறோம்:

 - [OpenAI](https://platform.openai.com/docs/models?WT.mc_id=academic-105485-koreyst) பல்வேறு மாதிரிகளுடன், முக்கிய GPT தொடர் உட்பட.
 - [Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/?WT.mc_id=academic-105485-koreyst) OpenAI மாதிரிகளுக்கான தொழில்துறை தயார்நிலை மையமாக.
 - [Hugging Face](https://huggingface.co/docs/hub/index?WT.mc_id=academic-105485-koreyst) திறந்த மூல மாதிரிகள் மற்றும் inference server க்காக.

**இந்த பயிற்சிகளுக்கான உங்கள் சொந்த கணக்குகளை நீங்கள் பயன்படுத்த வேண்டும்**. பணி விருப்பமானது, எனவே உங்கள் ஆர்வத்தின் அடிப்படையில் ஒரு, அனைத்தும் - அல்லது எதுவும் இல்லாமல் வழங்குநர்களை அமைக்க முடியும். பதிவு செய்ய சில வழிகாட்டுதல்கள்:

| பதிவு | செலவு | API Key | Playground | கருத்துக்கள் |
|:---|:---|:---|:---|:---|
| [OpenAI](https://platform.openai.com/signup?WT.mc_id=academic-105485-koreyst)| [விலை](https://openai.com/pricing#language-models?WT.mc_id=academic-105485-koreyst)| [Project-based](https://platform.openai.com/api-keys?WT.mc_id=academic-105485-koreyst) | [No-Code, Web](https://platform.openai.com/playground?WT.mc_id=academic-105485-koreyst) | பல மாதிரிகள் கிடைக்கின்றன |
| [Azure](https://aka.ms/azure/free?WT.mc_id=academic-105485-koreyst)| [விலை](https://azure.microsoft.com/pricing/details/cognitive-services/openai-service/?WT.mc_id=academic-105485-koreyst)| [SDK Quickstart](https://learn.microsoft.com/azure/ai-services/openai/quickstart?WT.mc_id=academic-105485-koreyst)| [Studio Quickstart](https://learn.microsoft.com/azure/ai-services/openai/quickstart?WT.mc_id=academic-105485-koreyst) |  [அனுமதி பெற முன்பே விண்ணப்பிக்க வேண்டும்](https://learn.microsoft.com/azure/ai-services/openai/?WT.mc_id=academic-105485-koreyst)|
| [Hugging Face](https://huggingface.co/join?WT.mc_id=academic-105485-koreyst) | [விலை](https://huggingface.co/pricing) | [Access Tokens](https://huggingface.co/docs/hub/security-tokens?WT.mc_id=academic-105485-koreyst) | [Hugging Chat](https://huggingface.co/chat/?WT.mc_id=academic-105485-koreyst)| [Hugging Chat க்கு வரையறுக்கப்பட்ட மாதிரிகள் உள்ளன](https://huggingface.co/chat/models?WT.mc_id=academic-105485-koreyst) |
| | | | | |

கீழே உள்ள வழிகாட்டுதல்களை பின்பற்றி இந்த repository ஐ பல்வேறு வழங்குநர்களுடன் பயன்படுத்த _configure_ செய்யுங்கள். குறிப்பிட்ட வழங்குநரை தேவைப்படும் பணிகள், filename இல் கீழ்க்காணும் குறிச்சொற்களை கொண்டிருக்கும்:

- `aoai` - Azure OpenAI endpoint, key தேவை
- `oai` - OpenAI endpoint, key தேவை
- `hf` - Hugging Face token தேவை

நீங்கள் ஒரு, எதுவும் இல்லாமல், அல்லது அனைத்து வழங்குநர்களையும் அமைக்க முடியும். தொடர்புடைய பணிகள் credentials இல்லாமல் simply error ஆகும்.

## `.env` கோப்பை உருவாக்கவும்

மேலே உள்ள வழிகாட்டுதலை நீங்கள் ஏற்கனவே படித்துவிட்டு, தொடர்புடைய வழங்குநருடன் பதிவு செய்து, தேவையான authentication credentials (API_KEY அல்லது token) பெற்றிருக்கிறீர்கள் என்று நாங்கள் கருதுகிறோம். Azure OpenAI க்கான விஷயத்தில், நீங்கள் Azure OpenAI சேவையின் (endpoint) ஒரு செல்லுபடியாகும் deployment ஐ GPT மாதிரியை chat completion க்காக deploy செய்திருக்க வேண்டும்.

அடுத்த படியாக, உங்கள் **local environment variables** ஐ பின்வருமாறு configure செய்ய வேண்டும்:

1. `.env.copy` என்ற கோப்பை root folder இல் தேடுங்கள், இது கீழ்க்காணும் உள்ளடக்கங்களை கொண்டிருக்கும்:

   ```bash
   # OpenAI Provider
   OPENAI_API_KEY='<add your OpenAI API key here>'

   ## Azure OpenAI
   AZURE_OPENAI_API_VERSION='2024-02-01' # Default is set!
   AZURE_OPENAI_API_KEY='<add your AOAI key here>'
   AZURE_OPENAI_ENDPOINT='<add your AOIA service endpoint here>'
   AZURE_OPENAI_DEPLOYMENT='<add your chat completion model name here>' 
   AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT='<add your embeddings model name here>'

   ## Hugging Face
   HUGGING_FACE_API_KEY='<add your HuggingFace API or token here>'
   ```

2. கீழே உள்ள கட்டளையை பயன்படுத்தி `.env` க்கு அந்த கோப்பை copy செய்யுங்கள். இந்த கோப்பு _gitignore-d_ ஆகும், இதனால் ரகசியங்கள் பாதுகாக்கப்படும்.

   ```bash
   cp .env.copy .env
   ```

3. கீழே உள்ள பகுதியில் விளக்கப்பட்ட placeholders ஐ மாற்றி மதிப்புகளை நிரப்புங்கள்.

4. (விருப்பம்) நீங்கள் GitHub Codespaces ஐ பயன்படுத்தினால், இந்த repository உடன் தொடர்புடைய _Codespaces secrets_ ஆக environment variables ஐ சேமிக்க விருப்பம் உங்களுக்கு உள்ளது. இந்த வழியில் `.env` கோப்பை அமைக்க தேவையில்லை. **ஆனால், இந்த விருப்பம் GitHub Codespaces ஐ பயன்படுத்தினால் மட்டுமே செயல்படும்.** Docker Desktop ஐ பயன்படுத்தினால் `.env` கோப்பை அமைக்கவேண்டும்.

## `.env` கோப்பை நிரப்பவும்

Variable பெயர்கள் என்னை பிரதிபலிக்கின்றன என்பதை விரைவாக பார்ப்போம்:

| Variable  | விளக்கம்  |
| :--- | :--- |
| HUGGING_FACE_API_KEY | உங்கள் profile இல் அமைக்கப்பட்ட user access token |
| OPENAI_API_KEY | non-Azure OpenAI endpoints க்கான authorization key |
| AZURE_OPENAI_API_KEY | அந்த சேவையை பயன்படுத்த authorization key |
| AZURE_OPENAI_ENDPOINT | Azure OpenAI resource க்கான deployed endpoint |
| AZURE_OPENAI_DEPLOYMENT | இது _text generation_ மாதிரி deployment endpoint |
| AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT | இது _text embeddings_ மாதிரி deployment endpoint |
| | |

குறிப்பு: கடைசி இரண்டு Azure OpenAI variables chat completion (text generation) மற்றும் vector search (embeddings) க்கான default மாதிரியை பிரதிபலிக்கின்றன. அவற்றை அமைக்க வழிகாட்டுதல்கள் தொடர்புடைய பணிகளில் வரையறுக்கப்படும்.

## Azure ஐ அமைக்க: Portal மூலம்

Azure OpenAI endpoint மற்றும் key மதிப்புகள் [Azure Portal](https://portal.azure.com?WT.mc_id=academic-105485-koreyst) இல் கிடைக்கும், எனவே அங்கு தொடங்குவோம்.

1. [Azure Portal](https://portal.azure.com?WT.mc_id=academic-105485-koreyst) க்கு செல்லவும்
1. Sidebar (இடது மெனு) இல் **Keys and Endpoint** விருப்பத்தை கிளிக் செய்யவும்.
1. **Show Keys** ஐ கிளிக் செய்யவும் - KEY 1, KEY 2 மற்றும் Endpoint ஆகியவற்றை நீங்கள் காணலாம்.
1. KEY 1 மதிப்பை AZURE_OPENAI_API_KEY க்காக பயன்படுத்தவும்.
1. Endpoint மதிப்பை AZURE_OPENAI_ENDPOINT க்காக பயன்படுத்தவும்.

அடுத்ததாக, deploy செய்துள்ள மாதிரிகளுக்கான endpoints தேவை.

1. Azure OpenAI resource க்கான Sidebar (இடது மெனு) இல் **Model deployments** விருப்பத்தை கிளிக் செய்யவும்.
1. Destination பக்கத்தில் **Manage Deployments** ஐ கிளிக் செய்யவும்.

இது Azure OpenAI Studio வலைத்தளத்திற்கு உங்களை அழைத்துச் செல்லும், அங்கு கீழே விவரிக்கப்பட்டுள்ள மற்ற மதிப்புகளை காணலாம்.

## Azure ஐ அமைக்க: Studio மூலம்

1. [Azure OpenAI Studio](https://oai.azure.com?WT.mc_id=academic-105485-koreyst) க்கு **உங்கள் resource** மூலம் மேலே விவரிக்கப்பட்டபடி செல்லவும்.
1. Sidebar (இடது மெனு) இல் **Deployments** tab ஐ கிளிக் செய்து deploy செய்யப்பட்ட மாதிரிகளை பார்வையிடவும்.
1. உங்கள் விருப்பமான மாதிரி deploy செய்யப்படவில்லை என்றால், **Create new deployment** ஐ பயன்படுத்தி deploy செய்யவும்.
1. உங்களுக்கு _text-generation_ மாதிரி தேவை - **gpt-35-turbo** ஐ பரிந்துரைக்கிறோம்.
1. உங்களுக்கு _text-embedding_ மாதிரி தேவை - **text-embedding-ada-002** ஐ பரிந்துரைக்கிறோம்.

இப்போது environment variables ஐ _Deployment name_ ஐ பிரதிபலிக்க update செய்யுங்கள். இது பொதுவாக மாதிரி பெயருடன் ஒரே மாதிரியானதாக இருக்கும், நீங்கள் அதை explicitly மாற்றவில்லை என்றால். எனவே, உதாரணமாக, நீங்கள் இதைப் பெறலாம்:

```bash
AZURE_OPENAI_DEPLOYMENT='gpt-35-turbo'
AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT='text-embedding-ada-002'
```

**.env கோப்பை save செய்ய மறக்காதீர்கள்**. கோப்பை exit செய்து notebook ஐ இயக்குவதற்கான வழிகாட்டுதலுக்கு திரும்பலாம்.

## OpenAI ஐ அமைக்க: Profile மூலம்

உங்கள் OpenAI API key ஐ [OpenAI account](https://platform.openai.com/api-keys?WT.mc_id=academic-105485-koreyst) இல் காணலாம். உங்களுக்கு API key இல்லையெனில், ஒரு கணக்கை பதிவு செய்து API key ஐ உருவாக்கலாம். Key ஐ பெற்றவுடன், `.env` கோப்பில் `OPENAI_API_KEY` variable ஐ நிரப்ப பயன்படுத்தலாம்.

## Hugging Face ஐ அமைக்க: Profile மூலம்

உங்கள் Hugging Face token ஐ [Access Tokens](https://huggingface.co/settings/tokens?WT.mc_id=academic-105485-koreyst) இல் உங்கள் profile இல் காணலாம். இதை பொதுவாக பகிர வேண்டாம் அல்லது வெளியிட வேண்டாம். இந்த project பயன்பாட்டிற்காக புதிய token ஐ உருவாக்கி, `.env` கோப்பில் `HUGGING_FACE_API_KEY` variable கீழ் copy செய்யவும். _குறிப்பு:_ இது தொழில்நுட்ப ரீதியாக API key அல்ல, ஆனால் authentication க்காக பயன்படுத்தப்படுகிறது, எனவே consistency க்காக அந்த பெயரிடல் வழக்கத்தை வைத்திருக்கிறோம்.

---

**குறிப்பு**:  
இந்த ஆவணம் AI மொழிபெயர்ப்பு சேவை [Co-op Translator](https://github.com/Azure/co-op-translator) பயன்படுத்தி மொழிபெயர்க்கப்பட்டுள்ளது. எங்கள் துல்லியத்திற்கான முயற்சிகள் இருந்தாலும், தானியங்கி மொழிபெயர்ப்புகளில் பிழைகள் அல்லது தவறுகள் இருக்கக்கூடும் என்பதை கவனத்தில் கொள்ளவும். அதன் தாய்மொழியில் உள்ள மூல ஆவணம் அதிகாரப்பூர்வ ஆதாரமாக கருதப்பட வேண்டும். முக்கியமான தகவல்களுக்கு, தொழில்முறை மனித மொழிபெயர்ப்பு பரிந்துரைக்கப்படுகிறது. இந்த மொழிபெயர்ப்பைப் பயன்படுத்துவதால் ஏற்படும் எந்த தவறான புரிதல்கள் அல்லது தவறான விளக்கங்களுக்கு நாங்கள் பொறுப்பல்ல.