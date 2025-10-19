<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "8a50125da1d2836fab30bb91c19def97",
  "translation_date": "2025-10-11T11:41:15+00:00",
  "source_file": "00-course-setup/02-setup-local.md",
  "language_code": "ta"
}
-->
# உள்ளூர் அமைப்பு 🖥️

**உங்கள் சொந்த லேப்டாப்பில் அனைத்தையும் இயக்க விரும்பினால் இந்த வழிகாட்டியைப் பயன்படுத்தவும்.**  
உங்களுக்கு இரண்டு வழிகள் உள்ளன: **(A) இயல்பான Python + virtual-env** அல்லது **(B) VS Code Dev Container Docker உடன்**.  
எது எளிதாக தோன்றுகிறதோ அதைத் தேர்ந்தெடுக்கவும்—இரண்டும் ஒரே பாடங்களுக்கு வழிவகுக்கும்.

## 1.  முன் தேவைகள்

| கருவி               | பதிப்பு / குறிப்புகள்                                                                      |
|--------------------|--------------------------------------------------------------------------------------|
| **Python**         | 3.10 + (<https://python.org> இல் இருந்து பெறவும்)                                            |
| **Git**            | சமீபத்தியது (Xcode / Windows க்கான Git / Linux package manager உடன் வருகிறது)                   |
| **VS Code**        | விருப்பமானது ஆனால் பரிந்துரைக்கப்படுகிறது <https://code.visualstudio.com>                             |
| **Docker Desktop** | *Option B* க்கானது மட்டுமே. இலவசமாக நிறுவவும்: <https://docs.docker.com/desktop/>                |

> 💡 **குறிப்பு** – கருவிகளை ஒரு terminal இல் சரிபார்க்கவும்:  
> `python --version`, `git --version`, `docker --version`, `code --version`  

## 2.  Option A – இயல்பான Python (வேகமானது)

### படி 1  இந்த repo ஐ clone செய்யவும்

```bash
git clone https://github.com/<your-github>/generative-ai-for-beginners
cd generative-ai-for-beginners
```

### படி 2 ஒரு virtual environment உருவாக்கி செயல்படுத்தவும்

```bash
python -m venv .venv          # make one
source .venv/bin/activate     # macOS / Linux
.\.venv\Scripts\activate      # Windows PowerShell
```

✅ Prompt இப்போது (.venv) உடன் தொடங்க வேண்டும்—அதுவே நீங்கள் env உள்ளே உள்ளீர்கள் என்பதைக் குறிக்கிறது.

### படி 3 Dependencies ஐ நிறுவவும்

```bash
pip install -r requirements.txt
```

[API keys](../../../00-course-setup) பற்றிய பிரிவுக்கு செல்லவும்

## 2. Option B – VS Code Dev Container (Docker)

இந்த repository மற்றும் course ஐ [development container](https://containers.dev?WT.mc_id=academic-105485-koreyst) உடன் அமைத்துள்ளோம், இது Python3, .NET, Node.js மற்றும் Java development ஐ ஆதரிக்க Universal runtime உடன் வருகிறது. தொடர்புடைய configuration இந்த repository இன் root இல் உள்ள `.devcontainer/` கோப்பகத்தில் உள்ள `devcontainer.json` கோப்பில் வரையறுக்கப்பட்டுள்ளது.

>**ஏன் இதைத் தேர்ந்தெடுக்க வேண்டும்?**
>Codespaces உடன் ஒரே மாதிரியான சூழல்; dependency மாற்றம் இல்லை.

### படி 0 கூடுதல் கருவிகளை நிறுவவும்

Docker Desktop – ```docker --version``` வேலை செய்கிறதா என்பதை உறுதிப்படுத்தவும்.  
VS Code Remote – Containers extension (ID: ms-vscode-remote.remote-containers).

### படி 1 Repo ஐ VS Code இல் திறக்கவும்

File ▸ Open Folder…  → generative-ai-for-beginners

VS Code `.devcontainer/` ஐ கண்டறிந்து ஒரு prompt ஐ காட்டும்.

### படி 2 Container இல் மீண்டும் திறக்கவும்

“Reopen in Container” ஐ கிளிக் செய்யவும். Docker image ஐ build செய்கிறது (முதல் முறையில் ≈ 3 நிமிடம்).  
Terminal prompt தோன்றும் போது, நீங்கள் container உள்ளே உள்ளீர்கள்.

## 2.  Option C – Miniconda

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) என்பது [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python மற்றும் சில packages ஐ நிறுவ ஒரு lightweight installer ஆகும்.  
Conda என்பது ஒரு package manager ஆகும், இது Python [**virtual environments**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) மற்றும் packages ஐ அமைக்கவும் மாற்றவும் எளிதாக்குகிறது.  
இது `pip` மூலம் கிடைக்காத packages ஐ நிறுவுவதற்கும் உதவுகிறது.

### படி 0  Miniconda ஐ நிறுவவும்

[MiniConda installation guide](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst) ஐ பின்பற்றி அமைக்கவும்.

```bash
conda --version
```

### படி 1 ஒரு virtual environment உருவாக்கவும்

ஒரு புதிய environment கோப்பை (*environment.yml*) உருவாக்கவும்.  
Codespaces ஐப் பயன்படுத்தி பின்பற்றினால், `.devcontainer` directory இல் இதை உருவாக்கவும், அதாவது `.devcontainer/environment.yml`.

### படி 2  உங்கள் environment கோப்பை நிரப்பவும்

`environment.yml` இல் பின்வரும் snippet ஐ சேர்க்கவும்:

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

### படி 3 உங்கள் Conda environment ஐ உருவாக்கவும்

கீழே உள்ள commands ஐ உங்கள் command line/terminal இல் இயக்கவும்:

```bash 
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

Conda environments guide](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst) ஐப் பார்க்கவும், ஏதேனும் பிரச்சினைகள் ஏற்பட்டால்.

## 2  Option D – Classic Jupyter / Jupyter Lab (உங்கள் browser இல்)

> **இது யாருக்கானது?**  
> Classic Jupyter interface ஐ விரும்புபவர்கள் அல்லது VS Code இல்லாமல் notebooks ஐ இயக்க விரும்புபவர்கள்.  

### படி 1  Jupyter நிறுவப்பட்டுள்ளதா என்பதை உறுதிப்படுத்தவும்

Jupyter ஐ உள்ளூர் அளவில் தொடங்க, terminal/command line க்கு செல்லவும், course directory க்கு navigate செய்யவும், மற்றும் கீழே உள்ளதை இயக்கவும்:

```bash
jupyter notebook
```

அல்லது

```bash
jupyterhub
```

இது Jupyter instance ஐ தொடங்கும், மற்றும் அதை அணுக URL command line window இல் காட்டப்படும்.

URL ஐ அணுகியவுடன், course outline ஐ காணலாம் மற்றும் எந்த `*.ipynb` கோப்பிற்கும் navigate செய்யலாம்.  
உதாரணமாக, `08-building-search-applications/python/oai-solution.ipynb`.

## 3. உங்கள் API Keys ஐச் சேர்க்கவும்

API keys ஐ பாதுகாப்பாகவும் பாதுகாப்பாகவும் வைத்திருப்பது எந்தவொரு வகையான application ஐ உருவாக்கும்போதும் முக்கியமானது.  
API keys ஐ நேரடியாக உங்கள் code இல் சேமிக்க பரிந்துரைக்கவில்லை.  
அந்த விவரங்களை ஒரு public repository க்கு commit செய்வது security பிரச்சினைகள் மற்றும் unwanted செலவுகளை ஏற்படுத்தலாம்.  
Python க்கான `.env` கோப்பை உருவாக்கி `GITHUB_TOKEN` ஐச் சேர்க்க எப்படி என்பதைப் பற்றிய படி-படி வழிகாட்டி இதோ:

1. **உங்கள் Project Directory க்கு செல்லவும்**:  
Terminal அல்லது command prompt ஐ திறந்து, `.env` கோப்பை உருவாக்க விரும்பும் உங்கள் project இன் root directory க்கு செல்லவும்.

   ```bash
   cd path/to/your/project
   ```

2. **`.env` கோப்பை உருவாக்கவும்**:  
உங்கள் விருப்பமான text editor ஐப் பயன்படுத்தி `.env` என்ற புதிய கோப்பை உருவாக்கவும்.  
Command line ஐப் பயன்படுத்தினால், `touch` (Unix-based systems) அல்லது `echo` (Windows) ஐப் பயன்படுத்தலாம்:

   Unix-based systems:

   ```bash
   touch .env
   ```

   Windows:

   ```cmd
   echo . > .env
   ```

3. **`.env` கோப்பை திருத்தவும்**:  
`.env` கோப்பை ஒரு text editor (உதா., VS Code, Notepad++ அல்லது வேறு editor) இல் திறக்கவும்.  
கீழே உள்ள வரியை கோப்பில் சேர்க்கவும், `your_github_token_here` ஐ உங்கள் GitHub token உடன் மாற்றவும்:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```

4. **கோப்பை சேமிக்கவும்**:  
மாற்றங்களைச் சேமித்து text editor ஐ மூடவும்.

5. **`python-dotenv` ஐ நிறுவவும்**:  
இன்னும் நிறுவவில்லை என்றால், `.env` கோப்பிலிருந்து environment variables ஐ Python application க்கு load செய்ய `python-dotenv` package ஐ நிறுவ வேண்டும்.  
`pip` ஐப் பயன்படுத்தி இதை நிறுவலாம்:

   ```bash
   pip install python-dotenv
   ```

6. **Python script இல் Environment Variables ஐ load செய்யவும்**:  
Python script இல், `.env` கோப்பிலிருந்து environment variables ஐ load செய்ய `python-dotenv` package ஐப் பயன்படுத்தவும்:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```

அதுவே! `.env` கோப்பை வெற்றிகரமாக உருவாக்கி, உங்கள் GitHub token ஐச் சேர்த்து, Python application க்கு load செய்துள்ளீர்கள்.

🔐 `.env` ஐ commit செய்ய வேண்டாம்—இது ஏற்கனவே `.gitignore` இல் உள்ளது.  
முழு provider வழிகாட்டிகள் [`providers.md`](03-providers.md) இல் உள்ளன.

## 4. அடுத்தது என்ன?

| நான் செய்ய விரும்புகிறேன்…          | செல்ல…                                                                  |
|---------------------|-------------------------------------------------------------------------|
| Lesson 1 ஐ தொடங்கவும்      | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)     |
| ஒரு LLM Provider ஐ அமைக்கவும் | [`providers.md`](03-providers.md)                                       |
| மற்ற learners ஐ சந்திக்கவும் | [எங்கள் Discord ஐச் சேரவும்](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)   |

## 5. Troubleshooting

| அறிகுறி                                   | தீர்வு                                                             |
|-------------------------------------------|-----------------------------------------------------------------|
| `python not found`                        | Python ஐ PATH க்கு சேர்க்கவும் அல்லது install பின் terminal ஐ மீண்டும் திறக்கவும்            |
| `pip` cannot build wheels (Windows)       | `pip install --upgrade pip setuptools wheel` பின்னர் மீண்டும் முயற்சிக்கவும்.        |
| `ModuleNotFoundError: dotenv`             | `pip install -r requirements.txt` ஐ இயக்கவும் (env install செய்யப்படவில்லை).   |
| Docker build fails *No space left*        | Docker Desktop ▸ *Settings* ▸ *Resources* → disk size ஐ அதிகரிக்கவும். |
| VS Code keeps prompting to reopen         | நீங்கள் இரண்டு Options ஐயும் செயல்படுத்தியிருக்கலாம்; ஒன்று (venv **அல்லது** container) தேர்ந்தெடுக்கவும்|
| OpenAI 401 / 429 errors                   | `OPENAI_API_KEY` மதிப்பு / request rate limits ஐ சரிபார்க்கவும்.             |
| Conda ஐப் பயன்படுத்தும் போது பிழைகள்      | Microsft AI libraries ஐ `conda install -c microsoft azure-ai-ml` மூலம் நிறுவவும்|

---

**குறிப்பு**:  
இந்த ஆவணம் [Co-op Translator](https://github.com/Azure/co-op-translator) என்ற AI மொழிபெயர்ப்பு சேவையைப் பயன்படுத்தி மொழிபெயர்க்கப்பட்டுள்ளது. நாங்கள் துல்லியத்திற்காக முயற்சிக்கிறோம், ஆனால் தானியக்க மொழிபெயர்ப்புகளில் பிழைகள் அல்லது தவறான தகவல்கள் இருக்கக்கூடும் என்பதை தயவுசெய்து கவனத்தில் கொள்ளுங்கள். அதன் தாய்மொழியில் உள்ள மூல ஆவணம் அதிகாரப்பூர்வ ஆதாரமாக கருதப்பட வேண்டும். முக்கியமான தகவல்களுக்கு, தொழில்முறை மனித மொழிபெயர்ப்பு பரிந்துரைக்கப்படுகிறது. இந்த மொழிபெயர்ப்பைப் பயன்படுத்துவதால் ஏற்படும் எந்த தவறான புரிதல்கள் அல்லது தவறான விளக்கங்களுக்கு நாங்கள் பொறுப்பல்ல.