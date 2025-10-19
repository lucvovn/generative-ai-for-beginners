<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-18T00:34:51+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "pa"
}
-->
# ਇਸ ਕੋਰਸ ਨਾਲ ਸ਼ੁਰੂਆਤ ਕਰਨਾ

ਅਸੀਂ ਬਹੁਤ ਉਤਸ਼ਾਹਿਤ ਹਾਂ ਕਿ ਤੁਸੀਂ ਇਸ ਕੋਰਸ ਨੂੰ ਸ਼ੁਰੂ ਕਰ ਰਹੇ ਹੋ ਅਤੇ ਦੇਖ ਰਹੇ ਹੋ ਕਿ ਜਨਰੇਟਿਵ AI ਨਾਲ ਤੁਸੀਂ ਕੀ ਬਣਾਉਣ ਲਈ ਪ੍ਰੇਰਿਤ ਹੋ ਸਕਦੇ ਹੋ!

ਤੁਹਾਡੀ ਸਫਲਤਾ ਨੂੰ ਯਕੀਨੀ ਬਣਾਉਣ ਲਈ, ਇਹ ਪੰਨਾ ਸੈਟਅੱਪ ਕਦਮਾਂ, ਤਕਨੀਕੀ ਲੋੜਾਂ, ਅਤੇ ਜਿੱਥੇ ਜ਼ਰੂਰਤ ਹੋਵੇ ਮਦਦ ਪ੍ਰਾਪਤ ਕਰਨ ਲਈ ਜਾਣਕਾਰੀ ਦਿੰਦਾ ਹੈ।

## ਸੈਟਅੱਪ ਕਦਮ

ਇਸ ਕੋਰਸ ਨੂੰ ਸ਼ੁਰੂ ਕਰਨ ਲਈ, ਤੁਹਾਨੂੰ ਹੇਠਾਂ ਦਿੱਤੇ ਕਦਮਾਂ ਨੂੰ ਪੂਰਾ ਕਰਨ ਦੀ ਲੋੜ ਹੋਵੇਗੀ।

### 1. ਇਸ ਰਿਪੋ ਨੂੰ ਫੋਰਕ ਕਰੋ

[ਇਸ ਪੂਰੇ ਰਿਪੋ ਨੂੰ ਫੋਰਕ ਕਰੋ](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) ਆਪਣੇ GitHub ਅਕਾਊਂਟ ਵਿੱਚ ਤਾਂ ਜੋ ਤੁਸੀਂ ਕੋਈ ਵੀ ਕੋਡ ਬਦਲ ਸਕੋ ਅਤੇ ਚੈਲੈਂਜ ਪੂਰੇ ਕਰ ਸਕੋ। ਤੁਸੀਂ ਇਸ ਰਿਪੋ ਨੂੰ [ਸਟਾਰ (🌟)](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) ਵੀ ਕਰ ਸਕਦੇ ਹੋ ਤਾਂ ਜੋ ਇਸਨੂੰ ਅਤੇ ਸੰਬੰਧਿਤ ਰਿਪੋਜ਼ਿਟਰੀਜ਼ ਨੂੰ ਆਸਾਨੀ ਨਾਲ ਲੱਭ ਸਕੋ।

### 2. ਇੱਕ ਕੋਡਸਪੇਸ ਬਣਾਓ

ਕੋਡ ਚਲਾਉਣ ਸਮੇਂ ਕਿਸੇ ਵੀ ਡਿਪੈਂਡੈਂਸੀ ਸਮੱਸਿਆ ਤੋਂ ਬਚਣ ਲਈ, ਅਸੀਂ ਇਸ ਕੋਰਸ ਨੂੰ [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst) ਵਿੱਚ ਚਲਾਉਣ ਦੀ ਸਿਫਾਰਸ਼ ਕਰਦੇ ਹਾਂ।

ਤੁਹਾਡੇ ਫੋਰਕ ਵਿੱਚ: **Code -> Codespaces -> New on main**

![ਕੋਡਸਪੇਸ ਬਣਾਉਣ ਲਈ ਬਟਨ ਦਿਖਾਉਣ ਵਾਲਾ ਡਾਇਲਾਗ](../../../00-course-setup/images/who-will-pay.webp)

#### 2.1 ਇੱਕ ਸਿਕ੍ਰੇਟ ਸ਼ਾਮਲ ਕਰੋ

1. ⚙️ ਗੀਅਰ ਆਈਕਨ -> ਕਮਾਂਡ ਪੈਲੇਟ -> Codespaces : Manage user secret -> Add a new secret.
2. OPENAI_API_KEY ਨਾਮ ਰੱਖੋ, ਆਪਣੀ ਕੀ ਪੇਸਟ ਕਰੋ, ਸੇਵ ਕਰੋ।

### 3. ਅਗਲਾ ਕੀ ਹੈ?

| ਮੈਂ ਚਾਹੁੰਦਾ ਹਾਂ...          | ਜਾਓ...                                                                  |
|---------------------|-------------------------------------------------------------------------|
| ਪਾਠ 1 ਸ਼ੁਰੂ ਕਰੋ      | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)     |
| ਆਫਲਾਈਨ ਕੰਮ ਕਰੋ        | [`setup-local.md`](02-setup-local.md)                                   |
| ਇੱਕ LLM ਪ੍ਰਦਾਤਾ ਸੈਟਅੱਪ ਕਰੋ | [`providers.md`](03-providers.md)                                        |
| ਹੋਰ ਸਿੱਖਣ ਵਾਲਿਆਂ ਨੂੰ ਮਿਲੋ | [ਸਾਡੇ Discord ਵਿੱਚ ਸ਼ਾਮਲ ਹੋਵੋ](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)   |

## ਸਮੱਸਿਆ ਹੱਲ

| ਲੱਛਣ                                   | ਹੱਲ                                                             |
|-------------------------------------------|-----------------------------------------------------------------|
| ਕੰਟੇਨਰ ਬਣਾਉਣ > 10 ਮਿੰਟ ਲਈ ਫਸਿਆ            | **Codespaces ➜ “Rebuild Container”**                            |
| `python: command not found`               | ਟਰਮੀਨਲ ਜੁੜਿਆ ਨਹੀਂ; **+** ➜ *bash* 'ਤੇ ਕਲਿੱਕ ਕਰੋ                    |
| OpenAI ਤੋਂ `401 Unauthorized`            | ਗਲਤ / ਮਿਆਦ ਖਤਮ `OPENAI_API_KEY`                                |
| VS Code “Dev container mounting…” ਦਿਖਾਉਂਦਾ ਹੈ   | ਬ੍ਰਾਊਜ਼ਰ ਟੈਬ ਨੂੰ ਰਿਫ੍ਰੈਸ਼ ਕਰੋ—Codespaces ਕਦੇ-ਕਦੇ ਕਨੈਕਸ਼ਨ ਗੁਆ ਲੈਂਦਾ ਹੈ   |
| ਨੋਟਬੁੱਕ ਕਰਨਲ ਗਾਇਬ                   | ਨੋਟਬੁੱਕ ਮੀਨੂ ➜ **Kernel ▸ Select Kernel ▸ Python 3**           |

   ਯੂਨਿਕਸ-ਅਧਾਰਿਤ ਸਿਸਟਮ:

   ```bash
   touch .env
   ```

   Windows:

   ```cmd
   echo . > .env
   ```

3. **`.env` ਫਾਈਲ ਨੂੰ ਸੋਧੋ**: `.env` ਫਾਈਲ ਨੂੰ ਕਿਸੇ ਟੈਕਸਟ ਐਡੀਟਰ (ਜਿਵੇਂ ਕਿ VS Code, Notepad++, ਜਾਂ ਕੋਈ ਹੋਰ ਐਡੀਟਰ) ਵਿੱਚ ਖੋਲ੍ਹੋ। ਫਾਈਲ ਵਿੱਚ ਹੇਠਾਂ ਦਿੱਤੀ ਲਾਈਨ ਸ਼ਾਮਲ ਕਰੋ, `your_github_token_here` ਨੂੰ ਆਪਣੇ ਅਸਲ GitHub ਟੋਕਨ ਨਾਲ ਬਦਲੋ:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```

4. **ਫਾਈਲ ਸੇਵ ਕਰੋ**: ਬਦਲਾਅ ਸੇਵ ਕਰੋ ਅਤੇ ਟੈਕਸਟ ਐਡੀਟਰ ਬੰਦ ਕਰੋ।

5. **`python-dotenv` ਇੰਸਟਾਲ ਕਰੋ**: ਜੇਕਰ ਤੁਸੀਂ ਪਹਿਲਾਂ ਨਹੀਂ ਕੀਤਾ, ਤੁਹਾਨੂੰ `.env` ਫਾਈਲ ਤੋਂ ਆਪਣੇ Python ਐਪਲੀਕੇਸ਼ਨ ਵਿੱਚ ਵਾਤਾਵਰਣ ਵੈਰੀਏਬਲ ਲੋਡ ਕਰਨ ਲਈ `python-dotenv` ਪੈਕੇਜ ਇੰਸਟਾਲ ਕਰਨ ਦੀ ਲੋੜ ਹੋਵੇਗੀ। ਤੁਸੀਂ ਇਸਨੂੰ `pip` ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਇੰਸਟਾਲ ਕਰ ਸਕਦੇ ਹੋ:

   ```bash
   pip install python-dotenv
   ```

6. **ਆਪਣੇ Python ਸਕ੍ਰਿਪਟ ਵਿੱਚ ਵਾਤਾਵਰਣ ਵੈਰੀਏਬਲ ਲੋਡ ਕਰੋ**: ਆਪਣੇ Python ਸਕ੍ਰਿਪਟ ਵਿੱਚ, `.env` ਫਾਈਲ ਤੋਂ ਵਾਤਾਵਰਣ ਵੈਰੀਏਬਲ ਲੋਡ ਕਰਨ ਲਈ `python-dotenv` ਪੈਕੇਜ ਦੀ ਵਰਤੋਂ ਕਰੋ:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```

ਇਹ ਹੋ ਗਿਆ! ਤੁਸੀਂ ਸਫਲਤਾਪੂਰਵਕ `.env` ਫਾਈਲ ਬਣਾਈ, ਆਪਣਾ GitHub ਟੋਕਨ ਸ਼ਾਮਲ ਕੀਤਾ, ਅਤੇ ਇਸਨੂੰ ਆਪਣੇ Python ਐਪਲੀਕੇਸ਼ਨ ਵਿੱਚ ਲੋਡ ਕੀਤਾ।

## ਆਪਣੇ ਕੰਪਿਊਟਰ 'ਤੇ ਲੋਕਲ ਚਲਾਉਣ ਦਾ ਤਰੀਕਾ

ਕੋਡ ਨੂੰ ਆਪਣੇ ਕੰਪਿਊਟਰ 'ਤੇ ਲੋਕਲ ਚਲਾਉਣ ਲਈ, ਤੁਹਾਨੂੰ [Python](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst) ਦਾ ਕੁਝ ਵਰਜਨ ਇੰਸਟਾਲ ਕਰਨਾ ਪਵੇਗਾ।

ਫਿਰ ਰਿਪੋਜ਼ਿਟਰੀ ਦੀ ਵਰਤੋਂ ਕਰਨ ਲਈ, ਤੁਹਾਨੂੰ ਇਸਨੂੰ ਕਲੋਨ ਕਰਨ ਦੀ ਲੋੜ ਹੋਵੇਗੀ:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

ਜਦੋਂ ਤੁਹਾਡੇ ਕੋਲ ਸਭ ਕੁਝ ਚੈੱਕ ਆਉਟ ਹੋਵੇ, ਤਾਂ ਤੁਸੀਂ ਸ਼ੁਰੂ ਕਰ ਸਕਦੇ ਹੋ!

## ਵਿਕਲਪਿਕ ਕਦਮ

### Miniconda ਇੰਸਟਾਲ ਕਰਨਾ

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python, ਅਤੇ ਕੁਝ ਪੈਕੇਜਾਂ ਨੂੰ ਇੰਸਟਾਲ ਕਰਨ ਲਈ ਇੱਕ ਹਲਕਾ ਇੰਸਟਾਲਰ ਹੈ।  
Conda ਖੁਦ ਇੱਕ ਪੈਕੇਜ ਮੈਨੇਜਰ ਹੈ, ਜੋ ਵੱਖ-ਵੱਖ Python [**ਵਰਚੁਅਲ ਵਾਤਾਵਰਣਾਂ**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) ਅਤੇ ਪੈਕੇਜਾਂ ਨੂੰ ਸੈਟਅੱਪ ਅਤੇ ਸਵਿੱਚ ਕਰਨਾ ਆਸਾਨ ਬਣਾਉਂਦਾ ਹੈ। ਇਹ ਉਹ ਪੈਕੇਜ ਇੰਸਟਾਲ ਕਰਨ ਲਈ ਵੀ ਸਹਾਇਕ ਹੈ ਜੋ `pip` ਰਾਹੀਂ ਉਪਲਬਧ ਨਹੀਂ ਹਨ।

ਤੁਸੀਂ [MiniConda ਇੰਸਟਾਲੇਸ਼ਨ ਗਾਈਡ](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst) ਦੀ ਪਾਲਣਾ ਕਰਕੇ ਇਸਨੂੰ ਸੈਟਅੱਪ ਕਰ ਸਕਦੇ ਹੋ।

Miniconda ਇੰਸਟਾਲ ਕਰਨ ਦੇ ਨਾਲ, ਤੁਹਾਨੂੰ [ਰਿਪੋਜ਼ਿਟਰੀ](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) ਕਲੋਨ ਕਰਨ ਦੀ ਲੋੜ ਹੋਵੇਗੀ (ਜੇਕਰ ਤੁਸੀਂ ਪਹਿਲਾਂ ਨਹੀਂ ਕੀਤਾ)

ਅਗਲੇ ਕਦਮ ਵਿੱਚ, ਤੁਹਾਨੂੰ ਇੱਕ ਵਰਚੁਅਲ ਵਾਤਾਵਰਣ ਬਣਾਉਣ ਦੀ ਲੋੜ ਹੋਵੇਗੀ। Conda ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਇਹ ਕਰਨ ਲਈ, ਇੱਕ ਨਵਾਂ ਵਾਤਾਵਰਣ ਫਾਈਲ (_environment.yml_) ਬਣਾਓ। ਜੇਕਰ ਤੁਸੀਂ Codespaces ਦੀ ਵਰਤੋਂ ਕਰ ਰਹੇ ਹੋ, ਤਾਂ ਇਸਨੂੰ `.devcontainer` ਡਾਇਰੈਕਟਰੀ ਵਿੱਚ ਬਣਾਓ, ਇਸ ਤਰ੍ਹਾਂ `.devcontainer/environment.yml`।

ਆਪਣੀ ਵਾਤਾਵਰਣ ਫਾਈਲ ਨੂੰ ਹੇਠਾਂ ਦਿੱਤੇ ਸਨਿੱਪੇ ਨਾਲ ਭਰੋ:

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

ਜੇਕਰ ਤੁਹਾਨੂੰ conda ਦੀ ਵਰਤੋਂ ਕਰਦੇ ਸਮੇਂ ਸਮੱਸਿਆਵਾਂ ਆਉਂਦੀਆਂ ਹਨ, ਤਾਂ ਤੁਸੀਂ ਹੱਥੋਂ Microsoft AI Libraries ਨੂੰ ਹੇਠਾਂ ਦਿੱਤੇ ਕਮਾਂਡ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਟਰਮੀਨਲ ਵਿੱਚ ਇੰਸਟਾਲ ਕਰ ਸਕਦੇ ਹੋ।

```
conda install -c microsoft azure-ai-ml
```

ਵਾਤਾਵਰਣ ਫਾਈਲ ਉਹ ਡਿਪੈਂਡੈਂਸੀਜ਼ ਦਰਸਾਉਂਦੀ ਹੈ ਜਿਨ੍ਹਾਂ ਦੀ ਸਾਨੂੰ ਲੋੜ ਹੈ। `<environment-name>` ਉਸ ਨਾਮ ਨੂੰ ਦਰਸਾਉਂਦਾ ਹੈ ਜੋ ਤੁਸੀਂ ਆਪਣੇ Conda ਵਾਤਾਵਰਣ ਲਈ ਵਰਤਣਾ ਚਾਹੁੰਦੇ ਹੋ, ਅਤੇ `<python-version>` Python ਦੇ ਵਰਜਨ ਨੂੰ ਦਰਸਾਉਂਦਾ ਹੈ ਜੋ ਤੁਸੀਂ ਵਰਤਣਾ ਚਾਹੁੰਦੇ ਹੋ, ਉਦਾਹਰਨ ਲਈ, `3` Python ਦਾ ਨਵਾਂ ਵਰਜਨ ਹੈ।

ਇਸਨੂੰ ਪੂਰਾ ਕਰਨ ਦੇ ਨਾਲ, ਤੁਸੀਂ ਹੇਠਾਂ ਦਿੱਤੇ ਕਮਾਂਡਾਂ ਨੂੰ ਚਲਾਕੇ ਆਪਣਾ Conda ਵਾਤਾਵਰਣ ਬਣਾਉਣ ਲਈ ਜਾ ਸਕਦੇ ਹੋ:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

ਜੇਕਰ ਤੁਹਾਨੂੰ ਕੋਈ ਸਮੱਸਿਆ ਆਉਂਦੀ ਹੈ, ਤਾਂ [Conda ਵਾਤਾਵਰਣ ਗਾਈਡ](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst) ਨੂੰ ਵੇਖੋ।

### Python ਸਪੋਰਟ ਐਕਸਟੈਂਸ਼ਨ ਨਾਲ Visual Studio Code ਦੀ ਵਰਤੋਂ

ਅਸੀਂ ਇਸ ਕੋਰਸ ਲਈ [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) ਐਡੀਟਰ ਦੀ ਸਿਫਾਰਸ਼ ਕਰਦੇ ਹਾਂ ਜਿਸ ਵਿੱਚ [Python ਸਪੋਰਟ ਐਕਸਟੈਂਸ਼ਨ](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) ਇੰਸਟਾਲ ਹੈ। ਹਾਲਾਂਕਿ, ਇਹ ਸਿਰਫ ਸਿਫਾਰਸ਼ ਹੈ, ਲਾਜ਼ਮੀ ਨਹੀਂ।

> **ਨੋਟ**: ਜਦੋਂ ਤੁਸੀਂ VS Code ਵਿੱਚ ਕੋਰਸ ਰਿਪੋਜ਼ਿਟਰੀ ਖੋਲ੍ਹਦੇ ਹੋ, ਤੁਹਾਡੇ ਕੋਲ ਇਸਨੂੰ ਇੱਕ ਕੰਟੇਨਰ ਵਿੱਚ ਸੈਟਅੱਪ ਕਰਨ ਦਾ ਵਿਕਲਪ ਹੁੰਦਾ ਹੈ। ਇਹ [ਖਾਸ `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) ਡਾਇਰੈਕਟਰੀ ਦੇ ਕਾਰਨ ਹੈ ਜੋ ਕੋਰਸ ਰਿਪੋਜ਼ਿਟਰੀ ਵਿੱਚ ਪਾਈ ਜਾਂਦੀ ਹੈ। ਇਸ ਬਾਰੇ ਹੋਰ ਜਾਣਕਾਰੀ ਬਾਅਦ ਵਿੱਚ।

> **ਨੋਟ**: ਜਦੋਂ ਤੁਸੀਂ VS Code ਵਿੱਚ ਡਾਇਰੈਕਟਰੀ ਕਲੋਨ ਕਰਦੇ ਹੋ ਅਤੇ ਖੋਲ੍ਹਦੇ ਹੋ, ਇਹ ਤੁਹਾਨੂੰ Python ਸਪੋਰਟ ਐਕਸਟੈਂਸ਼ਨ ਇੰਸਟਾਲ ਕਰਨ ਦੀ ਸਲਾਹ ਦੇਵੇਗਾ।

> **ਨੋਟ**: ਜੇਕਰ VS Code ਤੁਹਾਨੂੰ ਰਿਪੋਜ਼ਿਟਰੀ ਨੂੰ ਕੰਟੇਨਰ ਵਿੱਚ ਦੁਬਾਰਾ ਖੋਲ੍ਹਣ ਦੀ ਸਲਾਹ ਦਿੰਦਾ ਹੈ, ਤਾਂ ਇਸ ਬੇਨਤੀ ਨੂੰ ਅਸਵੀਕਾਰ ਕਰੋ ਤਾਂ ਜੋ ਤੁਸੀਂ ਲੋਕਲ ਇੰਸਟਾਲ ਕੀਤੇ Python ਵਰਜਨ ਦੀ ਵਰਤੋਂ ਕਰ ਸਕੋ।

### ਬ੍ਰਾਊਜ਼ਰ ਵਿੱਚ Jupyter ਦੀ ਵਰਤੋਂ

ਤੁਸੀਂ [Jupyter ਵਾਤਾਵਰਣ](https://jupyter.org?WT.mc_id=academic-105485-koreyst) ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਪ੍ਰੋਜੈਕਟ 'ਤੇ ਕੰਮ ਕਰ ਸਕਦੇ ਹੋ। ਕਲਾਸਿਕ Jupyter ਅਤੇ [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) ਆਟੋ-ਕੰਪਲੀਸ਼ਨ, ਕੋਡ ਹਾਈਲਾਈਟਿੰਗ ਆਦਿ ਵਰਗੇ ਸੁਵਿਧਾਵਾਂ ਨਾਲ ਇੱਕ ਸੁਹਣੇ ਵਿਕਾਸ ਵਾਤਾਵਰਣ ਦੀ ਪੇਸ਼ਕਸ਼ ਕਰਦੇ ਹਨ।

Jupyter ਨੂੰ ਲੋਕਲ ਸ਼ੁਰੂ ਕਰਨ ਲਈ, ਟਰਮੀਨਲ/ਕਮਾਂਡ ਲਾਈਨ 'ਤੇ ਜਾਓ, ਕੋਰਸ ਡਾਇਰੈਕਟਰੀ ਵਿੱਚ ਜਾਓ, ਅਤੇ ਇਹ ਚਲਾਓ:

```bash
jupyter notebook
```

ਜਾਂ

```bash
jupyterhub
```

ਇਹ Jupyter ਇੰਸਟੈਂਸ ਸ਼ੁਰੂ ਕਰੇਗਾ ਅਤੇ ਇਸਨੂੰ ਐਕਸੈਸ ਕਰਨ ਲਈ URL ਕਮਾਂਡ ਲਾਈਨ ਵਿੰਡੋ ਵਿੱਚ ਦਿਖਾਈ ਦੇਵੇਗਾ।

ਜਦੋਂ ਤੁਸੀਂ URL ਨੂੰ ਐਕਸੈਸ ਕਰਦੇ ਹੋ, ਤਾਂ ਤੁਹਾਨੂੰ ਕੋਰਸ ਆਉਟਲਾਈਨ ਦਿਖਾਈ ਦੇਵੇਗੀ ਅਤੇ ਤੁਸੀਂ ਕਿਸੇ ਵੀ `*.ipynb` ਫਾਈਲ 'ਤੇ ਜਾ ਸਕਦੇ ਹੋ। ਉਦਾਹਰਨ ਲਈ, `08-building-search-applications/python/oai-solution.ipynb`।

### ਕੰਟੇਨਰ ਵਿੱਚ ਚਲਾਉਣਾ

ਆਪਣੇ ਕੰਪਿਊਟਰ ਜਾਂ Codespace 'ਤੇ ਸਭ ਕੁਝ ਸੈਟਅੱਪ ਕਰਨ ਦੇ ਬਦਲੇ, ਤੁਸੀਂ [ਕੰਟੇਨਰ](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>) ਦੀ ਵਰਤੋਂ ਕਰ ਸਕਦੇ ਹੋ। ਕੋਰਸ ਰਿਪੋਜ਼ਿਟਰੀ ਵਿੱਚ ਮੌਜੂਦ ਖਾਸ `.devcontainer` ਫੋਲਡਰ VS Code ਨੂੰ ਪ੍ਰੋਜੈਕਟ ਨੂੰ ਇੱਕ ਕੰਟੇਨਰ ਵਿੱਚ ਸੈਟਅੱਪ ਕਰਨ ਦੇ ਯੋਗ ਬਣਾਉਂਦਾ ਹੈ। Codespaces ਤੋਂ ਬਾਹਰ, ਇਸ ਲਈ Docker ਦੀ ਇੰਸਟਾਲੇਸ਼ਨ ਦੀ ਲੋੜ ਹੋਵੇਗੀ, ਅਤੇ ਸੱਚਮੁੱਚ, ਇਸ ਵਿੱਚ ਕੁਝ ਕੰਮ ਸ਼ਾਮਲ ਹੈ, ਇਸ ਲਈ ਅਸੀਂ ਇਸਨੂੰ ਸਿਰਫ ਉਹਨਾਂ ਨੂੰ ਸਿਫਾਰਸ਼ ਕਰਦੇ ਹਾਂ ਜਿਨ੍ਹਾਂ ਨੂੰ ਕੰਟੇਨਰਾਂ ਨਾਲ ਕੰਮ ਕਰਨ ਦਾ ਤਜਰਬਾ ਹੈ।

ਜਦੋਂ ਤੁਸੀਂ GitHub Codespaces ਦੀ ਵਰਤੋਂ ਕਰਦੇ ਹੋ, ਤਾਂ ਆਪਣੀਆਂ API ਕੁੰਜੀਆਂ ਨੂੰ ਸੁਰੱਖਿਅਤ ਰੱਖਣ ਦਾ ਇੱਕ ਵਧੀਆ ਤਰੀਕਾ Codespace Secrets ਦੀ ਵਰਤੋਂ ਕਰਨਾ ਹੈ। ਕਿਰਪਾ ਕਰਕੇ [Codespaces ਸਿਕ੍ਰੇਟ ਮੈਨੇਜਮੈਂਟ](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst) ਗਾਈਡ ਦੀ ਪਾਲਣਾ ਕਰੋ ਇਸ ਬਾਰੇ ਹੋਰ ਜਾਣਨ ਲਈ।

## ਪਾਠ ਅਤੇ ਤਕਨੀਕੀ ਲੋੜਾਂ

ਕੋਰਸ ਵਿੱਚ 6 ਕਾਨਸੈਪਟ ਪਾਠ ਅਤੇ 6 ਕੋਡਿੰਗ ਪਾਠ ਹਨ।

ਕੋਡਿੰਗ ਪਾਠਾਂ ਲਈ, ਅਸੀਂ Azure OpenAI Service ਦੀ ਵਰਤੋਂ ਕਰ ਰਹੇ ਹਾਂ। ਇਸ ਕੋਡ ਨੂੰ ਚਲਾਉਣ ਲਈ ਤੁਹਾਨੂੰ Azure OpenAI ਸੇਵਾ ਅਤੇ ਇੱਕ API ਕੁੰਜੀ ਦੀ ਪਹੁੰਚ ਦੀ ਲੋੜ ਹੋਵੇਗੀ। ਤੁਸੀਂ [ਇਹ ਅਰਜ਼ੀ ਪੂਰੀ ਕਰਕੇ](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst) ਪਹੁੰਚ ਪ੍ਰਾਪਤ ਕਰਨ ਲਈ ਅਰਜ਼ੀ ਦੇ ਸਕਦੇ ਹੋ।

ਜਦੋਂ ਤੁਸੀਂ ਆਪਣੀ ਅਰਜ਼ੀ ਦੀ ਪ੍ਰਕਿਰਿਆ ਦੀ ਉਡੀਕ ਕਰ ਰਹੇ ਹੋ, ਹਰ ਕੋਡਿੰਗ ਪਾਠ ਵਿੱਚ ਇੱਕ `README.md` ਫਾਈਲ ਵੀ ਸ਼ਾਮਲ ਹੈ ਜਿੱਥੇ ਤੁਸੀਂ ਕੋਡ ਅਤੇ ਆਉਟਪੁੱਟ ਵੇਖ ਸਕਦੇ ਹੋ।

## ਪਹਿਲੀ ਵਾਰ Azure OpenAI ਸੇਵਾ ਦੀ ਵਰਤੋਂ ਕਰਨਾ

ਜੇਕਰ ਇਹ ਪਹਿਲੀ ਵਾਰ ਹੈ ਕਿ ਤੁਸੀਂ Azure OpenAI ਸੇਵਾ ਨਾਲ ਕੰਮ ਕਰ ਰਹੇ ਹੋ, ਤਾਂ ਕਿਰਪਾ ਕਰਕੇ [Azure OpenAI ਸੇਵਾ ਰਿਸੋਰਸ ਬਣਾਉਣ ਅਤੇ ਡਿਪਲੌਇ ਕਰਨ](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst) ਬਾਰੇ ਇਸ ਗਾਈਡ ਦੀ ਪਾਲਣਾ ਕਰੋ।

## ਪਹਿਲੀ ਵਾਰ OpenAI API ਦੀ ਵਰਤੋਂ ਕਰਨਾ

ਜੇਕਰ ਇਹ ਪਹਿਲੀ ਵਾਰ ਹੈ ਕਿ ਤੁਸੀਂ OpenAI API ਨਾਲ ਕੰਮ ਕਰ ਰਹੇ ਹੋ, ਤਾਂ ਕਿਰਪਾ ਕਰਕੇ [ਇੰਟਰਫੇਸ ਬਣਾਉਣ ਅਤੇ ਵਰਤਣ](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst) ਬਾਰੇ ਗਾਈਡ ਦੀ ਪਾਲਣਾ ਕਰੋ।

## ਹੋਰ ਸਿੱਖਣ ਵਾਲਿਆਂ ਨੂੰ ਮਿਲੋ

ਅਸੀਂ ਆਪਣੇ ਅਧਿਕਾਰਕ [AI Community Discord ਸਰਵਰ](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) ਵਿੱਚ ਹੋਰ ਸਿੱਖਣ ਵਾਲਿਆਂ ਨੂੰ ਮਿਲਣ ਲਈ ਚੈਨਲ ਬਣਾਏ ਹਨ। ਇਹ ਜਨਰੇਟਿਵ AI ਵਿੱਚ ਲੈਵਲ ਅੱਪ ਕਰਨ ਦੀ ਖੋਜ ਕਰ ਰਹੇ ਹੋਰ ਸਮਾਨ ਵਿਚਾਰਧਾਰਾ ਵਾਲੇ ਉਦਯੋਗਪਤੀਆਂ, ਨਿਰਮਾਤਾ, ਵਿਦ
ਹੁਣ ਜਦੋਂ ਤੁਸੀਂ ਇਸ ਕੋਰਸ ਨੂੰ ਪੂਰਾ ਕਰਨ ਲਈ ਲੋੜੀਂਦੇ ਕਦਮ ਪੂਰੇ ਕਰ ਲਏ ਹਨ, ਤਾਂ ਆਓ ਸ਼ੁਰੂ ਕਰੀਏ [ਜਨਰੇਟਿਵ AI ਅਤੇ LLMs ਦਾ ਪਰਿਚਯ](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst) ਪ੍ਰਾਪਤ ਕਰਕੇ।

---

**ਅਸਵੀਕਰਤਾ**:  
ਇਹ ਦਸਤਾਵੇਜ਼ AI ਅਨੁਵਾਦ ਸੇਵਾ [Co-op Translator](https://github.com/Azure/co-op-translator) ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਅਨੁਵਾਦ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀ ਹੋਣ ਦੀ ਕੋਸ਼ਿਸ਼ ਕਰਦੇ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਦਿਓ ਕਿ ਸਵੈਚਾਲਿਤ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸੁੱਤੀਆਂ ਹੋ ਸਕਦੀਆਂ ਹਨ। ਮੂਲ ਦਸਤਾਵੇਜ਼, ਜੋ ਇਸਦੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਹੈ, ਨੂੰ ਅਧਿਕਾਰਤ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਮਹੱਤਵਪੂਰਨ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਤੋਂ ਪੈਦਾ ਹੋਣ ਵਾਲੇ ਕਿਸੇ ਵੀ ਗਲਤਫਹਿਮੀ ਜਾਂ ਗਲਤ ਵਿਆਖਿਆ ਲਈ ਅਸੀਂ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।