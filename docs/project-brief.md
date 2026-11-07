# Mutation Lens: východiská projektu

Stav: záznam požiadaviek z diskusie, nie schválený technický návrh.
Dátum: 2026-11-07.

## Cieľ

Vytvoriť VS Code rozšírenie na cielené mutačné testovanie s pomocou LLM.
Hlavným spôsobom používania má byť UI. Prioritou je jednoduché nastavenie,
nízke náklady na obsluhu a dostatočne rýchla, užitočná spätná väzba pri vývoji.
Ide o prototyp pre diplomovú prácu.

## Požiadavky potvrdené používateľom

- VS Code extension ako počiatočná forma produktu.
- Jazykovo všeobecný prístup; produkt nemá byť obmedzený na Python ani iný jeden jazyk.
- UI zobrazí zmeny podľa zvoleného porovnania v Gite; presné režimy ešte treba dopracovať.
- Zobrazené zmeny budú predvolene všetky vybrané. Používateľ môže výber upraviť.
- Používateľ chce aj možnosť pridať označený kód cez kontextové menu editora; presný spôsob je otvorený.
- LLM dostane vybraný kód, potrebný kontext, existujúce testy a prípadné používateľské usmernenie.
- LLM navrhne cielené mutácie v strojovo spracovateľnom formáte.
- Nástroj bude mutácie vykonávať samostatne a pre každú spustí testy.
- UI zobrazí zachytené a preživšie mutácie s vysvetlením a krátkymi odporúčaniami.
- Nastavenie spúšťania testov sa uloží pre projekt a bude sa dať neskôr meniť.
- Predvolený beh môže spustiť všetky testy podľa uloženého nastavenia.
- Pred jednotlivým behom bude možné zvoliť testovacie súbory. Výber jednotlivých testov v súbore sa zatiaľ nevyžaduje.
- Používateľ má záujem aj o voliteľné generovanie chýbajúcich testov; zaradenie do prvej verzie nie je rozhodnuté.

## Nápady, ktoré ešte nie sú rozhodnuté

- Triedenie preživších mutácií do kategórií code issue, test issue a unknown.
- Algoritmické skóre a prípadné hodnotenie od LLM.
- Konkrétne režimy Git porovnania a ich predvolené nastavenie.
- Výber LLM poskytovateľa, modelu, spôsobu autentifikácie a kontextového rozpočtu.
- Konkrétne rozloženie UI, limity mutácií, časové limity a cena jedného behu.
- Formát mutácií, reportov a konfigurácie.
- Využitie existujúcich mutation testing frameworkov oproti vlastnému vykonávaniu LLM zmien.
- Rozsah využitia doterajšej práce s Cosmic Ray a MCP serverom.
- Automatické rozpoznávanie test runnerov a spôsob odovzdania vybraných súborov.
- Technológie implementácie a architektúra rozšírenia.

## Technické odporúčania z diskusie na posúdenie

Tieto body navrhol asistent; nepredstavujú samostatne schválené rozhodnutia.

- Overiť východiskový stav testov pred mutovaním.
- Použiť izolovanú pracovnú kópiu a nemeniť používateľove rozpracované súbory.
- Odlíšiť výsledok testovania od LLM interpretácie.
- Rozlišovať preživšiu mutáciu, neplatnú mutáciu, chybu vykonávania a timeout.
- Pri behu s podmnožinou testov výslovne uviesť, že mutácia prežila vybrané testy.
- Neinterpretovať prežitie mutácie ako dôkaz chyby pôvodného kódu.
- Označovať LLM klasifikácie ako odhady; zohľadniť ekvivalentné alebo nerelevantné mutácie.
- Vygenerované testy overovať: musia prejsť na pôvodnom kóde a zlyhať na príslušnom mutantovi.
- Jazykovo všeobecné vykonávanie oddeliť od automatického objavovania testov, ktoré vyžaduje znalosť runnera.
- Obmedziť počet mutácií a umožniť zrušenie behu.
- Pri odosielaní kontextu jasne ukázať, ktoré súbory opúšťajú lokálny projekt.

## Overenie prínosu diplomovej práce

Používateľ požaduje ľahké nastavenie, jednoduché používanie a dostatočnú pridanú hodnotu.
Konkrétna experimentálna metodika ešte nie je dohodnutá.

Možné merania: čas prvého nastavenia, zásahy používateľa, trvanie a cena behov,
platnosť a užitočnosť mutácií, odhalené medzery v testoch a užitočnosť vysvetlení.
Pri porovnávaní treba oddeliť účinok obmedzenia na zmenený kód od prínosu LLM.

## Inšpirácia

Meta ACH: Mutation-Guided LLM-based Test Generation at Meta.
Preberaný princíp: cielená simulovaná chyba a test, ktorý ju zachytí.
Mutation Lens sa v diskutovanom návrhu sústreďuje na interaktívnu kontrolu
vývojárom vybraných zmien a existujúcich testov.

## Ďalší krok

Dopracovať konkrétny používateľský priebeh a technický návrh prvej verzie,
označiť otvorené rozhodnutia a až potom plánovať implementáciu.
