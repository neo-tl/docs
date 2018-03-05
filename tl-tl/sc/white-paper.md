# NeoContract na White Paper

## 1. Paunang Salita

Ang matalinong na mga kontrata ay sumasangguni sa anumang kompyuter na program na maaaring awtomatikong magsagawa ng mga termino sa kontrata na naka-preprogram nito. Ang ideya ng matalinong kontrata ay unang iminungkahi ng kriptograper na si Nick Szabo noong 1994, ginagawa itong kasing luma sa Internet. Dahil sa kakulangan ng isang maaasahang environment ng pagpapatupad, ang matalinong mga kontrata ay hindi malawakang nagamit. 

Sa 2008, isang tao na nasa ilalim ng pangalan na Satoshi Nakamoto ay naglabas ng Bitcoin, at bumalangkas sa pampundasyon na mga konsepto ng isang blockchain. Sa loob ng Bitcoin na blockchain, si Nakamoto ay gumagamit ng isang hanay ng mga scripting language upang tulungan ang mga gumagamit na makamit ang mas kakayahang umangkop sa pagkontrol ng kanilang personal na mga account at mag padala ng proseso, na sa kalaunan ay naging embryonic na porma ng isang nakabase sa chain, ang matalinong kontrata na sistema.

Sa 2014, isang binatilyo na nakapangalan Vitalik Buterin ay naglabas ng Ethereum, na nagbibigay ng isang nakabase sa chain, Turing-complete, ang mataling kontrata na sistema na maaaring gamiting upang lumikha ng isang iba't ibang mga aplikasyon ng decentralized na blockchain.

Ang NEO na blockchain ay isang digital asset at aplikasyon na plataporma, na nagbibigay ng isang bagong matalinong kontrata na sistema, ang NeoContract. Sa kaloob-looban ng Neo na plataporma, ang network ay nagbibigay ng maramihang mga punsyon katulad ng mga kakayahan ng digital asset, ang NeoAsset, at digital na pagkakakilanlan, ang NeoID, na nagpapahintulot sa mga gumagamit na madaling makisali sa digital na mga negosyo, at hindi na limitado lamang sa pagpapalabas likas na mga token sa blockchain.

Ang artikulong ito ay magpapakilala sa mga tampok ng NeoContract at magsisiyasat sa hindi teknikal na mga detalye. Mangyaring sumangguni sa teknikal na dokumentasyon para sa teknikal na mga detalye: [docs.neo.org](http://docs.neo.org).

## 2. Mga Tampok

### 2.1 Katiyakan

Kung ang isang program ay tumatakbo sa magkaibang mga kompyuter, o sa magkaibang panahon sa parehong kompyuter, ang pagkilos ng program ay matutukoy kung ang parehong input ay garantisadong makakagawa ng parehong output, at kabaligtaran.

Ang Blockchain ay isang multi-party na imbakan, at kalkulasyon na pamamaraan, kung saan ang datos sa loob nitong ipinamamahaging sistema ay ang resulta ng maasahang mga kalkulasyon, at hindi maaaring mabago. Ang matalinong mga kontrata ay gumagana sa loob ng multi-node, ang ipinamamahaging blockchain na network. Kung ang isang matalinong kontrata ay non-deterministic, ang mga resulta ng magkaibang mga node ay maaaring hindi pantay-pantay. Bilang resulta, ang pagkasunduan sa pagitan ng mga node ay hindi maaaring maabot, at ang network ay magiging hindi umuunlad. Samakatuwid, sa disenyo ng isang matalinong kontrata na sistema, mayroong isang pangangailangan na mag-alis ng anumang mga kadahilanan na maaaring magsanhi ng non-deterministic na pagkilos.

#### 2.1.1 Oras

Ang pagkakaroon ng system-time ay isang napakakaraniwang punsyon ng sistema, na maaaring mabigat na nailalapat sa tiyak na mga pamamaraan ng time-sensitive na kontrata. Gayunpaman, ang pagkakaroon ng system-time ay isang non-deterministic na punsyon ng sistema, at mahirap kumuha ng isang pinag-isa, tumpak na oras sa isang ipinamamahaging na sistema, batay sa mga resulta ng magkaibang mga node ay hindi magkakapantay. Ang NeoContract ay nagbibigay ng isang block-based na system-call na tinatrato ang buong blockchain, bilang isang timestamp na server, at kumukuha ng timestamp kailanman nabuo ang isang bagong bloke. Karaniwan, ang NEO na network ay lumilikha ng isang bagong bloke sa bawat 15 na mga segundo, kaya ang kontrata ay tumatakbo sa humigit-kumulang na parehong oras sa pinakabagong block-time, dagdag bawas ng 15 na mga segundo.

#### 2.1.2 Pagkasapalaran

Maraming matalinong kontrata na mga program, katulad ng pagsusugal na mga kontrata at maliliit na mga laro, ay gumagamit ng sapalarang numero na mga function. Gayunpaman, ang sapalarang numero na mga punsyon ay isang tipikal na hindi natutukoy na function, at bawat system-call ay kumukuha ng magkaibang mga resulta. Sa isang ipinamamahaging sistema, may maraming mga paraan upang malutas ang problemang ito: Una, ang parehong sapalaran na seed ay maaaring gamitin para sa lahat ng mga node, upang ang return na pagkakasunod-sunod ng buong sapalaran na punsyon ay matutukoy, ngunit ang paraang ito ay naglalantad sa buong sapalaran na resulta nang maaga, labis na nagbabawas ng praktikal na halaga ng sapalarang numero. Isa pang posibleng solusyon, ay hayaan ang lahat ng node na makipag-usap sa isang kolaboratibong paraan upang bumuo ng sapalarang mga numero. Maaari itong makamit sa paggamit ng cryptographic na mga pamamaraan upang lumikha ng isang patas na sapalarang numero, ngunit ang kawalan ay nakapatong sa napakababaw na pagganap, at sa pangangailangan ng karagdagang pananaw sa komunikasyon. Ang isang sentralisadong tagapagtustos ng sapalarang numero ay maaaring gamitin upang bumuo ng sapalarang mga numero na nangangako ng walang pagbabago at pagganap, ngunit ang sagabal sa ganitong paraan ay halata; Ang mga gumagamit ay kailangang walang kondisyong magtiwala sa sentralisadong tagapagtustos ng numero.

Mayroong dalawang paraan upang makabuo ng isang sapalarang numero sa NEO:

1. Kapag ang bawat bloke ay nabuo, ang consensus na node ay aabot sa isang pagkakasundo sa isang sapalarang numero, at ipupuno ito sa Nonce na patlang sa bagong bloke. Ang kontrata na program ay madaling makakuha ng sapalarang numero sa anumang bloke, sa pamamagitan ng pagreperensya ng Nonce na patlang

2. Ang kontrata na program ay maaaring gumamit ng hash na halaga sa bloke bilang isang generator ng sapalarang numero, dahil ang block hash na halaga ay may tiyak na likas na pagkasapalaran. Ang paraang ito ay maaaring gamitin upang makakuha ng isang mahinang sapalarang numero

#### 2.1.3 Data Source

Kung ang isang program ay nakakuha ng datos sa run-time, ito ay maaaring maging isang non-deterministic na program kung ang data source ay nagbibigay ng non-deterministic na datos. Halimbawa, ang paggamit ng magkaibang mga search engine upang makakuha ng nangungunang 10 na mga resulta sa paghanap para sa isang partikular na keywork, ay maaaring mag-ani ng magkaibang mga resulta, sa iba't ibang paraan ng pagkakaayos, kung magkaibang mga IP address ang ginamit.

Para sa matalinong mga kontrata, ang NEO ay nagbibigay ng dalawang mga uri ng natutukoy na mga data source:

1. **Blockchain na Ledger**
	
   Ang kontrata na pamamaraan ay maaaring mag-access sa lahat ng datos sa buong chain gamit ang interoperable na mga serbisyo, kabilang ang kumpletong mga bloke at mga transaksyon, at para sa bawat patlang nila. Ang datos sa mga bloke ay natutukoy at hindi nagbabago, kaya maaari silang ligtas na ma-access gamit ang matalinong mga kontrata.

2. **Ispasyo Na Imbakan ng Kontrata**

   Bawat kontratang nai-deploy sa NEO na network, ay mayroong isang pribadong ispasiyo na imbakan na maaari lamang ma-access gamit ang kontrata. Ang mekanismo sa pagkakasundo ng NEO ay sumisigurado sa hindi pagbabago ng estado ng imbakan, sa bawat node sa network.

Para sa mga sitwasyon kung saan ang pag-access sa hindi blockchain na datos ay kinakailangan, ang NEO ay hindi nagbibigay ng isang direktang paraan upang makipag-ugnayan sa mga datos na ito.
Ang hindi blockchain na datos ay kailangang ilipat sa NEO na blockchain gamit ang mga transaksyon, at pagkatapos ay isinalin sa alinmang nabanggit na mga data source, upang ma-access gamit ang matalinong mga kontrata. 

#### 2.1.4 Kontrata na Pagtawag

Ang matalinong mga kontrata sa NeoContract ay maaaring tumawag sa isa't isa, ngunit hindi dapat tawaging naka-recursive. Ang recursion ay maaaring makamit sa loob ng kontrata, ngunit hindi kayang tumawid sa mga hangganan ng kasalukuyang kontrata. Sa karagdagan, ang relasyon ng pagtawag sa pagitan ng mga kontrata ay dapat naka-static: Ang target ay hindi dapat tukuyin sa runtime. Ito ay nagpapahintulot ng pagkilos ng program upang maging buong determinado bago ang pagpapatupad, at ang relasyon ng pagtawag nito upang maging buong matukoy bago ito maaaring patakbuhin. Batay nito, ang maramihang mga kontrata ay maaaring dynamic na ma-partition upang makamit ang nakahilerang pagpapatupad.

### 2.2 Mataas na Pagganap

Ang environment ng pagpapatupad ng isang matalinong kontrata ay naglalaro ng isang mahalagang papel sa pagganap nito. Kapag ating pinag-aralan ang pagganap sa anumang environment ng pagpapatupad, may dalawang pangunahing tagapagpahiwatig na kritikal:

1. Bilis ng pagpapatupad ng tagubilin
2. Bilis ng startup ng environment na pagpapatupad

Para sa matalinong mga kontrata, ang environment ng pagpapatupad ay kadalasang mas importante kaysa sa bilis ng pagpapatupad ng tagubilin. Ang matalinong mga kontrata ay mas kasangkot sa IO na operasyon ng lohika, upang matukoy ang mga tagubilin, kung saan ang implementasyon ng mga tagubiling ito ay madaling mapaunlad. Sa bawat pagkakataon na tinawag nag matalinong kontrata, dapat itong magsimula ng isang panibagong birtwal na makina / container. Samakatuwid, ang bilis ng pagpapatupad sa environment (pagsisimula ng isang birtwal na makina / container) ay may mas malaking epekto sa pagganap ng matalinong kontrata na sistema.

Ang NEO ay gumagamit ng isang magaang NeoVM (Birtwal na Makina ng NEO) bilang matalinong kontratang execution environment nito, na mayroong isang napakabilis na start up at kumukuha ng napakaliit na mga resource, perpekto para sa maikling mga program katulad ng matalinong mga kontrata. Ang paggamit ng pag-compile at pag-cache ng hotspot na matalinong mga kontrata gamit ang JIT (totoong-oras na compiler) ay maaaring makabuluhang magpabuti sa kahusayan ng mga birtwal na makina.

### 2.3 Kakayahan sa Pag-iskala

#### 2.3.1 Mataas na pagkakasabay at dynamic na pagpartisyon

Kapag tayo ay nagtatalakay ng kakayahan sa pag-iskala ng isang sistema, ito ay nagsasangkot ng dalawang pangunahing mga aspeto: Ang bertikal na pag-iskala at pahalang na pag-iskala. Ang bertikal na pag-iskala ay tumutukoy sa optimisasyon ng nagpoprosesong workflow, na nagpapahintulot sa sistema na gamitin ng husto sa umiiral na kapasidad ng kagamitan. Sa pamamaraang ito, ang mga limitasyon ng sistema ay madaling maaabot, dahil ang series-based processing na kapasidad ay nakabase sa limitasyon ng hardware sa isang solong aparato. Kapag kailangan nating iiskala ang sistema, mayroon bang paraan upang mag-transform ng mga serye na sistema sa isang kahilera na sistema? Sa pagkateoretikal, kailangan lamang nating dagdagan ang bilang ng mga aparato, at maaari na nating makamit ang halos walang limitasyon na kakayahan sa pag-iskala. Pwede ba nating makamit ang walang limitasyon na pag-iskala sa ibinahaging mga blockchain network? Sa ibang salita, maaari bang magsagawa ang blockchain ng mga program na nakahilera?

Ang blockchain ay isang ibinahaging ledger, na nagtatala ng iba't-ibang estado ng datos at mga panuntunan na namamahala sa mga pagbabago sa estado ng mga datos na ito. Ang mga matalinong kontrata ay ginamit bilang mga tagapagdala, upang magtala sa mga panuntunang ito. Ang mga blockchain ay maaaring magproseso ng mga program na nakahilera, lamang kung, ang maramihang mga matalinong kontrata ay maaaring maisagawa nang sabay-sabay at sa isang hindi magkasunod-sunod na paraan. Sa madaling salita, kung ang mga kontrata ay hindi nakikipag-ugnayan sa isa't isa, o kung ang kontrata ay hindi nagbabago ng parehong estado ng datos, sa parehong panahon, ang kanilang pagpapatupad ay hindi magkakasunod at maaaring isagawa nang sabay-sabay. Kung hindi, ito ay magsasagawa lamang nang nakaserye, na sumusunod sa isang magkakasunod na pagkakaayos, at ang network ay hindi maaaring mag-iskala nang pahalang.

Base sa pagsusuri sa itaas, maaari tayong madaling magdisenyo ng "walang limitasyon na pag-iskala" sa mga sistema ng matalinong kontrata. Ang lahat nang dapat nating gawin ay ang pag-set up ng simpleng mga panuntunan:
 
 * **Ang isang matalinong kontrata ay maaari lamang magbago ng estado na rekord sa kontrata kung saan ito nabibilang**

 * **Sa parehong transaksyon na batch (block), ang isang kontrata ay maaari lamang patakbuhin sa isang beses**

Bilang isang resulta, ang lahat ng mga matalinong kontrata ay maaari lamang maproseso na nakahilera sa sunud-sunod na pagkakaayos na walang kaugnayan sa resulta. Gayunpaman, kung ang isang "matalinong kontrata ay maaari lamang magbago ng estado na rekord sa kontrata kung saan ito nabibilang", ito ay nagpapahiwatig na ang kontrata ay hindi makakatawag sa isa't isa. Ang bawat kontrata, ay isang hiwalay na isla; kung "Sa parehong transaksyon na batch (block), ang isang kontrata ay maaari lamang patakbuhin sa isang beses", ito ay nagpapahiwatigna ang isang digital asset na ibinigay gamit ang isang matalinong kontrata, maaari lamang mag-asikaso ng isang transaksyon sa bawat bloke. Ito ay isang mundo ng pagkakaiba sa mga layunin ng orihinal na disenyo ng "matalinong" mga kontrata, na titigil sa pagiging "matalino". Sa wakas, ang aming mga disenyo na layunin ay parehong mutwal na pagtawag sa pagitan ng mga kontrata, at maramihang pagpapatupad ng parehong pagtawag, sa parehong bloke.

Sa kabutihang-palad, ang mga matalinong kontrata sa NEO ay may isang static call na relasyon, at ang call target ay hindi maaaring tukuyin sa run time. Pinapayagan nito ang pag-uugali ng program na maging buong nakatukoy bago sa pagpapatupad, at buong nakatukoy ang call na relasyon nito bago ito maaaring tumakbo. Kinakailangan namin na ang bawat kontrata ay tahasang ipahiwatig ang mga kontrata na maaaring matatawag, upang ang nag-ooperang environment ay maaaring magkalkula sa kumpletong call tree bago magpapatakbo ng kontrata na pamamaraan, at partisyon na pagpapatupad ng mga kontrata, base sa call tree. Ang mga kontrata na maaaring baguhin ang parehong estado na rekord, ay maisasagawa sa isang 
magkakasunod na paraan sa loob ng parehong partisyon, kung saan ang magkaibang mga partisyon ay maaari nang isagawa na nakahilera.

#### 2.3.2 Mababang coupling

Ang coupling ay isang sukatan ng dependensya sa pagitan ng dalawa o maraming mga entity. Ang NeoContract na sistema ay gumagamit ng isang mababang-coupling na disenyo, na naipapatupad sa NeoVM, at nakikipag-ugnayan sa hindi blockchain na datos gamit ang interoperable na service layer. Bilang isang resulta, ang karamihan sa mga upgrade sa matalinong kontrata na mga function ay maaaring makamit sa pamamagitan ng pagpapalaki ng API ng mga interoperable service.

## 3. Paggamit ng Kontrata

### 3.1 Beripikasyon ng Kontrata

Hindi tulad ng public-key account na sistema na ginamit sa Bitcoin, ang account na sistema ng NEO ay gumagamit ng kontratang account na sistema. Ang bawat account sa NEO ay tumutugon sa isang beripikasyong kontrata, at ang hash na halaga ng beripikasyong kontrata, ay ang account address; Ang program na lohika ng beripikasyong kontrata ay kumukontrol sa pagmamay-ari ng account. Kapag naglilipat mula sa isang account, una mong kakailanganing magpatupad ng beripikasyong kontrata para sa account na iyon. Ang balidasyong kontrata ay maaaring tumanggap ng isang hanay ng mga parametro (kadalasan ang isang digital signature o ibang pamantayan), at nagsasauli ng isang boolean na halaga pagkatapos ng beripikasyon, nagpapahiwatig sa tagumpay ng beripikasyon sa sistema.

Ang user ay maaari munang mag-deploy ng beripikasyong kontrata sa blockchain, o mag-publish ng kontratang nilalaman nang direkta sa transaksyon habang nasa paglipat na proseso.

### 3.2 Kontratang Aplikasyon

Ang aplikasyon na kontrata ay nati-trigger ng isang espesyal na transaksyon, na maaaring mag-access at magbago ng global na estado ng sistema, at ang pribadong estado ng kontrata (storage area) sa run time. Halimbawa, maaari kang lumikha ng isang global digital asset sa isang kontrata, bumoto, mag-save ng datos, at kahit dynamic na lumikha ng isang bagong kontrata, kapag ang kontrata ay tumatakbo.

Ang pagpapatupad ng aplikasyon na kontrata ay nangangailangan ng pagsisingil gamit ang instruksiyon. Kapag ang transaksyon na fee ay natupok, ang kontrata ay mabibigo at hihinto sa pagpapatupad, at ang lahat ng estadong pagbabago ay maibabalik. Ang tagumpay ng kontrata ay hindi nakakaapekto sa bisa ng transaksyon.

### 3.3 Kontratang Function

Ang function na kontrata ay ginagamit upang magbigay ng ilang publiko o karaniwang ginagamit na mga function, na maaaring matawag sa ibang mga kontrata. Ang matalinong kontrata na code ay maaaring magamit muli, upang ang mga developer ay maaaring magsulat ng lalong nagiging kumplikadong lohika ng negosyo. Ang bawat function na kontrata, kapag na-deploy, ay maaaring pumili na magkaroon ng isang pribadong storage area na alinman ay nabasa o naisulat sa datos sa isang hinaharap na kontrata, nakakamit ang pagpapanatili ng estado.

Ang function na kontrata ay dapat munang naka-pre-deploy sa chain upang matawag, at matanggal mula sa chain gamit ang isang "self-destructing" na sistemang function, na hindi na magagamit at ang pribadong storage nito ay mawawasak. Ang lumang kontratang datos ay maaaring awtomatikong malilipat sa ibang subcontract bago ito mawasak, gamit ang contract migration na mga kasangkapan.

## 4. Birtwal na Makina

### 4.1 Birtwal na Hardware

Ang NeoVM ay nagbibigay ng isang birtwal na hardware layer, upang sumuporta ng mga matalinong kontrata, kabilang ang:

 * **CPU**

 Ang CPU ay responsable para sa pagbabasa at magkakasunod na pagkakaayos ng pagpapatupad ng mga instruksyon sa kontrata, ayon sa punsyon ng flow control ng instruksyon, aritmetikang mga operasyon, lohikang mga operasyon. Ang hinaharap ng CPU na punsyon ay maaaring mapalawak, gamit ang pagpapakilala ng JIT (real-time na kompayler) na punsyon, sa gayon ay nagpapabuti sa kahusayan na pagpapatupad ng instruksyon.

 * **Call Stack**

   Ang call stack ay ginagamit upang maghawak ng mga kontekstong impormasyon ng pagpapatupad ng program sa bawat pagtawag ng punsyon, upang ito ay maaaring magpatuloy sa pagpapatupad sa kasalukuyang konteksto pagkatapos ng pagpapatupad at pagsasauli ng punsyon.

 * **Calculate Stack**

   Ang lahat ng run-time na datos ng NeoVM ay naka-imbak sa kalkulasyon na stack, kung kailan matatapos ang implementasyon ng magkaibang mga instruksyon, ang stack ay ikakalkula sa nararapat na mga elemento na datos sa operasyon. Halimbawa, kapag ang karagdagang mga instruksyon ay naipatupad, ang dalawang mga operasyon na lumalahok sa pagdaragdag ay papaalisin mula sa kalkulasyon na stack, at ang resulta ng pagdaragdag ay itutulak sa itaas ng stack. Ang mga parametro sa pagtawag ng punsyon ay dapat ding makalkula mula sa kanan patungo sa kaliwa, ayon sa pakakaayos ng stack. Pagkatapos ng matagumpay na pagpatupad ng punsyon, ang nasa itaas ng stack fetch-function ay magsasauli ng halaga.

 * **Spare Stack**

  Kapag kailangan mong mag-iskedyul o mag-ayos muli ng mga elemento sa stack, maaari mong pansamantalang iimbak ang mga elemento sa spare stack at kunin ang mga ito sa hinaharap.

### 4.2 Pangkat ng instruksyon 

Ang NeoVM ay nagbibigay ng isang pangkat ng simple, at praktikal na mga instruksyon para sa pagbubuo ng matalinong kontratang mga program.
Ayon sa mga punsyon, ang pangunahing mga kategorya ay ang mga sumusunod:

 * Constant na instruksyon
 * Prosesong kontrol na instruksyon
 * Stack na operasyon na instruksyon
 * String na instruksyon
 * Lohikang instruksyon
 * Aritmetikang operasyon na instruksyon
 * Cryptographic na instruksyon
 * Datos na operasyon na instruksyon

Mahalagang tandaan na ang NeoVM na pangkat ng instruksyon ay nagbibigay ng isang serye ng cryptographic na mga instruksyon, katulad ng ECDSA, SHA at iba pang mga algoritmo upang mas mapabuti ang kahusayan ng implementasyon ng cryptographic na mga algoritmo sa mga matalinong kontrata. Sa karagdagan, ang pagmanipula ng datos na mga instruksyon ay direktang sumusuporta ng mga array at kumplikadong mga istraktura ng datos.

### 4.3 Interoperable na service layer

Ang birtwal na makina kung saan ipinapatupad ang matalinong kontrata ay isang sandbox environment, na nangangailangan ng isang interoperable na service layer, sa mga panahon kapag ito ay kailangang mag-access ng datos sa labas ng sandbox o upang panatilihing matiyaga ang run-time na datos. Sa loob ng interoperable na service layer, ang NEO na kontrata ay maaaring magbukas ng isang serye ng sistema na punsyon at mga serbisyo gamit ang program ng matalinong kontrata, at mga kontratang ito ay maaaring matawag at ma-access, kagaya ng ordinaryong mga punsyon. Ang lahat ng mga sistema na punsyon ay kasabay na isinasagawa, kaya hindi na kailangang mangamba tungkol sa kakayahan sa pag-iskala.

### 4.4 Punsyon ng Pag-debug	

Kadalasan, ang pag-develop ng mga matalinong kontrata ay napakahirap, dahil sa kakulangang ng mabuting debugging at testing na mga pamamaraan. Ang NeoVM ay nagbibigay ng program debugging na supporta at ang birtwal na makinang lebel, kung saan maaari mong itakda ang breakpoint sa kontratang code, o single-step, single-process na pagpapatupad. Salamat sa mababang coupling na disenyo sa pagitan ng birtwal na makina at ang blockchain, madaling direktang pagsamahin ang NeoVM sa iba't ibang mga IDE, upang magbigay ng isang test na enviroment na naaalinsunod sa huling produksyon na environment.

## 5. Mataas na lebel na lengguwahe

### 5.1 C#, VB.Net, F#

Ang mga developer ay maaaring gumamit ng NeoContract para sa halos anumang mataas na lebel na lengguwahe kung saan sila mahusay. Ang unang pangkat ng suportadong mga lengguwahe ay C #, VB.Net, F #, etc. Nagbigay kami ng mga kompayler at mga plug-in para sa mga lengguwaheng ito, na nagpapahintulot sa pagkompayl nitong mga mataas na lebel na lengguwahe sa hanay ng instruksyon, na suportado ng NeoVM. Habang ang kompayler ay nakatutok sa MSIL (Microsoft intermediate language) sa panahon ng pagkompayl, kaya batay sa teorya, kahit anong. Net na lengguwahe ay maaaring isalin sa MSIL na lengguwahe, at maging direktang suportado.

Isang malaking bilang ng mga developer ay mahuhusay sa mga lengguwaheng ito, at ang nasa itaas na mga lengguwahe ay may isang napalakas na integrated development na environment. Ang mga developer ay maaaring mag-develop, bumuo, sumubok at mag-debug, lahat sa loob ng Visual Studio, kung saan sila ay maaaring buong makakagamit ng mga development template ng matalinong kontrata na binigay namin, upang makamit ang isang pangunahing panimula.

### 5.2 Java, Kotlin

Ang Java at Kotlin ay bumubuo sa pangalawang pangkat ng suportadong mga lengguwahe, kung saan nagbigay kami ng mga kompayler at IDE na mga plugin para sa mga lengguwaheng ito, upang tulungan ang mga developer sa paggamit ng nakabase sa JVM na lengguwahe upang mag-develop sa Matalinong Kontratang mga aplikasyon ng NEO.

Ang Java ay malawakang ginagamit, at ang Kotlin ay kamakailang naging opisyal na rekomendado ng Google, Android-development na lengguwahe. Naniniwala kami na ang pagsuporta sa mga lengguwaheng ito ay tutulong sa lubhang pagtaas ng bilang ng mga developer ng matalinong kontrata ng NEO. 

### 5.3 Ibang mga Lengguwahe

Pagkatapos, ang NeoContract ay magdaragdag ng suporta para sa ibang mataas na lebel na mga lengguwahe, batay sa antas ng kahirapan, sa proseso ng development ng kompayler. Ang ilang mga lengguwahe na maaaring nasuportahan, ay kabilang ang:

 * C, C++, GO
 * Python, JavaScript

Sa hinaharap, patuloy kaming magdaragdag ng marami pang suporta ng mataas na lebel na lengguwahe. Ang aming layunin ay makakita ng higit pa sa 90% ng mga developer ng NEO na nagde-develop gamit ang NeoContract, nang hindi nangangailangang mag-aral ng isang panibagong lengguwahe, at kahit posibleng direktang maglipat ng umiiral na pangnegosyong sistema na code tungo sa blockchain.

## 6. Serbisyo	

### 6.1 Blockchain na Ledger

Ang mga Matalinong Kontrata ay maaaring makakuha ng kumpletong bloke na datos para sa NEO blockchain, kabilang na ang kumpletong mga bloke at mga transaksyon, at bawat mga field nito, sa runtime, gamit ang sistema na mga punsyong binigay ng interoperable na serbisyo. Sa partikular, maaari kang mag-query ng mga datos na ito:

 * Taas ng blockchain
 * Block head, kasalukuyang block
 * Mga transaksyon
 * Uri ng transaksyon, mga katangian, input, awtput, etc.

Gamit ang mga datos na ito, maaari kang mag-develop ng ilang kawili-wiling mga aplikasyon, katulad ng isang awtomatikong mga payout, mga matalinong mga kontrata batay sa pagpapatunay ng workload.

### 6.2 Mga Digital Asset

Gamit ang interoperable na mga serbisyo na binigay ng digital asset na interface, ang mga matalinong kontrata ay maaari lamang mag-query ng NEO blockchain sa mga katangian at mga istatistika ng iba't ibang mga digital asset, ngunit, bumuo rin ng panibagong mga digital asset habang nasa run-time nito. Ang mga digital asset na nalikha ng mga matalinong kontrata maaaring iisyu, ilipat, mapalitan sa labas ng kontrata. Sila ay kapareho sa orihinal na mga asset sa NEO, at maaaring mapamahalaan gamit ang anumang NEO-compatible, wallet na software. Ang tiyak na interface na ito ay kabilang ang:

 * Asset attribute na pag-usisa
 * Asset statistics na query
 * Asset life cycle na pamamahala: paglikha, pagbago, pagwasak, etc.
 * Asset na pamamahala: multi-language na pangalan, kabuuang pagbabago, katumpakang pagbabago, mga pagbabago sa administrador

### 6.3 Pagtitiyaga

Ang bawat program ng matalinong kontrata na naka-deploy sa NEO blockchain, ay magkakaroon ng isang pribadong storage na lawak na maaari lamang mabasa at masulatan ng kontrata mismo. Ang mga matalinong kontrata ay may buong gumaganang mga permiso sa datos sa sarili nitong imbakan: maaaring basahin, sulatan, baguhin, at burahin. Ang datos ay nakaimbak sa porma ng key-value na pares at nagbibigay nitong mga interface:

 * Traverse all the records stored
 * Return to a specific record according to the specified key
 * Modify or write new records according to the specified key
 * Delete the record according to the specified key

In general, a contract can only read and write data from its own store, with one exception: when a contract is invoked, the invoked contract can access the caller's store through a cross-domain request, provided that the caller provides authorization. In addition, for a sub-contract that is dynamically created at the time of contract execution, the parent contract gets instant access to its store.

Cross-domain requests enable NeoContract to implement rich library capabilities, that provide highly scalable data management capabilities for the callers.

## 7. Fees

### 7.1 Deployment Fee

NEO's distributed architecture provides high redundancy of storage capacity, and the use of this capacity is not free. Deploying a smart contract on the NEO network requires a fee, currently fixed at 500GAS, which is collected by the system and recorded as a system gain. Future fees will be adjusted according to the actual operating cost in the system. The smart contract deployed on the blockchain can be used multiple times, until the contract is destroyed by the deployer.

### 7.2 Implementation Fee

NEO provides a credible execution environment for smart contracts, and the execution of contracts requires the consumption of computing resources for each node, therefore users are required to pay for the execution of smart contracts. The fee is determined by the computational resources consumed with each execution, and the unit price is also in GAS. If the implementation of the smart contract fails due to lack of GAS, the cost of consumption will not be returned, and this prevents malicious attacks on the network power consumption.

For most simple contracts, they can be executed for free, so long as the execution costs remain under 10 GAS, thus greatly reducing costs for the user. 

## 8. Application Scenarios

### 8.1 Superconducting Transactions

Digital assets on the blockchain inherently require some form of liquidity and usually point-to-point transactions cannot provide it sufficiently.  Therefore, there is a need for exchanges to provide users with trading services. Digital asset exchanges can be broadly divided into two categories:

1. **Central exchanges:** where the user needs to deposit the digital assets with the exchange, and subsequent place pending orders for trading, on the website
2. **Decentralized exchanges:** where its trading system is built into the blockchain, and the system provides the matching services.

Centralized exchanges can provide very high performance and diversified services, but need to have a strong credit guarantee, otherwise there will be moral hazards; such as misappropriation of user funds, fraud, etc. Comparatively, decentralized exchange has no moral hazard, but the user experience is poor, and there is greater performance bottleneck. Is there a way to combine both solutions and achieve the best of both worlds?

Superconducting transactions is a mechanism that can do this; Users do not need to deposit assets, where they are able to use their own assets on the blockchain in trading. Transaction settlement complete on the blockchain, but the process of matching orders occurs off-chain, by a central exchange that provides matching services. Since the matching is conducted off-chain, its efficiency is like centralized exchanges, but the assets remain under the control of the user. Exchanges uses the user's trading intent to carry out matching services, with no moral hazards involved, such as misappropriation of user funds, fraud, etc.

At present, within the NEO community, development of smart contracts to achieve blockchain superconducting transactions has emerged, such as OTCGO.

### 8.2 Smart Fund

Smart funds based on the blockchain have the benefit of being decentralized, open and transparent, possessing a higher degree of security and freedom as compared to traditional funds. These smart funds are also cross-border and open to investors worldwide, where outstanding projects can be funded with capital from all across the world.

Nest is a NeoContract-based smart fund project, which is very similar to the TheDAO project based on Ethereum, where improved security measures is needed to avoid the mistakes of TheDAO (hackers).

### 8.3 Cross-chain Interoperability

In the foreseeable future, there will be many public chains and thousands of alliance chains or private chains in existence worldwide. These isolated blockchain systems are islands of value and information, which are not interoperable with each other. Through the cross-chain interoperability mechanism, numerous isolated blockchains can be linked, so that the values in different blockchains can be exchanged with each other, to achieve the true value of the Internet.

NeoContract provides support for the implementation of cross-chain interoperability, ensuring consistency within cross-chain asset exchange, cross-chain distributed transactions, and execution of smart contracts on different blockchains.

### 8.4 Oracle Machines

The concept of oracles in folktale lies in the ability of a certain supernatural entity that can answer a particular set of questions. In the blockchain, oracle machines open the door to the outside world for smart contracts, making it possible for smart contracts to use real-world information as a condition for contract execution.

NeoContract does not provide the ability to directly access external data, such as access to resources on the Internet, because this will introduce non-deterministic behavior, resulting in inconsistencies between nodes during contract execution. Implementing the oracle machine in NeoContract requires that external data be sent to the blockchain by a trusted third party, integrating these data feeds as part of the blockchain ledger, thereby eliminating non-determinism.

The credible third party mentioned above, may be a person or institution that is co-trusted by both parties in the contract, or a decentralized data provider that is guaranteed by economic incentives. In this manner, NeoContract can be used in the implementation of such Oracle machines.

### 8.5 Ethereum DAPP

Bitcoin created the era of blockchains and electronic cash, and Ethereum created the era of smart contracts. Ethereum, the pioneers of smart contract on the blockchain, has made great contributions to the design idea, economic model and technological realization of a smart contract system. At the same time, the Ethereum platform has seen many DAPPs (distributed applications), where functionalities including: gambling agreements, digital assets, electronic gold, gaming platform, medical insurance, marriage platform, with widespread use over many industries. In theory, all of these DAPPs can be easily transplanted onto the NeoContract platform, as a NEO application.
