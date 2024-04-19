# Atak WannaCry

12 maja 2017 7:44 UTC

notes:
Czy ktoś słyszał o tym ataku?

Jeden z największych i najbardziej niszczycielski ataków w historii.
Pozostawił ogromne straty. ***DEWASTUJĄCY***

W przeciągu kilku godzin zdążył zainfekować setki tysięcy urządzeń

Co z telefonami

Oberwały:

- szpitale
- banki
- sklepy
- małe i duże firmy
- Zwykli użytkownicy

Pierwszy przypadek ataku pojawił się 12 maja 2017 roku o godzinie 7:44 UTC (8:44 w Krakowie),
ale na razie nie zdradzę kiedy został powstrzymany.

---
### Dlaczego wirus rozprzestrzenił się tak szybko?

notes:
Prosta odpowiedź, która padała już w wielu poprzednich projektach

Zapytać kto to może być hmmmm 🤔🤔🤔

---
## Equation Group

notes: 
Grupa mająca powiązania z...

---
## Tailored Access Operations

notes:
Nie mylić z tao tao (oni robią sosy)
To jest natomiast bardzo duży wydział, który przynależy do...

---
### Signal Intelligence Directorate - SIGINT/SID

notes:
Niektórym może świtać np. taki projekt jak ECHELON

---
## ECHELON

![](echelon.webp|700)

---
## NSA

![](nsa.png)

notes:
No kto by się spodziewał :)

No ale wróćmy 
*raczej dalej hehe*

---
## Tailored Access Operations

notes:
Bardzo duży oddział NSA zajmujący się szpiegostwem i tzw. *Cyber-Warfare*

Składał się z ponad 1000 specjalistów bezpieczeństwa, hackerów, hardware i software developerów, zarówno cywilnych jak i wojskowych. *Wcale nie brzmi groźnie*

Według wycieków Edwarda Snowdena posiadali oni exploity pozwalające przejmować kontrolę na bardzo popularnymi urządzeniami w szczególności switch i routerów.

Ale po co?
Oczywiście, żeby śledzić

---
## ANT Catalog

![](NSA_quantum_cat.jpg|600)

notes:
Obrazek jest z prezentacji NSA tłumaczącej jak działa projekt QUANTUM
Dla przykładu narzędzie QUANTUM
Sprawiało, że cały ruch był duplikowany. Jedna część idzie tam gdzie miała iść, a druga na servery NSA.

Jest to tylko jedno z narzędzi, które znajduje się na tak zwanej *ANT Catalog*
Czyli liście 50 programów do szpiegowania, niektóre takie zwykłe jak SURLYSPAWN przechwytywanie wpisywanych znaków z klawiatury nawet kiedy komputer nie jest połączony do internetu (taki drobny szczegół)

Lub TOTEGHOST, czyli software, który po zainstalowaniu na telefonie z systemem Windows pozwalał na jego **pełną** zdalną kontrolę

Mówi się też, że Tailored Access Operation było zaangażowane razem z siłami Izraela w produkcji Stuxnetu.

*Bardzo poważne sprawy*

*12 min opowiadanie do tego momentu*

---
## Equation Group

notes:
Equation Group to jedna z najbardziej wyrafinowanych grup hakerskich składającej się z około 60 osób operujących głównie w Iranie, Rosji, Pakistanie, Afghanistanie, Indiach Syrii i Mali

NSA odkrywało i tworzyło exploity wykorzystujące luki 0-day, o których nikt nie wiedział
...do czasu aż grupa *Shadow Brokers* nie wykradła explaitów i ich nie opublikowała

Exploit użyty przez WannaCry to DOUBLEPULSAR oraz EternalBlue, który jak nazwa wskazuje wykorzystywał nie Bluetooth, tylko SMBv1 (Server Messeging Block v1) czyli protokół do komunikacji i wymiany plików między komputerami z systemem Windows.

EternalBlue został również użyty w takich atakach jak Petya czy DanderSpritz Listening Post


---
## Jak to wszystko działało?

Ostrzeżenie: zaraz pojawi się dużo czarnej magii

---
## EternalBlue

Kernel Ring 0

![](kernel ring.png)

notes:
EternalBlue wykorzystuje Kernel Pool Grooming czyli alokowanie pamięci w ring0 (Kernel mode).
Kiedy kod znajdujący się w takiej pamięci zostanie uruchomiony to z robi to z najwyższymi uprawnieniami. 

---
## EternalBlue

Kernel Memory Pool

![](1.png)

notes:
W dużym uproszczeniu:

---
## EternalBlue

![](2.png)

notes:
Na początku wysyłane są dane, które są zaalokowane w pamięci Kernela (mechanizmu nie - wytłumaczę, bo nie wiem dlaczego tak). 

---
## EternalBlue

![](3.png)

notes:
Pamięć zostaje zwolniona, a zaraz po tym wysyłany jest pakiet SMB. 

---
## EternalBlue

![](4.png)

notes:
Potem wysyłana jest druga wiadomość SMB o połowę mniejsza, która nadpisuje poprzednią - wiadomość. Z racji tego, że druga wiadomość jest o połowę krótsza, to druga część staje się - dostępna da payloadu. 

---
## EternalBlue

![](5.png)

notes:
Potem wysyłany jest payload w specjalnie przygotowaną pamięć. 

Na koniec wykonywany jest RIP hijacking, czyli wskazanie rejestru RIP na miejsce w pamięci gdzie znajduje się payload, aby mógł się wykonać.

---
## DOUBLEPULSAR

notes:
Druga część ataku polega na egzekucji payloadu, którym jest drugi exploit *DOUBLEPULSAR* (również stworzony przez Equation Group i wykradziony przez Shadow Brokers). 

Nie wiem do końca jak działa, bo jest to pogmatwane, wiem że miał dostęp do komend ping, exec i kill.

Pozwalało to na instalację WannaCry na urządzeniu

---
## WannaCry
*no w końcu*

notes:
Po instalacji za pomocą backdoora i jego uruchomieniu zaczęły dziać się prawdziwe zniszczenia.

WannaCry rozprzestrzeniał się dalej tak jak opowiedziałem o tym wcześniej. 
Jeżeli połącznie nie powiodło się, wirus szyfrował wszystkie pliki na komputerze (poza plikami potrzebnymi do funkcjonowania komputera).

---
## Domena

http://iuqerfsodp9ifjaposdfjhgosurijfaewrwergwea.com/

notes:
Następnie próbował połączyć się ze stroną internetową, ale o tej stronie później. 

Jeżeli połącznie nie powiodło się, wirus szyfrował wszystkie pliki na komputerze (poza plikami potrzebnymi do funkcjonowania komputera).

---
### Ransom

![](wannacry.jpg|700)

notes:
Po zaszyfrowaniu komputera wyświetlało się okno z żądaniem okupu. 
300$ w bitcoinie wysłany na podany adres. 
Jeśli pieniędzy nie wyślemy w ciągu 3 dni, okup zwiększa się 2 krotnie. Po 7 dniach od infekcji, plików nie da się odzyskać. 

---
### Przykładowe odszyfrowanie

![](wannacry_ransom_note.png|700)

notes:
Aby "zakładnicy" uwierzyli, że hakerzy nie kłamią, dało się odszyfrować 10 losowych plików za darmo. To mogło oznaczać, że klucz dało się przechwycić

Niestety okazuje się, że klucza nie dało się przechwycić. 
Losowe 10 plików było szyfrowane hardcodowanym kluczem RSA, a pozostałe szyfrowane były wygenerowanym kluczem AES, który był też zaszyfrowany za pomocą wygenerowanego klucza RSA. Klucz szyfrowania w takiej formie znajdował się w headerze zaszyfrowanego pliku .WNRY. Po zapłaceniu okupu otrzymywaliśmy nasz klucz RSA, a potem z górki. Niektóre strony przestrzegały przed płaceniem i mówiły, że nie działały, lecz inny artykuł z bardzo dokładną analizą pokazuje, że działa.

---
### Domeny tor

- gx7ekbenv2riucmf.onion
- 57g7spgrzlojinas.onion
- xxlvbrloxvriy2c5.onion
- 76jdd2ir2embyv47.onion
- cwwnhwhlz52maqm7.onion

---
![](wannacry schemat.png)

---
## Przecież to nie powinno działać 🤔

14 marca Microsoft wydał łatkę

Atak nastąpił 2 miesiące później

---
## WannaCry zawierał błędy

---
## Adresy Bitcoin

- [13AM4VW2dhxYgXeQepoHkHSQuy6NgaEb94](https://blockchain.info/address/13AM4VW2dhxYgXeQepoHkHSQuy6NgaEb94)
- [12t9YDPgwueZ9NyMgw519p7AA8isjr6SMw](https://blockchain.info/address/12t9YDPgwueZ9NyMgw519p7AA8isjr6SMw)
- [115p7UMMngoj1pMvkpHijcRdfJNXj6LrLn](https://blockchain.info/address/115p7UMMngoj1pMvkpHijcRdfJNXj6LrLn)

notes:
WannaCry miał generować dla każdego urządzenia, unikalny adres bitcoina na który miał być zapłacony okup. Miało to na celu znaczne utrudnienie w namierzeniu docelowego adresu i monitorowanie transakcji. Jednak bug spowodował, że adresy nie były generowane i deafaultowo pojawiały się te 3 adresy:

---
## Bot na X (Twitter)

![](twitter bot.png)

https://twitter.com/actual_ransom

---
## Zarobki

![](bitcoin chart.png|400)

notes:
To tylko 1 z 3 adresów!!!
https://www.blockchain.com/explorer/addresses/btc/12t9YDPgwueZ9NyMgw519p7AA8isjr6SMw

---
Wartość Bitcoina:
- wtedy $2,804 (stan na 3.08.2017)
- dzisiaj $46,684 (stan na 10.01.2024) 

Zarobili 52.2 Bitcoinów - a tylko 0.1% ofiar zapłaciło

Zyskali "tylko" \$142,000 (Dzisiaj byłoby to 2,436,000)

*Co było celem?*

---
## Hipotetycznie

Gdyby 10% ofiar zapłaciło $50

Zyskali by $2,439,000 (Dzisiaj byłoby to 40,615,000!!!)  

---
## Najgorszy błąd (?)

notes:
Największym błędem (lub celowym działaniem, specjaliści do dziś się o to spierają) była implementacja kill switcha. Domena, z którą łączył się wirus właśnie nim była. 

---
# Marcus Hutchins

### The "Accidental" Hero

![](better marcus.webp|370)

---
## Kill Switch

Początek ataku - 12.05.2017 7:44 UTC

Koniec ataku - 12.05.2017 15:03 UTC

http://iuqerfsodp9ifjaposdfjhgosurijfaewrwergwea.com/

notes:
Tego samego dnia tj. 12.05.2017 niecałe kilka godzin później tj. 15:03 UTC, Marcus Hutchins odnalazł kill switcha zupełnie przez przypadek. 

Kiedy usłyszał o trwającym ataku, postanowił pomóc. Zdobył próbkę wirusa i rozpoczął inżynierię wsteczną. 

Zauważył, że malware próbuje połączyć się ze stroną internetową. Pomyślał, że jest to server Command & Control, więc chciał postawić tam botneta, żeby śledzić kolejne ruchy atakujących. 

Ku jemu zdziwieniu, domena nie istniała. Zarejestrował ją. 

---
#### Zatrzymać potężny atak malware potężnym 
# $10.69

notes:
Tym sposobem jeden z największych ataków malware został zatrzymany za jedyne $10.69.

Otrzymał on przydomek *The Accidental Hero*

Wszystko super, ale czy ktoś widzi problem?

---
## Ostatni Bastion

notes:
Wszystkie zainfekowane urządzenia zaczęły pingowaś jedną domenę. 

Atak WannaCry zamienił się dosłownie w atak DDoS, lecz w tym wypadku, kiedy strona padnie, cały świat ogarnie chaos. 

Prasa podawała liczbę 200 000 zainfekowanych urządzeń, lecz Kryptos Logic (firma w której pracuje Marcus) mając dostęp do domeny, mogli dokładniej oszacować liczbę infekcji. 

Za każdym razem kiedy wirus się uruchamiał, wysyłał pojedyncze zapytanie. Jeżeli strona odpowiedziała, więcej zgłoszeń nie było wysyłanych. 

200 000 bierze się z unikalnych adresów łączących się z domeną. Kiedy podliczymy jednak liczbę połączeń, widać, że wiele tych samych adresów próbuje się połączyć. Dzieje się tak przez protokół NAT, za którym kryje się dużo urządzeń. 

Gdyby policzyć każdą próbę połączenia, wychodzi nam około 14-16 mln zainfekowanych urządzeń. Liczba ta jednak może być niedokładna, ponieważ połączenie nawiązywane jest za każdym razem kiedy zainfekowane urządzenie się uruchamia (WannaCry znajduje się w autostarcie).

Liczby są niemałe co sprawia, że domena jest pod nieprzerwanym atakiem DDoS i to o dużym natężeniu.

---
## Ale to nie koniec :)

---
## Mirai

Botnet służący do przeprowadzania ataków DDoS

Potrafiący osiągnąć nawet 1.1 TB/s przepustowości

notes:
Do tego na pewno nie pomogły faktyczne ataki DDoS takie jak Mirai. Dosyć znany atak o ogromnej przepustowości. Potrafił zdjąć stronę natychmiastowo osiągając nawet 1.1 TB/s przepustowości.

Mirai został użyty również w tym przypadku, lecz Kryptos Logic zdołali rozdzielić ruch na inne serwery.

Po tygodniu CloudFlare oraz Amazon zaoferowało swoje usługi, przejmując na siebie tyle ruchu ile tylko mogli, tym samym kończąc trwające ponad tydzień "oblężenie".

Marcus w wywiadie powiedział, że spał łącznie 3h. Po tygodniu poszedł w końcu spać, a jego pracodawca troszcząc się o jego samopoczucie zapłacił mu $1000 za każdą przespaną godzinę

---
## Łatka?

notes:
Załatanie kill-switcha jest trywialnie proste i atak z łatwością mógł być powtórzony ze zmienionym kill-switchem lub kompletnie bez niego. Możliwe, że celem ataku nie były pieniądze, ani zniszczenia? Nikt do dzisiaj tego nie wie.

---
## Kolejne domeny

- ifferfsodp9ifjaposdfjhgosurijfaewrwergwea.com
- iuqerfsodp9ifjaposdfjhgosurijfaewrwergwea.com
- iuqerfsodp9ifjaposdfjhgosurijfaewrwergwea.test
- ayylmaotjhsstasdfasdfasdfasdfasdfasdfasdf.com

notes:
Pojawiło się kilka kolejnych wariantów z innymi domenami, ale bardzo szybko były opanowywane, często zanim zdążyły zainfekować kolejne komputery.

Atak został zatrzymany lecz nie zneutralizowany. Tak jakby wirus był zamrożony *in stasis*, czekając tylko aż ktoś go uwolni.

Zanim kompletnie zostanie powstrzymany miną jeszcze długie lata, ponieważ dużo urządzeń nadal nie zostało zaktualizowanych, a wirus tylko na nie czyha.

---
## Straty i zniszczenia

![](WannaCry Map May 12 2017 - April 1 2018.webp|600)

---
## Straty i zniszczenia

- Szpitale
- Banki
- Firmy bankrutowały
- Dane utracone

Straty wyniosły około $4 mld i  
prawdopodobnie zginęli ludzie

notes:
Jak wspominałem na początku WannaCry uderzył wszędzie. Straty liczy się w 150 krajach. Banki, szpitale, placówki publiczne, firmy małe i duże i zwykłych użytkowników. Dużo firm zbankrutowało, możliwe, że ludzie (w szpitalach) mogli umrzeć, utracono bardzo dużo danych i atak spowodował chaos. Atak był dewastujący. Straty szacuje się na około $4 mld 

NHS - Operacje przerwane, lub znacznie utrudnione, ambulansy nie mogły mieć wyznaczonych tras, komunikacja mogła nie działać kompletnie

---
## Kto za tym wszystkim stoi?

notes:
Nie do końca wiadomo kto stoi za atakiem. Głównym podejrzanym jest jednak Północno Koreańska grupa Lazarus Group. Widać było fragmenty kodu wykorzystywane we wcześniejszych atakach tej grupy, jednak pewności mieć nie można zważając na to jak rozwinięta jest branża IT, gdzie każdy kopiuje czyiś kod chociażby ze StackOverflow.

USA oskarżyło Koreę Północną o ten atak, jednak oni się do tego nie przyznają. No kto by się spodziewał

---
## Warto aktualizować komputery

![](windows update.png)

---
## Dziękuję za uwagę!!!

---
Prezentacja zostala stworzona za pomocą Obsidian oraz wtyczki Advanced Slides

Inspiracja: [www.youtube.com/c/NoBoilerplate](https://www.youtube.com/c/NoBoilerplate "https://www.youtube.com/c/NoBoilerplate")

---

# Źródła

Niestety się nie mieszczą :(