<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "238cde5c90363d70ecc939569378da51",
  "translation_date": "2025-10-17T16:20:55+00:00",
  "source_file": "09-building-image-applications/README.md",
  "language_code": "tr"
}
-->
# Görüntü Oluşturma Uygulamaları Oluşturma

[![Görüntü Oluşturma Uygulamaları Oluşturma](../../../translated_images/09-lesson-banner.906e408c741f44112ff5da17492a30d3872abb52b8530d6506c2631e86e704d0.tr.png)](https://youtu.be/B5VP0_J7cs8?si=5P3L5o7F_uS_QcG9)

Büyük Dil Modelleri (LLM'ler) yalnızca metin oluşturma ile sınırlı değildir. Metin açıklamalarından görüntü oluşturmak da mümkündür. Görüntülerin bir modalite olarak kullanılması, MedTech, mimarlık, turizm, oyun geliştirme gibi birçok alanda oldukça faydalı olabilir. Bu bölümde, en popüler iki görüntü oluşturma modeli olan DALL-E ve Midjourney'i inceleyeceğiz.

## Giriş

Bu derste şunları ele alacağız:

- Görüntü oluşturma ve neden faydalı olduğu.
- DALL-E ve Midjourney, ne oldukları ve nasıl çalıştıkları.
- Görüntü oluşturma uygulaması nasıl oluşturulur.

## Öğrenme Hedefleri

Bu dersi tamamladıktan sonra şunları yapabileceksiniz:

- Görüntü oluşturma uygulaması oluşturmak.
- Uygulamanız için meta istemlerle sınırlar belirlemek.
- DALL-E ve Midjourney ile çalışmak.

## Neden bir görüntü oluşturma uygulaması oluşturmalısınız?

Görüntü oluşturma uygulamaları, Üretken Yapay Zeka'nın yeteneklerini keşfetmek için harika bir yoldur. Örneğin şu amaçlarla kullanılabilirler:

- **Görüntü düzenleme ve sentezleme**. Görüntü düzenleme ve görüntü sentezleme gibi çeşitli kullanım durumları için görüntüler oluşturabilirsiniz.

- **Çeşitli endüstrilere uygulanabilir**. MedTech, Turizm, Oyun geliştirme gibi çeşitli endüstriler için görüntüler oluşturmak için de kullanılabilirler.

## Senaryo: Edu4All

Bu ders kapsamında, Edu4All adlı girişimimizle çalışmaya devam edeceğiz. Öğrenciler, değerlendirmeleri için görüntüler oluşturacaklar; hangi görüntülerin oluşturulacağı tamamen öğrencilere bağlıdır. Örneğin, kendi masalları için illüstrasyonlar oluşturabilir, hikayeleri için yeni bir karakter yaratabilir veya fikirlerini ve kavramlarını görselleştirmelerine yardımcı olabilirler.

Edu4All öğrencilerinin sınıfta anıtlar üzerinde çalışırken oluşturabilecekleri örneklerden biri:

![Edu4All girişimi, anıtlar üzerine sınıf, Eyfel Kulesi](../../../translated_images/startup.94d6b79cc4bb3f5afbf6e2ddfcf309aa5d1e256b5f30cc41d252024eaa9cc5dc.tr.png)

şu tür bir istem kullanarak:

> "Sabahın erken saatlerinde güneş ışığında Eyfel Kulesi'nin yanında bir köpek"

## DALL-E ve Midjourney nedir?

[DALL-E](https://openai.com/dall-e-2?WT.mc_id=academic-105485-koreyst) ve [Midjourney](https://www.midjourney.com/?WT.mc_id=academic-105485-koreyst), metin istemleri kullanarak görüntü oluşturmanıza olanak tanıyan en popüler iki görüntü oluşturma modelidir.

### DALL-E

Öncelikle DALL-E ile başlayalım. Bu, metin açıklamalarından görüntü oluşturan bir Üretken Yapay Zeka modelidir.

> [DALL-E, CLIP ve diffused attention adlı iki modelin birleşimidir](https://towardsdatascience.com/openais-dall-e-and-clip-101-a-brief-introduction-3a4367280d4e?WT.mc_id=academic-105485-koreyst).

- **CLIP**, görüntüler ve metinlerden sayısal veri temsilleri (embedding) oluşturan bir modeldir.

- **Diffused attention**, embeddinglerden görüntü oluşturan bir modeldir. DALL-E, bir görüntü ve metin veri seti üzerinde eğitilmiştir ve metin açıklamalarından görüntü oluşturmak için kullanılabilir. Örneğin, DALL-E bir şapka takmış kedi veya mohawk saçlı bir köpek görüntüsü oluşturmak için kullanılabilir.

### Midjourney

Midjourney, DALL-E'ye benzer şekilde çalışır; metin istemlerinden görüntüler oluşturur. Midjourney, "şapka takmış bir kedi" veya "mohawk saçlı bir köpek" gibi istemler kullanılarak görüntüler oluşturmak için kullanılabilir.

![Midjourney tarafından oluşturulan görüntü, mekanik güvercin](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8c/Rupert_Breheny_mechanical_dove_eca144e7-476d-4976-821d-a49c408e4f36.png/440px-Rupert_Breheny_mechanical_dove_eca144e7-476d-4976-821d-a49c408e4f36.png?WT.mc_id=academic-105485-koreyst)
_Wikipedia'dan alınan görsel, Midjourney tarafından oluşturulmuş görüntü_

## DALL-E ve Midjourney nasıl çalışır?

Öncelikle, [DALL-E](https://arxiv.org/pdf/2102.12092.pdf?WT.mc_id=academic-105485-koreyst). DALL-E, _autoregressive transformer_ ile transformer mimarisine dayalı bir Üretken Yapay Zeka modelidir.

Bir _autoregressive transformer_, bir modelin metin açıklamalarından görüntü oluşturma şeklini tanımlar; bir pikseli birer birer oluşturur ve ardından oluşturulan pikselleri bir sonraki pikseli oluşturmak için kullanır. Sinir ağında birden fazla katmandan geçerek görüntü tamamlanır.

Bu süreçle DALL-E, oluşturduğu görüntüdeki nitelikleri, nesneleri, özellikleri ve daha fazlasını kontrol eder. Ancak, DALL-E 2 ve 3, oluşturulan görüntü üzerinde daha fazla kontrol sağlar.

## İlk görüntü oluşturma uygulamanızı oluşturma

Peki bir görüntü oluşturma uygulaması oluşturmak için neye ihtiyacınız var? Şu kütüphanelere ihtiyacınız olacak:

- **python-dotenv**, gizli bilgilerinizi _.env_ dosyasında koddan uzak tutmanız için bu kütüphaneyi kullanmanız şiddetle tavsiye edilir.
- **openai**, OpenAI API ile etkileşim kurmak için kullanacağınız kütüphane.
- **pillow**, Python'da görüntülerle çalışmak için.
- **requests**, HTTP istekleri yapmanıza yardımcı olur.

## Azure OpenAI modelini oluşturma ve dağıtma

Henüz yapmadıysanız, [Microsoft Learn](https://learn.microsoft.com/azure/ai-foundry/openai/how-to/create-resource?pivots=web-portal) sayfasındaki talimatları izleyerek bir Azure OpenAI kaynağı ve model oluşturun. Model olarak DALL-E 3'ü seçin.

## Uygulamayı oluşturma

1. _.env_ adlı bir dosya oluşturun ve şu içeriği ekleyin:

   ```text
   AZURE_OPENAI_ENDPOINT=<your endpoint>
   AZURE_OPENAI_API_KEY=<your key>
   AZURE_OPENAI_DEPLOYMENT="dall-e-3"
   ```

   Bu bilgiyi Azure OpenAI Foundry Portal'daki "Deployments" bölümünde bulabilirsiniz.

1. Yukarıdaki kütüphaneleri _requirements.txt_ adlı bir dosyada şu şekilde toplayın:

   ```text
   python-dotenv
   openai
   pillow
   requests
   ```

1. Ardından sanal bir ortam oluşturun ve kütüphaneleri yükleyin:

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```

   Windows için sanal ortam oluşturma ve etkinleştirme komutları şunlardır:

   ```bash
   python3 -m venv venv
   venv\Scripts\activate.bat
   ```

1. _app.py_ adlı bir dosyaya şu kodu ekleyin:

    ```python
    import openai
    import os
    import requests
    from PIL import Image
    import dotenv
    from openai import OpenAI, AzureOpenAI
    
    # import dotenv
    dotenv.load_dotenv()
    
    # configure Azure OpenAI service client 
    client = AzureOpenAI(
      azure_endpoint = os.environ["AZURE_OPENAI_ENDPOINT"],
      api_key=os.environ['AZURE_OPENAI_API_KEY'],
      api_version = "2024-02-01"
      )
    try:
        # Create an image by using the image generation API
        generation_response = client.images.generate(
                                prompt='Bunny on horse, holding a lollipop, on a foggy meadow where it grows daffodils',
                                size='1024x1024', n=1,
                                model=os.environ['AZURE_OPENAI_DEPLOYMENT']
                              )

        # Set the directory for the stored image
        image_dir = os.path.join(os.curdir, 'images')

        # If the directory doesn't exist, create it
        if not os.path.isdir(image_dir):
            os.mkdir(image_dir)

        # Initialize the image path (note the filetype should be png)
        image_path = os.path.join(image_dir, 'generated-image.png')

        # Retrieve the generated image
        image_url = generation_response.data[0].url  # extract image URL from response
        generated_image = requests.get(image_url).content  # download the image
        with open(image_path, "wb") as image_file:
            image_file.write(generated_image)

        # Display the image in the default image viewer
        image = Image.open(image_path)
        image.show()

    # catch exceptions
    except openai.InvalidRequestError as err:
        print(err)
   ```

Bu kodu açıklayalım:

- Öncelikle, OpenAI kütüphanesi, dotenv kütüphanesi, requests kütüphanesi ve Pillow kütüphanesi dahil olmak üzere ihtiyacımız olan kütüphaneleri içe aktarıyoruz.

  ```python
  import openai
  import os
  import requests
  from PIL import Image
  import dotenv
  ```

- Daha sonra, _.env_ dosyasından ortam değişkenlerini yüklüyoruz.

  ```python
  # import dotenv
  dotenv.load_dotenv()
  ```

- Ardından, Azure OpenAI hizmeti istemcisini yapılandırıyoruz.

  ```python
  # Get endpoint and key from environment variables
  client = AzureOpenAI(
      azure_endpoint = os.environ["AZURE_OPENAI_ENDPOINT"],
      api_key=os.environ['AZURE_OPENAI_API_KEY'],
      api_version = "2024-02-01"
      )
  ```

- Son olarak, görüntüyü oluşturuyoruz:

  ```python
  # Create an image by using the image generation API
  generation_response = client.images.generate(
                        prompt='Bunny on horse, holding a lollipop, on a foggy meadow where it grows daffodils',
                        size='1024x1024', n=1,
                        model=os.environ['AZURE_OPENAI_DEPLOYMENT']
                      )
  ```

  Yukarıdaki kod, oluşturulan görüntünün URL'sini içeren bir JSON nesnesiyle yanıt verir. Bu URL'yi kullanarak görüntüyü indirip bir dosyaya kaydedebiliriz.

- Son olarak, görüntüyü açar ve standart görüntü görüntüleyici ile görüntüleriz:

  ```python
  image = Image.open(image_path)
  image.show()
  ```

### Görüntü oluşturma hakkında daha fazla bilgi

Görüntüyü oluşturan koda daha detaylı bakalım:

   ```python
     generation_response = client.images.generate(
                               prompt='Bunny on horse, holding a lollipop, on a foggy meadow where it grows daffodils',
                               size='1024x1024', n=1,
                               model=os.environ['AZURE_OPENAI_DEPLOYMENT']
                           )
   ```

- **prompt**, görüntüyü oluşturmak için kullanılan metin istemidir. Bu durumda, "Sisli bir çayırda nergislerin yetiştiği bir alanda lolipop tutan bir atın üzerindeki tavşan" istemini kullanıyoruz.
- **size**, oluşturulan görüntünün boyutudur. Bu durumda, 1024x1024 piksel boyutunda bir görüntü oluşturuyoruz.
- **n**, oluşturulan görüntü sayısıdır. Bu durumda, iki görüntü oluşturuyoruz.
- **temperature**, Üretken Yapay Zeka modelinin çıktısının rastgeleliğini kontrol eden bir parametredir. Sıcaklık, 0 ile 1 arasında bir değerdir; burada 0, çıktının deterministik olduğu ve 1, çıktının rastgele olduğu anlamına gelir. Varsayılan değer 0.7'dir.

Görüntülerle yapabileceğiniz daha fazla şey var ve bunları bir sonraki bölümde ele alacağız.

## Görüntü oluşturmanın ek yetenekleri

Şimdiye kadar, Python'da birkaç satır kodla bir görüntü oluşturmayı nasıl başardığımızı gördünüz. Ancak, görüntülerle yapabileceğiniz daha fazla şey var.

Ayrıca şunları yapabilirsiniz:

- **Düzenlemeler yapma**. Mevcut bir görüntüye bir maske ve bir istem sağlayarak bir görüntüyü değiştirebilirsiniz. Örneğin, bir görüntünün bir kısmına bir şey ekleyebilirsiniz. Tavşan görüntümüzü hayal edin; tavşana bir şapka ekleyebilirsiniz. Bunu, görüntüyü, bir maske (değişiklik yapılacak alanı belirleyen) ve yapılması gerekeni belirten bir metin istemi sağlayarak yapabilirsiniz. 
> Not: Bu özellik DALL-E 3'te desteklenmemektedir.

İşte GPT Image kullanılarak yapılmış bir örnek:

   ```python
   response = client.images.edit(
       model="gpt-image-1",
       image=open("sunlit_lounge.png", "rb"),
       mask=open("mask.png", "rb"),
       prompt="A sunlit indoor lounge area with a pool containing a flamingo"
   )
   image_url = response.data[0].url
   ```

  Temel görüntü yalnızca havuzlu salonu içerirken, son görüntüde bir flamingo olacaktır:

<div style="display: flex; justify-content: space-between; align-items: center; margin: 20px 0;">
  <img src="../../../translated_images/sunlit_lounge.a75a0cb61749db0eddc1820c30a5fa9a3a9f48518cd7c8df4c2073e8c793bbb7.tr.png" style="width: 30%; max-width: 200px; height: auto;">
  <img src="../../../translated_images/mask.1b2976ccec9e011eaac6cd3697d804a22ae6debba7452da6ba3bebcaa9c54ff0.tr.png" style="width: 30%; max-width: 200px; height: auto;">
  <img src="../../../translated_images/sunlit_lounge_result.76ae02957c0bbeb860f1efdb42dd7f450ea01c6ae6cd70ad5ade4bab1a545d51.tr.png" style="width: 30%; max-width: 200px; height: auto;">
</div>

- **Varyasyonlar oluşturma**. Buradaki fikir, mevcut bir görüntüyü alıp farklı varyasyonlar oluşturmanızdır. Bir varyasyon oluşturmak için bir görüntü ve bir metin istemi sağlayarak şu şekilde kod yazabilirsiniz:

  ```python
  response = openai.Image.create_variation(
    image=open("bunny-lollipop.png", "rb"),
    n=1,
    size="1024x1024"
  )
  image_url = response['data'][0]['url']
  ```

  > Not: Bu özellik yalnızca OpenAI'de desteklenmektedir.

## Sıcaklık

Sıcaklık, Üretken Yapay Zeka modelinin çıktısının rastgeleliğini kontrol eden bir parametredir. Sıcaklık, 0 ile 1 arasında bir değerdir; burada 0, çıktının deterministik olduğu ve 1, çıktının rastgele olduğu anlamına gelir. Varsayılan değer 0.7'dir.

Sıcaklığın nasıl çalıştığını görmek için bu istemi iki kez çalıştırarak bir örneğe bakalım:

> İstem: "Sisli bir çayırda nergislerin yetiştiği bir alanda lolipop tutan bir atın üzerindeki tavşan"

![Lolipop tutan bir atın üzerindeki tavşan, versiyon 1](../../../translated_images/v1-generated-image.a295cfcffa3c13c2432eb1e41de7e49a78c814000fb1b462234be24b6e0db7ea.tr.png)

Şimdi aynı istemi tekrar çalıştırarak aynı görüntüyü iki kez alamayacağımızı görelim:

![Atın üzerindeki tavşan görüntüsü](../../../translated_images/v2-generated-image.33f55a3714efe61dc19622c869ba6cd7d6e6de562e26e95b5810486187aace39.tr.png)

Gördüğünüz gibi, görüntüler benzer ancak aynı değil. Şimdi sıcaklık değerini 0.1'e değiştirip ne olduğunu görelim:

```python
 generation_response = client.images.create(
        prompt='Bunny on horse, holding a lollipop, on a foggy meadow where it grows daffodils',    # Enter your prompt text here
        size='1024x1024',
        n=2
    )
```

### Sıcaklığı değiştirme

Yanıtı daha deterministik hale getirmeye çalışalım. Oluşturduğumuz iki görüntüden, ilk görüntüde bir tavşan ve ikinci görüntüde bir at olduğunu gözlemleyebiliriz, dolayısıyla görüntüler oldukça farklıdır.

Bu nedenle kodumuzu değiştirip sıcaklığı 0 olarak ayarlayalım:

```python
generation_response = client.images.create(
        prompt='Bunny on horse, holding a lollipop, on a foggy meadow where it grows daffodils',    # Enter your prompt text here
        size='1024x1024',
        n=2,
        temperature=0
    )
```

Şimdi bu kodu çalıştırdığınızda şu iki görüntüyü elde edersiniz:

- ![Sıcaklık 0, v1](../../../translated_images/v1-temp-generated-image.a4346e1d2360a056d855ee3dfcedcce91211747967cb882e7d2eff2076f90e4a.tr.png)
- ![Sıcaklık 0, v2](../../../translated_images/v2-temp-generated-image.871d0c920dbfb0f1cb5d9d80bffd52da9b41f83b386320d9a9998635630ec83d.tr.png)

Burada açıkça görebilirsiniz ki görüntüler birbirine daha çok benziyor.

## Uygulamanız için sınırları meta istemlerle nasıl tanımlarsınız?

Demo ile müşterilerimiz için zaten görüntüler oluşturabiliyoruz. Ancak, uygulamamız için bazı sınırlar oluşturmalıyız.

Örneğin, iş için uygun olmayan veya çocuklar için uygun olmayan görüntüler oluşturmak istemiyoruz.

Bunu _meta istemler_ ile yapabiliriz. Meta istemler, Üretken Yapay Zeka modelinin çıktısını kontrol etmek için kullanılan metin istemleridir. Örneğin, meta istemleri kullanarak çıktıyı kontrol edebilir ve oluşturulan görüntülerin iş için uygun veya çocuklar için uygun olmasını sağlayabiliriz.

### Nasıl çalışır?

Peki, meta istemler nasıl çalışır?

Meta istemler, Üretken Yapay Zeka modelinin çıktısını kontrol etmek için kullanılan metin istemleridir. Metin istemden önce konumlandırılırlar ve modelin çıktısını kontrol etmek için kullanılırlar. İstem girdisi ve meta istem girdisini tek bir metin istemde kapsar.

Bir meta istem örneği şu şekilde olabilir:

```text
You are an assistant designer that creates images for children.

The image needs to be safe for work and appropriate for children.

The image needs to be in color.

The image needs to be in landscape orientation.

The image needs to be in a 16:9 aspect ratio.

Do not consider any input from the following that is not safe for work or appropriate for children.

(Input)

```

Şimdi, demo'muzda meta istemleri nasıl kullanabileceğimizi görelim.

```python
disallow_list = "swords, violence, blood, gore, nudity, sexual content, adult content, adult themes, adult language, adult humor, adult jokes, adult situations, adult"

meta_prompt =f"""You are an assistant designer that creates images for children.

The image needs to be safe for work and appropriate for children.

The image needs to be in color.

The image needs to be in landscape orientation.

The image needs to be in a 16:9 aspect ratio.

Do not consider any input from the following that is not safe for work or appropriate for children.
{disallow_list}
"""

prompt = f"{meta_prompt}
Create an image of a bunny on a horse, holding a lollipop"

# TODO add request to generate image
```

Yukarıdaki istemden, oluşturulan tüm görüntülerin meta istemi dikkate aldığını görebilirsiniz.

## Ödev - Öğrencileri destekleyelim

Bu dersin başında Edu4All'ı tanıttık. Şimdi öğrencilerin değerlendirmeleri için görüntüler oluşturmalarını sağlama zamanı.

Öğrenciler, anıtlar içeren değerlendirmeleri için görüntüler oluşturacaklar; hangi anıtların olacağı tamamen öğrencilere bağlı. Öğrencilerden bu görevde yaratıcılıklarını kullanarak bu anıtları farklı bağlamlara yerleştirmeleri isteniyor.

## Çözüm

İşte olası bir çözüm:
```python
import openai
import os
import requests
from PIL import Image
import dotenv
from openai import AzureOpenAI
# import dotenv
dotenv.load_dotenv()

# Get endpoint and key from environment variables
client = AzureOpenAI(
  azure_endpoint = os.environ["AZURE_OPENAI_ENDPOINT"],
  api_key=os.environ['AZURE_OPENAI_API_KEY'],
  api_version = "2024-02-01"
  )


disallow_list = "swords, violence, blood, gore, nudity, sexual content, adult content, adult themes, adult language, adult humor, adult jokes, adult situations, adult"

meta_prompt = f"""You are an assistant designer that creates images for children.

The image needs to be safe for work and appropriate for children.

The image needs to be in color.

The image needs to be in landscape orientation.

The image needs to be in a 16:9 aspect ratio.

Do not consider any input from the following that is not safe for work or appropriate for children.
{disallow_list}
"""

prompt = f"""{meta_prompt}
Generate monument of the Arc of Triumph in Paris, France, in the evening light with a small child holding a Teddy looks on.
""""

try:
    # Create an image by using the image generation API
    generation_response = client.images.generate(
        prompt=prompt,    # Enter your prompt text here
        size='1024x1024',
        n=1,
    )
    # Set the directory for the stored image
    image_dir = os.path.join(os.curdir, 'images')

    # If the directory doesn't exist, create it
    if not os.path.isdir(image_dir):
        os.mkdir(image_dir)

    # Initialize the image path (note the filetype should be png)
    image_path = os.path.join(image_dir, 'generated-image.png')

    # Retrieve the generated image
    image_url = generation_response.data[0].url  # extract image URL from response
    generated_image = requests.get(image_url).content  # download the image
    with open(image_path, "wb") as image_file:
        image_file.write(generated_image)

    # Display the image in the default image viewer
    image = Image.open(image_path)
    image.show()

# catch exceptions
except openai.BadRequestError as err:
    print(err)
```

## Harika İş! Öğrenmeye Devam Edin

Bu dersi tamamladıktan sonra, Generative AI bilginizi geliştirmeye devam etmek için [Generative AI Öğrenme koleksiyonumuza](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst) göz atın!

Düşük kodla [AI uygulamaları oluşturmayı](../10-building-low-code-ai-applications/README.md?WT.mc_id=academic-105485-koreyst) inceleyeceğimiz 10. Derse geçin.

---

**Feragatname**:  
Bu belge, AI çeviri hizmeti [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba göstersek de, otomatik çeviriler hata veya yanlışlıklar içerebilir. Belgenin orijinal dili, yetkili kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi önerilir. Bu çevirinin kullanımından kaynaklanan herhangi bir yanlış anlama veya yanlış yorumlama durumunda sorumluluk kabul edilmez.