<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-17T18:36:40+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "th"
}
-->
# เริ่มต้นกับคอร์สนี้

เรารู้สึกตื่นเต้นมากที่คุณจะเริ่มต้นคอร์สนี้ และได้เห็นสิ่งที่คุณจะสร้างสรรค์ด้วย Generative AI!

เพื่อให้คุณประสบความสำเร็จ หน้านี้จะอธิบายขั้นตอนการตั้งค่า ข้อกำหนดทางเทคนิค และแหล่งข้อมูลที่คุณสามารถขอความช่วยเหลือได้หากจำเป็น

## ขั้นตอนการตั้งค่า

เพื่อเริ่มต้นคอร์สนี้ คุณจำเป็นต้องทำตามขั้นตอนต่อไปนี้

### 1. Fork Repo นี้

[Fork Repo ทั้งหมดนี้](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) ไปยังบัญชี GitHub ของคุณเอง เพื่อให้คุณสามารถแก้ไขโค้ดและทำแบบฝึกหัดได้ นอกจากนี้คุณยังสามารถ [star (🌟) Repo นี้](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) เพื่อค้นหา Repo นี้และ Repo ที่เกี่ยวข้องได้ง่ายขึ้น

### 2. สร้าง Codespace

เพื่อหลีกเลี่ยงปัญหาเกี่ยวกับ Dependency เมื่อรันโค้ด เราแนะนำให้คุณรันคอร์สนี้ใน [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst)

ใน Fork ของคุณ: **Code -> Codespaces -> New on main**

![หน้าต่างแสดงปุ่มสำหรับสร้าง Codespace](../../../00-course-setup/images/who-will-pay.webp)

#### 2.1 เพิ่ม Secret

1. ⚙️ ไอคอนรูปเฟือง -> Command Pallete -> Codespaces : Manage user secret -> Add a new secret  
2. ตั้งชื่อ OPENAI_API_KEY วางคีย์ของคุณ แล้วกด Save

### 3. ทำอะไรต่อ?

| ฉันต้องการ…         | ไปที่…                                                                 |
|---------------------|-------------------------------------------------------------------------|
| เริ่มบทเรียนที่ 1   | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)     |
| ทำงานแบบออฟไลน์    | [`setup-local.md`](02-setup-local.md)                                   |
| ตั้งค่าผู้ให้บริการ LLM | [`providers.md`](03-providers.md)                                        |
| พบปะผู้เรียนคนอื่น  | [เข้าร่วม Discord ของเรา](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)   |

## การแก้ไขปัญหา

| อาการ                                    | วิธีแก้ไข                                                      |
|------------------------------------------|-----------------------------------------------------------------|
| การสร้าง Container ใช้เวลานานเกิน 10 นาที | **Codespaces ➜ “Rebuild Container”**                            |
| `python: command not found`              | Terminal ไม่ได้เชื่อมต่อ; คลิก **+** ➜ *bash*                   |
| `401 Unauthorized` จาก OpenAI            | `OPENAI_API_KEY` ผิดหรือหมดอายุ                                |
| VS Code แสดง “Dev container mounting…”   | รีเฟรชแท็บเบราว์เซอร์—บางครั้ง Codespaces อาจหลุดการเชื่อมต่อ |
| Kernel ของ Notebook หายไป                | เมนู Notebook ➜ **Kernel ▸ Select Kernel ▸ Python 3**           |

   ระบบ Unix-based:

   ```bash
   touch .env
   ```
  
   Windows:

   ```cmd
   echo . > .env
   ```
  
3. **แก้ไขไฟล์ `.env`**: เปิดไฟล์ `.env` ในโปรแกรมแก้ไขข้อความ (เช่น VS Code, Notepad++ หรือโปรแกรมอื่น ๆ) เพิ่มบรรทัดต่อไปนี้ในไฟล์ โดยแทนที่ `your_github_token_here` ด้วย GitHub token ของคุณ:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```
  
4. **บันทึกไฟล์**: บันทึกการเปลี่ยนแปลงและปิดโปรแกรมแก้ไขข้อความ

5. **ติดตั้ง `python-dotenv`**: หากคุณยังไม่ได้ติดตั้ง คุณจำเป็นต้องติดตั้งแพ็กเกจ `python-dotenv` เพื่อโหลดตัวแปรสภาพแวดล้อมจากไฟล์ `.env` ไปยังแอปพลิเคชัน Python ของคุณ คุณสามารถติดตั้งได้โดยใช้ `pip`:

   ```bash
   pip install python-dotenv
   ```
  
6. **โหลดตัวแปรสภาพแวดล้อมในสคริปต์ Python ของคุณ**: ในสคริปต์ Python ของคุณ ใช้แพ็กเกจ `python-dotenv` เพื่อโหลดตัวแปรสภาพแวดล้อมจากไฟล์ `.env`:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```
  
แค่นี้เอง! คุณได้สร้างไฟล์ `.env` เพิ่ม GitHub token ของคุณ และโหลดมันเข้าสู่แอปพลิเคชัน Python ของคุณเรียบร้อยแล้ว

## วิธีรันโค้ดในเครื่องของคุณ

เพื่อรันโค้ดในเครื่องของคุณ คุณจำเป็นต้องมี [Python เวอร์ชันใดก็ได้ติดตั้ง](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst)

จากนั้นเพื่อใช้งาน Repository คุณต้อง Clone มัน:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```
  
เมื่อคุณตรวจสอบทุกอย่างแล้ว คุณก็สามารถเริ่มต้นได้เลย!

## ขั้นตอนเพิ่มเติม

### การติดตั้ง Miniconda

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) เป็นตัวติดตั้งน้ำหนักเบาสำหรับการติดตั้ง [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python และแพ็กเกจบางตัว  
Conda เองเป็นตัวจัดการแพ็กเกจที่ทำให้การตั้งค่าและการสลับระหว่าง [**virtual environments**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) และแพ็กเกจต่าง ๆ เป็นเรื่องง่าย นอกจากนี้ยังมีประโยชน์สำหรับการติดตั้งแพ็กเกจที่ไม่สามารถใช้ได้ผ่าน `pip`

คุณสามารถทำตาม [คู่มือการติดตั้ง MiniConda](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst) เพื่อเริ่มต้นใช้งาน

เมื่อคุณติดตั้ง Miniconda แล้ว คุณต้อง Clone [Repository](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) (หากคุณยังไม่ได้ทำ)

ต่อไป คุณต้องสร้าง Virtual Environment เพื่อทำสิ่งนี้ด้วย Conda ให้สร้างไฟล์ Environment ใหม่ (_environment.yml_) หากคุณกำลังทำตามใน Codespaces ให้สร้างไฟล์นี้ในไดเรกทอรี `.devcontainer` ดังนั้น `.devcontainer/environment.yml`

ไปที่ไฟล์ Environment ของคุณและเพิ่มโค้ดด้านล่าง:

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
  
หากคุณพบข้อผิดพลาดในการใช้ Conda คุณสามารถติดตั้ง Microsoft AI Libraries ด้วยคำสั่งต่อไปนี้ใน Terminal:

```
conda install -c microsoft azure-ai-ml
```
  
ไฟล์ Environment ระบุ Dependencies ที่เราต้องการ `<environment-name>` หมายถึงชื่อที่คุณต้องการใช้สำหรับ Conda Environment และ `<python-version>` คือเวอร์ชันของ Python ที่คุณต้องการใช้ เช่น `3` ซึ่งเป็นเวอร์ชันหลักล่าสุดของ Python

เมื่อเสร็จแล้ว คุณสามารถสร้าง Conda Environment ของคุณได้โดยรันคำสั่งด้านล่างใน Command Line/Terminal

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```
  
ดู [คู่มือ Conda environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst) หากคุณพบปัญหา

### การใช้ Visual Studio Code กับส่วนขยาย Python

เราแนะนำให้ใช้ [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) พร้อมกับ [ส่วนขยาย Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) สำหรับคอร์สนี้ อย่างไรก็ตาม นี่เป็นเพียงคำแนะนำ ไม่ใช่ข้อบังคับ

> **หมายเหตุ**: โดยการเปิด Repository คอร์สใน VS Code คุณมีตัวเลือกในการตั้งค่าโปรเจกต์ใน Container เนื่องจาก [ไดเรกทอรี `.devcontainer` พิเศษ](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) ที่อยู่ใน Repository คอร์สนี้ รายละเอียดเพิ่มเติมจะกล่าวถึงในภายหลัง

> **หมายเหตุ**: เมื่อคุณ Clone และเปิดไดเรกทอรีใน VS Code มันจะเสนอให้คุณติดตั้งส่วนขยาย Python โดยอัตโนมัติ

> **หมายเหตุ**: หาก VS Code แนะนำให้คุณเปิด Repository ใน Container ให้ปฏิเสธคำขอนี้เพื่อใช้ Python เวอร์ชันที่ติดตั้งในเครื่อง

### การใช้ Jupyter ในเบราว์เซอร์

คุณสามารถทำงานในโปรเจกต์โดยใช้ [Jupyter environment](https://jupyter.org?WT.mc_id=academic-105485-koreyst) ในเบราว์เซอร์ของคุณได้เช่นกัน ทั้ง Jupyter แบบคลาสสิกและ [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) มอบประสบการณ์การพัฒนาที่ดีพร้อมฟีเจอร์ เช่น การเติมคำอัตโนมัติ การไฮไลต์โค้ด เป็นต้น

เพื่อเริ่มต้น Jupyter ในเครื่อง ให้ไปที่ Terminal/Command Line ไปยังไดเรกทอรีคอร์ส และรันคำสั่ง:

```bash
jupyter notebook
```
  
หรือ

```bash
jupyterhub
```
  
นี่จะเริ่มต้น Jupyter และ URL สำหรับการเข้าถึงจะปรากฏในหน้าต่าง Command Line

เมื่อคุณเข้าถึง URL คุณจะเห็นโครงร่างคอร์สและสามารถไปยังไฟล์ `*.ipynb` ใดก็ได้ เช่น `08-building-search-applications/python/oai-solution.ipynb`

### การรันใน Container

อีกทางเลือกหนึ่งในการตั้งค่าทุกอย่างในเครื่องของคุณหรือ Codespace คือการใช้ [Container](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>) ไดเรกทอรี `.devcontainer` พิเศษใน Repository คอร์สทำให้ VS Code สามารถตั้งค่าโปรเจกต์ใน Container ได้ นอกเหนือจาก Codespaces สิ่งนี้จะต้องติดตั้ง Docker และค่อนข้างซับซ้อน ดังนั้นเราขอแนะนำเฉพาะผู้ที่มีประสบการณ์ในการทำงานกับ Container

หนึ่งในวิธีที่ดีที่สุดในการรักษาความปลอดภัย API Key ของคุณเมื่อใช้ GitHub Codespaces คือการใช้ Codespace Secrets โปรดทำตาม [คู่มือการจัดการ Secrets ใน Codespaces](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst) เพื่อเรียนรู้เพิ่มเติมเกี่ยวกับเรื่องนี้

## บทเรียนและข้อกำหนดทางเทคนิค

คอร์สนี้มีบทเรียนแนวคิด 6 บท และบทเรียนการเขียนโค้ด 6 บท

สำหรับบทเรียนการเขียนโค้ด เราใช้บริการ Azure OpenAI Service คุณจะต้องเข้าถึงบริการ Azure OpenAI และมี API Key เพื่อรันโค้ดนี้ คุณสามารถสมัครเพื่อขอเข้าถึงได้โดย [กรอกแบบฟอร์มนี้](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst)

ในขณะที่คุณรอการอนุมัติการสมัคร แต่ละบทเรียนการเขียนโค้ดยังมีไฟล์ `README.md` ที่คุณสามารถดูโค้ดและผลลัพธ์ได้

## การใช้บริการ Azure OpenAI เป็นครั้งแรก

หากนี่เป็นครั้งแรกที่คุณทำงานกับบริการ Azure OpenAI โปรดทำตามคู่มือเกี่ยวกับวิธี [สร้างและปรับใช้ทรัพยากรบริการ Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst)

## การใช้ OpenAI API เป็นครั้งแรก

หากนี่เป็นครั้งแรกที่คุณทำงานกับ OpenAI API โปรดทำตามคู่มือเกี่ยวกับวิธี [สร้างและใช้ Interface](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst)

## พบปะผู้เรียนคนอื่น

เราได้สร้างช่องทางใน [เซิร์ฟเวอร์ Discord ชุมชน AI อย่างเป็นทางการ](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst) เพื่อให้คุณได้พบปะกับผู้เรียนคนอื่น ๆ นี่เป็นวิธีที่ดีในการสร้างเครือข่ายกับผู้ประกอบการ ผู้สร้าง นักเรียน และผู้ที่ต้องการพัฒนาทักษะใน Generative AI

[![เข้าร่วมช่อง Discord](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

ทีมโปรเจกต์จะอยู่ในเซิร์ฟเวอร์ Discord นี้เพื่อช่วยเหลือผู้เรียนทุกคน

## การมีส่วนร่วม

คอร์สนี้เป็นโครงการโอเพ่นซอร์ส หากคุณเห็นจุดที่สามารถปรับปรุงหรือพบปัญหา โปรดสร้าง [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) หรือบันทึก [GitHub issue](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst)

ทีมโปรเจกต์จะติดตามการมีส่วนร่วมทั้งหมด การมีส่วนร่วมในโอเพ่นซอร์สเป็นวิธีที่ยอดเยี่ยมในการสร้างอาชีพใน Generative AI

การมีส่วนร่วมส่วนใหญ่ต้องการให้คุณยอมรับ Contributor License Agreement (CLA) ซึ่งระบุว่าคุณมีสิทธิ์และให้สิทธิ์เราในการใช้การมีส่วนร่วมของคุณ สำหรับรายละเอียดเพิ่มเติม โปรดเยี่ยมชม [เว็บไซต์ CLA, Contributor License Agreement](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst)

สำคัญ: เมื่อแปลข้อความใน Repo นี้ โปรดตรวจสอบให้แน่ใจว่าคุณไม่ได้ใช้การแปลด้วยเครื่อง เราจะตรวจสอบการแปลผ่านชุมชน ดังนั้นโปรดอาสาแปลเฉพาะในภาษาที่คุณมีความชำนาญ

เมื่อคุณส่ง Pull Request CLA-bot จะตรวจสอบโดยอัตโนมัติว่าคุณจำเป็นต้องให้ CLA หรือไม่ และจะตกแต่ง PR ตามความเหมาะสม (เช่น เพิ่มป้ายกำกับหรือความคิดเห็น) เพียงทำตามคำแนะนำที่บอทให้ คุณจะต้องทำสิ่งนี้เพียงครั้งเดียวสำหรับทุก Repository ที่ใช้ CLA ของเรา

โครงการนี้ได้นำ [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst) มาใช้ สำหรับข้อมูลเพิ่มเติม โปรดอ่าน Code of Conduct FAQ หรือ ติดต่อ [Email opencode](opencode@microsoft.com) หากมีคำถามหรือความคิดเห็นเพิ่มเติม

## มาเริ่มกันเลย!
ตอนนี้คุณได้ทำตามขั้นตอนที่จำเป็นเพื่อจบหลักสูตรนี้แล้ว มาเริ่มต้นกันด้วยการ [แนะนำเกี่ยวกับ Generative AI และ LLMs](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst)

---

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษา AI [Co-op Translator](https://github.com/Azure/co-op-translator) แม้ว่าเราจะพยายามให้การแปลมีความถูกต้อง แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่ถูกต้อง เอกสารต้นฉบับในภาษาดั้งเดิมควรถือเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลสำคัญ ขอแนะนำให้ใช้บริการแปลภาษามนุษย์ที่เป็นมืออาชีพ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความผิดที่เกิดจากการใช้การแปลนี้