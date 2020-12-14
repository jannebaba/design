---
Title: Analys02
Description: Part 2, Speed.
---


Utvärdering av webbplatsers laddningstid och användbarhet (v2)
=======================

Jag skall välja ut ett antal olika webbplatser och testa dem för att mäta hur snabbt de laddas och om de innehåller några saker som kan förbättras med tanke på laddningstid och användbarhet.


När man mäter laddningstid via devtools och filken “Network” så använd shift-ctrl-r så att webbläsaren inte använder sina cachade objekt.


Urval och process
-----------------------
Jag tar samma tre sidor som jag gjorde den första analysen på. Då har jag lite insikt i hur mycket information som finns på sidorna och kanske kan använda det i mitt arbete med analysen. Det var dessa webbsidor jag valde.
http://www.dressmann.se
http://www.nelly.com
http://www.next.se

Jag kommer prata övervägande om data poängen och då jag syftar till mobil mätningarna kommer jag att informera om det så att det är tydligt vilken mätning jag pratar om. 

Jag tar ett medel av dem tre mätningarna från devtools och slår ihop till en slags performance score. Där tanken är att en så låg score som möjligt är att föredra, detta är inget konkret utan bara en till sak att jämföra hur mycket och hur snabbt det laddas. Eftersom jag räknar både hur mycket och hur snabbt det laddas så blir det lite missvisande om man tänker på det som något annat.

Jag kommer ta den information jag får från PageSpeed Insights mätningen och med det jag lärt mig göra en analys av vad som skulle kunna förbättras för att optimera laddningstiderna. 

Jag har gjort mina PageSpeed Insight mätnigar på deras sida med hjälp av urlen och fört ner all data i excel arket innan jag såg att det finns som plugin på chrome. Jag får så väldigt annorlunda värden när jag använder pluginet men jag kommer utgå från den datan jag fick från deras webbplats.

Verktyg
-----------------------
https://developers.google.com/speed/pagespeed/insights/
devtools

Resultat
-----------------------

Dressmann har en överlägset hög Insight performance score om man jämför med dem andra två sidorna jag mätte. Den har en tredjedel så många requests som Nelly och hälften av Next. Med 0.2 MegaBytes mer transferred än Next och dubbelt så mycket som Nelly, så får man känslan av att Dressmann har gjort ett mycket bra jobb med sin performance optimizing. I alla fall i jämförelse med dessa två. 

"How Big Should Web Pages Be? Web performance expert Tammy Everts recommends 1MB as the ideal size for fast-loading web pages." Detta kommer inte någon av dessa sidor i närheten av tyvärr, och det märks, väldigt tydligt på Nelly och Next.

#Nelly: 
Nelly 

159 requests
1.3 MB transferred
5.5 MB resources
Finish: 9.31 s
DOMContentLoaded: 1.98 s
Load: 2.31 s

153 requests
1.1 MB transferred
5.5 MB resources
Finish: 7.88 s
DOMContentLoaded: 2.14 s
Load: 2.57 s


150 requests
1.2 MB transferred
5.5 MB resources
Finish: 8.14 s
DOMContentLoaded: 1.41 s
Load: 1.82 s

#Dressman:

57 requests
2.4 MB transferred
4.5 MB resources
Finish: 14.12 s
DOMContentLoaded: 1.92 s
Load: 3.85 s

52 requests
2.4 MB transferred
4.5 MB resources
Finish: 13.76 s
DOMContentLoaded: 2.07 s
Load: 3.45 s

52 requests
2.4 MB transferred
4.5 MB resources
Finish: 3.56 s
DOMContentLoaded: 1.69 s
Load: 3.09 s

#Next: 

114 requests
2.2 MB transferred
4.8 MB resources
Finish: 5.66 s
DOMContentLoaded: 3.12 s
Load: 4.49 s

106 requests
2.2 MB transferred
4.8 MB resources
Finish: 5.13 s
DOMContentLoaded: 2.70 s
Load: 4.01 s

109 requests
2.2 MB transferred
4.8 MB resources
Finish: 5.21 s
DOMContentLoaded: 2.35 s
Load: 4.11 s

All info finns i excel arket, med medelvärdet uträknat för både desktop och mobil.

https://docs.google.com/spreadsheets/d/1C5M6hQnQzDHp4PvZtAkbUXJQsqrL9qcHmyXoK6gTr2k/edit?usp=sharing

Analys
-----------------------

Låt oss gå in lite djupare på vad dem individuellt kan göra för att förbättra sin prestanda. Jag börjar med Next som har lägst score på 53. Det dem kan spara in mest på är att ta bort resurser som blockerar renderingen som det så vackert utrycks. Det ligger 5 stycken ganska rediga JPEG bilder above the fold och sidan lider av oanvänd css och JavaScript. Den här sidan är en katastrof rent ut sagt, prestationsmässigt det vill säga.

Nellys största tidsbov verkar vara oanvänd css, genom att ta bort regler som inte används och skuta upp inläsningen av allt som inte är above the fold har en uppskattad tidsbesparing på 4.18s, en avsevärd siffra i sammanhanget. Sen är det även här resurser som blockerar sidans första rendering vilket också skulle kunna förbättras enormt. Det verkar även finnas JavaScript som inte hade behövts laddas till en början. Enligt devtools hade Nelly minst MB transferred och flest requests av alla sidorna. Det finns väldigt mycket att förbättra. med tanke på att det bara är en bild, några länkar och en header som är above the fold på deras sida så tycker man dom borde ha ett mycket högre performance score än 67. 

Dressman som var den som fick absolut bäst resultat, på allt förutom på Finish i devtools mätningen. Detta tyder på att dom varit smart, valt ut vad som behövs för att informationen "above the fold" och allt nödvändigt för att rendera sidan först för att sedan skicka resterande information. Det finns några saker även dom har kunnat förbättra såklart. Kod från tredje part kan påverka inläsningsprestandan betydligt och är något som pingades på deras test. Den klagar även på lite JavaScript som inte används men det är marginellt, detsamma med passiva eventlyssnare.

Angående rangordning vinner Dressmann överlägset och hästlängder räcker inte ens till att jämföra med. Ett helt stall isåfall om man ska jämföra mot Nelly som var helt klart sämst. Jag känner inte att jag behöver kommentera det mycket mer än så, det var så extremt tydliga siffror tycker jag. 

Gränsen för laddningstid verkar enligt allmän åsikt vara runt 4 sekunder har jag fått uppfattningen om. Personligen tycker jag det är alldeles för segt med 4 sekunder, även fast jag satt med ett 56k modem på 90 talet så har man börjat förvänta sig en viss standard med tiden.
 "One analysis of 5 million desktop and mobile pages found that the average time it takes to fully load a webpage is 10.3 seconds on desktop, and 27.3 seconds on mobile. 5 nov. 2020"( Maura Monaghan in Building Websites https://www.websitebuilderexpert.com/) Den här statistiken gör att man tänker om lite och tycker 4-5 sekunder inte är så mycket i jämförelse med snittet. Men hon fortsätter skriva längre ner i artikeln https://www.websitebuilderexpert.com/building-websites/website-load-time-statistics/
 "So, how fast should a website load?"
Ideally, you’ll want your website to load within three seconds, or two seconds if it’s an ecommerce site. The two-to-three second mark is the turning point where bounce rates skyrocket – in fact, 40% of consumers will wait no more than three seconds before abandoning a site." 3 Sekunder! Det låter rimligt tycker jag. Så allt under 4 är väl faktiskt helt okej egentligen och jag måste väl ändå hålla med. Dressmann hade 1 av 3 under fyra sekunder, annars var det långt ifrån för alla tre sidor jag analyserade. Ingen av dem klarar sig.


Referenser
-----------------------
https://dressmann.com/sv/ </br>
https://nelly.com/se/ </br>
https://www.next.se/sv </br>
https://developers.google.com/speed/pagespeed/insights/ </br>
https://docs.google.com/spreadsheets/d/1C5M6hQnQzDHp4PvZtAkbUXJQsqrL9qcHmyXoK6gTr2k/edit?usp=sharing </br>
https://www.websitebuilderexpert.com/

![dressmann screenshot](/img/dressmann.png "dressmann screenshot")
![nelly screenshot](/img/nelly.png "nelly screenshot")
![dressmann screenshot](/img/next.png "dressmann screenshot")

-----------------------

Dennis Öström.