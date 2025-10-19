<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-18T02:38:45+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "ta"
}
-->
# இந்த பாடத்தை தொடங்குவது

இந்த பாடத்தை நீங்கள் தொடங்குவதற்கு நாங்கள் மிகவும் உற்சாகமாக உள்ளோம், மேலும் Generative AI உடன் நீங்கள் உருவாக்குவதற்கு என்ன உந்துதல் பெறுகிறீர்கள் என்பதை பார்க்க விரும்புகிறோம்!

உங்கள் வெற்றியை உறுதிப்படுத்த, இந்த பக்கம் அமைப்பு நடவடிக்கைகள், தொழில்நுட்ப தேவைகள் மற்றும் உதவி தேவைப்பட்டால் எங்கு பெறுவது என்பதை விளக்குகிறது.

## அமைப்பு நடவடிக்கைகள்

இந்த பாடத்தை தொடங்க, நீங்கள் பின்வரும் நடவடிக்கைகளை முடிக்க வேண்டும்.

### 1. இந்த Repo ஐ Fork செய்யுங்கள்

[இந்த Repo ஐ முழுமையாக Fork செய்யுங்கள்](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) உங்கள் சொந்த GitHub கணக்கில், இதனால் நீங்கள் எந்தவொரு குறியீட்டையும் மாற்றி சவால்களை முடிக்க முடியும். மேலும் [இந்த Repo ஐ Star (🌟)](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) செய்து அதை மற்றும் தொடர்புடைய Repo களை எளிதாக கண்டுபிடிக்கலாம்.

### 2. Codespace உருவாக்குங்கள்

குறியீட்டை இயக்கும்போது எந்தவொரு சார்பு பிரச்சினைகளையும் தவிர்க்க, இந்த பாடத்தை [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst) இல் இயக்க பரிந்துரைக்கிறோம்.

உங்கள் Fork இல்: **Code -> Codespaces -> New on main**

![Codespace உருவாக்குவதற்கான பொத்தான்கள் காட்டும் உரையாடல்](../../../00-course-setup/images/who-will-pay.webp)

#### 2.1 ஒரு ரகசியத்தை சேர்க்கவும்

1. ⚙️ Gear ஐகான் -> Command Pallete-> Codespaces : Manage user secret -> Add a new secret.
2. பெயர் OPENAI_API_KEY, உங்கள் கீயை ஒட்டவும், சேமிக்கவும்.

### 3. அடுத்தது என்ன?

| நான் செய்ய விரும்புகிறேன்... | செல்ல வேண்டிய இடம்... |
|-----------------------------|-----------------------|
| பாடம் 1 ஐ தொடங்குங்கள்      | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md) |
| ஆஃப்லைனில் வேலை செய்யுங்கள் | [`setup-local.md`](02-setup-local.md) |
| ஒரு LLM வழங்குநரை அமைக்கவும் | [`providers.md`](03-providers.md) |
| மற்ற கற்றவர்களை சந்திக்கவும் | [எங்கள் Discord ஐ சேரவும்](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) |

## பிரச்சினைகளை சரிசெய்தல்

| அறிகுறி                                   | தீர்வு |
|-------------------------------------------|-------|
| Container build 10 நிமிடங்களுக்கு மேல் சிக்கியது | **Codespaces ➜ “Rebuild Container”** |
| `python: command not found`               | Terminal இணைக்கப்படவில்லை; **+** ➜ *bash* ஐ கிளிக் செய்யவும் |
| OpenAI இல் இருந்து `401 Unauthorized`     | தவறான / காலாவதியான `OPENAI_API_KEY` |
| VS Code “Dev container mounting…” காட்டுகிறது | உலாவி தாவலைப் புதுப்பிக்கவும்—Codespaces சில நேரங்களில் இணைப்பை இழக்கிறது |
| Notebook kernel காணவில்லை               | Notebook menu ➜ **Kernel ▸ Select Kernel ▸ Python 3** |

   Unix அடிப்படையிலான அமைப்புகள்:

   ```bash
   touch .env
   ```

   Windows:

   ```cmd
   echo . > .env
   ```

3. **`.env` கோப்பை திருத்தவும்**: `.env` கோப்பை ஒரு உரை திருத்தியில் திறக்கவும் (எ.கா., VS Code, Notepad++ அல்லது வேறு எந்த திருத்தியும்). உங்கள் GitHub டோக்கனை மாற்றி, கீழே உள்ள வரியை கோப்பில் சேர்க்கவும்:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```

4. **கோப்பை சேமிக்கவும்**: மாற்றங்களைச் சேமித்து, உரை திருத்தியை மூடவும்.

5. **`python-dotenv` ஐ நிறுவவும்**: நீங்கள் இதுவரை நிறுவவில்லை என்றால், `.env` கோப்பிலிருந்து உங்கள் Python பயன்பாட்டில் சூழல் மாறிகளை ஏற்ற `python-dotenv` தொகுப்பை நிறுவ வேண்டும். நீங்கள் `pip` ஐப் பயன்படுத்தி அதை நிறுவலாம்:

   ```bash
   pip install python-dotenv
   ```

6. **உங்கள் Python ஸ்கிரிப்டில் சூழல் மாறிகளை ஏற்றவும்**: உங்கள் Python ஸ்கிரிப்டில், `.env` கோப்பிலிருந்து சூழல் மாறிகளை ஏற்ற `python-dotenv` தொகுப்பைப் பயன்படுத்தவும்:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```

அதுவே! நீங்கள் வெற்றிகரமாக `.env` கோப்பை உருவாக்கி, உங்கள் GitHub டோக்கனைச் சேர்த்து, அதை உங்கள் Python பயன்பாட்டில் ஏற்றியுள்ளீர்கள்.

## உங்கள் கணினியில் உள்ளூர் ரீதியாக இயக்குவது எப்படி

குறியீட்டை உங்கள் கணினியில் உள்ளூர் ரீதியாக இயக்க, [Python நிறுவப்பட்ட](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst) சில பதிப்புகள் தேவைப்படும்.

பின்னர் Repo ஐ பயன்படுத்த, நீங்கள் அதை Clone செய்ய வேண்டும்:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

உங்கள் எல்லாவற்றையும் சரிபார்த்த பிறகு, நீங்கள் தொடங்கலாம்!

## விருப்பமான நடவடிக்கைகள்

### Miniconda ஐ நிறுவுதல்

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) என்பது [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python மற்றும் சில தொகுப்புகளை நிறுவ ஒரு எளிய நிறுவல் கருவியாகும். Conda என்பது ஒரு தொகுப்பு மேலாளர், இது Python [**மெய்நிகர் சூழல்களை**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) மற்றும் தொகுப்புகளை அமைக்கவும் மாறவும் எளிதாக்குகிறது. இது `pip` மூலம் கிடைக்காத தொகுப்புகளை நிறுவுவதற்கும் உதவுகிறது.

[MiniConda நிறுவல் வழிகாட்டி](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst) ஐ பின்பற்றவும்.

Miniconda நிறுவப்பட்ட பிறகு, [Repo ஐ Clone செய்ய](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) வேண்டும் (நீங்கள் இதுவரை செய்யவில்லை என்றால்).

அடுத்ததாக, நீங்கள் ஒரு மெய்நிகர் சூழலை உருவாக்க வேண்டும். Conda உடன் இதை செய்ய, ஒரு புதிய சூழல் கோப்பை (_environment.yml_) உருவாக்கவும். Codespaces ஐப் பயன்படுத்தி பின்பற்றினால், இதை `.devcontainer` கோப்பகத்திற்குள் உருவாக்கவும், அதாவது `.devcontainer/environment.yml`.

உங்கள் சூழல் கோப்பை கீழே உள்ள குறியீட்டு துண்டுடன் நிரப்பவும்:

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

Conda ஐப் பயன்படுத்தும்போது பிழைகள் ஏற்படுவதாக நீங்கள் கண்டால், கீழே உள்ள கட்டளையை ஒரு டெர்மினலில் பயன்படுத்தி Microsoft AI Libraries ஐ கையேடு மூலம் நிறுவலாம்.

```
conda install -c microsoft azure-ai-ml
```

சூழல் கோப்பு நமக்கு தேவையான சார்புகளை குறிப்பிடுகிறது. `<environment-name>` என்பது உங்கள் Conda சூழலுக்கு நீங்கள் பயன்படுத்த விரும்பும் பெயர் மற்றும் `<python-version>` என்பது நீங்கள் பயன்படுத்த விரும்பும் Python பதிப்பு, உதாரணமாக, `3` என்பது Python இன் சமீபத்திய முக்கிய பதிப்பு.

அதன் பிறகு, உங்கள் Conda சூழலை உருவாக்க கீழே உள்ள கட்டளைகளை உங்கள் கட்டளை வரி/டெர்மினலில் இயக்கலாம்.

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

எந்தவொரு பிரச்சினைகளையும் சந்தித்தால், [Conda சூழல் வழிகாட்டி](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst) ஐப் பார்க்கவும்.

### Python ஆதரவு நீட்டிப்புடன் Visual Studio Code ஐ பயன்படுத்துதல்

இந்த பாடத்திட்டத்திற்காக [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) திருத்தியை [Python ஆதரவு நீட்டிப்பு](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) நிறுவியுடன் பயன்படுத்த பரிந்துரைக்கிறோம். இது, எனினும், ஒரு பரிந்துரை மட்டுமே, கட்டாயமான தேவையாக இல்லை.

> **குறிப்பு**: VS Code இல் பாட Repo ஐ திறக்கும்போது, நீங்கள் திட்டத்தை ஒரு container இல் அமைக்க விருப்பத்தை பெறுவீர்கள். இது Repo இல் உள்ள [சிறப்பு `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) கோப்பகத்தால் சாத்தியமாகிறது. இதைப் பற்றி மேலும் பின்னர்.

> **குறிப்பு**: நீங்கள் Repo ஐ Clone செய்து VS Code இல் திறந்தவுடன், Python ஆதரவு நீட்டிப்பை நிறுவுவதற்கு அது தானாகவே பரிந்துரை செய்யும்.

> **குறிப்பு**: VS Code Repo ஐ container இல் மீண்டும் திறக்க பரிந்துரைத்தால், Python இன் உள்ளூர் நிறுவப்பட்ட பதிப்பைப் பயன்படுத்த இந்த கோரிக்கையை நிராகரிக்கவும்.

### உலாவியில் Jupyter ஐ பயன்படுத்துதல்

நீங்கள் [Jupyter சூழல்](https://jupyter.org?WT.mc_id=academic-105485-koreyst) ஐ உலாவியில் நேரடியாக பயன்படுத்தி திட்டத்தில் வேலை செய்யலாம். பாரம்பரிய Jupyter மற்றும் [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) ஆகியவை தானியக்க நிறைவு, குறியீடு விளக்கமிடல் போன்ற அம்சங்களுடன் மிகவும் வசதியான மேம்பாட்டு சூழலை வழங்குகின்றன.

Jupyter ஐ உள்ளூர் ரீதியாக தொடங்க, டெர்மினல்/கட்டளை வரிக்கு செல்லவும், பாட கோப்பகத்திற்குச் செல்லவும், மற்றும் கீழே உள்ளதை இயக்கவும்:

```bash
jupyter notebook
```

அல்லது

```bash
jupyterhub
```

இது Jupyter ஐ தொடங்கும் மற்றும் அதை அணுக URL கட்டளை வரி சாளரத்தில் காட்டப்படும்.

URL ஐ அணுகியவுடன், நீங்கள் பாடத்தின் சுருக்கத்தை காணலாம் மற்றும் எந்த `*.ipynb` கோப்பிற்கும் செல்ல முடியும். உதாரணமாக, `08-building-search-applications/python/oai-solution.ipynb`.

### ஒரு container இல் இயக்குதல்

உங்கள் கணினியில் அல்லது Codespace இல் அனைத்தையும் அமைப்பதற்கான மாற்றாக, [container](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>) ஐ பயன்படுத்தலாம். Repo இல் உள்ள சிறப்பு `.devcontainer` கோப்பகம் VS Code இல் திட்டத்தை ஒரு container இல் அமைக்க சாத்தியமாக்குகிறது. Codespaces க்கு வெளியே, இது Docker ஐ நிறுவ வேண்டும், மேலும் இது சிறிது வேலை சிக்கலாக இருக்கும், எனவே containers உடன் வேலை செய்யும் அனுபவம் உள்ளவர்களுக்கு மட்டுமே இதை பரிந்துரைக்கிறோம்.

GitHub Codespaces ஐப் பயன்படுத்தும்போது உங்கள் API கீகளை பாதுகாப்பாக வைத்திருக்க சிறந்த வழிகளில் ஒன்றாக Codespace Secrets ஐ பயன்படுத்துவது ஆகும். [Codespaces ரகசிய மேலாண்மை](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst) வழிகாட்டியைப் பின்பற்றவும்.

## பாடங்கள் மற்றும் தொழில்நுட்ப தேவைகள்

இந்த பாடத்திட்டத்தில் 6 கருத்து பாடங்கள் மற்றும் 6 குறியீட்டு பாடங்கள் உள்ளன.

குறியீட்டு பாடங்களுக்கு, நாங்கள் Azure OpenAI Service ஐ பயன்படுத்துகிறோம். இந்த குறியீட்டை இயக்க, Azure OpenAI சேவைக்கு அணுகல் மற்றும் API கீ தேவைப்படும். [இந்த விண்ணப்பத்தை](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst) முடித்து அணுகலைப் பெற விண்ணப்பிக்கலாம்.

உங்கள் விண்ணப்பம் செயல்படுத்தப்படுவதற்காக காத்திருக்கும் போது, ஒவ்வொரு குறியீட்டு பாடத்திலும் `README.md` கோப்பு அடங்கும், இதில் நீங்கள் குறியீடு மற்றும் வெளியீடுகளை காணலாம்.

## Azure OpenAI சேவையை முதன்முதலாக பயன்படுத்துதல்

இது உங்கள் முதல் முறை Azure OpenAI சேவையுடன் வேலை செய்யும் போது, [Azure OpenAI சேவையின் resource ஐ உருவாக்கி, deploy செய்யும்](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst) வழிகாட்டியைப் பின்பற்றவும்.

## OpenAI API ஐ முதன்முதலாக பயன்படுத்துதல்

இது உங்கள் முதல் முறை OpenAI API உடன் வேலை செய்யும் போது, [Interface ஐ உருவாக்கி பயன்படுத்த](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst) வழிகாட்டியைப் பின்பற்றவும்.

## மற்ற கற்றவர்களை சந்திக்கவும்

எங்கள் அதிகாரப்பூர்வ [AI Community Discord server](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) இல் மற்ற கற்றவர்களை சந்திக்க சேனல்கள் உருவாக்கப்பட்டுள்ளன. இது Generative AI இல் மேம்பட விரும்பும் மற்ற தொழில்முனைவோர், கட்டுமானர்கள், மாணவர்கள் மற்றும் யாருடன் நெட்வொர்க் செய்ய வேண்டும் என்று நினைக்கும் அனைவருக்கும் ஒரு சிறந்த வழியாகும்.

[![Discord சேனலைச் சேரவும்](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

கற்றவர்களுக்கு உதவ திட்ட குழுவும் இந்த Discord server இல் இருக்கும்.

## பங்களிக்கவும்

இந்த பாடத்திட்டம் ஒரு திறந்த மூல முயற்சியாகும். மேம்படுத்த வேண்டிய பகுதிகள் அல்லது பிரச்சினைகள் உள்ளன என்று நீங்கள் நினைத்தால், [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) ஐ உருவாக்கவும் அல்லது [GitHub issue](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst) ஐ பதிவு செய்யவும்.

திட்ட குழு அனைத்து பங்களிப்புகளையும் கண்காணிக்கும். திறந்த மூலத்திற்கு பங்களிப்பது Generative AI இல் உங்கள் தொழில்முனைவுத் திறனை உருவாக்க ஒரு அற்புதமான வழியாகும்.

பெரும்பாலான பங்களிப்புகள் Contributor License Agreement (CLA) ஐ ஒப்புக்கொள்வதற்கு உங்களை ஒப்புக்கொள்கின்றன, இது உங்களுக்கு உரிமை உள்ளது மற்றும் உண்மையில் உங்கள் பங்களிப்பைப் பயன்படுத்த எங்களுக்கு உரிமைகளை வழங்குகிறது என்பதை அறிவிக்கிறது. மேலும் விவரங்களுக்கு [CLA, Contributor License Agreement website](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst) ஐ பார்வையிடவும்.

ஒரு pull request ஐ சமர்ப்பிக்கும்போது, CLA-bot தானாகவே நீங்கள் CLA ஐ வழங்க வேண்டியதா என்பதைத் தீர்மானித்து PR ஐ சரியாக அலங்கரிக்கும் (எ.கா., லேபிள், கருத்து). Bot வழங்கிய வழிகாட்டுதல்களைப் பின்பற்றவும். எங்கள் CLA ஐப் பயன்படுத்தும் அனைத்து Repo களிலும் நீங்கள் இதை ஒருமுறை மட்டுமே செய்ய வேண்டும்.

இந்த திட்டம் [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst) ஐ ஏற்றுக்கொண்டது. மேலும் தகவலுக்கு Code of Conduct FAQ ஐ படிக்கவும் அல்லது [Email opencode](opencode@microsoft.com) ஐ தொடர்பு கொள்ளவும்.

## தொடங்குவோம்
இப்போது நீங்கள் இந்த பாடத்தை முடிக்க தேவையான படிகளை முடித்துள்ளீர்கள், ஜெனரேட்டிவ் AI மற்றும் LLMகளின் [அறிமுகத்தைப் பெறுவதன் மூலம்](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst) தொடங்கலாம்.

---

**குறிப்பு**:  
இந்த ஆவணம் AI மொழிபெயர்ப்பு சேவை [Co-op Translator](https://github.com/Azure/co-op-translator) பயன்படுத்தி மொழிபெயர்க்கப்பட்டுள்ளது. நாங்கள் துல்லியத்திற்காக முயற்சிக்கிறோம், ஆனால் தானியங்கி மொழிபெயர்ப்புகளில் பிழைகள் அல்லது தவறுகள் இருக்கக்கூடும் என்பதை கவனத்தில் கொள்ளவும். அதன் தாய்மொழியில் உள்ள மூல ஆவணம் அதிகாரப்பூர்வ ஆதாரமாக கருதப்பட வேண்டும். முக்கியமான தகவல்களுக்கு, தொழில்முறை மனித மொழிபெயர்ப்பு பரிந்துரைக்கப்படுகிறது. இந்த மொழிபெயர்ப்பைப் பயன்படுத்துவதால் ஏற்படும் எந்த தவறான புரிதல்கள் அல்லது தவறான விளக்கங்களுக்கு நாங்கள் பொறுப்பல்ல.