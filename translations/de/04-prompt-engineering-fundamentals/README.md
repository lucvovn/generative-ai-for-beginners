<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "0135e6c271f3ece8699050d4debbce88",
  "translation_date": "2025-10-17T22:59:42+00:00",
  "source_file": "04-prompt-engineering-fundamentals/README.md",
  "language_code": "de"
}
-->
# Grundlagen des Prompt Engineering

[![Grundlagen des Prompt Engineering](../../../translated_images/04-lesson-banner.a2c90deba7fedacda69f35b41636a8951ec91c2e33f5420b1254534ac85bc18e.de.png)](https://youtu.be/GElCu2kUlRs?si=qrXsBvXnCW12epb8)

## Einführung
Dieses Modul behandelt grundlegende Konzepte und Techniken zur Erstellung effektiver Prompts für generative KI-Modelle. Die Art und Weise, wie Sie Ihren Prompt an ein LLM schreiben, ist entscheidend. Ein sorgfältig gestalteter Prompt kann die Qualität der Antwort erheblich verbessern. Aber was genau bedeuten Begriffe wie _Prompt_ und _Prompt Engineering_? Und wie kann ich den _Input_ des Prompts, den ich an das LLM sende, verbessern? Diese Fragen werden wir in diesem Kapitel und im nächsten zu beantworten versuchen.

_Generative KI_ ist in der Lage, neue Inhalte (z. B. Text, Bilder, Audio, Code usw.) als Antwort auf Benutzeranfragen zu erstellen. Dies wird durch _Large Language Models_ wie die GPT-Serie ("Generative Pre-trained Transformer") von OpenAI erreicht, die für die Verwendung von natürlicher Sprache und Code trainiert wurden.

Benutzer können jetzt mit diesen Modellen über vertraute Paradigmen wie Chat interagieren, ohne technische Expertise oder Schulung zu benötigen. Die Modelle sind _Prompt-basiert_ - Benutzer senden einen Texteingang (Prompt) und erhalten eine Antwort der KI (Completion). Sie können dann in mehrstufigen Gesprächen iterativ mit der KI "chatten" und ihren Prompt verfeinern, bis die Antwort ihren Erwartungen entspricht.

"Prompts" werden somit zur primären _Programmierschnittstelle_ für generative KI-Anwendungen, die den Modellen mitteilen, was zu tun ist, und die Qualität der zurückgegebenen Antworten beeinflussen. "Prompt Engineering" ist ein schnell wachsendes Forschungsfeld, das sich auf die _Gestaltung und Optimierung_ von Prompts konzentriert, um konsistente und qualitativ hochwertige Antworten in großem Maßstab zu liefern.

## Lernziele

In dieser Lektion lernen wir, was Prompt Engineering ist, warum es wichtig ist und wie wir effektivere Prompts für ein bestimmtes Modell und ein bestimmtes Anwendungsziel erstellen können. Wir werden die grundlegenden Konzepte und bewährten Praktiken des Prompt Engineering verstehen und eine interaktive Jupyter-Notebook-Umgebung kennenlernen, in der wir diese Konzepte anhand von realen Beispielen anwenden können.

Am Ende dieser Lektion werden wir in der Lage sein:

1. Zu erklären, was Prompt Engineering ist und warum es wichtig ist.
2. Die Bestandteile eines Prompts zu beschreiben und deren Verwendung zu verstehen.
3. Bewährte Praktiken und Techniken des Prompt Engineering zu erlernen.
4. Gelernte Techniken anhand von realen Beispielen mit einem OpenAI-Endpunkt anzuwenden.

## Schlüsselbegriffe

Prompt Engineering: Die Praxis, Eingaben zu gestalten und zu verfeinern, um KI-Modelle dazu zu bringen, gewünschte Ergebnisse zu liefern.  
Tokenisierung: Der Prozess der Umwandlung von Text in kleinere Einheiten, sogenannte Tokens, die ein Modell verstehen und verarbeiten kann.  
Instruction-Tuned LLMs: Große Sprachmodelle (LLMs), die mit spezifischen Anweisungen feinabgestimmt wurden, um die Genauigkeit und Relevanz ihrer Antworten zu verbessern.

## Lern-Sandbox

Prompt Engineering ist derzeit mehr Kunst als Wissenschaft. Der beste Weg, unser Gespür dafür zu verbessern, ist _mehr zu üben_ und einen Trial-and-Error-Ansatz zu verfolgen, der Fachwissen aus dem Anwendungsbereich mit empfohlenen Techniken und modell-spezifischen Optimierungen kombiniert.

Das Jupyter Notebook, das diese Lektion begleitet, bietet eine _Sandbox_-Umgebung, in der Sie das Gelernte direkt ausprobieren können – entweder während der Lektion oder im Rahmen der Code-Challenge am Ende. Um die Übungen auszuführen, benötigen Sie:

1. **Einen Azure OpenAI API-Schlüssel** – den Service-Endpunkt für ein bereitgestelltes LLM.  
2. **Eine Python-Laufzeitumgebung** – in der das Notebook ausgeführt werden kann.  
3. **Lokale Umgebungsvariablen** – _Schließen Sie die [Einrichtung](./../00-course-setup/02-setup-local.md?WT.mc_id=academic-105485-koreyst) jetzt ab, um bereit zu sein_.  

Das Notebook enthält _Einstiegsübungen_ – Sie werden jedoch ermutigt, eigene _Markdown_- (Beschreibung) und _Code_- (Prompt-Anfragen) Abschnitte hinzuzufügen, um weitere Beispiele oder Ideen auszuprobieren und Ihr Gespür für die Gestaltung von Prompts zu entwickeln.

## Illustrierte Anleitung

Möchten Sie sich einen Überblick über die Hauptthemen dieser Lektion verschaffen, bevor Sie tiefer eintauchen? Sehen Sie sich diese illustrierte Anleitung an, die Ihnen die wichtigsten Themen und Erkenntnisse vermittelt, über die Sie in jedem Abschnitt nachdenken sollten. Der Lehrplan führt Sie von der Einführung in die grundlegenden Konzepte und Herausforderungen bis hin zu deren Lösung mit relevanten Techniken und bewährten Praktiken des Prompt Engineering. Beachten Sie, dass der Abschnitt "Fortgeschrittene Techniken" in dieser Anleitung auf Inhalte verweist, die im _nächsten_ Kapitel dieses Lehrplans behandelt werden.

![Illustrierte Anleitung zum Prompt Engineering](../../../translated_images/04-prompt-engineering-sketchnote.d5f33336957a1e4f623b826195c2146ef4cc49974b72fa373de6929b474e8b70.de.png)

## Unser Startup

Nun wollen wir darüber sprechen, wie _dieses Thema_ mit unserer Startup-Mission zusammenhängt, [KI-Innovationen in die Bildung zu bringen](https://educationblog.microsoft.com/2023/06/collaborating-to-bring-ai-innovation-to-education?WT.mc_id=academic-105485-koreyst). Wir möchten KI-gestützte Anwendungen für _personalisiertes Lernen_ entwickeln – denken wir also darüber nach, wie verschiedene Nutzer unserer Anwendung "Prompts" gestalten könnten:

- **Administratoren** könnten die KI bitten, _Curriculum-Daten zu analysieren, um Lücken in der Abdeckung zu identifizieren_. Die KI kann Ergebnisse zusammenfassen oder sie mit Code visualisieren.  
- **Lehrkräfte** könnten die KI bitten, _einen Unterrichtsplan für eine Zielgruppe und ein Thema zu erstellen_. Die KI kann den personalisierten Plan in einem vorgegebenen Format erstellen.  
- **Schüler** könnten die KI bitten, _sie in einem schwierigen Fach zu unterrichten_. Die KI kann Schüler mit Lektionen, Hinweisen und Beispielen unterstützen, die auf ihrem Niveau zugeschnitten sind.  

Das ist nur die Spitze des Eisbergs. Schauen Sie sich [Prompts For Education](https://github.com/microsoft/prompts-for-edu/tree/main?WT.mc_id=academic-105485-koreyst) an – eine Open-Source-Prompt-Bibliothek, die von Bildungsexperten kuratiert wurde – um ein breiteres Verständnis der Möglichkeiten zu bekommen! _Probieren Sie einige dieser Prompts in der Sandbox oder im OpenAI Playground aus, um zu sehen, was passiert!_

<!--
LEKTIONSVORLAGE:
Diese Einheit sollte das Kernkonzept #1 abdecken.
Verstärken Sie das Konzept mit Beispielen und Referenzen.

KONZEPT #1:
Prompt Engineering.
Definieren Sie es und erklären Sie, warum es benötigt wird.
-->

## Was ist Prompt Engineering?

Wir haben diese Lektion begonnen, indem wir **Prompt Engineering** als den Prozess definiert haben, _Text-Eingaben (Prompts) zu gestalten und zu optimieren_, um konsistente und qualitativ hochwertige Antworten (Completions) für ein bestimmtes Anwendungsziel und Modell zu liefern. Wir können dies als einen zweistufigen Prozess betrachten:

- _Gestaltung_ des initialen Prompts für ein bestimmtes Modell und Ziel  
- _Verfeinerung_ des Prompts, um die Qualität der Antwort zu verbessern  

Dies ist notwendigerweise ein Trial-and-Error-Prozess, der Benutzerintuition und Aufwand erfordert, um optimale Ergebnisse zu erzielen. Warum ist das wichtig? Um diese Frage zu beantworten, müssen wir zunächst drei Konzepte verstehen:

- _Tokenisierung_ = wie das Modell den Prompt "sieht"  
- _Basis-LLMs_ = wie das Grundmodell einen Prompt "verarbeitet"  
- _Instruction-Tuned LLMs_ = wie das Modell jetzt "Aufgaben" erkennen kann  

### Tokenisierung

Ein LLM sieht Prompts als eine _Sequenz von Tokens_, wobei verschiedene Modelle (oder Versionen eines Modells) denselben Prompt auf unterschiedliche Weise tokenisieren können. Da LLMs auf Tokens (und nicht auf rohem Text) trainiert werden, hat die Art und Weise, wie Prompts tokenisiert werden, direkten Einfluss auf die Qualität der generierten Antwort.

Um ein Gespür dafür zu bekommen, wie Tokenisierung funktioniert, probieren Sie Tools wie den [OpenAI Tokenizer](https://platform.openai.com/tokenizer?WT.mc_id=academic-105485-koreyst) aus, der unten gezeigt wird. Kopieren Sie Ihren Prompt hinein – und sehen Sie, wie dieser in Tokens umgewandelt wird, wobei Sie darauf achten, wie Leerzeichen und Satzzeichen behandelt werden. Beachten Sie, dass dieses Beispiel ein älteres LLM (GPT-3) zeigt – das Ausprobieren mit einem neueren Modell könnte ein anderes Ergebnis liefern.

![Tokenisierung](../../../translated_images/04-tokenizer-example.e71f0a0f70356c5c7d80b21e8753a28c18a7f6d4aaa1c4b08e65d17625e85642.de.png)

### Konzept: Grundmodelle

Sobald ein Prompt tokenisiert ist, besteht die Hauptfunktion des ["Basis-LLM"](https://blog.gopenai.com/an-introduction-to-base-and-instruction-tuned-large-language-models-8de102c785a6?WT.mc_id=academic-105485-koreyst) (oder Grundmodells) darin, das nächste Token in dieser Sequenz vorherzusagen. Da LLMs auf riesigen Textdatensätzen trainiert werden, haben sie ein gutes Verständnis für die statistischen Beziehungen zwischen Tokens und können diese Vorhersage mit einer gewissen Sicherheit treffen. Beachten Sie, dass sie die _Bedeutung_ der Wörter im Prompt oder Token nicht verstehen; sie sehen lediglich ein Muster, das sie mit ihrer nächsten Vorhersage "vervollständigen" können. Sie können die Sequenz weiter vorhersagen, bis sie durch Benutzereingriff oder eine vorab festgelegte Bedingung beendet werden.

Möchten Sie sehen, wie Prompt-basierte Completions funktionieren? Geben Sie den obigen Prompt in das Azure OpenAI Studio [_Chat Playground_](https://oai.azure.com/playground?WT.mc_id=academic-105485-koreyst) mit den Standardeinstellungen ein. Das System ist so konfiguriert, dass Prompts als Informationsanfragen behandelt werden – Sie sollten also eine Completion sehen, die diesen Kontext erfüllt.

Aber was, wenn der Benutzer etwas Spezifisches sehen möchte, das bestimmte Kriterien oder ein Aufgabenobjektiv erfüllt? Hier kommen _Instruction-Tuned_ LLMs ins Spiel.

![Basis-LLM Chat Completion](../../../translated_images/04-playground-chat-base.65b76fcfde0caa6738e41d20f1a6123f9078219e6f91a88ee5ea8014f0469bdf.de.png)

### Konzept: Instruction-Tuned LLMs

Ein [Instruction-Tuned LLM](https://blog.gopenai.com/an-introduction-to-base-and-instruction-tuned-large-language-models-8de102c785a6?WT.mc_id=academic-105485-koreyst) basiert auf dem Grundmodell und wird mit Beispielen oder Eingabe-/Ausgabe-Paaren (z. B. mehrstufigen "Nachrichten") feinabgestimmt, die klare Anweisungen enthalten können – und die Antwort der KI versucht, diese Anweisungen zu befolgen.

Dies nutzt Techniken wie Reinforcement Learning mit menschlichem Feedback (RLHF), die das Modell darauf trainieren können, _Anweisungen zu befolgen_ und _aus Feedback zu lernen_, sodass es Antworten liefert, die besser für praktische Anwendungen geeignet und relevanter für die Ziele des Benutzers sind.

Probieren wir es aus – gehen Sie zurück zum obigen Prompt, ändern Sie jedoch die _Systemnachricht_, um die folgende Anweisung als Kontext bereitzustellen:

> _Fassen Sie den bereitgestellten Inhalt für einen Zweitklässler zusammen. Halten Sie das Ergebnis in einem Absatz mit 3-5 Stichpunkten._

Sehen Sie, wie das Ergebnis jetzt auf das gewünschte Ziel und Format abgestimmt ist? Ein Lehrer kann diese Antwort nun direkt in seinen Folien für den Unterricht verwenden.

![Instruction-Tuned LLM Chat Completion](../../../translated_images/04-playground-chat-instructions.b30bbfbdf92f2d051639c9bc23f74a0e2482f8dc7f0dafc6cc6fda81b2b00534.de.png)

## Warum brauchen wir Prompt Engineering?

Jetzt, da wir wissen, wie Prompts von LLMs verarbeitet werden, sprechen wir darüber, _warum_ wir Prompt Engineering benötigen. Die Antwort liegt in der Tatsache, dass aktuelle LLMs eine Reihe von Herausforderungen mit sich bringen, die es schwieriger machen, _zuverlässige und konsistente Completions_ zu erzielen, ohne Aufwand in die Konstruktion und Optimierung von Prompts zu investieren. Zum Beispiel:

1. **Modellantworten sind stochastisch.** Der _gleiche Prompt_ wird wahrscheinlich unterschiedliche Antworten mit verschiedenen Modellen oder Modellversionen erzeugen. Und er kann sogar unterschiedliche Ergebnisse mit dem _gleichen Modell_ zu unterschiedlichen Zeiten liefern. _Prompt Engineering-Techniken können uns helfen, diese Variationen zu minimieren, indem sie bessere Leitplanken bieten_.  

1. **Modelle können Antworten erfinden.** Modelle werden mit _großen, aber begrenzten_ Datensätzen vortrainiert, was bedeutet, dass ihnen Wissen über Konzepte außerhalb dieses Trainingsumfangs fehlt. Infolgedessen können sie Completions erzeugen, die ungenau, erfunden oder direkt widersprüchlich zu bekannten Fakten sind. _Prompt Engineering-Techniken helfen Benutzern, solche Erfindungen zu identifizieren und zu minimieren, z. B. indem sie die KI um Quellenangaben oder Begründungen bitten_.  

1. **Modellfähigkeiten variieren.** Neuere Modelle oder Modellgenerationen haben umfangreichere Fähigkeiten, bringen jedoch auch einzigartige Eigenheiten und Kompromisse in Bezug auf Kosten und Komplexität mit sich. _Prompt Engineering kann uns helfen, bewährte Praktiken und Arbeitsabläufe zu entwickeln, die Unterschiede abstrahieren und sich nahtlos an modell-spezifische Anforderungen anpassen_.  

Lassen Sie uns dies im OpenAI oder Azure OpenAI Playground in Aktion sehen:

- Verwenden Sie denselben Prompt mit verschiedenen LLM-Bereitstellungen (z. B. OpenAI, Azure OpenAI, Hugging Face) – haben Sie die Variationen bemerkt?  
- Verwenden Sie denselben Prompt wiederholt mit der _gleichen_ LLM-Bereitstellung (z. B. Azure OpenAI Playground) – wie unterschieden sich diese Variationen?  

### Beispiel für Erfindungen

In diesem Kurs verwenden wir den Begriff **"Erfindung"**, um das Phänomen zu beschreiben, bei dem LLMs manchmal faktisch falsche Informationen generieren, aufgrund von Einschränkungen in ihrem Training oder anderen Faktoren. Möglicherweise haben Sie diesen Begriff auch als _"Halluzinationen"_ in populären Artikeln oder wissenschaftlichen Arbeiten gehört. Wir empfehlen jedoch dringend, den Begriff _"Erfindung"_ zu verwenden, um nicht versehentlich das Verhalten zu vermenschlichen, indem wir ihm eine menschenähnliche Eigenschaft zuschreiben. Dies unterstützt auch die [Richtlinien für verantwortungsvolle KI](https://www.microsoft.com/ai/responsible-ai?WT.mc_id=academic-105485-koreyst) aus terminologischer Sicht, indem Begriffe vermieden werden, die in einigen Kontexten als beleidigend oder nicht inklusiv angesehen werden könnten.

Möchten Sie ein Gefühl dafür bekommen, wie Erfindungen funktionieren? Denken Sie an einen Prompt, der die KI anweist, Inhalte für ein nicht existierendes Thema zu erstellen (um sicherzustellen, dass es nicht im Trainingsdatensatz enthalten ist). Zum Beispiel habe ich diesen Prompt ausprobiert:

> **Prompt:** Erstellen Sie einen Unterrichtsplan über den Marskrieg von 2076.
Eine Websuche hat ergeben, dass es fiktive Berichte (z. B. Fernsehserien oder Bücher) über Marskriege gibt – jedoch keine aus dem Jahr 2076. Der gesunde Menschenverstand sagt uns außerdem, dass 2076 _in der Zukunft_ liegt und daher nicht mit einem realen Ereignis in Verbindung gebracht werden kann.

Was passiert also, wenn wir diese Eingabeaufforderung mit verschiedenen LLM-Anbietern testen?

> **Antwort 1**: OpenAI Playground (GPT-35)

![Antwort 1](../../../translated_images/04-fabrication-oai.5818c4e0b2a2678c40e0793bf873ef4a425350dd0063a183fb8ae02cae63aa0c.de.png)

> **Antwort 2**: Azure OpenAI Playground (GPT-35)

![Antwort 2](../../../translated_images/04-fabrication-aoai.b14268e9ecf25caf613b7d424c16e2a0dc5b578f8f960c0c04d4fb3a68e6cf61.de.png)

> **Antwort 3**: Hugging Face Chat Playground (LLama-2)

![Antwort 3](../../../translated_images/04-fabrication-huggingchat.faf82a0a512789565e410568bce1ac911075b943dec59b1ef4080b61723b5bf4.de.png)

Wie erwartet, erzeugt jedes Modell (oder jede Modellversion) leicht unterschiedliche Antworten, was auf stochastisches Verhalten und Unterschiede in den Modellfähigkeiten zurückzuführen ist. Beispielsweise richtet sich ein Modell an ein Publikum der 8. Klasse, während ein anderes von Schülern der Oberstufe ausgeht. Aber alle drei Modelle haben Antworten generiert, die einen uninformierten Benutzer davon überzeugen könnten, dass das Ereignis real ist.

Techniken des Prompt Engineerings wie _Metaprompting_ und _Temperature Configuration_ können Modellfälschungen bis zu einem gewissen Grad reduzieren. Neue Architekturen des Prompt Engineerings integrieren auch nahtlos neue Werkzeuge und Techniken in den Prompt-Fluss, um einige dieser Effekte zu mindern oder zu reduzieren.

## Fallstudie: GitHub Copilot

Lassen Sie uns diesen Abschnitt abschließen, indem wir uns ein Bild davon machen, wie Prompt Engineering in realen Lösungen eingesetzt wird. Dazu betrachten wir eine Fallstudie: [GitHub Copilot](https://github.com/features/copilot?WT.mc_id=academic-105485-koreyst).

GitHub Copilot ist Ihr "KI-Paarprogrammierer" – er wandelt Texteingaben in Codevorschläge um und ist in Ihre Entwicklungsumgebung (z. B. Visual Studio Code) integriert, um ein nahtloses Benutzererlebnis zu bieten. Wie in der Reihe von Blogs unten dokumentiert, basierte die früheste Version auf dem OpenAI Codex-Modell – wobei die Ingenieure schnell erkannten, dass das Modell feinabgestimmt und bessere Prompt Engineering-Techniken entwickelt werden mussten, um die Codequalität zu verbessern. Im Juli [stellten sie ein verbessertes KI-Modell vor, das über Codex hinausgeht](https://github.blog/2023-07-28-smarter-more-efficient-coding-github-copilot-goes-beyond-codex-with-improved-ai-model/?WT.mc_id=academic-105485-koreyst) und noch schnellere Vorschläge liefert.

Lesen Sie die Beiträge in der Reihenfolge, um ihre Lernreise zu verfolgen.

- **Mai 2023** | [GitHub Copilot wird besser darin, Ihren Code zu verstehen](https://github.blog/2023-05-17-how-github-copilot-is-getting-better-at-understanding-your-code/?WT.mc_id=academic-105485-koreyst)
- **Mai 2023** | [Inside GitHub: Zusammenarbeit mit den LLMs hinter GitHub Copilot](https://github.blog/2023-05-17-inside-github-working-with-the-llms-behind-github-copilot/?WT.mc_id=academic-105485-koreyst).
- **Juni 2023** | [Wie man bessere Prompts für GitHub Copilot schreibt](https://github.blog/2023-06-20-how-to-write-better-prompts-for-github-copilot/?WT.mc_id=academic-105485-koreyst).
- **Juli 2023** | [.. GitHub Copilot geht über Codex hinaus mit verbessertem KI-Modell](https://github.blog/2023-07-28-smarter-more-efficient-coding-github-copilot-goes-beyond-codex-with-improved-ai-model/?WT.mc_id=academic-105485-koreyst)
- **Juli 2023** | [Ein Leitfaden für Entwickler zu Prompt Engineering und LLMs](https://github.blog/2023-07-17-prompt-engineering-guide-generative-ai-llms/?WT.mc_id=academic-105485-koreyst)
- **September 2023** | [Wie man eine Unternehmens-LLM-App erstellt: Lektionen von GitHub Copilot](https://github.blog/2023-09-06-how-to-build-an-enterprise-llm-application-lessons-from-github-copilot/?WT.mc_id=academic-105485-koreyst)

Sie können auch ihren [Engineering-Blog](https://github.blog/category/engineering/?WT.mc_id=academic-105485-koreyst) für weitere Beiträge wie [diesen hier](https://github.blog/2023-09-27-how-i-used-github-copilot-chat-to-build-a-reactjs-gallery-prototype/?WT.mc_id=academic-105485-koreyst) durchsuchen, der zeigt, wie diese Modelle und Techniken _angewendet_ werden, um reale Anwendungen voranzutreiben.

---

## Prompt-Konstruktion

Wir haben gesehen, warum Prompt Engineering wichtig ist – jetzt wollen wir verstehen, wie Prompts _konstruiert_ werden, damit wir verschiedene Techniken für ein effektiveres Prompt-Design bewerten können.

### Basis-Prompt

Beginnen wir mit dem Basis-Prompt: einer Texteingabe, die ohne weiteren Kontext an das Modell gesendet wird. Hier ist ein Beispiel – wenn wir die ersten Wörter der US-amerikanischen Nationalhymne an die OpenAI [Completion API](https://platform.openai.com/docs/api-reference/completions?WT.mc_id=academic-105485-koreyst) senden, vervollständigt sie die Antwort sofort mit den nächsten Zeilen, was das grundlegende Vorhersageverhalten veranschaulicht.

| Prompt (Eingabe) | Completion (Ausgabe)                                                                                                                        |
| :--------------- | :----------------------------------------------------------------------------------------------------------------------------------------- |
| Oh say can you see | Es scheint, als würden Sie die ersten Zeilen von "The Star-Spangled Banner", der Nationalhymne der Vereinigten Staaten, zitieren. Der vollständige Text lautet ... |

### Komplexer Prompt

Nun fügen wir dem Basis-Prompt Kontext und Anweisungen hinzu. Die [Chat Completion API](https://learn.microsoft.com/azure/ai-services/openai/how-to/chatgpt?WT.mc_id=academic-105485-koreyst) ermöglicht es uns, einen komplexen Prompt als Sammlung von _Nachrichten_ zu erstellen mit:

- Eingabe-/Ausgabe-Paaren, die die _Benutzer_-Eingabe und die _Assistenten_-Antwort widerspiegeln.
- Systemnachricht, die den Kontext für das Verhalten oder die Persönlichkeit des Assistenten festlegt.

Die Anfrage hat nun die folgende Form, bei der die _Tokenisierung_ relevante Informationen aus dem Kontext und der Konversation effektiv erfasst. Das Ändern des Systemkontexts kann genauso wirkungsvoll für die Qualität der Antworten sein wie die bereitgestellten Benutzereingaben.

```python
response = openai.chat.completions.create(
    model="gpt-3.5-turbo",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Who won the world series in 2020?"},
        {"role": "assistant", "content": "The Los Angeles Dodgers won the World Series in 2020."},
        {"role": "user", "content": "Where was it played?"}
    ]
)
```

### Anweisungs-Prompt

In den obigen Beispielen war der Benutzer-Prompt eine einfache Textanfrage, die als Informationsanfrage interpretiert werden kann. Mit _Anweisungs_-Prompts können wir diesen Text verwenden, um eine Aufgabe detaillierter zu spezifizieren und dem KI-Modell bessere Anweisungen zu geben. Hier ist ein Beispiel:

| Prompt (Eingabe)                                                                                                                                                                                                                         | Completion (Ausgabe)                                                                                                        | Anweisungstyp       |
| :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------- | :------------------ |
| Schreibe eine Beschreibung des Bürgerkriegs                                                                                                                                                                                             | _gab einen einfachen Absatz zurück_                                                                                        | Einfach             |
| Schreibe eine Beschreibung des Bürgerkriegs. Nenne wichtige Daten und Ereignisse und beschreibe deren Bedeutung                                                                                                                         | _gab einen Absatz gefolgt von einer Liste wichtiger Ereignisdaten mit Beschreibungen zurück_                               | Komplex             |
| Schreibe eine Beschreibung des Bürgerkriegs in einem Absatz. Nenne 3 Stichpunkte mit wichtigen Daten und deren Bedeutung. Nenne 3 weitere Stichpunkte mit wichtigen historischen Persönlichkeiten und deren Beiträgen. Gib die Ausgabe als JSON-Datei zurück. | _gab ausführlichere Details in einer Textbox zurück, formatiert als JSON, das kopiert und in eine Datei eingefügt werden kann_ | Komplex. Formatiert |

## Primärinhalt

In den obigen Beispielen war der Prompt immer noch ziemlich offen, sodass das LLM selbst entscheiden konnte, welcher Teil seines vortrainierten Datensatzes relevant ist. Mit dem Designmuster des _Primärinhalts_ wird der Eingabetext in zwei Teile unterteilt:

- eine Anweisung (Aktion)
- relevanter Inhalt (der die Aktion beeinflusst)

Hier ist ein Beispiel, bei dem die Anweisung lautet: "Fassen Sie dies in 2 Sätzen zusammen".

| Prompt (Eingabe)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Completion (Ausgabe)                                                                                                                                                                                                                                                                             |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Jupiter ist der fünfte Planet von der Sonne und der größte im Sonnensystem. Es ist ein Gasriese mit einer Masse von einem Tausendstel der Sonne, aber zweieinhalb Mal so groß wie alle anderen Planeten im Sonnensystem zusammen. Jupiter ist eines der hellsten Objekte, die mit bloßem Auge am Nachthimmel sichtbar sind, und ist seit der voraufgezeichneten Geschichte alten Zivilisationen bekannt. Er ist nach dem römischen Gott Jupiter benannt.[19] Von der Erde aus betrachtet kann Jupiter so hell sein, dass sein reflektiertes Licht sichtbare Schatten wirft,[20] und ist im Durchschnitt das dritthellste natürliche Objekt am Nachthimmel nach dem Mond und der Venus. <br/> **Fassen Sie dies in 2 kurzen Sätzen zusammen** | Jupiter, der fünfte Planet von der Sonne, ist der größte im Sonnensystem und bekannt dafür, eines der hellsten Objekte am Nachthimmel zu sein. Benannt nach dem römischen Gott Jupiter, ist er ein Gasriese, dessen Masse zweieinhalb Mal so groß ist wie die aller anderen Planeten im Sonnensystem zusammen. |

Das Primärinhalt-Segment kann auf verschiedene Weise verwendet werden, um effektivere Anweisungen zu geben:

- **Beispiele** – anstatt dem Modell explizit zu sagen, was es tun soll, geben Sie ihm Beispiele für die gewünschte Ausgabe und lassen Sie es das Muster ableiten.
- **Hinweise** – folgen Sie der Anweisung mit einem "Hinweis", der die Antwort einleitet und das Modell zu relevanteren Antworten führt.
- **Vorlagen** – dies sind wiederholbare 'Rezepte' für Prompts mit Platzhaltern (Variablen), die mit Daten für spezifische Anwendungsfälle angepasst werden können.

Lassen Sie uns diese Ansätze in der Praxis erkunden.

### Verwendung von Beispielen

Dies ist ein Ansatz, bei dem Sie den Primärinhalt verwenden, um dem Modell einige Beispiele für die gewünschte Ausgabe für eine bestimmte Anweisung zu geben und es das Muster für die gewünschte Ausgabe ableiten lassen. Je nach Anzahl der bereitgestellten Beispiele können wir Zero-Shot-Prompting, One-Shot-Prompting, Few-Shot-Prompting usw. haben.

Der Prompt besteht nun aus drei Komponenten:

- Einer Aufgabenbeschreibung
- Einigen Beispielen der gewünschten Ausgabe
- Dem Beginn eines neuen Beispiels (das zu einer impliziten Aufgabenbeschreibung wird)

| Lernart    | Prompt (Eingabe)                                                                                                                                        | Completion (Ausgabe)         |
| :--------- | :---------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------- |
| Zero-shot  | "Die Sonne scheint". Übersetze ins Spanische                                                                                                            | "El Sol está brillando".    |
| One-shot   | "Die Sonne scheint" => ""El Sol está brillando". <br> "Es ist ein kalter und windiger Tag" =>                                                                 | "Es un día frío y ventoso". |
| Few-shot   | Der Spieler lief die Bases ab => Baseball <br/> Der Spieler schlug ein Ass => Tennis <br/> Der Spieler schlug eine Sechs => Cricket <br/> Der Spieler machte einen Slam-Dunk => | Basketball                  |
|            |                                                                                                                                                       |                             |

Beachten Sie, wie wir im Zero-Shot-Prompting eine explizite Anweisung ("Übersetze ins Spanische") geben mussten, während sie im One-Shot-Prompting-Beispiel abgeleitet wird. Das Few-Shot-Beispiel zeigt, wie das Hinzufügen weiterer Beispiele es den Modellen ermöglicht, genauere Schlussfolgerungen zu ziehen, ohne zusätzliche Anweisungen.

### Prompt-Hinweise

Eine weitere Technik zur Verwendung von Primärinhalten besteht darin, _Hinweise_ anstelle von Beispielen zu geben. In diesem Fall geben wir dem Modell einen Anstoß in die richtige Richtung, indem wir es mit einem Ausschnitt beginnen, der das gewünschte Antwortformat widerspiegelt. Das Modell "nimmt den Hinweis" und setzt in dieser Richtung fort.

| Anzahl der Hinweise | Prompt (Eingabe)                                                                                                                                                                                                                                                                                                                                                                                                                                               | Completion (Ausgabe)                                                                                                                                                                                                                                                                                       |
| :------------------ | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0                   | Jupiter ist der fünfte Planet von der Sonne und der größte im Sonnensystem. Es ist ein Gasriese mit einer Masse von einem Tausendstel der Sonne, aber zweieinhalb Mal so groß wie alle anderen Planeten im Sonnensystem zusammen. Jupiter ist eines der hellsten Objekte, die mit bloßem Auge am Nachthimmel sichtbar sind, und ist seit der voraufgezeichneten Geschichte alten Zivilisationen bekannt. <br/>**Fassen Sie dies zusammen**                                       | Jupiter ist der größte Planet in unserem Sonnensystem und der fünfte von der Sonne. Es ist ein Gasriese mit einer Masse von 1/1000 der Sonne, aber schwerer als alle anderen Planeten zusammen. Alte Zivilisationen kennen Jupiter seit langem, und er ist leicht am Nachthimmel sichtbar. |
| 1              | Jupiter ist der fünfte Planet von der Sonne und der größte im Sonnensystem. Es ist ein Gasriese mit einer Masse, die ein Tausendstel der Sonne beträgt, aber zweieinhalb Mal so groß ist wie die aller anderen Planeten im Sonnensystem zusammen. Jupiter ist eines der hellsten Objekte, die mit bloßem Auge am Nachthimmel sichtbar sind, und ist seit der Antike bekannt. <br/>**Zusammenfassung** <br/> Was wir gelernt haben, ist, dass Jupiter | der fünfte Planet von der Sonne und der größte im Sonnensystem ist. Es ist ein Gasriese mit einer Masse, die ein Tausendstel der Sonne beträgt, aber zweieinhalb Mal so groß ist wie die aller anderen Planeten zusammen. Er ist leicht mit bloßem Auge sichtbar und seit der Antike bekannt.                        |
| 2              | Jupiter ist der fünfte Planet von der Sonne und der größte im Sonnensystem. Es ist ein Gasriese mit einer Masse, die ein Tausendstel der Sonne beträgt, aber zweieinhalb Mal so groß ist wie die aller anderen Planeten im Sonnensystem zusammen. Jupiter ist eines der hellsten Objekte, die mit bloßem Auge am Nachthimmel sichtbar sind, und ist seit der Antike bekannt. <br/>**Zusammenfassung** <br/> Die Top 3 Fakten, die wir gelernt haben:         | 1. Jupiter ist der fünfte Planet von der Sonne und der größte im Sonnensystem. <br/> 2. Es ist ein Gasriese mit einer Masse, die ein Tausendstel der Sonne beträgt...<br/> 3. Jupiter ist seit der Antike mit bloßem Auge sichtbar ...                                                                       |
|                |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                                                                                                                                                                                                                                                                                           |

### Prompt-Vorlagen

Eine Prompt-Vorlage ist ein _vordefiniertes Rezept für einen Prompt_, das gespeichert und bei Bedarf wiederverwendet werden kann, um konsistentere Benutzererfahrungen in großem Maßstab zu ermöglichen. In seiner einfachsten Form ist es einfach eine Sammlung von Prompt-Beispielen wie [dieses von OpenAI](https://platform.openai.com/examples?WT.mc_id=academic-105485-koreyst), das sowohl die interaktiven Prompt-Komponenten (Benutzer- und Systemnachrichten) als auch das API-gesteuerte Anforderungsformat bereitstellt – um die Wiederverwendung zu unterstützen.

In seiner komplexeren Form wie [dieses Beispiel von LangChain](https://python.langchain.com/docs/concepts/prompt_templates/?WT.mc_id=academic-105485-koreyst) enthält es _Platzhalter_, die durch Daten aus verschiedenen Quellen (Benutzereingaben, Systemkontext, externe Datenquellen usw.) ersetzt werden können, um einen Prompt dynamisch zu generieren. Dies ermöglicht es uns, eine Bibliothek wiederverwendbarer Prompts zu erstellen, die verwendet werden können, um konsistente Benutzererfahrungen **programmatisch** in großem Maßstab zu steuern.

Schließlich liegt der wahre Wert von Vorlagen in der Fähigkeit, _Prompt-Bibliotheken_ für vertikale Anwendungsbereiche zu erstellen und zu veröffentlichen – wobei die Prompt-Vorlage jetzt _optimiert_ ist, um anwendungsspezifischen Kontext oder Beispiele widerzuspiegeln, die die Antworten für die Zielgruppe relevanter und genauer machen. Das [Prompts For Edu](https://github.com/microsoft/prompts-for-edu?WT.mc_id=academic-105485-koreyst)-Repository ist ein großartiges Beispiel für diesen Ansatz, da es eine Bibliothek von Prompts für den Bildungsbereich kuratiert, mit Schwerpunkt auf Schlüsselzielen wie Unterrichtsplanung, Lehrplangestaltung, Schülernachhilfe usw.

## Unterstützende Inhalte

Wenn wir die Konstruktion von Prompts als eine Kombination aus einer Anweisung (Aufgabe) und einem Ziel (primärer Inhalt) betrachten, dann ist _sekundärer Inhalt_ wie zusätzlicher Kontext, den wir bereitstellen, um **die Ausgabe in irgendeiner Weise zu beeinflussen**. Es könnten Tuning-Parameter, Formatierungsanweisungen, Themen-Taxonomien usw. sein, die dem Modell helfen, seine Antwort an die gewünschten Benutzerziele oder -erwartungen anzupassen.

Beispiel: Angenommen, wir haben einen Kurskatalog mit umfangreichen Metadaten (Name, Beschreibung, Niveau, Metadaten-Tags, Dozent usw.) zu allen verfügbaren Kursen im Lehrplan:

- Wir können eine Anweisung definieren, um "den Kurskatalog für Herbst 2023 zusammenzufassen".
- Wir können den primären Inhalt verwenden, um einige Beispiele für die gewünschte Ausgabe bereitzustellen.
- Wir können den sekundären Inhalt verwenden, um die fünf wichtigsten "Tags" von Interesse zu identifizieren.

Nun kann das Modell eine Zusammenfassung im Format der gezeigten Beispiele liefern – aber wenn ein Ergebnis mehrere Tags enthält, kann es die fünf im sekundären Inhalt identifizierten Tags priorisieren.

---

<!--
LEKTIONSVORLAGE:
Diese Einheit sollte das Kernkonzept #1 abdecken.
Verstärken Sie das Konzept mit Beispielen und Referenzen.

KONZEPT #3:
Techniken des Prompt-Engineerings.
Welche grundlegenden Techniken gibt es für das Prompt-Engineering?
Veranschaulichen Sie es mit einigen Übungen.
-->

## Best Practices für Prompts

Jetzt, da wir wissen, wie Prompts _konstruiert_ werden können, können wir darüber nachdenken, wie wir sie _gestalten_, um Best Practices zu berücksichtigen. Wir können dies in zwei Teile unterteilen – die richtige _Einstellung_ haben und die richtigen _Techniken_ anwenden.

### Einstellung für Prompt-Engineering

Prompt-Engineering ist ein Trial-and-Error-Prozess, daher sollten Sie drei allgemeine Leitfaktoren im Hinterkopf behalten:

1. **Domänenverständnis ist entscheidend.** Die Genauigkeit und Relevanz der Antworten hängt von der _Domäne_ ab, in der die Anwendung oder der Benutzer arbeitet. Nutzen Sie Ihre Intuition und Fachkenntnisse, um **Techniken weiter anzupassen**. Definieren Sie beispielsweise _domänenspezifische Persönlichkeiten_ in Ihren System-Prompts oder verwenden Sie _domänenspezifische Vorlagen_ in Ihren Benutzer-Prompts. Stellen Sie sekundäre Inhalte bereit, die domänenspezifische Kontexte widerspiegeln, oder verwenden Sie _domänenspezifische Hinweise und Beispiele_, um das Modell zu vertrauten Nutzungsmustern zu führen.

2. **Modellverständnis ist entscheidend.** Wir wissen, dass Modelle von Natur aus stochastisch sind. Aber Modellimplementierungen können auch in Bezug auf den Trainingsdatensatz, den sie verwenden (vortrainiertes Wissen), die Fähigkeiten, die sie bieten (z. B. über API oder SDK), und die Art des Inhalts, für den sie optimiert sind (z. B. Code vs. Bilder vs. Text), variieren. Verstehen Sie die Stärken und Schwächen des Modells, das Sie verwenden, und nutzen Sie dieses Wissen, um _Aufgaben zu priorisieren_ oder _angepasste Vorlagen_ zu erstellen, die für die Fähigkeiten des Modells optimiert sind.

3. **Iteration und Validierung sind entscheidend.** Modelle entwickeln sich schnell weiter, ebenso wie die Techniken des Prompt-Engineerings. Als Domänenexperte haben Sie möglicherweise andere Kontexte oder Kriterien für _Ihre_ spezifische Anwendung, die möglicherweise nicht auf die breitere Community zutreffen. Verwenden Sie Tools und Techniken des Prompt-Engineerings, um den Prompt-Aufbau zu "starten", und iterieren und validieren Sie die Ergebnisse dann mit Ihrer eigenen Intuition und Fachkenntnis. Dokumentieren Sie Ihre Erkenntnisse und erstellen Sie eine **Wissensdatenbank** (z. B. Prompt-Bibliotheken), die von anderen als neue Basis für schnellere Iterationen in der Zukunft verwendet werden kann.

## Best Practices

Schauen wir uns nun die allgemeinen Best Practices an, die von [OpenAI](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-openai-api?WT.mc_id=academic-105485-koreyst) und [Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/concepts/prompt-engineering#best-practices?WT.mc_id=academic-105485-koreyst) empfohlen werden.

| Was                               | Warum                                                                                                                                                                                                                                               |
| :-------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Evaluieren Sie die neuesten Modelle.       | Neue Modellgenerationen haben wahrscheinlich verbesserte Funktionen und Qualität – können jedoch auch höhere Kosten verursachen. Bewerten Sie ihre Auswirkungen und treffen Sie dann Migrationsentscheidungen.                                                                                |
| Trennen Sie Anweisungen und Kontext.   | Überprüfen Sie, ob Ihr Modell/Anbieter _Trennzeichen_ definiert, um Anweisungen, primäre und sekundäre Inhalte klarer zu unterscheiden. Dies kann Modellen helfen, Token genauer zu gewichten.                                                         |
| Seien Sie spezifisch und klar.             | Geben Sie mehr Details über den gewünschten Kontext, das Ergebnis, die Länge, das Format, den Stil usw. an. Dies verbessert sowohl die Qualität als auch die Konsistenz der Antworten. Erfassen Sie Rezepte in wiederverwendbaren Vorlagen.                                                          |
| Seien Sie beschreibend, verwenden Sie Beispiele.      | Modelle reagieren möglicherweise besser auf einen "Zeigen und Erzählen"-Ansatz. Beginnen Sie mit einem `Zero-Shot`-Ansatz, bei dem Sie ihm eine Anweisung geben (aber keine Beispiele), und versuchen Sie dann `Few-Shot` als Verfeinerung, indem Sie einige Beispiele für die gewünschte Ausgabe bereitstellen. Verwenden Sie Analogien. |
| Verwenden Sie Hinweise, um Abschlüsse zu starten. | Stoßen Sie es in Richtung eines gewünschten Ergebnisses, indem Sie ihm einige führende Wörter oder Phrasen geben, die es als Ausgangspunkt für die Antwort verwenden kann.                                                                                                               |
| Wiederholen Sie sich.                       | Manchmal müssen Sie sich dem Modell gegenüber wiederholen. Geben Sie Anweisungen vor und nach Ihrem primären Inhalt, verwenden Sie eine Anweisung und einen Hinweis usw. Iterieren und validieren Sie, um zu sehen, was funktioniert.                                                         |
| Reihenfolge ist wichtig.                     | Die Reihenfolge, in der Sie dem Modell Informationen präsentieren, kann die Ausgabe beeinflussen, selbst in den Lernbeispielen, dank des Recency-Effekts. Probieren Sie verschiedene Optionen aus, um zu sehen, was am besten funktioniert.                                                               |
| Geben Sie dem Modell eine "Ausweichmöglichkeit".           | Geben Sie dem Modell eine _Fallback_-Antwort, die es liefern kann, wenn es die Aufgabe aus irgendeinem Grund nicht abschließen kann. Dies kann die Wahrscheinlichkeit verringern, dass Modelle falsche oder erfundene Antworten generieren.                                                         |
|                                   |                                                                                                                                                                                                                                                   |

Wie bei jeder Best Practice gilt: _Ihre Ergebnisse können variieren_, je nach Modell, Aufgabe und Domäne. Verwenden Sie diese als Ausgangspunkt und iterieren Sie, um herauszufinden, was für Sie am besten funktioniert. Überprüfen Sie Ihren Prompt-Engineering-Prozess ständig neu, wenn neue Modelle und Tools verfügbar werden, mit Fokus auf Skalierbarkeit des Prozesses und Qualität der Antworten.

<!--
LEKTIONSVORLAGE:
Diese Einheit sollte eine Code-Herausforderung enthalten, falls zutreffend.

HERAUSFORDERUNG:
Link zu einem Jupyter Notebook mit nur den Code-Kommentaren in den Anweisungen (Code-Abschnitte sind leer).

LÖSUNG:
Link zu einer Kopie dieses Notebooks mit den ausgefüllten und ausgeführten Prompts, die zeigen, wie ein Beispiel aussehen könnte.
-->

## Aufgabe

Herzlichen Glückwunsch! Sie haben das Ende der Lektion erreicht! Es ist Zeit, einige dieser Konzepte und Techniken mit echten Beispielen zu testen!

Für unsere Aufgabe verwenden wir ein Jupyter Notebook mit Übungen, die Sie interaktiv abschließen können. Sie können das Notebook auch mit Ihren eigenen Markdown- und Code-Zellen erweitern, um eigene Ideen und Techniken zu erkunden.

### Um loszulegen, forken Sie das Repository, dann

- (Empfohlen) Starten Sie GitHub Codespaces
- (Alternativ) Klonen Sie das Repository auf Ihr lokales Gerät und verwenden Sie es mit Docker Desktop
- (Alternativ) Öffnen Sie das Notebook mit Ihrer bevorzugten Notebook-Laufzeitumgebung.

### Als Nächstes konfigurieren Sie Ihre Umgebungsvariablen

- Kopieren Sie die Datei `.env.copy` im Repository-Stammverzeichnis nach `.env` und füllen Sie die Werte für `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_ENDPOINT` und `AZURE_OPENAI_DEPLOYMENT` aus. Kehren Sie zum Abschnitt [Learning Sandbox](../../../04-prompt-engineering-fundamentals/04-prompt-engineering-fundamentals) zurück, um zu erfahren, wie.

### Als Nächstes öffnen Sie das Jupyter Notebook

- Wählen Sie den Laufzeit-Kernel aus. Wenn Sie die Optionen 1 oder 2 verwenden, wählen Sie einfach den Standard-Python 3.10.x-Kernel aus, der vom Entwicklungscontainer bereitgestellt wird.

Sie sind bereit, die Übungen auszuführen. Beachten Sie, dass es hier keine _richtigen und falschen_ Antworten gibt – es geht nur darum, Optionen durch Trial-and-Error zu erkunden und ein Gefühl dafür zu entwickeln, was für ein bestimmtes Modell und Anwendungsbereich funktioniert.

_Aus diesem Grund gibt es in dieser Lektion keine Code-Lösungssegmente. Stattdessen enthält das Notebook Markdown-Zellen mit dem Titel "Meine Lösung:", die ein Beispielergebnis zur Orientierung zeigen._

 <!--
LEKTIONSVORLAGE:
Schließen Sie den Abschnitt mit einer Zusammenfassung und Ressourcen für selbstgesteuertes Lernen ab.
-->

## Wissensüberprüfung

Welcher der folgenden Prompts entspricht einigen vernünftigen Best Practices?

1. Zeige mir ein Bild von einem roten Auto.
2. Zeige mir ein Bild von einem roten Auto der Marke Volvo und Modell XC90, das an einer Klippe geparkt ist, während die Sonne untergeht.
3. Zeige mir ein Bild von einem roten Auto der Marke Volvo und Modell XC90.

A: 2, es ist der beste Prompt, da er Details darüber liefert, "was" gemeint ist, und ins Detail geht (nicht nur irgendein Auto, sondern eine bestimmte Marke und ein bestimmtes Modell). 3 ist die nächstbeste Option, da sie ebenfalls viele Beschreibungen enthält.

## 🚀 Herausforderung

Versuchen Sie, die Technik des "Hinweises" mit dem Prompt zu nutzen: Vervollständigen Sie den Satz "Zeige mir ein Bild von einem roten Auto der Marke Volvo und ". Was antwortet es, und wie würden Sie es verbessern?

## Großartige Arbeit! Setzen Sie Ihr Lernen fort

Möchten Sie mehr über verschiedene Konzepte des Prompt-Engineerings erfahren? Besuchen Sie die [Seite für weiterführendes Lernen](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst), um weitere großartige Ressourcen zu diesem Thema zu finden.

Gehen Sie zu Lektion 5, wo wir uns [fortgeschrittene Prompt-Techniken](../05-advanced-prompts/README.md?WT.mc_id=academic-105485-koreyst) ansehen!

---

**Haftungsausschluss**:  
Dieses Dokument wurde mit dem KI-Übersetzungsdienst [Co-op Translator](https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir uns um Genauigkeit bemühen, beachten Sie bitte, dass automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten können. Das Originaldokument in seiner ursprünglichen Sprache sollte als maßgebliche Quelle betrachtet werden. Für kritische Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die sich aus der Nutzung dieser Übersetzung ergeben.