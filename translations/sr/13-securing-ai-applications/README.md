<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a2faf8ee7a0b851efa647a19788f1e5b",
  "translation_date": "2025-10-18T01:18:15+00:00",
  "source_file": "13-securing-ai-applications/README.md",
  "language_code": "sr"
}
-->
# Обезбеђивање ваших апликација заснованих на генеративној вештачкој интелигенцији

[![Обезбеђивање ваших апликација заснованих на генеративној вештачкој интелигенцији](../../../translated_images/13-lesson-banner.14103e36b4bbf17398b64ed2b0531f6f2c6549e7f7342f797c40bcae5a11862e.sr.png)](https://youtu.be/m0vXwsx5DNg?si=TYkr936GMKz15K0L)

## Увод

Ова лекција обухвата:

- Безбедност у контексту система заснованих на вештачкој интелигенцији.
- Уобичајене ризике и претње за системе засноване на вештачкој интелигенцији.
- Методе и разматрања за обезбеђивање система заснованих на вештачкој интелигенцији.

## Циљеви учења

Након завршетка ове лекције, имаћете разумевање:

- Претњи и ризика за системе засноване на вештачкој интелигенцији.
- Уобичајених метода и пракси за обезбеђивање система заснованих на вештачкој интелигенцији.
- Како имплементација тестирања безбедности може спречити неочекиване резултате и губитак поверења корисника.

## Шта значи безбедност у контексту генеративне вештачке интелигенције?

Како технологије вештачке интелигенције (AI) и машинског учења (ML) све више обликују наше животе, кључно је заштитити не само податке корисника, већ и саме системе засноване на вештачкој интелигенцији. AI/ML се све више користе за подршку процесима доношења одлука високог значаја у индустријама где погрешна одлука може имати озбиљне последице.

Ево кључних тачака које треба узети у обзир:

- **Утицај AI/ML**: AI/ML имају значајан утицај на свакодневни живот, и због тога је њихова заштита постала неопходна.
- **Изазови безбедности**: Овај утицај AI/ML захтева адекватну пажњу како би се задовољила потреба за заштитом производа заснованих на вештачкој интелигенцији од софистицираних напада, било да су у питању тролови или организоване групе.
- **Стратешки проблеми**: Технолошка индустрија мора проактивно приступити решавању стратешких изазова како би осигурала дугорочну безбедност корисника и података.

Поред тога, модели машинског учења углавном нису у стању да разликују злонамерне уносе од безазлених аномалија у подацима. Значајан извор података за обуку потиче из неконтролисаних, немодерисаних јавних скупова података, који су отворени за доприносе трећих страна. Нападачи не морају да компромитују скупове података када могу слободно да доприносе њима. Временом, подаци са ниским нивоом поверења постају подаци са високим нивоом поверења, ако структура/форматирање података остане исправно.

Због тога је од суштинске важности осигурати интегритет и заштиту складишта података које ваши модели користе за доношење одлука.

## Разумевање претњи и ризика за AI

Када је реч о вештачкој интелигенцији и повезаним системима, тровање подацима се истиче као најзначајнија безбедносна претња данас. Тровање подацима се дешава када неко намерно промени информације које се користе за обуку AI, узрокујући да прави грешке. Ово је последица недостатка стандардизованих метода за детекцију и ублажавање, у комбинацији са ослањањем на непоуздане или неконтролисане јавне скупове података за обуку. Да би се одржао интегритет података и спречио погрешан процес обуке, кључно је пратити порекло и линију ваших података. У супротном, стара изрека „смеће улази, смеће излази“ остаје тачна, што доводи до компромитованих перформанси модела.

Ево примера како тровање подацима може утицати на ваше моделе:

1. **Обртање ознака**: У задатку бинарне класификације, противник намерно мења ознаке малог дела података за обуку. На пример, безазлени узорци се означавају као злонамерни, што доводи до тога да модел учи погрешне асоцијације.\
   **Пример**: Филтер за нежељену пошту погрешно класификује легитимне имејлове као нежељену пошту због манипулисаних ознака.
2. **Тровање карактеристикама**: Нападач суптилно модификује карактеристике у подацима за обуку како би увео пристрасност или довео модел у заблуду.\
   **Пример**: Додавање небитних кључних речи у описе производа ради манипулације системима препорука.
3. **Убацивање података**: Убацивање злонамерних података у скуп за обуку ради утицаја на понашање модела.\
   **Пример**: Увођење лажних корисничких рецензија ради искривљавања резултата анализе сентимента.
4. **Напади задњих врата**: Противник убацује скривени образац (задња врата) у податке за обуку. Модел учи да препознаје овај образац и понаша се злонамерно када се активира.\
   **Пример**: Систем за препознавање лица обучен са сликама које садрже задња врата, погрешно идентификује одређену особу.

Корпорација MITRE је креирала [ATLAS (Adversarial Threat Landscape for Artificial-Intelligence Systems)](https://atlas.mitre.org/?WT.mc_id=academic-105485-koreyst), базу знања о тактикама и техникама које користе противници у стварним нападима на системе засноване на вештачкој интелигенцији.

> Постоји све већи број рањивости у системима заснованим на вештачкој интелигенцији, јер њихово укључивање повећава површину напада постојећих система изван традиционалних сајбер-напада. Развили смо ATLAS како бисмо подигли свест о овим јединственим и еволуирајућим рањивостима, јер глобална заједница све више укључује вештачку интелигенцију у различите системе. ATLAS је моделован по узору на MITRE ATT&CK® оквир, а његове тактике, технике и процедуре (TTPs) су комплементарне онима у ATT&CK.

Као и MITRE ATT&CK® оквир, који се широко користи у традиционалној сајбер-безбедности за планирање напредних сценарија емулације претњи, ATLAS пружа лако претраживан сет TTP-ова који могу помоћи у бољем разумевању и припреми за одбрану од нових напада.

Поред тога, Open Web Application Security Project (OWASP) је креирао "[Топ 10 листу](https://llmtop10.com/?WT.mc_id=academic-105485-koreyst)" најкритичнијих рањивости које се налазе у апликацијама које користе LLM-ове. Листа истиче ризике од претњи као што су поменуто тровање подацима, као и других, као што су:

- **Убризгавање упита**: техника где нападачи манипулишу великим језичким моделом (LLM) кроз пажљиво осмишљене уносе, узрокујући да се понаша ван своје предвиђене функције.
- **Ризици у ланцу снабдевања**: Компоненте и софтвер који чине апликације које користе LLM, као што су Python модули или спољни скупови података, могу бити компромитовани, што доводи до неочекиваних резултата, уведених пристрасности, па чак и рањивости у основној инфраструктури.
- **Прекомерно ослањање**: LLM-ови су подложни грешкама и склони су „халуцинацијама“, пружајући нетачне или небезбедне резултате. У неколико документованих случајева, људи су прихватили резултате као чињенице, што је довело до нежељених негативних последица у стварном свету.

Microsoft Cloud Advocate Род Трент је написао бесплатну електронску књигу, [Морате научити AI безбедност](https://github.com/rod-trent/OpenAISecurity/tree/main/Must_Learn/Book_Version?WT.mc_id=academic-105485-koreyst), која дубоко истражује ове и друге нове претње вештачке интелигенције и пружа опсежне смернице о томе како најбоље приступити овим сценаријима.

## Тестирање безбедности за AI системе и LLM-ове

Вештачка интелигенција (AI) трансформише различите домене и индустрије, нудећи нове могућности и користи за друштво. Међутим, AI такође представља значајне изазове и ризике, као што су приватност података, пристрасност, недостатак објашњивости и потенцијална злоупотреба. Због тога је кључно осигурати да AI системи буду безбедни и одговорни, што значи да се придржавају етичких и правних стандарда и да могу бити поуздани од стране корисника и заинтересованих страна.

Тестирање безбедности је процес процене безбедности AI система или LLM-а, идентификовањем и искоришћавањем њихових рањивости. Ово могу обављати програмери, корисници или независни ревизори, у зависности од сврхе и обима тестирања. Неки од најчешћих метода тестирања безбедности за AI системе и LLM-ове су:

- **Санитизација података**: Ово је процес уклањања или анонимизације осетљивих или приватних информација из података за обуку или уноса AI система или LLM-а. Санитизација података може помоћи у спречавању цурења података и злонамерне манипулације смањењем изложености поверљивих или личних података.
- **Адверзаријално тестирање**: Ово је процес генерисања и примене адверзаријалних примера на унос или излаз AI система или LLM-а ради процене њихове робусности и отпорности на адверзаријалне нападе. Адверзаријално тестирање може помоћи у идентификовању и ублажавању рањивости и слабости AI система или LLM-а које нападачи могу искористити.
- **Верификација модела**: Ово је процес верификације исправности и потпуности параметара модела или архитектуре AI система или LLM-а. Верификација модела може помоћи у откривању и спречавању крађе модела осигуравањем да је модел заштићен и аутентификован.
- **Валидација излаза**: Ово је процес валидације квалитета и поузданости излаза AI система или LLM-а. Валидација излаза може помоћи у откривању и исправљању злонамерне манипулације осигуравањем да је излаз конзистентан и тачан.

OpenAI, лидер у AI системима, поставио је серију _процена безбедности_ као део своје иницијативе за мрежу црвених тимова, са циљем тестирања излаза AI система у нади да ће допринети безбедности вештачке интелигенције.

> Процене могу варирати од једноставних тестова питања и одговора до сложенијих симулација. Као конкретни примери, ево узорака процена које је развио OpenAI за процену понашања AI из различитих углова:

#### Убеђивање

- [MakeMeSay](https://github.com/openai/evals/tree/main/evals/elsuite/make_me_say/readme.md?WT.mc_id=academic-105485-koreyst): Колико добро AI систем може да убеди други AI систем да изговори тајну реч?
- [MakeMePay](https://github.com/openai/evals/tree/main/evals/elsuite/make_me_pay/readme.md?WT.mc_id=academic-105485-koreyst): Колико добро AI систем може да убеди други AI систем да донира новац?
- [Ballot Proposal](https://github.com/openai/evals/tree/main/evals/elsuite/ballots/readme.md?WT.mc_id=academic-105485-koreyst): Колико добро AI систем може да утиче на подршку другог AI система за политички предлог?

#### Стеганографија (скривене поруке)

- [Steganography](https://github.com/openai/evals/tree/main/evals/elsuite/steganography/readme.md?WT.mc_id=academic-105485-koreyst): Колико добро AI систем може да пренесе тајне поруке без да га други AI систем открије?
- [Text Compression](https://github.com/openai/evals/tree/main/evals/elsuite/text_compression/readme.md?WT.mc_id=academic-105485-koreyst): Колико добро AI систем може да компресује и декомпресује поруке, омогућавајући скривање тајних порука?
- [Schelling Point](https://github.com/openai/evals/blob/main/evals/elsuite/schelling_point/README.md?WT.mc_id=academic-105485-koreyst): Колико добро AI систем може да координира са другим AI системом, без директне комуникације?

### Безбедност вештачке интелигенције

Неопходно је да тежимо заштити AI система од злонамерних напада, злоупотребе или нежељених последица. Ово укључује предузимање корака за осигурање безбедности, поузданости и поверења у AI системе, као што су:

- Заштита података и алгоритама који се користе за обуку и рад AI модела
- Спречавање неовлашћеног приступа, манипулације или саботирања AI система
- Откривање и ублажавање пристрасности, дискриминације или етичких проблема у AI системима
- Осигурање одговорности, транспарентности и објашњивости одлука и радњи AI система
- Усклађивање циљева и вредности AI система са људима и друштвом

Безбедност вештачке интелигенције је важна за осигурање интегритета, доступности и поверљивости AI система и података. Неки од изазова и прилика у области безбедности вештачке интелигенције су:

- Прилика: Укључивање AI у стратегије сајбер-безбедности, јер може играти кључну улогу у идентификовању претњи и побољшању времена реаговања. AI може помоћи у аутоматизацији и унапређењу откривања и ублажавања сајбер-напада, као што су фишинг, малвер или рансомвер.
- Изазов: AI може бити коришћен од стране противника за покретање софистицираних напада, као што су генерисање лажног или обмањујућег садржаја, имитирање корисника или искоришћавање рањивости у AI системима. Због
Emuliranje pretnji iz stvarnog sveta sada se smatra standardnom praksom u izgradnji otpornijih AI sistema, koristeći slične alate, taktike i procedure za identifikaciju rizika za sisteme i testiranje odgovora branilaca.

> Praksa AI red timinga se razvila i dobila šire značenje: ne pokriva samo ispitivanje sigurnosnih ranjivosti, već uključuje i ispitivanje drugih sistemskih grešaka, kao što je generisanje potencijalno štetnog sadržaja. AI sistemi donose nove rizike, a red timing je ključan za razumevanje tih novih rizika, kao što su ubrizgavanje upita i proizvodnja neosnovanog sadržaja. - [Microsoft AI Red Team building future of safer AI](https://www.microsoft.com/security/blog/2023/08/07/microsoft-ai-red-team-building-future-of-safer-ai/?WT.mc_id=academic-105485-koreyst)

[![Uputstva i resursi za red timing](../../../translated_images/13-AI-red-team.642ed54689d7e8a4d83bdf0635768c4fd8aa41ea539d8e3ffe17514aec4b4824.sr.png)]()

Ispod su ključni uvidi koji su oblikovali Microsoftov AI Red Team program.

1. **Širok opseg AI red timinga:**
   AI red timing sada obuhvata i sigurnosne i odgovorne AI (RAI) ishode. Tradicionalno, red timing se fokusirao na sigurnosne aspekte, tretirajući model kao vektor (npr. krađa osnovnog modela). Međutim, AI sistemi uvode nove sigurnosne ranjivosti (npr. ubrizgavanje upita, trovanje), što zahteva posebnu pažnju. Pored sigurnosti, AI red timing takođe ispituje pitanja pravednosti (npr. stereotipizacija) i štetnog sadržaja (npr. veličanje nasilja). Rano prepoznavanje ovih problema omogućava prioritizaciju ulaganja u odbranu.
2. **Zlonamerne i bezazlene greške:**
   AI red timing razmatra greške iz perspektive i zlonamernih i bezazlenih aktera. Na primer, kada se radi red timing za novi Bing, istražujemo ne samo kako zlonamerni protivnici mogu da naruše sistem, već i kako obični korisnici mogu naići na problematičan ili štetan sadržaj. Za razliku od tradicionalnog sigurnosnog red timinga, koji se uglavnom fokusira na zlonamerne aktere, AI red timing uzima u obzir širi spektar persona i potencijalnih grešaka.
3. **Dinamična priroda AI sistema:**
   AI aplikacije se stalno razvijaju. U aplikacijama koje koriste velike jezičke modele, programeri se prilagođavaju promenljivim zahtevima. Kontinuirani red timing osigurava stalnu budnost i prilagođavanje evolutivnim rizicima.

AI red timing nije sveobuhvatan i treba ga smatrati dopunom dodatnim kontrolama kao što su [kontrola pristupa zasnovana na ulogama (RBAC)](https://learn.microsoft.com/azure/ai-services/openai/how-to/role-based-access-control?WT.mc_id=academic-105485-koreyst) i sveobuhvatna rešenja za upravljanje podacima. Njegova svrha je da dopuni strategiju sigurnosti koja se fokusira na primenu sigurnih i odgovornih AI rešenja koja uzimaju u obzir privatnost i sigurnost, dok teže minimizaciji pristrasnosti, štetnog sadržaja i dezinformacija koje mogu narušiti poverenje korisnika.

Evo liste dodatnih materijala za čitanje koji vam mogu pomoći da bolje razumete kako red timing može pomoći u identifikaciji i ublažavanju rizika u vašim AI sistemima:

- [Planiranje red timinga za velike jezičke modele (LLMs) i njihove aplikacije](https://learn.microsoft.com/azure/ai-services/openai/concepts/red-teaming?WT.mc_id=academic-105485-koreyst)
- [Šta je OpenAI Red Teaming Network?](https://openai.com/blog/red-teaming-network?WT.mc_id=academic-105485-koreyst)
- [AI Red Teaming - Ključna praksa za izgradnju sigurnijih i odgovornijih AI rešenja](https://rodtrent.substack.com/p/ai-red-teaming?WT.mc_id=academic-105485-koreyst)
- MITRE [ATLAS (Adversarial Threat Landscape for Artificial-Intelligence Systems)](https://atlas.mitre.org/?WT.mc_id=academic-105485-koreyst), baza znanja o taktikama i tehnikama koje koriste protivnici u stvarnim napadima na AI sisteme.

## Provera znanja

Šta bi mogao biti dobar pristup za održavanje integriteta podataka i sprečavanje zloupotrebe?

1. Imati snažne kontrole pristupa zasnovane na ulogama za upravljanje podacima
1. Implementirati i proveravati označavanje podataka kako bi se sprečila pogrešna interpretacija ili zloupotreba podataka
1. Osigurati da vaša AI infrastruktura podržava filtriranje sadržaja

A:1, Iako su sve tri preporuke odlične, osiguravanje da pravilno dodeljujete privilegije pristupa podacima korisnicima će značajno doprineti sprečavanju manipulacije i pogrešne interpretacije podataka koje koriste LLM-ovi.

## 🚀 Izazov

Pročitajte više o tome kako možete [upravljati i zaštititi osetljive informacije](https://learn.microsoft.com/training/paths/purview-protect-govern-ai/?WT.mc_id=academic-105485-koreyst) u eri AI.

## Odlično urađeno, nastavite sa učenjem

Nakon završetka ove lekcije, pogledajte našu [kolekciju za učenje o generativnoj AI](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst) kako biste nastavili sa unapređivanjem znanja o generativnoj AI!

Pređite na Lekciju 14 gde ćemo se baviti [životnim ciklusom aplikacija generativne AI](../14-the-generative-ai-application-lifecycle/README.md?WT.mc_id=academic-105485-koreyst)!

---

**Одрицање од одговорности**:  
Овај документ је преведен помоћу услуге за превођење уз помоћ вештачке интелигенције [Co-op Translator](https://github.com/Azure/co-op-translator). Иако настојимо да обезбедимо тачност, молимо вас да имате у виду да аутоматизовани преводи могу садржати грешке или нетачности. Оригинални документ на изворном језику треба сматрати меродавним извором. За критичне информације препоручује се професионални превод од стране људи. Не преузимамо одговорност за било каква погрешна тумачења или неспоразуме који могу настати услед коришћења овог превода.