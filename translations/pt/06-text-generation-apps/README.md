<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "df027997f1448323d6159b78a1b669bf",
  "translation_date": "2025-10-18T00:37:16+00:00",
  "source_file": "06-text-generation-apps/README.md",
  "language_code": "pt"
}
-->
# Construção de Aplicações de Geração de Texto

[![Construção de Aplicações de Geração de Texto](../../../translated_images/06-lesson-banner.a5c629f990a636c852353c5533f1a6a218ece579005e91f96339d508d9cf8f47.pt.png)](https://youtu.be/0Y5Luf5sRQA?si=t_xVg0clnAI4oUFZ)

> _(Clique na imagem acima para ver o vídeo desta lição)_

Até agora, neste currículo, vimos conceitos fundamentais como prompts e até mesmo uma disciplina inteira chamada "engenharia de prompts". Muitas ferramentas com as quais pode interagir, como o ChatGPT, Office 365, Microsoft Power Platform e outras, permitem que utilize prompts para realizar tarefas.

Para adicionar essa experiência a uma aplicação, é necessário compreender conceitos como prompts, completions e escolher uma biblioteca para trabalhar. É exatamente isso que aprenderá neste capítulo.

## Introdução

Neste capítulo, você irá:

- Aprender sobre a biblioteca openai e os seus conceitos principais.
- Construir uma aplicação de geração de texto usando openai.
- Compreender como usar conceitos como prompt, temperatura e tokens para construir uma aplicação de geração de texto.

## Objetivos de aprendizagem

No final desta lição, você será capaz de:

- Explicar o que é uma aplicação de geração de texto.
- Construir uma aplicação de geração de texto usando openai.
- Configurar a sua aplicação para usar mais ou menos tokens e também alterar a temperatura para obter resultados variados.

## O que é uma aplicação de geração de texto?

Normalmente, quando constrói uma aplicação, ela possui algum tipo de interface, como as seguintes:

- Baseada em comandos. Aplicações de consola são típicas, onde você digita um comando e ela executa uma tarefa. Por exemplo, o `git` é uma aplicação baseada em comandos.
- Interface de utilizador (UI). Algumas aplicações possuem interfaces gráficas (GUIs) onde você clica em botões, insere texto, seleciona opções e muito mais.

### Aplicações de consola e UI são limitadas

Compare com uma aplicação baseada em comandos onde você digita um comando:

- **É limitada**. Não pode simplesmente digitar qualquer comando, apenas os que a aplicação suporta.
- **Específica para um idioma**. Algumas aplicações suportam muitos idiomas, mas, por padrão, a aplicação é construída para um idioma específico, mesmo que possa adicionar suporte a mais idiomas.

### Benefícios das aplicações de geração de texto

Então, como uma aplicação de geração de texto é diferente?

Numa aplicação de geração de texto, tem mais flexibilidade, não está limitado a um conjunto de comandos ou a um idioma de entrada específico. Em vez disso, pode usar linguagem natural para interagir com a aplicação. Outro benefício é que já está a interagir com uma fonte de dados que foi treinada num vasto corpus de informações, enquanto uma aplicação tradicional pode estar limitada ao que está numa base de dados.

### O que posso construir com uma aplicação de geração de texto?

Há muitas coisas que pode construir. Por exemplo:

- **Um chatbot**. Um chatbot que responde a perguntas sobre tópicos, como a sua empresa e os seus produtos, pode ser uma boa opção.
- **Assistente**. Os LLMs são ótimos para coisas como resumir texto, obter insights de texto, produzir textos como currículos e muito mais.
- **Assistente de código**. Dependendo do modelo de linguagem que usar, pode construir um assistente de código que o ajude a escrever código. Por exemplo, pode usar um produto como o GitHub Copilot, bem como o ChatGPT, para o ajudar a escrever código.

## Como posso começar?

Bem, precisa encontrar uma forma de integrar com um LLM, o que geralmente envolve as duas abordagens seguintes:

- Usar uma API. Aqui, está a construir pedidos web com o seu prompt e a obter texto gerado como resposta.
- Usar uma biblioteca. As bibliotecas ajudam a encapsular as chamadas de API e tornam-nas mais fáceis de usar.

## Bibliotecas/SDKs

Existem algumas bibliotecas bem conhecidas para trabalhar com LLMs, como:

- **openai**, esta biblioteca facilita a conexão com o seu modelo e o envio de prompts.

Depois, há bibliotecas que operam num nível mais alto, como:

- **Langchain**. Langchain é bem conhecida e suporta Python.
- **Semantic Kernel**. Semantic Kernel é uma biblioteca da Microsoft que suporta as linguagens C#, Python e Java.

## Primeira aplicação usando openai

Vamos ver como podemos construir a nossa primeira aplicação, quais bibliotecas precisamos, o que é necessário e assim por diante.

### Instalar openai

Existem muitas bibliotecas para interagir com o OpenAI ou Azure OpenAI. É possível usar várias linguagens de programação, como C#, Python, JavaScript, Java e mais. Escolhemos usar a biblioteca Python `openai`, então usaremos o `pip` para instalá-la.

```bash
pip install openai
```

### Criar um recurso

Precisa realizar os seguintes passos:

- Criar uma conta no Azure [https://azure.microsoft.com/free/](https://azure.microsoft.com/free/?WT.mc_id=academic-105485-koreyst).
- Obter acesso ao Azure OpenAI. Vá para [https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai](https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai?WT.mc_id=academic-105485-koreyst) e solicite acesso.

  > [!NOTE]
  > No momento da escrita, é necessário solicitar acesso ao Azure OpenAI.

- Instalar Python <https://www.python.org/>
- Criar um recurso de Serviço Azure OpenAI. Veja este guia sobre como [criar um recurso](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal?WT.mc_id=academic-105485-koreyst).

### Localizar a chave da API e o endpoint

Neste ponto, precisa informar à biblioteca `openai` qual chave da API usar. Para encontrar a sua chave da API, vá à secção "Keys and Endpoint" do recurso Azure OpenAI e copie o valor de "Key 1".

![Chaves e Endpoint no painel de recursos do Azure Portal](https://learn.microsoft.com/azure/ai-services/openai/media/quickstarts/endpoint.png?WT.mc_id=academic-105485-koreyst)

Agora que tem esta informação copiada, vamos instruir as bibliotecas a usá-la.

> [!NOTE]
> Vale a pena separar a sua chave da API do seu código. Pode fazer isso usando variáveis de ambiente.
>
> - Defina a variável de ambiente `OPENAI_API_KEY` para a sua chave da API.
>   `export OPENAI_API_KEY='sk-...'`

### Configuração do Azure

Se estiver a usar o Azure OpenAI, veja como configurar:

```python
openai.api_type = 'azure'
openai.api_key = os.environ["OPENAI_API_KEY"]
openai.api_version = '2023-05-15'
openai.api_base = os.getenv("API_BASE")
```

Acima, estamos a definir o seguinte:

- `api_type` para `azure`. Isso informa à biblioteca para usar o Azure OpenAI e não o OpenAI.
- `api_key`, esta é a sua chave da API encontrada no Portal do Azure.
- `api_version`, esta é a versão da API que deseja usar. No momento da escrita, a versão mais recente é `2023-05-15`.
- `api_base`, este é o endpoint da API. Pode encontrá-lo no Portal do Azure ao lado da sua chave da API.

> [!NOTE] > `os.getenv` é uma função que lê variáveis de ambiente. Pode usá-la para ler variáveis de ambiente como `OPENAI_API_KEY` e `API_BASE`. Defina estas variáveis de ambiente no seu terminal ou usando uma biblioteca como `dotenv`.

## Gerar texto

A forma de gerar texto é usar a classe `Completion`. Aqui está um exemplo:

```python
prompt = "Complete the following: Once upon a time there was a"

completion = openai.Completion.create(model="davinci-002", prompt=prompt)
print(completion.choices[0].text)
```

No código acima, criamos um objeto de completion e passamos o modelo que queremos usar e o prompt. Depois, imprimimos o texto gerado.

### Compleções de chat

Até agora, viu como usamos `Completion` para gerar texto. Mas há outra classe chamada `ChatCompletion` que é mais adequada para chatbots. Aqui está um exemplo de como usá-la:

```python
import openai

openai.api_key = "sk-..."

completion = openai.ChatCompletion.create(model="gpt-3.5-turbo", messages=[{"role": "user", "content": "Hello world"}])
print(completion.choices[0].message.content)
```

Mais sobre esta funcionalidade num capítulo futuro.

## Exercício - a sua primeira aplicação de geração de texto

Agora que aprendemos como configurar e configurar o openai, é hora de construir a sua primeira aplicação de geração de texto. Para construir a sua aplicação, siga estes passos:

1. Crie um ambiente virtual e instale o openai:

   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install openai
   ```

   > [!NOTE]
   > Se estiver a usar Windows, digite `venv\Scripts\activate` em vez de `source venv/bin/activate`.

   > [!NOTE]
   > Localize a sua chave do Azure OpenAI indo para [https://portal.azure.com/](https://portal.azure.com/?WT.mc_id=academic-105485-koreyst), procure por `Open AI`, selecione o recurso `Open AI` e, em seguida, selecione `Keys and Endpoint` e copie o valor de `Key 1`.

1. Crie um ficheiro _app.py_ e insira o seguinte código:

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
   > Se estiver a usar o Azure OpenAI, precisa definir o `api_type` como `azure` e definir o `api_key` como a sua chave do Azure OpenAI.

   Deve ver um resultado como o seguinte:

   ```output
    very unhappy _____.

   Once upon a time there was a very unhappy mermaid.
   ```

## Diferentes tipos de prompts, para diferentes finalidades

Agora viu como gerar texto usando um prompt. Já tem até um programa em funcionamento que pode modificar e alterar para gerar diferentes tipos de texto.

Os prompts podem ser usados para várias tarefas. Por exemplo:

- **Gerar um tipo de texto**. Por exemplo, pode gerar um poema, perguntas para um questionário, etc.
- **Pesquisar informações**. Pode usar prompts para procurar informações, como no exemplo: "O que significa CORS no desenvolvimento web?".
- **Gerar código**. Pode usar prompts para gerar código, por exemplo, desenvolver uma expressão regular para validar e-mails ou até mesmo gerar um programa inteiro, como uma aplicação web.

## Um caso prático: um gerador de receitas

Imagine que tem ingredientes em casa e quer cozinhar algo. Para isso, precisa de uma receita. Uma forma de encontrar receitas é usar um motor de busca ou pode usar um LLM para isso.

Poderia escrever um prompt como este:

> "Mostre-me 5 receitas para um prato com os seguintes ingredientes: frango, batatas e cenouras. Por receita, liste todos os ingredientes usados."

Dado o prompt acima, pode obter uma resposta semelhante a:

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

Este resultado é ótimo, já sei o que cozinhar. Neste ponto, melhorias úteis poderiam ser:

- Eliminar ingredientes que não gosto ou aos quais sou alérgico.
- Produzir uma lista de compras, caso não tenha todos os ingredientes em casa.

Para os casos acima, vamos adicionar um prompt adicional:

> "Por favor, remova receitas com alho, pois sou alérgico, e substitua-o por outra coisa. Além disso, produza uma lista de compras para as receitas, considerando que já tenho frango, batatas e cenouras em casa."

Agora tem um novo resultado, nomeadamente:

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

Essas são as suas cinco receitas, sem menção de alho, e também tem uma lista de compras considerando o que já tem em casa.

## Exercício - construir um gerador de receitas

Agora que simulamos um cenário, vamos escrever código para corresponder ao cenário demonstrado. Para isso, siga estes passos:

1. Use o ficheiro _app.py_ existente como ponto de partida.
1. Localize a variável `prompt` e altere o seu código para o seguinte:

   ```python
   prompt = "Show me 5 recipes for a dish with the following ingredients: chicken, potatoes, and carrots. Per recipe, list all the ingredients used"
   ```

   Se agora executar o código, deverá ver um resultado semelhante a:

   ```output
   -Chicken Stew with Potatoes and Carrots: 3 tablespoons oil, 1 onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 1/2 cups chicken broth, 1/2 cup dry white wine, 2 tablespoons chopped fresh parsley, 2 tablespoons unsalted butter, 1 1/2 pounds boneless, skinless chicken thighs, cut into 1-inch pieces
   -Oven-Roasted Chicken with Potatoes and Carrots: 3 tablespoons extra-virgin olive oil, 1 tablespoon Dijon mustard, 1 tablespoon chopped fresh rosemary, 1 tablespoon chopped fresh thyme, 4 cloves garlic, minced, 1 1/2 pounds small red potatoes, quartered, 1 1/2 pounds carrots, quartered lengthwise, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 (4-pound) whole chicken
   -Chicken, Potato, and Carrot Casserole: cooking spray, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and shredded, 1 potato, peeled and shredded, 1/2 teaspoon dried thyme leaves, 1/4 teaspoon salt, 1/4 teaspoon black pepper, 2 cups fat-free, low-sodium chicken broth, 1 cup frozen peas, 1/4 cup all-purpose flour, 1 cup 2% reduced-fat milk, 1/4 cup grated Parmesan cheese

   -One Pot Chicken and Potato Dinner: 2 tablespoons olive oil, 1 pound boneless, skinless chicken thighs, cut into 1-inch pieces, 1 large onion, chopped, 3 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 2 cups chicken broth, 1/2 cup dry white wine

   -Chicken, Potato, and Carrot Curry: 1 tablespoon vegetable oil, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 teaspoon ground coriander, 1 teaspoon ground cumin, 1/2 teaspoon ground turmeric, 1/2 teaspoon ground ginger, 1/4 teaspoon cayenne pepper, 2 cups chicken broth, 1/2 cup dry white wine, 1 (15-ounce) can chickpeas, drained and rinsed, 1/2 cup raisins, 1/2 cup chopped fresh cilantro
   ```

   > NOTA, o seu LLM é não determinístico, por isso pode obter resultados diferentes sempre que executar o programa.

   Ótimo, vamos ver como podemos melhorar as coisas. Para melhorar, queremos garantir que o código seja flexível, para que os ingredientes e o número de receitas possam ser ajustados e alterados.

1. Vamos alterar o código da seguinte forma:

   ```python
   no_recipes = input("No of recipes (for example, 5): ")

   ingredients = input("List of ingredients (for example, chicken, potatoes, and carrots): ")

   # interpolate the number of recipes into the prompt an ingredients
   prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used"
   ```

   Executar o código de teste pode parecer assim:

   ```output
   No of recipes (for example, 5): 3
   List of ingredients (for example, chicken, potatoes, and carrots): milk,strawberries

   -Strawberry milk shake: milk, strawberries, sugar, vanilla extract, ice cubes
   -Strawberry shortcake: milk, flour, baking powder, sugar, salt, unsalted butter, strawberries, whipped cream
   -Strawberry milk: milk, strawberries, sugar, vanilla extract
   ```

### Melhorar adicionando filtro e lista de compras

Agora temos uma aplicação funcional capaz de produzir receitas e é flexível, pois depende das entradas do utilizador, tanto no número de receitas quanto nos ingredientes usados.

Para melhorar ainda mais, queremos adicionar o seguinte:

- **Eliminar ingredientes**. Queremos ser capazes de eliminar ingredientes que não gostamos ou aos quais somos alérgicos. Para realizar esta alteração, podemos editar o nosso prompt existente e adicionar uma condição de filtro ao final, como segue:

  ```python
  filter = input("Filter (for example, vegetarian, vegan, or gluten-free): ")

  prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used, no {filter}"
  ```

  Acima, adicionamos `{filter}` ao final do prompt e também capturamos o valor do filtro do utilizador.

  Um exemplo de entrada ao executar o programa pode agora parecer assim:

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

  Como pode ver, quaisquer receitas com leite foram eliminadas. Mas, se for intolerante à lactose, pode querer eliminar também receitas com queijo, por isso é necessário ser claro.

- **Produzir uma lista de compras**. Queremos produzir uma lista de compras, considerando o que já temos em casa.

  Para esta funcionalidade, poderíamos tentar resolver tudo num único prompt ou dividi-lo em dois prompts. Vamos tentar a última abordagem. Aqui sugerimos adicionar um prompt adicional, mas para que isso funcione, precisamos adicionar o resultado do primeiro prompt como contexto ao segundo prompt.

  Localize a parte do código que imprime o resultado do primeiro prompt e adicione o seguinte código abaixo:
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

  Note o seguinte:

  1. Estamos a construir um novo prompt ao adicionar o resultado do primeiro prompt ao novo prompt:

     ```python
     new_prompt = f"{old_prompt_result} {prompt}"
     ```

  1. Fazemos um novo pedido, mas também considerando o número de tokens que pedimos no primeiro prompt, então desta vez dizemos que `max_tokens` é 1200.

     ```python
     completion = openai.Completion.create(engine=deployment_name, prompt=new_prompt, max_tokens=1200)
     ```

     Testando este código, chegamos agora ao seguinte resultado:

     ```output
     No of recipes (for example, 5): 2
     List of ingredients (for example, chicken, potatoes, and carrots): apple,flour
     Filter (for example, vegetarian, vegan, or gluten-free): sugar


     -Apple and flour pancakes: 1 cup flour, 1/2 tsp baking powder, 1/2 tsp baking soda, 1/4 tsp salt, 1 tbsp sugar, 1 egg, 1 cup buttermilk or sour milk, 1/4 cup melted butter, 1 Granny Smith apple, peeled and grated
     -Apple fritters: 1-1/2 cups flour, 1 tsp baking powder, 1/4 tsp salt, 1/4 tsp baking soda, 1/4 tsp nutmeg, 1/4 tsp cinnamon, 1/4 tsp allspice, 1/4 cup sugar, 1/4 cup vegetable shortening, 1/4 cup milk, 1 egg, 2 cups shredded, peeled apples
     Shopping list:
     -Flour, baking powder, baking soda, salt, sugar, egg, buttermilk, butter, apple, nutmeg, cinnamon, allspice
     ```

## Melhore a sua configuração

O que temos até agora é um código que funciona, mas há alguns ajustes que devemos fazer para melhorar ainda mais. Algumas coisas que devemos fazer são:

- **Separar segredos do código**, como a chave da API. Segredos não devem estar no código e devem ser armazenados num local seguro. Para separar segredos do código, podemos usar variáveis de ambiente e bibliotecas como `python-dotenv` para carregá-los a partir de um ficheiro. Eis como isso ficaria no código:

  1. Crie um ficheiro `.env` com o seguinte conteúdo:

     ```bash
     OPENAI_API_KEY=sk-...
     ```

     > Nota, para Azure, precisa de definir as seguintes variáveis de ambiente:

     ```bash
     OPENAI_API_TYPE=azure
     OPENAI_API_VERSION=2023-05-15
     OPENAI_API_BASE=<replace>
     ```

     No código, carregaria as variáveis de ambiente desta forma:

     ```python
     from dotenv import load_dotenv

     load_dotenv()

     openai.api_key = os.environ["OPENAI_API_KEY"]
     ```

- **Uma palavra sobre o comprimento dos tokens**. Devemos considerar quantos tokens precisamos para gerar o texto que queremos. Os tokens têm um custo, então, sempre que possível, devemos tentar ser económicos com o número de tokens que usamos. Por exemplo, podemos formular o prompt de forma a usar menos tokens?

  Para alterar os tokens usados, pode usar o parâmetro `max_tokens`. Por exemplo, se quiser usar 100 tokens, faria o seguinte:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, max_tokens=100)
  ```

- **Experimentar com a temperatura**. A temperatura é algo que ainda não mencionámos, mas é um contexto importante para o desempenho do nosso programa. Quanto maior o valor da temperatura, mais aleatório será o resultado. Por outro lado, quanto menor o valor da temperatura, mais previsível será o resultado. Considere se deseja variação no seu resultado ou não.

  Para alterar a temperatura, pode usar o parâmetro `temperature`. Por exemplo, se quiser usar uma temperatura de 0.5, faria o seguinte:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, temperature=0.5)
  ```

  > Nota, quanto mais próximo de 1.0, mais variado será o resultado.

## Tarefa

Para esta tarefa, pode escolher o que construir.

Aqui estão algumas sugestões:

- Ajustar a aplicação de geração de receitas para melhorá-la ainda mais. Experimente valores de temperatura e os prompts para ver o que consegue criar.
- Construir um "companheiro de estudo". Esta aplicação deve ser capaz de responder a perguntas sobre um tópico, por exemplo, Python. Pode ter prompts como "O que é um determinado tópico em Python?", ou pode ter um prompt que diga "Mostra-me o código para um determinado tópico", etc.
- Bot de história, faça a história ganhar vida, instrua o bot para interpretar um determinado personagem histórico e faça-lhe perguntas sobre a sua vida e época.

## Solução

### Companheiro de estudo

Abaixo está um prompt inicial, veja como pode usá-lo e ajustá-lo ao seu gosto.

```text
- "You're an expert on the Python language

    Suggest a beginner lesson for Python in the following format:

    Format:
    - concepts:
    - brief explanation of the lesson:
    - exercise in code with solutions"
```

### Bot de história

Aqui estão alguns prompts que pode usar:

```text
- "You are Abe Lincoln, tell me about yourself in 3 sentences, and respond using grammar and words like Abe would have used"
- "You are Abe Lincoln, respond using grammar and words like Abe would have used:

   Tell me about your greatest accomplishments, in 300 words"
```

## Verificação de conhecimento

O que faz o conceito de temperatura?

1. Controla quão aleatório é o resultado.
1. Controla o tamanho da resposta.
1. Controla quantos tokens são usados.

## 🚀 Desafio

Ao trabalhar na tarefa, tente variar a temperatura, experimente defini-la para 0, 0.5 e 1. Lembre-se de que 0 é o menos variado e 1 é o mais variado. Que valor funciona melhor para a sua aplicação?

## Excelente trabalho! Continue a aprender

Depois de concluir esta lição, consulte a nossa [coleção de aprendizagem de IA generativa](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst) para continuar a aprofundar os seus conhecimentos sobre IA generativa!

Avance para a Lição 7, onde vamos explorar como [construir aplicações de chat](../07-building-chat-applications/README.md?WT.mc_id=academic-105485-koreyst)!

---

**Aviso Legal**:  
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos pela precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original na sua língua nativa deve ser considerado a fonte autoritária. Para informações críticas, recomenda-se uma tradução profissional realizada por humanos. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes do uso desta tradução.