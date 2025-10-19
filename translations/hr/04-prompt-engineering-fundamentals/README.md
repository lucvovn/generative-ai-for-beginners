<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "0135e6c271f3ece8699050d4debbce88",
  "translation_date": "2025-10-18T01:35:59+00:00",
  "source_file": "04-prompt-engineering-fundamentals/README.md",
  "language_code": "hr"
}
-->
# Osnove oblikovanja upita

[![Osnove oblikovanja upita](../../../translated_images/04-lesson-banner.a2c90deba7fedacda69f35b41636a8951ec91c2e33f5420b1254534ac85bc18e.hr.png)](https://youtu.be/GElCu2kUlRs?si=qrXsBvXnCW12epb8)

## Uvod
Ovaj modul pokriva osnovne koncepte i tehnike za stvaranje učinkovitih upita u generativnim AI modelima. Način na koji pišete svoj upit za LLM također je važan. Pažljivo osmišljen upit može postići bolju kvalitetu odgovora. Ali što točno znače pojmovi poput _upit_ i _oblikovanje upita_? I kako mogu poboljšati _unos upita_ koji šaljem LLM-u? To su pitanja na koja ćemo pokušati odgovoriti u ovom poglavlju i sljedećem.

_Generativna umjetna inteligencija_ sposobna je stvarati novi sadržaj (npr. tekst, slike, audio, kod itd.) kao odgovor na korisničke zahtjeve. To postiže pomoću _velikih jezičnih modela_ poput OpenAI-jevih GPT ("Generative Pre-trained Transformer") serija koji su obučeni za korištenje prirodnog jezika i koda.

Korisnici sada mogu komunicirati s ovim modelima koristeći poznate paradigme poput chata, bez potrebe za tehničkom stručnošću ili obukom. Modeli se temelje na _upitima_ - korisnici šalju tekstualni unos (upit) i dobivaju AI odgovor (dovršetak). Zatim mogu "razgovarati s AI-jem" iterativno, u višekratnim razgovorima, usavršavajući svoj upit dok odgovor ne zadovolji njihova očekivanja.

"Upiti" sada postaju primarno _programsko sučelje_ za generativne AI aplikacije, govoreći modelima što da rade i utječući na kvalitetu dobivenih odgovora. "Oblikovanje upita" je brzo rastuće područje proučavanja koje se fokusira na _dizajn i optimizaciju_ upita kako bi se osigurali dosljedni i kvalitetni odgovori u velikim razmjerima.

## Ciljevi učenja

U ovoj lekciji naučit ćemo što je oblikovanje upita, zašto je važno i kako možemo osmisliti učinkovitije upite za određeni model i cilj aplikacije. Razumjet ćemo osnovne koncepte i najbolje prakse za oblikovanje upita - te ćemo naučiti o interaktivnom "sandbox" okruženju u Jupyter Notebooku gdje možemo primijeniti ove koncepte na stvarne primjere.

Na kraju ove lekcije moći ćemo:

1. Objasniti što je oblikovanje upita i zašto je važno.
2. Opisati komponente upita i kako se koriste.
3. Naučiti najbolje prakse i tehnike za oblikovanje upita.
4. Primijeniti naučene tehnike na stvarne primjere, koristeći OpenAI endpoint.

## Ključni pojmovi

Oblikovanje upita: Praksa dizajniranja i usavršavanja unosa kako bi se AI modeli usmjerili prema željenim izlazima.
Tokenizacija: Proces pretvaranja teksta u manje jedinice, zvane tokeni, koje model može razumjeti i obraditi.
Instrukcijski prilagođeni LLM-ovi: Veliki jezični modeli (LLM-ovi) koji su dodatno prilagođeni specifičnim uputama kako bi poboljšali točnost i relevantnost svojih odgovora.

## Sandbox za učenje

Oblikovanje upita trenutno je više umjetnost nego znanost. Najbolji način za poboljšanje intuicije za to je _više vježbati_ i usvojiti pristup pokušaja i pogrešaka koji kombinira stručnost u primjeni s preporučenim tehnikama i optimizacijama specifičnim za model.

Jupyter Notebook koji prati ovu lekciju pruža _sandbox_ okruženje u kojem možete isprobati ono što ste naučili - tijekom lekcije ili kao dio izazova kodiranja na kraju. Za izvođenje vježbi trebat će vam:

1. **Azure OpenAI API ključ** - krajnja točka usluge za implementirani LLM.
2. **Python Runtime** - u kojem se može izvršiti Notebook.
3. **Lokalne varijable okruženja** - _dovršite korake [POSTAVKE](./../00-course-setup/02-setup-local.md?WT.mc_id=academic-105485-koreyst) sada kako biste se pripremili_.

Notebook dolazi s _početnim_ vježbama - ali potičemo vas da dodate vlastite _Markdown_ (opis) i _Code_ (zahtjevi za upitima) sekcije kako biste isprobali više primjera ili ideja - i izgradili svoju intuiciju za dizajn upita.

## Ilustrirani vodič

Želite li dobiti širu sliku o tome što ova lekcija pokriva prije nego što se upustite u detalje? Pogledajte ovaj ilustrirani vodič koji vam daje uvid u glavne teme koje se obrađuju i ključne zaključke o kojima trebate razmisliti u svakoj od njih. Plan lekcije vodi vas od razumijevanja osnovnih koncepata i izazova do njihovog rješavanja relevantnim tehnikama oblikovanja upita i najboljim praksama. Napominjemo da se odjeljak "Napredne tehnike" u ovom vodiču odnosi na sadržaj obrađen u _sljedećem_ poglavlju ovog kurikuluma.

![Ilustrirani vodič za oblikovanje upita](../../../translated_images/04-prompt-engineering-sketchnote.d5f33336957a1e4f623b826195c2146ef4cc49974b72fa373de6929b474e8b70.hr.png)

## Naš startup

Sada, razgovarajmo o tome kako se _ova tema_ odnosi na našu misiju startupa da [donese AI inovacije u obrazovanje](https://educationblog.microsoft.com/2023/06/collaborating-to-bring-ai-innovation-to-education?WT.mc_id=academic-105485-koreyst). Želimo izgraditi AI aplikacije za _personalizirano učenje_ - pa razmislimo o tome kako bi različiti korisnici naše aplikacije mogli "dizajnirati" upite:

- **Administratori** bi mogli tražiti od AI-ja da _analizira podatke o kurikulumu kako bi identificirao praznine u pokrivenosti_. AI može sažeti rezultate ili ih vizualizirati pomoću koda.
- **Edukatori** bi mogli tražiti od AI-ja da _generira plan lekcije za ciljanu publiku i temu_. AI može izraditi personalizirani plan u određenom formatu.
- **Studenti** bi mogli tražiti od AI-ja da ih _podučava u teškom predmetu_. AI sada može voditi studente lekcijama, savjetima i primjerima prilagođenim njihovoj razini.

To je samo vrh ledenog brijega. Pogledajte [Upiti za obrazovanje](https://github.com/microsoft/prompts-for-edu/tree/main?WT.mc_id=academic-105485-koreyst) - otvorenu biblioteku upita koju su kurirali stručnjaci za obrazovanje - kako biste dobili širi uvid u mogućnosti! _Pokušajte pokrenuti neke od tih upita u sandboxu ili koristeći OpenAI Playground da vidite što se događa!_

## Što je oblikovanje upita?

Započeli smo ovu lekciju definiranjem **oblikovanja upita** kao procesa _dizajniranja i optimizacije_ tekstualnih unosa (upita) kako bi se osigurali dosljedni i kvalitetni odgovori (dovršetci) za određeni cilj aplikacije i model. Možemo razmišljati o tome kao o procesu u 2 koraka:

- _dizajniranje_ početnog upita za određeni model i cilj
- _usavršavanje_ upita iterativno kako bi se poboljšala kvaliteta odgovora

Ovo je nužno proces pokušaja i pogrešaka koji zahtijeva intuiciju korisnika i trud za postizanje optimalnih rezultata. Zašto je to važno? Da bismo odgovorili na to pitanje, prvo moramo razumjeti tri koncepta:

- _Tokenizacija_ = kako model "vidi" upit
- _Osnovni LLM-ovi_ = kako temeljni model "obrađuje" upit
- _Instrukcijski prilagođeni LLM-ovi_ = kako model sada vidi "zadatke"

### Tokenizacija

LLM vidi upite kao _niz tokena_ gdje različiti modeli (ili verzije modela) mogu tokenizirati isti upit na različite načine. Budući da su LLM-ovi obučeni na tokenima (a ne na sirovom tekstu), način na koji se upiti tokeniziraju ima izravan utjecaj na kvalitetu generiranog odgovora.

Da biste stekli intuiciju o tome kako tokenizacija funkcionira, isprobajte alate poput [OpenAI Tokenizer](https://platform.openai.com/tokenizer?WT.mc_id=academic-105485-koreyst) prikazanog dolje. Kopirajte svoj upit - i pogledajte kako se pretvara u tokene, obraćajući pažnju na to kako se obrađuju razmaci i interpunkcijski znakovi. Napominjemo da ovaj primjer prikazuje stariji LLM (GPT-3) - pa bi pokušaj s novijim modelom mogao proizvesti drugačiji rezultat.

![Tokenizacija](../../../translated_images/04-tokenizer-example.e71f0a0f70356c5c7d80b21e8753a28c18a7f6d4aaa1c4b08e65d17625e85642.hr.png)

### Koncept: Temeljni modeli

Nakon što se upit tokenizira, primarna funkcija ["Osnovnog LLM-a"](https://blog.gopenai.com/an-introduction-to-base-and-instruction-tuned-large-language-models-8de102c785a6?WT.mc_id=academic-105485-koreyst) (ili Temeljnog modela) je predvidjeti token u tom nizu. Budući da su LLM-ovi obučeni na ogromnim tekstualnim skupovima podataka, oni imaju dobar osjećaj za statističke odnose između tokena i mogu napraviti to predviđanje s određenom sigurnošću. Napominjemo da ne razumiju _značenje_ riječi u upitu ili tokenu; samo vide obrazac koji mogu "dovršiti" svojim sljedećim predviđanjem. Mogu nastaviti predviđati niz dok ih korisnik ne prekine ili dok se ne ispuni neki unaprijed postavljeni uvjet.

Želite li vidjeti kako funkcionira dovršavanje temeljeno na upitu? Unesite gornji upit u [_Chat Playground_](https://oai.azure.com/playground?WT.mc_id=academic-105485-koreyst) u Azure OpenAI Studio s zadanim postavkama. Sustav je konfiguriran da tretira upite kao zahtjeve za informacijama - pa biste trebali vidjeti dovršetak koji zadovoljava ovaj kontekst.

Ali što ako korisnik želi vidjeti nešto specifično što zadovoljava određene kriterije ili cilj zadatka? Tu dolaze _instrukcijski prilagođeni_ LLM-ovi.

![Dovršavanje chata osnovnog LLM-a](../../../translated_images/04-playground-chat-base.65b76fcfde0caa6738e41d20f1a6123f9078219e6f91a88ee5ea8014f0469bdf.hr.png)

### Koncept: Instrukcijski prilagođeni LLM-ovi

[Instrukcijski prilagođeni LLM](https://blog.gopenai.com/an-introduction-to-base-and-instruction-tuned-large-language-models-8de102c785a6?WT.mc_id=academic-105485-koreyst) započinje s temeljnim modelom i dodatno se prilagođava primjerima ili parovima ulaz/izlaz (npr. višekratnim "porukama") koji mogu sadržavati jasne upute - a odgovor AI-ja pokušava slijediti te upute.

Ovo koristi tehnike poput učenja pojačanja uz povratne informacije od ljudi (RLHF) koje mogu obučiti model da _slijedi upute_ i _uči iz povratnih informacija_ kako bi proizvodio odgovore koji su bolje prilagođeni praktičnim primjenama i relevantniji korisničkim ciljevima.

Pokušajmo to - ponovno posjetite gornji upit, ali sada promijenite _sistemski poruku_ kako biste dali sljedeću uputu kao kontekst:

> _Sažmi sadržaj koji ti je pružen za učenika drugog razreda. Zadrži rezultat u jednom odlomku s 3-5 točaka._

Vidite kako je rezultat sada prilagođen da odražava željeni cilj i format? Edukator sada može izravno koristiti ovaj odgovor u svojim prezentacijama za taj razred.

![Dovršavanje chata instrukcijski prilagođenog LLM-a](../../../translated_images/04-playground-chat-instructions.b30bbfbdf92f2d051639c9bc23f74a0e2482f8dc7f0dafc6cc6fda81b2b00534.hr.png)

## Zašto nam treba oblikovanje upita?

Sada kada znamo kako LLM-ovi obrađuju upite, razgovarajmo o _zašto_ nam treba oblikovanje upita. Odgovor leži u činjenici da trenutni LLM-ovi postavljaju niz izazova koji čine _pouzdane i dosljedne dovršetke_ teže postići bez ulaganja truda u konstrukciju i optimizaciju upita. Na primjer:

1. **Odgovori modela su stohastički.** _Isti upit_ vjerojatno će proizvesti različite odgovore s različitim modelima ili verzijama modela. I može čak proizvesti različite rezultate s _istim modelom_ u različito vrijeme. _Tehnike oblikovanja upita mogu nam pomoći minimizirati ove varijacije pružanjem boljih smjernica_.

1. **Modeli mogu izmišljati odgovore.** Modeli su unaprijed obučeni s _velikim ali ograničenim_ skupovima podataka, što znači da nemaju znanje o konceptima izvan tog opsega obuke. Kao rezultat toga, mogu proizvesti dovršetke koji su netočni, izmišljeni ili izravno kontradiktorni poznatim činjenicama. _Tehnike oblikovanja upita pomažu korisnicima identificirati i ublažiti takve izmišljotine, npr. traženjem od AI-ja citata ili obrazloženja_.

1. **Sposobnosti modela će varirati.** Noviji modeli ili generacije modela imat će bogatije sposobnosti, ali također donose jedinstvene osobitosti i kompromise u troškovima i složenosti. _Oblikovanje upita može nam pomoći razviti najbolje prakse i radne tokove koji apstrahiraju razlike i prilagođavaju se zahtjevima specifičnim za model na skalabilan i besprijekoran način_.

Pogledajmo ovo u praksi u OpenAI ili Azure OpenAI Playgroundu:

- Koristite isti upit s različitim LLM implementacijama (npr. OpenAI, Azure OpenAI, Hugging Face) - jeste li primijetili varijacije?
- Koristite isti upit više puta s _istom_ LLM implementacijom (npr. Azure OpenAI Playground) - kako su se te varijacije razlikovale?

### Primjer izmišljotina

U ovom tečaju koristimo izraz **"izmišljotina"** za označavanje fenomena kada LLM-ovi ponekad generiraju činjenično netočne informacije zbog ograničenja u njihovoj obuci ili drugih ograničenja. Možda ste također čuli da se to naziva _"halucinacijama"_ u popularnim člancima ili istraživačkim radovima. Međutim, snažno preporučujemo korištenje izraza _"izmišljotina"_ kako ne bismo slučajno antropomorfizirali ponašanje pripisujući ljudsku osobinu ishodu vođenom strojem. Ovo također jača [smjernice za odgovornu AI](https://www.microsoft.com/ai/responsible-ai?WT.mc_id=academic-105485-koreyst) s terminološke perspektive, uklanjajući izraze koji bi također mogli biti smatrani uvredljivima ili neuključivima u nekim kontekstima.

Želite li steći osjećaj kako izmišljotine funkcioniraju? Smislite upit koji upućuje AI da generira sadržaj za nepostojeću temu (kako biste osigurali da se ne nalazi u skupu podataka za obuku). Na primjer - pokušao sam s ovim upitom:

> **Upit:** generiraj plan lekcije o Marsovskom ratu iz 2076.
Pretraživanje na internetu pokazalo mi je da postoje izmišljeni prikazi (npr. televizijske serije ili knjige) o Marsovskim ratovima - ali nijedan iz 2076. Zdrav razum nam također govori da je 2076. _u budućnosti_ i stoga ne može biti povezana s stvarnim događajem.

Što se događa kada pokrenemo ovaj upit s različitim pružateljima LLM-a?

> **Odgovor 1**: OpenAI Playground (GPT-35)

![Odgovor 1](../../../translated_images/04-fabrication-oai.5818c4e0b2a2678c40e0793bf873ef4a425350dd0063a183fb8ae02cae63aa0c.hr.png)

> **Odgovor 2**: Azure OpenAI Playground (GPT-35)

![Odgovor 2](../../../translated_images/04-fabrication-aoai.b14268e9ecf25caf613b7d424c16e2a0dc5b578f8f960c0c04d4fb3a68e6cf61.hr.png)

> **Odgovor 3**: Hugging Face Chat Playground (LLama-2)

![Odgovor 3](../../../translated_images/04-fabrication-huggingchat.faf82a0a512789565e410568bce1ac911075b943dec59b1ef4080b61723b5bf4.hr.png)

Kao što se očekivalo, svaki model (ili verzija modela) proizvodi malo drugačije odgovore zahvaljujući stohastičkom ponašanju i varijacijama u sposobnostima modela. Na primjer, jedan model cilja publiku osmog razreda, dok drugi pretpostavlja srednjoškolsku razinu. No, sva tri modela generirala su odgovore koji bi mogli uvjeriti neinformiranog korisnika da je događaj stvaran.

Tehnike oblikovanja upita, poput _metapromptinga_ i _konfiguracije temperature_, mogu donekle smanjiti izmišljotine modela. Nove arhitekture za oblikovanje upita također integriraju nove alate i tehnike u tijek upita kako bi ublažile ili smanjile neke od ovih učinaka.

## Studija slučaja: GitHub Copilot

Završimo ovaj dio dobivanjem uvida u to kako se oblikovanje upita koristi u stvarnim rješenjima, pogledom na jednu studiju slučaja: [GitHub Copilot](https://github.com/features/copilot?WT.mc_id=academic-105485-koreyst).

GitHub Copilot je vaš "AI suprogramer" - pretvara tekstualne upite u prijedloge koda i integriran je u vaše razvojno okruženje (npr. Visual Studio Code) za besprijekorno korisničko iskustvo. Kao što je dokumentirano u seriji blogova u nastavku, najranija verzija temeljila se na OpenAI Codex modelu - s inženjerima koji su brzo shvatili potrebu za finim podešavanjem modela i razvojem boljih tehnika oblikovanja upita kako bi poboljšali kvalitetu koda. U srpnju su [predstavili poboljšani AI model koji nadilazi Codex](https://github.blog/2023-07-28-smarter-more-efficient-coding-github-copilot-goes-beyond-codex-with-improved-ai-model/?WT.mc_id=academic-105485-koreyst) za još brže prijedloge.

Pročitajte postove redoslijedom kako biste pratili njihov put učenja.

- **Svibanj 2023** | [GitHub Copilot postaje bolji u razumijevanju vašeg koda](https://github.blog/2023-05-17-how-github-copilot-is-getting-better-at-understanding-your-code/?WT.mc_id=academic-105485-koreyst)
- **Svibanj 2023** | [Unutar GitHuba: Rad s LLM-ovima iza GitHub Copilota](https://github.blog/2023-05-17-inside-github-working-with-the-llms-behind-github-copilot/?WT.mc_id=academic-105485-koreyst).
- **Lipanj 2023** | [Kako pisati bolje upite za GitHub Copilot](https://github.blog/2023-06-20-how-to-write-better-prompts-for-github-copilot/?WT.mc_id=academic-105485-koreyst).
- **Srpanj 2023** | [.. GitHub Copilot nadilazi Codex s poboljšanim AI modelom](https://github.blog/2023-07-28-smarter-more-efficient-coding-github-copilot-goes-beyond-codex-with-improved-ai-model/?WT.mc_id=academic-105485-koreyst)
- **Srpanj 2023** | [Vodič za programere o oblikovanju upita i LLM-ovima](https://github.blog/2023-07-17-prompt-engineering-guide-generative-ai-llms/?WT.mc_id=academic-105485-koreyst)
- **Rujan 2023** | [Kako izgraditi LLM aplikaciju za poduzeća: Lekcije iz GitHub Copilota](https://github.blog/2023-09-06-how-to-build-an-enterprise-llm-application-lessons-from-github-copilot/?WT.mc_id=academic-105485-koreyst)

Također možete pregledati njihov [inženjerski blog](https://github.blog/category/engineering/?WT.mc_id=academic-105485-koreyst) za više postova poput [ovog](https://github.blog/2023-09-27-how-i-used-github-copilot-chat-to-build-a-reactjs-gallery-prototype/?WT.mc_id=academic-105485-koreyst) koji pokazuje kako se ovi modeli i tehnike _primjenjuju_ za pokretanje stvarnih aplikacija.

---

## Konstrukcija upita

Vidjeli smo zašto je oblikovanje upita važno - sada ćemo razumjeti kako se upiti _konstruiraju_ kako bismo mogli procijeniti različite tehnike za učinkovitiji dizajn upita.

### Osnovni upit

Počnimo s osnovnim upitom: tekstualni unos koji se šalje modelu bez dodatnog konteksta. Evo primjera - kada pošaljemo prve riječi američke nacionalne himne OpenAI [Completion API](https://platform.openai.com/docs/api-reference/completions?WT.mc_id=academic-105485-koreyst), ona odmah _dovršava_ odgovor s idućim stihovima, ilustrirajući osnovno prediktivno ponašanje.

| Upit (Ulaz)     | Dovršetak (Izlaz)                                                                                                                        |
| :-------------- | :---------------------------------------------------------------------------------------------------------------------------------------- |
| Oh say can you see | Izgleda da započinjete stihove pjesme "The Star-Spangled Banner", nacionalne himne Sjedinjenih Američkih Država. Cijeli stihovi su ... |

### Složeni upit

Sada dodajmo kontekst i upute tom osnovnom upitu. [Chat Completion API](https://learn.microsoft.com/azure/ai-services/openai/how-to/chatgpt?WT.mc_id=academic-105485-koreyst) omogućuje nam konstrukciju složenog upita kao zbirke _poruka_ s:

- Parovima ulaz/izlaz koji odražavaju _korisnički_ unos i _odgovor asistenta_.
- Porukom sustava koja postavlja kontekst za ponašanje ili osobnost asistenta.

Zahtjev sada ima oblik prikazan dolje, gdje _tokenizacija_ učinkovito bilježi relevantne informacije iz konteksta i razgovora. Promjena konteksta sustava može biti jednako utjecajna na kvalitetu dovršetaka kao i pruženi korisnički unosi.

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

### Upit s uputama

U gore navedenim primjerima, korisnički upit bio je jednostavan tekstualni upit koji se može interpretirati kao zahtjev za informacijama. S _uputama_ u upitima, možemo koristiti taj tekst za detaljnije specificiranje zadatka, pružajući bolju smjernicu AI-u. Evo primjera:

| Upit (Ulaz)                                                                                                                                                                                                                         | Dovršetak (Izlaz)                                                                                                        | Vrsta upute         |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------- | :------------------ |
| Napiši opis Građanskog rata                                                                                                                                                                                                        | _vraćen jednostavan odlomak_                                                                                             | Jednostavna         |
| Napiši opis Građanskog rata. Navedi ključne datume i događaje te opiši njihovu važnost                                                                                                                                             | _vraćen odlomak praćen popisom ključnih datuma događaja s opisima_                                                       | Složena             |
| Napiši opis Građanskog rata u jednom odlomku. Navedi 3 ključna datuma i njihovu važnost u obliku točaka. Navedi još 3 ključne povijesne osobe i njihove doprinose. Vrati izlaz u obliku JSON datoteke.                              | _vraćeni su opsežniji detalji u tekstualnom okviru, formatirani kao JSON koji možete kopirati i zalijepiti u datoteku te provjeriti po potrebi_ | Složena. Formatirana.|

## Primarni sadržaj

U gore navedenim primjerima, upit je još uvijek bio prilično otvoren, dopuštajući LLM-u da odluči koji je dio njegovog unaprijed treniranog skupa podataka relevantan. S dizajnerskim uzorkom _primarnog sadržaja_, ulazni tekst podijeljen je na dva dijela:

- uputu (radnja)
- relevantan sadržaj (koji utječe na radnju)

Evo primjera gdje je uputa "sažmi ovo u 2 rečenice".

| Upit (Ulaz)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Dovršetak (Izlaz)                                                                                                                                                                                                                                                                             |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Jupiter je peti planet od Sunca i najveći u Sunčevom sustavu. To je plinoviti div s masom tisućiti dio mase Sunca, ali dva i pol puta većom od mase svih ostalih planeta u Sunčevom sustavu zajedno. Jupiter je jedan od najsjajnijih objekata vidljivih golim okom na noćnom nebu i poznat je drevnim civilizacijama od prije zabilježene povijesti. Ime je dobio po rimskom bogu Jupiteru.[19] Kada se gleda sa Zemlje, Jupiter može biti dovoljno svijetao da njegova reflektirana svjetlost baca vidljive sjene,[20] i prosječno je treći najsvjetliji prirodni objekt na noćnom nebu nakon Mjeseca i Venere. <br/> **Sažmi ovo u 2 kratke rečenice** | Jupiter, peti planet od Sunca, najveći je u Sunčevom sustavu i poznat je kao jedan od najsjajnijih objekata na noćnom nebu. Nazvan po rimskom bogu Jupiteru, to je plinoviti div čija je masa dva i pol puta veća od mase svih ostalih planeta u Sunčevom sustavu zajedno. |

Segment primarnog sadržaja može se koristiti na različite načine za učinkovitije davanje uputa:

- **Primjeri** - umjesto da modelu izričito kažete što treba učiniti, dajte mu primjere željenog izlaza i dopustite mu da zaključi obrazac.
- **Smjernice** - pratite uputu s "smjernicom" koja usmjerava dovršetak, vodeći model prema relevantnijim odgovorima.
- **Predlošci** - to su ponovljivi 'recepti' za upite s rezerviranim mjestima (varijablama) koje se mogu prilagoditi podacima za specifične slučajeve.

Istražimo ove primjere u praksi.

### Korištenje primjera

Ovo je pristup gdje koristite primarni sadržaj kako biste "nahranili model" nekim primjerima željenog izlaza za određenu uputu i dopustili mu da zaključi obrazac za željeni izlaz. Na temelju broja pruženih primjera, možemo imati upite bez primjera, s jednim primjerom, s nekoliko primjera itd.

Upit sada sadrži tri komponente:

- Opis zadatka
- Nekoliko primjera željenog izlaza
- Početak novog primjera (koji postaje implicitni opis zadatka)

| Vrsta učenja | Upit (Ulaz)                                                                                                                                        | Dovršetak (Izlaz)         |
| :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------ | :------------------------ |
| Bez primjera | "Sunce sja". Prevedi na španjolski                                                                                                                | "El Sol está brillando".  |
| Jedan primjer | "Sunce sja" => ""El Sol está brillando". <br> "Hladan i vjetrovit dan" =>                                                                         | "Es un día frío y ventoso". |
| Nekoliko primjera | Igrač je trčao po bazama => Baseball <br/> Igrač je pogodio as => Tenis <br/> Igrač je pogodio šesticu => Kriket <br/> Igrač je zakucao loptu => | Košarka                  |
|               |                                                                                                                                                   |                           |

Primijetite kako smo morali pružiti eksplicitnu uputu ("Prevedi na španjolski") u upitu bez primjera, ali ona se zaključuje u primjeru s jednim primjerom. Primjer s nekoliko primjera pokazuje kako dodavanje više primjera omogućuje modelima da donesu točnije zaključke bez dodatnih uputa.

### Smjernice u upitu

Druga tehnika za korištenje primarnog sadržaja je pružanje _smjernica_ umjesto primjera. U ovom slučaju, dajemo modelu poticaj u pravom smjeru _započinjanjem_ s isječkom koji odražava željeni format odgovora. Model tada "prihvaća smjernicu" i nastavlja u tom tonu.

| Broj smjernica | Upit (Ulaz)                                                                                                                                                                                                                                                                                                                                                                                                                                               | Dovršetak (Izlaz)                                                                                                                                                                                                                                                                                       |
| :------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0              | Jupiter je peti planet od Sunca i najveći u Sunčevom sustavu. To je plinoviti div s masom tisućiti dio mase Sunca, ali dva i pol puta većom od mase svih ostalih planeta u Sunčevom sustavu zajedno. Jupiter je jedan od najsjajnijih objekata vidljivih golim okom na noćnom nebu i poznat je drevnim civilizacijama od prije zabilježene povijesti. <br/>**Sažmi ovo**                                       | Jupiter je najveći planet u našem Sunčevom sustavu i peti od Sunca. To je plinoviti div s masom 1/1000 mase Sunca, ali teži od svih ostalih planeta zajedno. Drevne civilizacije poznaju Jupiter već dugo, a lako je vidljiv na noćnom nebu. |
| 1              | Jupiter je peti planet od Sunca i najveći u Sunčevom sustavu. To je plinoviti div s masom koja je tisućiti dio mase Sunca, ali dva i pol puta veća od mase svih ostalih planeta u Sunčevom sustavu zajedno. Jupiter je jedan od najsjajnijih objekata vidljivih golim okom na noćnom nebu i poznat je drevnim civilizacijama od prije pisane povijesti. <br/>**Sažmi ovo** <br/> Naučili smo da je Jupiter | peti planet od Sunca i najveći u Sunčevom sustavu. To je plinoviti div s masom koja je tisućiti dio mase Sunca, ali dva i pol puta veća od mase svih ostalih planeta zajedno. Lako je vidljiv golim okom i poznat je od davnina.                        |
| 2              | Jupiter je peti planet od Sunca i najveći u Sunčevom sustavu. To je plinoviti div s masom koja je tisućiti dio mase Sunca, ali dva i pol puta veća od mase svih ostalih planeta u Sunčevom sustavu zajedno. Jupiter je jedan od najsjajnijih objekata vidljivih golim okom na noćnom nebu i poznat je drevnim civilizacijama od prije pisane povijesti. <br/>**Sažmi ovo** <br/> Top 3 činjenice koje smo naučili:         | 1. Jupiter je peti planet od Sunca i najveći u Sunčevom sustavu. <br/> 2. To je plinoviti div s masom koja je tisućiti dio mase Sunca...<br/> 3. Jupiter je vidljiv golim okom od davnina ...                                                                       |
|                |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                                                                                                                                                                                                                                                                                           |

### Predlošci za upite

Predložak za upit je _unaprijed definirani recept za upit_ koji se može pohraniti i ponovno koristiti po potrebi, kako bi se omogućilo dosljedno korisničko iskustvo u velikom opsegu. U svom najjednostavnijem obliku, to je jednostavno zbirka primjera upita poput [ovog od OpenAI](https://platform.openai.com/examples?WT.mc_id=academic-105485-koreyst) koji pruža interaktivne komponente upita (poruke korisnika i sustava) i format zahtjeva temeljen na API-ju - za podršku ponovnoj upotrebi.

U svom složenijem obliku, poput [ovog primjera iz LangChain](https://python.langchain.com/docs/concepts/prompt_templates/?WT.mc_id=academic-105485-koreyst), sadrži _mjesta za unos_ koja se mogu zamijeniti podacima iz različitih izvora (korisnički unos, kontekst sustava, vanjski izvori podataka itd.) kako bi se dinamički generirao upit. To nam omogućuje stvaranje biblioteke upita koji se mogu koristiti za dosljedno korisničko iskustvo **programski** u velikom opsegu.

Na kraju, prava vrijednost predložaka leži u mogućnosti stvaranja i objavljivanja _biblioteka upita_ za vertikalne aplikacijske domene - gdje je predložak upita sada _optimiziran_ kako bi odražavao kontekst specifičan za aplikaciju ili primjere koji odgovore čine relevantnijima i točnijima za ciljanu publiku korisnika. [Prompts For Edu](https://github.com/microsoft/prompts-for-edu?WT.mc_id=academic-105485-koreyst) repozitorij je izvrstan primjer ovog pristupa, koji prikuplja biblioteku upita za obrazovnu domenu s naglaskom na ključne ciljeve poput planiranja lekcija, dizajna kurikuluma, podučavanja učenika itd.

## Pomoćni sadržaj

Ako razmišljamo o konstrukciji upita kao o zadatku (instrukcija) i cilju (primarni sadržaj), tada _sekundarni sadržaj_ predstavlja dodatni kontekst koji pružamo kako bismo **utjecali na izlaz na neki način**. To mogu biti parametri za podešavanje, upute za formatiranje, taksonomije tema itd., koji mogu pomoći modelu da _prilagodi_ svoj odgovor željenim ciljevima ili očekivanjima korisnika.

Na primjer: S obzirom na katalog tečajeva s opsežnim metapodacima (naziv, opis, razina, oznake metapodataka, instruktor itd.) o svim dostupnim tečajevima u kurikulumu:

- možemo definirati instrukciju "sažmi katalog tečajeva za jesen 2023."
- možemo koristiti primarni sadržaj za pružanje nekoliko primjera željenog izlaza
- možemo koristiti sekundarni sadržaj za identifikaciju 5 najvažnijih "oznaka".

Sada model može pružiti sažetak u formatu prikazanom kroz nekoliko primjera - ali ako rezultat ima više oznaka, može prioritizirati 5 oznaka identificiranih u sekundarnom sadržaju.

---

<!--
PREDLOŽAK LEKCIJE:
Ova jedinica treba pokriti osnovni koncept #1.
Ojačajte koncept primjerima i referencama.

KONCEPT #3:
Tehnike za oblikovanje upita.
Koje su osnovne tehnike za oblikovanje upita?
Ilustrirajte ih vježbama.
-->

## Najbolje prakse za oblikovanje upita

Sada kada znamo kako se upiti mogu _konstruirati_, možemo početi razmišljati o tome kako ih _dizajnirati_ prema najboljim praksama. Možemo razmišljati o tome u dva dijela - imati pravi _mentalni sklop_ i primijeniti prave _tehnike_.

### Mentalni sklop za oblikovanje upita

Oblikovanje upita je proces pokušaja i pogrešaka, stoga imajte na umu tri široka čimbenika:

1. **Razumijevanje domene je važno.** Točnost i relevantnost odgovora ovise o _domeni_ u kojoj aplikacija ili korisnik djeluje. Primijenite svoju intuiciju i stručnost u domeni kako biste dodatno **prilagodili tehnike**. Na primjer, definirajte _osobnosti specifične za domenu_ u upitima sustava ili koristite _predloške specifične za domenu_ u korisničkim upitima. Pružite sekundarni sadržaj koji odražava kontekste specifične za domenu ili koristite _naznake i primjere specifične za domenu_ kako biste usmjerili model prema poznatim obrascima korištenja.

2. **Razumijevanje modela je važno.** Znamo da su modeli stohastičke prirode. No, implementacije modela također se mogu razlikovati u pogledu skupa podataka za obuku koji koriste (predobučeno znanje), mogućnosti koje pružaju (npr. putem API-ja ili SDK-a) i vrste sadržaja za koje su optimizirani (npr. kod, slike, tekst). Razumijte snage i ograničenja modela koji koristite i iskoristite to znanje za _prioritetizaciju zadataka_ ili izgradnju _prilagođenih predložaka_ optimiziranih za mogućnosti modela.

3. **Iteracija i validacija su važne.** Modeli se brzo razvijaju, kao i tehnike za oblikovanje upita. Kao stručnjak za domenu, možda imate dodatni kontekst ili kriterije specifične za _vašu_ aplikaciju, koji možda ne vrijede za širu zajednicu. Koristite alate i tehnike za oblikovanje upita kako biste "započeli" konstrukciju upita, zatim iterirajte i validirajte rezultate koristeći vlastitu intuiciju i stručnost u domeni. Zabilježite svoja saznanja i stvorite **bazu znanja** (npr. biblioteke upita) koja se može koristiti kao nova osnova za brže iteracije u budućnosti.

## Najbolje prakse

Sada pogledajmo uobičajene najbolje prakse koje preporučuju [OpenAI](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-openai-api?WT.mc_id=academic-105485-koreyst) i [Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/concepts/prompt-engineering#best-practices?WT.mc_id=academic-105485-koreyst) praktičari.

| Što                              | Zašto                                                                                                                                                                                                                                               |
| :-------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Procijenite najnovije modele.       | Generacije novih modela vjerojatno imaju poboljšane značajke i kvalitetu - ali mogu također uzrokovati veće troškove. Procijenite njihov utjecaj, a zatim donesite odluke o migraciji.                                                                                |
| Odvojite instrukcije i kontekst   | Provjerite definira li vaš model/provajder _graničnike_ za jasnije razlikovanje instrukcija, primarnog i sekundarnog sadržaja. To može pomoći modelima da točnije dodijele težinu tokenima.                                                         |
| Budite specifični i jasni             | Dajte više detalja o željenom kontekstu, ishodu, duljini, formatu, stilu itd. To će poboljšati i kvalitetu i dosljednost odgovora. Zabilježite recepte u predlošcima koji se mogu ponovno koristiti.                                                          |
| Budite opisni, koristite primjere      | Modeli mogu bolje reagirati na pristup "pokaži i reci". Započnite s pristupom `zero-shot` gdje mu dajete instrukciju (ali bez primjera), a zatim pokušajte `few-shot` kao doradu, pružajući nekoliko primjera željenog izlaza. Koristite analogije. |
| Koristite naznake za pokretanje odgovora | Usmjerite ga prema željenom ishodu dajući mu nekoliko početnih riječi ili fraza koje može koristiti kao polazište za odgovor.                                                                                                               |
| Ponovite                       | Ponekad ćete morati ponoviti svoje upute modelu. Dajte instrukcije prije i nakon vašeg primarnog sadržaja, koristite instrukciju i naznaku itd. Iterirajte i validirajte kako biste vidjeli što najbolje funkcionira.                                                         |
| Redoslijed je važan                     | Redoslijed kojim predstavljate informacije modelu može utjecati na izlaz, čak i u primjerima učenja, zahvaljujući pristranosti prema novijim informacijama. Isprobajte različite opcije kako biste vidjeli što najbolje funkcionira.                                                               |
| Dajte modelu "izlaz"           | Dajte modelu _rezervni_ odgovor koji može pružiti ako iz bilo kojeg razloga ne može dovršiti zadatak. To može smanjiti šanse da modeli generiraju lažne ili izmišljene odgovore.                                                         |
|                                   |                                                                                                                                                                                                                                                   |

Kao i kod svake najbolje prakse, zapamtite da _vaše iskustvo može varirati_ ovisno o modelu, zadatku i domeni. Koristite ih kao početnu točku i iterirajte kako biste otkrili što najbolje funkcionira za vas. Neprestano ponovno procjenjujte svoj proces oblikovanja upita kako postaju dostupni novi modeli i alati, s fokusom na skalabilnost procesa i kvalitetu odgovora.

<!--
PREDLOŽAK LEKCIJE:
Ova jedinica treba pružiti izazov s kodom, ako je primjenjivo.

IZAZOV:
Poveznica na Jupyter Notebook s samo komentarima u kodu u uputama (sekcije koda su prazne).

RJEŠENJE:
Poveznica na kopiju tog Notebooka s ispunjenim i pokrenutim upitima, pokazujući što bi mogao biti jedan primjer.
-->

## Zadatak

Čestitamo! Došli ste do kraja lekcije! Vrijeme je da testirate neke od tih koncepata i tehnika s pravim primjerima!

Za naš zadatak koristit ćemo Jupyter Notebook s vježbama koje možete interaktivno dovršiti. Također možete proširiti Notebook s vlastitim Markdown i Code ćelijama kako biste istražili ideje i tehnike na vlastitu inicijativu.

### Za početak, napravite fork repozitorija, zatim

- (Preporučeno) Pokrenite GitHub Codespaces
- (Alternativno) Klonirajte repozitorij na svoj lokalni uređaj i koristite ga s Docker Desktop
- (Alternativno) Otvorite Notebook s vašim preferiranim runtime okruženjem za Notebook.

### Zatim konfigurirajte varijable okruženja

- Kopirajte datoteku `.env.copy` u korijenu repozitorija u `.env` i ispunite vrijednosti `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_ENDPOINT` i `AZURE_OPENAI_DEPLOYMENT`. Vratite se na [sekciju Learning Sandbox](../../../04-prompt-engineering-fundamentals/04-prompt-engineering-fundamentals) kako biste saznali kako.

### Zatim otvorite Jupyter Notebook

- Odaberite runtime kernel. Ako koristite opcije 1 ili 2, jednostavno odaberite zadani Python 3.10.x kernel koji pruža dev container.

Spremni ste za pokretanje vježbi. Imajte na umu da ovdje nema _točnih i netočnih_ odgovora - samo istražujete opcije metodom pokušaja i pogrešaka i gradite intuiciju za ono što funkcionira za određeni model i aplikacijsku domenu.

_Iz tog razloga u ovoj lekciji nema segmenata s rješenjima koda. Umjesto toga, Notebook će imati Markdown ćelije naslovljene "Moje rješenje:" koje prikazuju jedan primjer izlaza za referencu._

 <!--
PREDLOŽAK LEKCIJE:
Završite sekciju sa sažetkom i resursima za samostalno učenje.
-->

## Provjera znanja

Koji od sljedećih upita je dobar primjer koji slijedi razumne najbolje prakse?

1. Pokaži mi sliku crvenog automobila
2. Pokaži mi sliku crvenog automobila marke Volvo i modela XC90 parkiranog uz liticu s zalaskom sunca
3. Pokaži mi sliku crvenog automobila marke Volvo i modela XC90

O: 2, to je najbolji upit jer pruža detalje o "čemu" i ide u specifičnosti (ne samo bilo koji automobil, već određena marka i model) te također opisuje cjelokupni ambijent. 3 je sljedeći najbolji jer također sadrži puno opisa.

## 🚀 Izazov

Pokušajte iskoristiti tehniku "naznake" s upitom: Dovrši rečenicu "Pokaži mi sliku crvenog automobila marke Volvo i ". Što odgovara, i kako biste to poboljšali?

## Sjajan rad! Nastavite učiti

Želite li saznati više o različitim konceptima oblikovanja upita? Posjetite [stranicu za nastavak učenja](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst) kako biste pronašli druge izvrsne resurse o ovoj temi.

Prijeđite na Lekciju 5 gdje ćemo pogledati [napredne tehnike oblikovanja upita](../05-advanced-prompts/README.md?WT.mc_id=academic-105485-koreyst)!

---

**Izjava o odricanju odgovornosti**:  
Ovaj dokument je preveden pomoću AI usluge za prevođenje [Co-op Translator](https://github.com/Azure/co-op-translator). Iako nastojimo osigurati točnost, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati autoritativnim izvorom. Za ključne informacije preporučuje se profesionalni prijevod od strane čovjeka. Ne preuzimamo odgovornost za nesporazume ili pogrešna tumačenja koja mogu proizaći iz korištenja ovog prijevoda.