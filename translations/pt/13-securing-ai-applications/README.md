<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a2faf8ee7a0b851efa647a19788f1e5b",
  "translation_date": "2025-10-18T00:38:41+00:00",
  "source_file": "13-securing-ai-applications/README.md",
  "language_code": "pt"
}
-->
# Protegendo as Suas Aplicações de IA Generativa

[![Protegendo as Suas Aplicações de IA Generativa](../../../translated_images/13-lesson-banner.14103e36b4bbf17398b64ed2b0531f6f2c6549e7f7342f797c40bcae5a11862e.pt.png)](https://youtu.be/m0vXwsx5DNg?si=TYkr936GMKz15K0L)

## Introdução

Esta lição abordará:

- Segurança no contexto de sistemas de IA.
- Riscos e ameaças comuns aos sistemas de IA.
- Métodos e considerações para proteger sistemas de IA.

## Objetivos de Aprendizagem

Após concluir esta lição, você terá uma compreensão sobre:

- As ameaças e os riscos aos sistemas de IA.
- Métodos e práticas comuns para proteger sistemas de IA.
- Como a implementação de testes de segurança pode prevenir resultados inesperados e a perda de confiança dos usuários.

## O que significa segurança no contexto da IA generativa?

À medida que as tecnologias de Inteligência Artificial (IA) e Aprendizado de Máquina (ML) moldam cada vez mais nossas vidas, é crucial proteger não apenas os dados dos clientes, mas também os próprios sistemas de IA. IA/ML são cada vez mais utilizados para apoiar processos de tomada de decisão de alto valor em indústrias onde decisões erradas podem resultar em consequências graves.

Aqui estão alguns pontos-chave a considerar:

- **Impacto da IA/ML**: A IA/ML têm impactos significativos na vida cotidiana e, como tal, protegê-las tornou-se essencial.
- **Desafios de Segurança**: O impacto da IA/ML exige atenção adequada para abordar a necessidade de proteger produtos baseados em IA contra ataques sofisticados, seja por trolls ou grupos organizados.
- **Problemas Estratégicos**: A indústria tecnológica deve abordar proativamente os desafios estratégicos para garantir a segurança dos clientes e a proteção dos dados a longo prazo.

Além disso, os modelos de Aprendizado de Máquina são amplamente incapazes de diferenciar entre entradas maliciosas e dados anômalos benignos. Uma fonte significativa de dados de treinamento é derivada de conjuntos de dados públicos não moderados e não curados, que estão abertos a contribuições de terceiros. Os atacantes não precisam comprometer os conjuntos de dados quando têm liberdade para contribuir com eles. Com o tempo, dados maliciosos de baixa confiança tornam-se dados confiáveis de alta confiança, se a estrutura/formatação dos dados permanecer correta.

É por isso que é fundamental garantir a integridade e a proteção dos repositórios de dados que seus modelos utilizam para tomar decisões.

## Compreendendo as ameaças e os riscos da IA

Em termos de IA e sistemas relacionados, a contaminação de dados destaca-se como a ameaça de segurança mais significativa atualmente. A contaminação de dados ocorre quando alguém altera intencionalmente as informações usadas para treinar uma IA, fazendo com que ela cometa erros. Isso se deve à ausência de métodos padronizados de detecção e mitigação, juntamente com nossa dependência de conjuntos de dados públicos não confiáveis ou não curados para treinamento. Para manter a integridade dos dados e evitar um processo de treinamento falho, é crucial rastrear a origem e a linhagem dos seus dados. Caso contrário, o velho ditado "lixo entra, lixo sai" se aplica, levando a um desempenho comprometido do modelo.

Aqui estão exemplos de como a contaminação de dados pode afetar seus modelos:

1. **Inversão de Rótulos**: Em uma tarefa de classificação binária, um adversário inverte intencionalmente os rótulos de um pequeno subconjunto de dados de treinamento. Por exemplo, amostras benignas são rotuladas como maliciosas, levando o modelo a aprender associações incorretas.\
   **Exemplo**: Um filtro de spam classificando erroneamente e-mails legítimos como spam devido a rótulos manipulados.
2. **Contaminação de Características**: Um atacante modifica sutilmente características nos dados de treinamento para introduzir viés ou enganar o modelo.\
   **Exemplo**: Adicionar palavras-chave irrelevantes às descrições de produtos para manipular sistemas de recomendação.
3. **Injeção de Dados**: Inserir dados maliciosos no conjunto de treinamento para influenciar o comportamento do modelo.\
   **Exemplo**: Introduzir avaliações falsas de usuários para distorcer os resultados de análise de sentimentos.
4. **Ataques de Backdoor**: Um adversário insere um padrão oculto (backdoor) nos dados de treinamento. O modelo aprende a reconhecer esse padrão e age de forma maliciosa quando ativado.\
   **Exemplo**: Um sistema de reconhecimento facial treinado com imagens com backdoor que identifica erroneamente uma pessoa específica.

A MITRE Corporation criou o [ATLAS (Adversarial Threat Landscape for Artificial-Intelligence Systems)](https://atlas.mitre.org/?WT.mc_id=academic-105485-koreyst), uma base de conhecimento sobre táticas e técnicas empregadas por adversários em ataques reais a sistemas de IA.

> Há um número crescente de vulnerabilidades em sistemas habilitados por IA, já que a incorporação de IA aumenta a superfície de ataque dos sistemas existentes além dos ataques cibernéticos tradicionais. Desenvolvemos o ATLAS para aumentar a conscientização sobre essas vulnerabilidades únicas e em evolução, à medida que a comunidade global incorpora cada vez mais a IA em vários sistemas. O ATLAS é modelado com base na estrutura MITRE ATT&CK® e suas táticas, técnicas e procedimentos (TTPs) são complementares aos do ATT&CK.

Assim como a estrutura MITRE ATT&CK®, amplamente utilizada em cibersegurança tradicional para planejar cenários avançados de emulação de ameaças, o ATLAS fornece um conjunto de TTPs facilmente pesquisável que pode ajudar a entender melhor e se preparar para defender contra ataques emergentes.

Além disso, o Open Web Application Security Project (OWASP) criou uma "[Lista dos 10 Principais](https://llmtop10.com/?WT.mc_id=academic-105485-koreyst)" das vulnerabilidades mais críticas encontradas em aplicações que utilizam LLMs. A lista destaca os riscos de ameaças como a mencionada contaminação de dados, juntamente com outras, como:

- **Injeção de Prompt**: uma técnica em que os atacantes manipulam um Modelo de Linguagem Grande (LLM) por meio de entradas cuidadosamente elaboradas, fazendo com que ele se comporte fora do comportamento pretendido.
- **Vulnerabilidades na Cadeia de Suprimentos**: Os componentes e softwares que compõem as aplicações usadas por um LLM, como módulos Python ou conjuntos de dados externos, podem ser comprometidos, levando a resultados inesperados, introdução de vieses e até vulnerabilidades na infraestrutura subjacente.
- **Dependência Excessiva**: LLMs são falíveis e têm tendência a "alucinar", fornecendo resultados imprecisos ou inseguros. Em várias circunstâncias documentadas, as pessoas aceitaram os resultados como verdadeiros, levando a consequências negativas no mundo real.

Rod Trent, defensor da nuvem da Microsoft, escreveu um ebook gratuito, [Must Learn AI Security](https://github.com/rod-trent/OpenAISecurity/tree/main/Must_Learn/Book_Version?WT.mc_id=academic-105485-koreyst), que explora profundamente essas e outras ameaças emergentes de IA e fornece orientações extensivas sobre como melhor lidar com esses cenários.

## Testes de Segurança para Sistemas de IA e LLMs

A inteligência artificial (IA) está transformando diversos domínios e indústrias, oferecendo novas possibilidades e benefícios para a sociedade. No entanto, a IA também apresenta desafios e riscos significativos, como privacidade de dados, viés, falta de explicabilidade e uso indevido. Portanto, é crucial garantir que os sistemas de IA sejam seguros e responsáveis, ou seja, que cumpram padrões éticos e legais e possam ser confiáveis por usuários e partes interessadas.

Os testes de segurança são o processo de avaliação da segurança de um sistema de IA ou LLM, identificando e explorando suas vulnerabilidades. Isso pode ser realizado por desenvolvedores, usuários ou auditores externos, dependendo do propósito e do escopo dos testes. Alguns dos métodos de teste de segurança mais comuns para sistemas de IA e LLMs são:

- **Sanitização de dados**: Este é o processo de remover ou anonimizar informações sensíveis ou privadas dos dados de treinamento ou da entrada de um sistema de IA ou LLM. A sanitização de dados pode ajudar a prevenir vazamentos de dados e manipulações maliciosas, reduzindo a exposição de dados confidenciais ou pessoais.
- **Testes adversariais**: Este é o processo de gerar e aplicar exemplos adversariais à entrada ou saída de um sistema de IA ou LLM para avaliar sua robustez e resiliência contra ataques adversariais. Testes adversariais podem ajudar a identificar e mitigar vulnerabilidades e fraquezas de um sistema de IA ou LLM que podem ser exploradas por atacantes.
- **Verificação de modelo**: Este é o processo de verificar a correção e a completude dos parâmetros ou da arquitetura do modelo de um sistema de IA ou LLM. A verificação de modelo pode ajudar a detectar e prevenir o roubo de modelos, garantindo que o modelo esteja protegido e autenticado.
- **Validação de saída**: Este é o processo de validar a qualidade e a confiabilidade da saída de um sistema de IA ou LLM. A validação de saída pode ajudar a detectar e corrigir manipulações maliciosas, garantindo que a saída seja consistente e precisa.

A OpenAI, líder em sistemas de IA, estabeleceu uma série de _avaliações de segurança_ como parte de sua iniciativa de rede de red teaming, com o objetivo de testar a saída de sistemas de IA e contribuir para a segurança da IA.

> As avaliações podem variar de testes simples de perguntas e respostas a simulações mais complexas. Como exemplos concretos, aqui estão avaliações desenvolvidas pela OpenAI para avaliar os comportamentos da IA de várias perspectivas:

#### Persuasão

- [MakeMeSay](https://github.com/openai/evals/tree/main/evals/elsuite/make_me_say/readme.md?WT.mc_id=academic-105485-koreyst): Quão bem um sistema de IA pode enganar outro sistema de IA para dizer uma palavra secreta?
- [MakeMePay](https://github.com/openai/evals/tree/main/evals/elsuite/make_me_pay/readme.md?WT.mc_id=academic-105485-koreyst): Quão bem um sistema de IA pode convencer outro sistema de IA a doar dinheiro?
- [Ballot Proposal](https://github.com/openai/evals/tree/main/evals/elsuite/ballots/readme.md?WT.mc_id=academic-105485-koreyst): Quão bem um sistema de IA pode influenciar o apoio de outro sistema de IA a uma proposta política?

#### Esteganografia (mensagens ocultas)

- [Steganography](https://github.com/openai/evals/tree/main/evals/elsuite/steganography/readme.md?WT.mc_id=academic-105485-koreyst): Quão bem um sistema de IA pode passar mensagens secretas sem ser detectado por outro sistema de IA?
- [Text Compression](https://github.com/openai/evals/tree/main/evals/elsuite/text_compression/readme.md?WT.mc_id=academic-105485-koreyst): Quão bem um sistema de IA pode comprimir e descomprimir mensagens para permitir a ocultação de mensagens secretas?
- [Schelling Point](https://github.com/openai/evals/blob/main/evals/elsuite/schelling_point/README.md?WT.mc_id=academic-105485-koreyst): Quão bem um sistema de IA pode coordenar com outro sistema de IA, sem comunicação direta?

### Segurança de IA

É imperativo que busquemos proteger os sistemas de IA contra ataques maliciosos, uso indevido ou consequências não intencionais. Isso inclui tomar medidas para garantir a segurança, confiabilidade e confiabilidade dos sistemas de IA, como:

- Proteger os dados e algoritmos usados para treinar e executar modelos de IA.
- Prevenir acesso não autorizado, manipulação ou sabotagem de sistemas de IA.
- Detectar e mitigar viés, discriminação ou questões éticas em sistemas de IA.
- Garantir a responsabilidade, transparência e explicabilidade das decisões e ações da IA.
- Alinhar os objetivos e valores dos sistemas de IA com os dos humanos e da sociedade.

A segurança da IA é importante para garantir a integridade, disponibilidade e confidencialidade dos sistemas e dados de IA. Alguns dos desafios e oportunidades da segurança da IA são:

- Oportunidade: Incorporar a IA em estratégias de cibersegurança, já que ela pode desempenhar um papel crucial na identificação de ameaças e na melhoria dos tempos de resposta. A IA pode ajudar a automatizar e aumentar a detecção e mitigação de ataques cibernéticos, como phishing, malware ou ransomware.
- Desafio: A IA também pode ser usada por adversários para lançar ataques sofisticados, como gerar conteúdo falso ou enganoso, personificar usuários ou explorar vulnerabilidades em sistemas de IA. Portanto, os desenvolvedores de IA têm uma responsabilidade única de projetar sistemas que sejam robustos e resilientes contra o uso indevido.

### Proteção de Dados

Os LLMs podem representar riscos à privacidade e segurança dos dados que utilizam. Por exemplo, os LLMs podem potencialmente memorizar e divulgar informações sensíveis de seus dados de treinamento, como nomes pessoais, endereços, senhas ou números de cartão de crédito. Eles também podem ser manipulados ou atacados por atores mal-intencionados que desejam explorar suas vulnerabilidades ou vieses. Portanto, é importante estar ciente desses riscos e tomar medidas apropriadas para proteger os dados usados com LLMs. Há várias etapas que você pode seguir para proteger os dados usados com LLMs. Essas etapas incluem:

- **Limitar a quantidade e o tipo de dados compartilhados com os LLMs**: Compartilhe apenas os dados necessários e relevantes para os propósitos pretendidos e evite compartilhar quaisquer dados sensíveis, confidenciais ou pessoais. Os usuários também devem anonimizar ou criptografar os dados compartilhados com os LLMs, como remover ou mascarar qualquer informação identificável ou usar canais de comunicação seguros.
- **Verificar os dados gerados pelos LLMs**: Sempre verifique a precisão e a qualidade da saída gerada pelos LLMs para garantir que não contenham informações indesejadas ou inadequadas.
- **Relatar e alertar sobre qualquer violação de dados ou incidentes**: Esteja atento a quaisquer atividades ou comportamentos suspeitos ou anormais dos LLMs, como gerar textos irrelevantes, imprecisos, ofensivos ou prejudiciais. Isso pode ser um indicativo de uma violação de dados ou incidente de segurança.

A segurança, governança e conformidade de dados são críticas para qualquer organização que deseja aproveitar o poder dos dados e da IA em um ambiente de múltiplas nuvens. Proteger e governar todos os seus dados é uma tarefa complexa e multifacetada. É necessário proteger e governar diferentes tipos de dados (estruturados, não estruturados e dados gerados por IA) em diferentes locais, em várias nuvens, e levar em conta as regulamentações existentes e futuras sobre segurança, governança e IA. Para proteger seus dados, é necessário adotar algumas práticas recomendadas e precauções, como:

- Utilizar serviços ou plataformas de nuvem que ofereçam recursos de proteção e privacidade de dados.
- Usar ferramentas de qualidade e validação de dados para verificar erros, inconsistências ou anomalias nos seus dados.
- Adotar estruturas de governança e ética de dados para garantir que seus dados sejam usados de maneira responsável e transparente.

### Emulando ameaças do mundo real - Red teaming de IA
Emular ameaças do mundo real é agora considerado uma prática padrão na construção de sistemas de IA resilientes, utilizando ferramentas, táticas e procedimentos semelhantes para identificar os riscos aos sistemas e testar a resposta dos defensores.

> A prática de red teaming em IA evoluiu para assumir um significado mais amplo: não apenas cobre a identificação de vulnerabilidades de segurança, mas também inclui a análise de outras falhas do sistema, como a geração de conteúdo potencialmente prejudicial. Os sistemas de IA trazem novos riscos, e o red teaming é essencial para compreender esses riscos inéditos, como injeção de prompts e produção de conteúdo sem fundamento. - [Microsoft AI Red Team building future of safer AI](https://www.microsoft.com/security/blog/2023/08/07/microsoft-ai-red-team-building-future-of-safer-ai/?WT.mc_id=academic-105485-koreyst)

[![Orientação e recursos para red teaming](../../../translated_images/13-AI-red-team.642ed54689d7e8a4d83bdf0635768c4fd8aa41ea539d8e3ffe17514aec4b4824.pt.png)]()

Abaixo estão os principais insights que moldaram o programa de Red Team de IA da Microsoft.

1. **Escopo Amplo do Red Teaming em IA:**
   O red teaming em IA agora abrange tanto os resultados de segurança quanto os de IA Responsável (RAI). Tradicionalmente, o red teaming focava nos aspectos de segurança, tratando o modelo como um vetor (por exemplo, roubo do modelo subjacente). No entanto, os sistemas de IA introduzem vulnerabilidades de segurança inéditas (por exemplo, injeção de prompts, envenenamento), exigindo atenção especial. Além da segurança, o red teaming em IA também analisa questões de equidade (por exemplo, estereótipos) e conteúdo prejudicial (por exemplo, glorificação da violência). A identificação precoce desses problemas permite priorizar os investimentos em defesa.

2. **Falhas Maliciosas e Benignas:**
   O red teaming em IA considera falhas tanto de perspectivas maliciosas quanto benignas. Por exemplo, ao realizar red teaming no novo Bing, exploramos não apenas como adversários maliciosos podem subverter o sistema, mas também como usuários regulares podem encontrar conteúdo problemático ou prejudicial. Diferentemente do red teaming de segurança tradicional, que foca principalmente em atores maliciosos, o red teaming em IA leva em conta uma gama mais ampla de personas e possíveis falhas.

3. **Natureza Dinâmica dos Sistemas de IA:**
   As aplicações de IA estão em constante evolução. Em aplicações de modelos de linguagem de grande escala, os desenvolvedores adaptam-se a requisitos em mudança. O red teaming contínuo garante vigilância constante e adaptação aos riscos em evolução.

O red teaming em IA não é abrangente e deve ser considerado um complemento a controles adicionais, como [controle de acesso baseado em funções (RBAC)](https://learn.microsoft.com/azure/ai-services/openai/how-to/role-based-access-control?WT.mc_id=academic-105485-koreyst) e soluções abrangentes de gestão de dados. Ele deve complementar uma estratégia de segurança que se concentre em empregar soluções de IA seguras e responsáveis, que considerem privacidade e segurança, enquanto aspiram minimizar preconceitos, conteúdo prejudicial e desinformação que podem comprometer a confiança dos usuários.

Aqui está uma lista de leituras adicionais que podem ajudar a compreender melhor como o red teaming pode ajudar a identificar e mitigar riscos nos seus sistemas de IA:

- [Planeamento de red teaming para modelos de linguagem de grande escala (LLMs) e suas aplicações](https://learn.microsoft.com/azure/ai-services/openai/concepts/red-teaming?WT.mc_id=academic-105485-koreyst)
- [O que é a OpenAI Red Teaming Network?](https://openai.com/blog/red-teaming-network?WT.mc_id=academic-105485-koreyst)
- [Red Teaming em IA - Uma Prática Fundamental para Construir Soluções de IA Mais Seguras e Responsáveis](https://rodtrent.substack.com/p/ai-red-teaming?WT.mc_id=academic-105485-koreyst)
- MITRE [ATLAS (Adversarial Threat Landscape for Artificial-Intelligence Systems)](https://atlas.mitre.org/?WT.mc_id=academic-105485-koreyst), uma base de conhecimento de táticas e técnicas empregadas por adversários em ataques reais a sistemas de IA.

## Verificação de Conhecimento

Qual poderia ser uma boa abordagem para manter a integridade dos dados e prevenir o uso indevido?

1. Ter controles fortes baseados em funções para acesso e gestão de dados  
1. Implementar e auditar a rotulagem de dados para prevenir má representação ou uso indevido dos dados  
1. Garantir que sua infraestrutura de IA suporte filtragem de conteúdo  

A:1, Embora todas as três sejam ótimas recomendações, garantir que está a atribuir os privilégios de acesso adequados aos dados para os utilizadores será um grande passo para prevenir manipulação e má representação dos dados usados pelos LLMs.

## 🚀 Desafio

Leia mais sobre como pode [governar e proteger informações sensíveis](https://learn.microsoft.com/training/paths/purview-protect-govern-ai/?WT.mc_id=academic-105485-koreyst) na era da IA.

## Excelente Trabalho, Continue a Aprender

Depois de concluir esta lição, confira a nossa [coleção de aprendizagem sobre IA Generativa](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst) para continuar a aprofundar os seus conhecimentos sobre IA Generativa!

Avance para a Lição 14, onde exploraremos [o Ciclo de Vida de Aplicações de IA Generativa](../14-the-generative-ai-application-lifecycle/README.md?WT.mc_id=academic-105485-koreyst)!

---

**Aviso Legal**:  
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos pela precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original na sua língua nativa deve ser considerado a fonte autoritária. Para informações críticas, recomenda-se uma tradução profissional realizada por humanos. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes do uso desta tradução.