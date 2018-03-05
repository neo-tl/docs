# NeoContract na White Paper

## 1. Paunang Salita

Ang smart na mga kontrata ay sumasangguni sa anumang kompyuter na program na maaaring awtomatikong magsagawa ng mga termino sa kontrata na naka-preprogram nito. Ang ideya ng smart kontrata ay unang iminungkahi ng kriptograper na si Nick Szabo noong 1994, ginagawa itong kasing luma sa Internet. Dahil sa kakulangan ng isang maaasahang environment ng pagpapatupad, ang smart na mga kontrata ay hindi malawakang nagamit. 

Sa 2008, isang tao na nasa ilalim ng pangalan na Satoshi Nakamoto ay naglabas ng Bitcoin, at bumalangkas sa pampundasyon na mga konsepto ng isang blockchain. Sa loob ng Bitcoin na blockchain, si Nakamoto ay gumagamit ng isang hanay ng mga scripting language upang tulungan ang mga gumagamit na makamit ang mas kakayahang umangkop sa pagkontrol ng kanilang personal na mga account at mag padala ng proseso, na sa kalaunan ay naging embryonic na porma ng isang nakabase sa chain, ang smart na kontrata na sistema.

Sa 2014, isang binatilyo na nakapangalan Vitalik Buterin ay naglabas ng Ethereum, na nagbibigay ng isang nakabase sa chain, Turing-complete, ang mataling kontrata na sistema na maaaring gamiting upang lumikha ng isang iba't ibang mga aplikasyon ng decentralized na blockchain.

Ang NEO na blockchain ay isang digital asset at aplikasyon na plataporma, na nagbibigay ng isang bagong smart na kontrata na sistema, ang NeoContract. Sa kaloob-looban ng Neo na plataporma, ang network ay nagbibigay ng maramihang mga punsyon katulad ng mga kakayahan ng digital asset, ang NeoAsset, at digital na pagkakakilanlan, ang NeoID, na nagpapahintulot sa mga gumagamit na madaling makisali sa digital na mga negosyo, at hindi na limitado lamang sa pagpapalabas likas na mga token sa blockchain.

Ang artikulong ito ay magpapakilala sa mga tampok ng NeoContract at magsisiyasat sa hindi teknikal na mga detalye. Mangyaring sumangguni sa teknikal na dokumentasyon para sa teknikal na mga detalye: [docs.neo.org](http://docs.neo.org).

## 2. Mga Tampok

### 2.1 Katiyakan

Kung ang isang program ay tumatakbo sa magkaibang mga kompyuter, o sa magkaibang panahon sa parehong kompyuter, ang pagkilos ng program ay matutukoy kung ang parehong input ay garantisadong makakagawa ng parehong output, at kabaligtaran.

Ang Blockchain ay isang multi-party na imbakan, at kalkulasyon na pamamaraan, kung saan ang datos sa loob nitong ipinamamahaging sistema ay ang resulta ng maasahang mga kalkulasyon, at hindi maaaring mabago. Ang smart na mga kontrata ay gumagana sa loob ng multi-node, ang ipinamamahaging blockchain na network. Kung ang isang smart na kontrata ay non-deterministic, ang mga resulta ng magkaibang mga node ay maaaring hindi pantay-pantay. Bilang resulta, ang pagkasunduan sa pagitan ng mga node ay hindi maaaring maabot, at ang network ay magiging hindi umuunlad. Samakatuwid, sa disenyo ng isang smart na kontrata na sistema, mayroong isang pangangailangan na mag-alis ng anumang mga kadahilanan na maaaring magsanhi ng non-deterministic na pagkilos.

#### 2.1.1 Oras

Ang pagkakaroon ng system-time ay isang napakakaraniwang punsyon ng sistema, na maaaring mabigat na nailalapat sa tiyak na mga pamamaraan ng time-sensitive na kontrata. Gayunpaman, ang pagkakaroon ng system-time ay isang non-deterministic na punsyon ng sistema, at mahirap kumuha ng isang pinag-isa, tumpak na oras sa isang ipinamamahaging na sistema, batay sa mga resulta ng magkaibang mga node ay hindi magkakapantay. Ang NeoContract ay nagbibigay ng isang block-based na system-call na tinatrato ang buong blockchain, bilang isang timestamp na server, at kumukuha ng timestamp kailanman nabuo ang isang bagong bloke. Karaniwan, ang NEO na network ay lumilikha ng isang bagong bloke sa bawat 15 na mga segundo, kaya ang kontrata ay tumatakbo sa humigit-kumulang na parehong oras sa pinakabagong block-time, dagdag bawas ng 15 na mga segundo.

#### 2.1.2 Pagkasapalaran

Maraming smart na kontrata na mga program, katulad ng pagsusugal na mga kontrata at maliliit na mga laro, ay gumagamit ng sapalarang numero na mga function. Gayunpaman, ang sapalarang numero na mga punsyon ay isang tipikal na hindi natutukoy na function, at bawat system-call ay kumukuha ng magkaibang mga resulta. Sa isang ipinamamahaging sistema, may maraming mga paraan upang malutas ang problemang ito: Una, ang parehong sapalaran na seed ay maaaring gamitin para sa lahat ng mga node, upang ang return na pagkakasunod-sunod ng buong sapalaran na punsyon ay matutukoy, ngunit ang paraang ito ay naglalantad sa buong sapalaran na resulta nang maaga, labis na nagbabawas ng praktikal na halaga ng sapalarang numero. Isa pang posibleng solusyon, ay hayaan ang lahat ng node na makipag-usap sa isang kolaboratibong paraan upang bumuo ng sapalarang mga numero. Maaari itong makamit sa paggamit ng cryptographic na mga pamamaraan upang lumikha ng isang patas na sapalarang numero, ngunit ang kawalan ay nakapatong sa napakababaw na pagganap, at sa pangangailangan ng karagdagang pananaw sa komunikasyon. Ang isang sentralisadong tagapagtustos ng sapalarang numero ay maaaring gamitin upang bumuo ng sapalarang mga numero na nangangako ng walang pagbabago at pagganap, ngunit ang sagabal sa ganitong paraan ay halata; Ang mga gumagamit ay kailangang walang kondisyong magtiwala sa sentralisadong tagapagtustos ng numero.

Mayroong dalawang paraan upang makabuo ng isang sapalarang numero sa NEO:

1. Kapag ang bawat bloke ay nabuo, ang consensus na node ay aabot sa isang pagkakasundo sa isang sapalarang numero, at ipupuno ito sa Nonce na patlang sa bagong bloke. Ang kontrata na program ay madaling makakuha ng sapalarang numero sa anumang bloke, sa pamamagitan ng pagreperensya ng Nonce na patlang

2. Ang kontrata na program ay maaaring gumamit ng hash na halaga sa bloke bilang isang generator ng sapalarang numero, dahil ang block hash na halaga ay may tiyak na likas na pagkasapalaran. Ang paraang ito ay maaaring gamitin upang makakuha ng isang mahinang sapalarang numero

#### 2.1.3 Data Source

Kung ang isang program ay nakakuha ng datos sa run-time, ito ay maaaring maging isang non-deterministic na program kung ang data source ay nagbibigay ng non-deterministic na datos. Halimbawa, ang paggamit ng magkaibang mga search engine upang makakuha ng nangungunang 10 na mga resulta sa paghanap para sa isang partikular na keywork, ay maaaring mag-ani ng magkaibang mga resulta, sa iba't ibang paraan ng pagkakaayos, kung magkaibang mga IP address ang ginamit.

Para sa smart na mga kontrata, ang NEO ay nagbibigay ng dalawang mga uri ng natutukoy na mga data source:

1. **Blockchain na Ledger**
	
   Ang kontrata na pamamaraan ay maaaring mag-access sa lahat ng datos sa buong chain gamit ang interoperable na mga serbisyo, kabilang ang kumpletong mga bloke at mga transaksyon, at para sa bawat patlang nila. Ang datos sa mga bloke ay natutukoy at hindi nagbabago, kaya maaari silang ligtas na ma-access gamit ang smart na mga kontrata.

2. **Ispasyo Na Imbakan ng Kontrata**

   Bawat kontratang nai-deploy sa NEO na network, ay mayroong isang pribadong ispasiyo na imbakan na maaari lamang ma-access gamit ang kontrata. Ang mekanismo sa pagkakasundo ng NEO ay sumisigurado sa hindi pagbabago ng estado ng imbakan, sa bawat node sa network.

Para sa mga sitwasyon kung saan ang pag-access sa hindi blockchain na datos ay kinakailangan, ang NEO ay hindi nagbibigay ng isang direktang paraan upang makipag-ugnayan sa mga datos na ito.
Ang hindi blockchain na datos ay kailangang ilipat sa NEO na blockchain gamit ang mga transaksyon, at pagkatapos ay isinalin sa alinmang nabanggit na mga data source, upang ma-access gamit ang smart na mga kontrata. 

#### 2.1.4 Kontrata na Pagtawag

Ang smart na mga kontrata sa NeoContract ay maaaring tumawag sa isa't isa, ngunit hindi dapat tawaging naka-recursive. Ang recursion ay maaaring makamit sa loob ng kontrata, ngunit hindi kayang tumawid sa mga hangganan ng kasalukuyang kontrata. Sa karagdagan, ang relasyon ng pagtawag sa pagitan ng mga kontrata ay dapat naka-static: Ang target ay hindi dapat tukuyin sa runtime. Ito ay nagpapahintulot ng pagkilos ng program upang maging buong determinado bago ang pagpapatupad, at ang relasyon ng pagtawag nito upang maging buong matukoy bago ito maaaring patakbuhin. Batay nito, ang maramihang mga kontrata ay maaaring dynamic na ma-partition upang makamit ang nakahilerang pagpapatupad.

### 2.2 Mataas na Pagganap

Ang environment ng pagpapatupad ng isang smart na kontrata ay naglalaro ng isang mahalagang papel sa pagganap nito. Kapag ating pinag-aralan ang pagganap sa anumang environment ng pagpapatupad, may dalawang pangunahing tagapagpahiwatig na kritikal:

1. Bilis ng pagpapatupad ng tagubilin
2. Bilis ng startup ng environment na pagpapatupad

Para sa mga smart na kontrata, ang environment ng pagpapatupad ay kadalasang mas importante kaysa sa bilis ng pagpapatupad ng tagubilin. Ang mga smart na kontrata ay mas kasangkot sa IO na operasyon ng lohika, upang matukoy ang mga tagubilin, kung saan ang implementasyon ng mga tagubiling ito ay madaling mapaunlad. Sa bawat pagkakataon na tinawag na smart na kontrata, dapat itong magsimula ng isang panibagong birtwal na makina / container. Samakatuwid, ang bilis ng pagpapatupad sa environment (pagsisimula ng isang birtwal na makina / container) ay may mas malaking epekto sa pagganap ng smart na kontrata na sistema.

Ang NEO ay gumagamit ng isang magaang NeoVM (Birtwal na Makina ng NEO) bilang smart na kontratang execution environment nito, na mayroong isang napakabilis na start up at kumukuha ng napakaliit na mga resource, perpekto para sa maikling mga program katulad ng mga smart na kontrata. Ang paggamit ng pag-compile at pag-cache ng hotspot na mga smart na kontrata gamit ang JIT (totoong-oras na compiler) ay maaaring makabuluhang magpabuti sa kahusayan ng mga birtwal na makina.

### 2.3 Kakayahan sa Pag-iskala

#### 2.3.1 Mataas na pagkakasabay at dynamic na pagpartisyon

Kapag tayo ay nagtatalakay ng kakayahan sa pag-iskala ng isang sistema, ito ay nagsasangkot ng dalawang pangunahing mga aspeto: Ang bertikal na pag-iskala at pahalang na pag-iskala. Ang bertikal na pag-iskala ay tumutukoy sa optimisasyon ng nagpoprosesong workflow, na nagpapahintulot sa sistema na gamitin ng husto sa umiiral na kapasidad ng kagamitan. Sa pamamaraang ito, ang mga limitasyon ng sistema ay madaling maaabot, dahil ang series-based processing na kapasidad ay nakabase sa limitasyon ng hardware sa isang solong aparato. Kapag kailangan nating iiskala ang sistema, mayroon bang paraan upang mag-transform ng mga serye na sistema sa isang kahilera na sistema? Sa pagkateoretikal, kailangan lamang nating dagdagan ang bilang ng mga aparato, at maaari na nating makamit ang halos walang limitasyon na kakayahan sa pag-iskala. Pwede ba nating makamit ang walang limitasyon na pag-iskala sa ibinahaging mga blockchain network? Sa ibang salita, maaari bang magsagawa ang blockchain ng mga program na nakahilera?

Ang blockchain ay isang ibinahaging ledger, na nagtatala ng iba't-ibang estado ng datos at mga panuntunan na namamahala sa mga pagbabago sa estado ng mga datos na ito. Ang mga smart na kontrata ay ginamit bilang mga tagapagdala, upang magtala sa mga panuntunang ito. Ang mga blockchain ay maaaring magproseso ng mga program na nakahilera, lamang kung, ang maramihang mga smart na kontrata ay maaaring maisagawa nang sabay-sabay at sa isang hindi magkasunod-sunod na paraan. Sa madaling salita, kung ang mga kontrata ay hindi nakikipag-ugnayan sa isa't isa, o kung ang kontrata ay hindi nagbabago ng parehong estado ng datos, sa parehong panahon, ang kanilang pagpapatupad ay hindi magkakasunod at maaaring isagawa nang sabay-sabay. Kung hindi, ito ay magsasagawa lamang nang nakaserye, na sumusunod sa isang magkakasunod na pagkakaayos, at ang network ay hindi maaaring mag-iskala nang pahalang.

Base sa pagsusuri sa itaas, maaari tayong madaling magdisenyo ng "walang limitasyon na pag-iskala" sa mga sistema ng smart na kontrata. Ang lahat nang dapat nating gawin ay ang pag-set up ng simpleng mga panuntunan:
 
 * **Ang isang smart na kontrata ay maaari lamang magbago ng estado na rekord sa kontrata kung saan ito nabibilang**

 * **Sa parehong transaksyon na batch (block), ang isang kontrata ay maaari lamang patakbuhin sa isang beses**

Bilang isang resulta, ang lahat ng mga smart na kontrata ay maaari lamang maproseso na nakahilera sa sunud-sunod na pagkakaayos na walang kaugnayan sa resulta. Gayunpaman, kung ang isang "smart na kontrata ay maaari lamang magbago ng estado na rekord sa kontrata kung saan ito nabibilang", ito ay nagpapahiwatig na ang kontrata ay hindi makakatawag sa isa't isa. Ang bawat kontrata, ay isang hiwalay na isla; kung "Sa parehong transaksyon na batch (block), ang isang kontrata ay maaari lamang patakbuhin sa isang beses", ito ay nagpapahiwatigna ang isang digital asset na ibinigay gamit ang isang smart na kontrata, maaari lamang mag-asikaso ng isang transaksyon sa bawat bloke. Ito ay isang mundo ng pagkakaiba sa mga layunin ng orihinal na disenyo ng mga "smart" na kontrata, na titigil sa pagiging "smart". Sa wakas, ang aming mga disenyo na layunin ay parehong mutwal na pagtawag sa pagitan ng mga kontrata, at maramihang pagpapatupad ng parehong pagtawag, sa parehong bloke.

Sa kabutihang-palad, ang mga smart na kontrata sa NEO ay may isang static call na relasyon, at ang call target ay hindi maaaring tukuyin sa run time. Pinapayagan nito ang pag-uugali ng program na maging buong nakatukoy bago sa pagpapatupad, at buong nakatukoy ang call na relasyon nito bago ito maaaring tumakbo. Kinakailangan namin na ang bawat kontrata ay tahasang ipahiwatig ang mga kontrata na maaaring matatawag, upang ang nag-ooperang environment ay maaaring magkalkula sa kumpletong call tree bago magpapatakbo ng kontrata na pamamaraan, at partisyon na pagpapatupad ng mga kontrata, base sa call tree. Ang mga kontrata na maaaring baguhin ang parehong estado na rekord, ay maisasagawa sa isang 
magkakasunod na paraan sa loob ng parehong partisyon, kung saan ang magkaibang mga partisyon ay maaari nang isagawa na nakahilera.

#### 2.3.2 Mababang coupling

Ang coupling ay isang sukatan ng dependensya sa pagitan ng dalawa o maraming mga entity. Ang NeoContract na sistema ay gumagamit ng isang mababang-coupling na disenyo, na naipapatupad sa NeoVM, at nakikipag-ugnayan sa hindi blockchain na datos gamit ang interoperable na service layer. Bilang isang resulta, ang karamihan sa mga upgrade sa smart na kontrata na mga function ay maaaring makamit sa pamamagitan ng pagpapalaki ng API ng mga interoperable service.

## 3. Paggamit ng Kontrata

### 3.1 Beripikasyon ng Kontrata

Hindi tulad ng public-key account na sistema na ginamit sa Bitcoin, ang account na sistema ng NEO ay gumagamit ng kontratang account na sistema. Ang bawat account sa NEO ay tumutugon sa isang beripikasyong kontrata, at ang hash na halaga ng beripikasyong kontrata, ay ang account address; Ang program na lohika ng beripikasyong kontrata ay kumukontrol sa pagmamay-ari ng account. Kapag naglilipat mula sa isang account, una mong kakailanganing magpatupad ng beripikasyong kontrata para sa account na iyon. Ang balidasyong kontrata ay maaaring tumanggap ng isang hanay ng mga parametro (kadalasan ang isang digital signature o ibang pamantayan), at nagsasauli ng isang boolean na halaga pagkatapos ng beripikasyon, nagpapahiwatig sa tagumpay ng beripikasyon sa sistema.

Ang user ay maaari munang mag-deploy ng beripikasyong kontrata sa blockchain, o mag-publish ng kontratang nilalaman nang direkta sa transaksyon habang nasa paglipat na proseso.

### 3.2 Kontratang Aplikasyon

Ang aplikasyon na kontrata ay nati-trigger ng isang espesyal na transaksyon, na maaaring mag-access at magbago ng global na estado ng sistema, at ang pribadong estado ng kontrata (storage area) sa run time. Halimbawa, maaari kang lumikha ng isang global digital asset sa isang kontrata, bumoto, mag-save ng datos, at kahit dynamic na lumikha ng isang bagong kontrata, kapag ang kontrata ay tumatakbo.

Ang pagpapatupad ng aplikasyon na kontrata ay nangangailangan ng pagsisingil gamit ang instruksiyon. Kapag ang transaksyon na fee ay natupok, ang kontrata ay mabibigo at hihinto sa pagpapatupad, at ang lahat ng estadong pagbabago ay maibabalik. Ang tagumpay ng kontrata ay hindi nakakaapekto sa bisa ng transaksyon.

### 3.3 Kontratang Function

Ang function na kontrata ay ginagamit upang magbigay ng ilang publiko o karaniwang ginagamit na mga function, na maaaring matawag sa ibang mga kontrata. Ang smart na kontrata na code ay maaaring magamit muli, upang ang mga developer ay maaaring magsulat ng lalong nagiging kumplikadong lohika ng negosyo. Ang bawat function na kontrata, kapag na-deploy, ay maaaring pumili na magkaroon ng isang pribadong storage area na alinman ay nabasa o naisulat sa datos sa isang hinaharap na kontrata, nakakamit ang pagpapanatili ng estado.

Ang function na kontrata ay dapat munang naka-pre-deploy sa chain upang matawag, at matanggal mula sa chain gamit ang isang "self-destructing" na sistemang function, na hindi na magagamit at ang pribadong storage nito ay mawawasak. Ang lumang kontratang datos ay maaaring awtomatikong malilipat sa ibang subcontract bago ito mawasak, gamit ang contract migration na mga kasangkapan.

## 4. Birtwal na Makina

### 4.1 Birtwal na Hardware

Ang NeoVM ay nagbibigay ng isang birtwal na hardware layer, upang sumuporta ng mga smart na kontrata, kabilang ang:

 * **CPU**

 Ang CPU ay responsable para sa pagbabasa at magkakasunod na pagkakaayos ng pagpapatupad ng mga instruksyon sa kontrata, ayon sa punsyon ng flow control ng instruksyon, aritmetikang mga operasyon, lohikang mga operasyon. Ang hinaharap ng CPU na punsyon ay maaaring mapalawak, gamit ang pagpapakilala ng JIT (real-time na kompayler) na punsyon, sa gayon ay nagpapabuti sa kahusayan na pagpapatupad ng instruksyon.

 * **Call Stack**

   Ang call stack ay ginagamit upang maghawak ng mga kontekstong impormasyon ng pagpapatupad ng program sa bawat pagtawag ng punsyon, upang ito ay maaaring magpatuloy sa pagpapatupad sa kasalukuyang konteksto pagkatapos ng pagpapatupad at pagsasauli ng punsyon.

 * **Calculate Stack**

   Ang lahat ng run-time na datos ng NeoVM ay naka-imbak sa kalkulasyon na stack, kung kailan matatapos ang implementasyon ng magkaibang mga instruksyon, ang stack ay ikakalkula sa nararapat na mga elemento na datos sa operasyon. Halimbawa, kapag ang karagdagang mga instruksyon ay naipatupad, ang dalawang mga operasyon na lumalahok sa pagdaragdag ay papaalisin mula sa kalkulasyon na stack, at ang resulta ng pagdaragdag ay itutulak sa itaas ng stack. Ang mga parametro sa pagtawag ng punsyon ay dapat ding makalkula mula sa kanan patungo sa kaliwa, ayon sa pakakaayos ng stack. Pagkatapos ng matagumpay na pagpatupad ng punsyon, ang nasa itaas ng stack fetch-function ay magsasauli ng halaga.

 * **Spare Stack**

  Kapag kailangan mong mag-iskedyul o mag-ayos muli ng mga elemento sa stack, maaari mong pansamantalang iimbak ang mga elemento sa spare stack at kunin ang mga ito sa hinaharap.

### 4.2 Pangkat ng instruksyon 

Ang NeoVM ay nagbibigay ng isang pangkat ng simple, at praktikal na mga instruksyon para sa pagbubuo ng smart na kontratang mga program.
Ayon sa mga punsyon, ang pangunahing mga kategorya ay ang mga sumusunod:

 * Constant na instruksyon
 * Prosesong kontrol na instruksyon
 * Stack na operasyon na instruksyon
 * String na instruksyon
 * Lohikang instruksyon
 * Aritmetikang operasyon na instruksyon
 * Cryptographic na instruksyon
 * Datos na operasyon na instruksyon

Mahalagang tandaan na ang NeoVM na pangkat ng instruksyon ay nagbibigay ng isang serye ng cryptographic na mga instruksyon, katulad ng ECDSA, SHA at iba pang mga algoritmo upang mas mapabuti ang kahusayan ng implementasyon ng cryptographic na mga algoritmo sa mga smart na kontrata. Sa karagdagan, ang pagmanipula ng datos na mga instruksyon ay direktang sumusuporta ng mga array at kumplikadong mga istraktura ng datos.

### 4.3 Interoperable na service layer

Ang birtwal na makina kung saan ipinapatupad ang smart na kontrata ay isang sandbox environment, na nangangailangan ng isang interoperable na service layer, sa mga panahon kapag ito ay kailangang mag-access ng datos sa labas ng sandbox o upang panatilihing matiyaga ang run-time na datos. Sa loob ng interoperable na service layer, ang NEO na kontrata ay maaaring magbukas ng isang serye ng sistema na punsyon at mga serbisyo gamit ang program ng smart na kontrata, at mga kontratang ito ay maaaring matawag at ma-access, kagaya ng ordinaryong mga punsyon. Ang lahat ng mga sistema na punsyon ay kasabay na isinasagawa, kaya hindi na kailangang mangamba tungkol sa kakayahan sa pag-iskala.

### 4.4 Punsyon ng Pag-debug	

Kadalasan, ang pag-develop ng mga smart na kontrata ay napakahirap, dahil sa kakulangang ng mabuting debugging at testing na mga pamamaraan. Ang NeoVM ay nagbibigay ng program debugging na supporta at ang birtwal na makinang lebel, kung saan maaari mong itakda ang breakpoint sa kontratang code, o single-step, single-process na pagpapatupad. Salamat sa mababang coupling na disenyo sa pagitan ng birtwal na makina at ang blockchain, madaling direktang pagsamahin ang NeoVM sa iba't ibang mga IDE, upang magbigay ng isang test na enviroment na naaalinsunod sa huling produksyon na environment.

## 5. Mataas na lebel na lengguwahe

### 5.1 C#, VB.Net, F#

Ang mga developer ay maaaring gumamit ng NeoContract para sa halos anumang mataas na lebel na lengguwahe kung saan sila mahusay. Ang unang pangkat ng suportadong mga lengguwahe ay C #, VB.Net, F #, etc. Nagbigay kami ng mga kompayler at mga plug-in para sa mga lengguwaheng ito, na nagpapahintulot sa pagkompayl nitong mga mataas na lebel na lengguwahe sa hanay ng instruksyon, na suportado ng NeoVM. Habang ang kompayler ay nakatutok sa MSIL (Microsoft intermediate language) sa panahon ng pagkompayl, kaya batay sa teorya, kahit anong. Net na lengguwahe ay maaaring isalin sa MSIL na lengguwahe, at maging direktang suportado.

Isang malaking bilang ng mga developer ay mahuhusay sa mga lengguwaheng ito, at ang nasa itaas na mga lengguwahe ay may isang napalakas na integrated development na environment. Ang mga developer ay maaaring mag-develop, bumuo, sumubok at mag-debug, lahat sa loob ng Visual Studio, kung saan sila ay maaaring buong makakagamit ng mga development template ng smart na kontrata na binigay namin, upang makamit ang isang pangunahing panimula.

### 5.2 Java, Kotlin

Ang Java at Kotlin ay bumubuo sa pangalawang pangkat ng suportadong mga lengguwahe, kung saan nagbigay kami ng mga kompayler at IDE na mga plugin para sa mga lengguwaheng ito, upang tulungan ang mga developer sa paggamit ng nakabase sa JVM na lengguwahe upang mag-develop sa smart na kontratang mga aplikasyon ng NEO.

Ang Java ay malawakang ginagamit, at ang Kotlin ay kamakailang naging opisyal na rekomendado ng Google, Android-development na lengguwahe. Naniniwala kami na ang pagsuporta sa mga lengguwaheng ito ay tutulong sa lubhang pagtaas ng bilang ng mga developer ng smart na kontrata ng NEO. 

### 5.3 Ibang mga Lengguwahe

Pagkatapos, ang NeoContract ay magdaragdag ng suporta para sa ibang mataas na lebel na mga lengguwahe, batay sa antas ng kahirapan, sa proseso ng development ng kompayler. Ang ilang mga lengguwahe na maaaring nasuportahan, ay kabilang ang:

 * C, C++, GO
 * Python, JavaScript

Sa hinaharap, patuloy kaming magdaragdag ng marami pang suporta ng mataas na lebel na lengguwahe. Ang aming layunin ay makakita ng higit pa sa 90% ng mga developer ng NEO na nagde-develop gamit ang NeoContract, nang hindi nangangailangang mag-aral ng isang panibagong lengguwahe, at kahit posibleng direktang maglipat ng umiiral na pangnegosyong sistema na code tungo sa blockchain.

## 6. Serbisyo	

### 6.1 Blockchain na Ledger

Ang mga smart na kontrata ay maaaring makakuha ng kumpletong bloke na datos para sa NEO blockchain, kabilang na ang kumpletong mga bloke at mga transaksyon, at bawat mga field nito, sa runtime, gamit ang sistema na mga punsyong binigay ng interoperable na serbisyo. Sa partikular, maaari kang mag-query ng mga datos na ito:

 * Taas ng blockchain
 * Block head, kasalukuyang block
 * Mga transaksyon
 * Uri ng transaksyon, mga katangian, input, awtput, etc.

Gamit ang mga datos na ito, maaari kang mag-develop ng ilang kawili-wiling mga aplikasyon, katulad ng isang awtomatikong mga payout, mga mga smart na kontrata batay sa pagpapatunay ng workload.

### 6.2 Mga Digital Asset

Gamit ang interoperable na mga serbisyo na binigay ng digital asset na interface, ang mga smart na kontrata ay maaari lamang mag-query ng NEO blockchain sa mga katangian at mga istatistika ng iba't ibang mga digital asset, ngunit, bumuo rin ng panibagong mga digital asset habang nasa run-time nito. Ang mga digital asset na nalikha ng mga smart na kontrata maaaring iisyu, ilipat, mapalitan sa labas ng kontrata. Sila ay kapareho sa orihinal na mga asset sa NEO, at maaaring mapamahalaan gamit ang anumang NEO-compatible, wallet na software. Ang tiyak na interface na ito ay kabilang ang:

 * Asset attribute na pag-usisa
 * Asset statistics na query
 * Asset life cycle na pamamahala: paglikha, pagbago, pagwasak, etc.
 * Asset na pamamahala: multi-language na pangalan, kabuuang pagbabago, katumpakang pagbabago, mga pagbabago sa administrador

### 6.3 Pagtitiyaga

Ang bawat program ng smart na kontrata na naka-deploy sa NEO blockchain, ay magkakaroon ng isang pribadong storage na lawak na maaari lamang mabasa at masulatan ng kontrata mismo. Ang mga smart na kontrata ay may buong gumaganang mga permiso sa datos sa sarili nitong imbakan: maaaring basahin, sulatan, baguhin, at burahin. Ang datos ay nakaimbak sa porma ng key-value na pares at nagbibigay nitong mga interface:

 * Tatawid sa lahat ng mga rekord na nakaimbak
 * Babalik sa isang tiyak na rekord ayon sa natukoy na key
 * Babaguhin o susulat ng bagong mga rekord ayon sa natukoy na key
 * Buburahin ang rekord ayon sa natukoy na key

Sa pangkalahatan, ang isang kontrata ay maaari lamang magbasa at magsulat ng datos mula sa sarili nitong store, na may isang pagbubukod: kapag ang isang kontrata ay natawag, ang natawag na kontrata ay maaaring mag-access ng store ng tumatawag gamit ang isang cross-domain na kahilingan, kung ang tumatawag ay nagbibigay ng awtorisasyon. Sa karagdagan, para sa isang sub-contract na dynamic na nalikha sa panahon sa pagpapatupad ng kontrata, ang magulang na kontrata ay kukuha ng madaliang access sa store nito.

Ang cross-domain na mga kahilingan ay nagbibigay ng kakayahan sa NeoContract upang magpatupad ng rich library na mga kakayahan, na nagbibigay ng mataas na kakayahan sa pag-iskala na data management na mga kakayahan para sa mga tumatawag.

## 7. Mga Bayad

### 7.1 Bayad ng Pag-deploy

Ang naipamahaging arkitektura ng NEO ay nagbibigay ng mataas na kalabisan sa kapasidad ng imbakan, at ang gamit ng kapasidad na ito ay hindi libre. Ang pagde-deploy ng isang smart na kontrata sa NEO na network ay nangangailangan ng isang bayad, kasalukuyang nakapirmi sa 500GAS, na kinukolekta ng sistema at tinatala bilang isang kita ng sistema. Ang hinaharap na mga bayad ay inaakma ayon sa aktwal na gumaganang gastos ng sistema. Ang smart na kontrata na naka-deploy sa blockchain ay maaaring gamitin nang maraming beses, hanggang ang kontrata ay nawasak ng nag-deploy.

### 7.2 Bayad ng Implementasyon

Ang NEO ay nagbibigay ng isang mapaniniwalaang execution environment para sa mga smart na kontrata, at ang pagpapatupad ng mga kontrata ay nangangailangan ng pagkonsumo ng mga computing resource para sa bawat node, samakatuwid ang mga gumagamit ay kinakailangang magbayad para sa pagpapatupad ng mga smart na kontrata. Ang bayad ay nakatukoy sa mga computational resource na nakonsumo sa bawat pagpapatupad, at ang yunit na presyo ay nasa GAS din. Kung ang pagpapatupad ng smart na kontrata ay mabibigo dahil sa kakulangan ng GAS, ang presyo ng pagkonsumo ay hindi maisasauli, at iiwasan nito ang may masamang hangarin na mga atake sa network power na pagkonsumo.

Para sa kadalasang simpleng mga kontrata, ang mga ito ay maaaring maipatupad nang libre, hangga't ang pagpapatupad na mga halaga ay nananatiling mababa pa sa 10 GAS, kaya naman lubhang nababawasan ang mga halaga para sa gumagamit.

## 8. Application na mga Sitwasyon

### 8.1 Pag-superconduct ng mga Transaksyon

Ang mga digital asset sa blockchain ay kadikit na nangangailangan ng ilang porma ng liquidity at kadalasan ang punto-per-punto na mga transaksyon ay hindi sapat na naibibigay ito. Samakatuwid, may isang pangangailangan para sa pagpapalitan upang mabigyan ang mga gumagamit ng pangkalakal na mga serbisyo. Ang digital asset na mga pagpapalitan ay maaaring malawak na mahahati sa dalawang mga kategorya:

1. **Sentral na mga pagpapalitan:** kung saan ang gumagamit ay kailangang magdeposito ng mga digital asset gamit ang pagpapalitan, at kasunod na maglagay ng nakabinbin na mga order para sa kalakalan, sa website
2. **Desentralisadong mga pagpapalitan:** kung saan ang kalakalang sistema nito ay nabuo sa blockchain, at ang sistema ay nagbibigay ng tumutugmang mga serbisyo.

Ang sentralisadong mga pagpapalitan ay maaaring magbigay ng sobrang napakataas na pagganap at sari-saring mga serbisyo, ngunit kailangang magkaroon ng isang malakas na credit na garantiya, kung hindi man ay magkakaroon ng moral na mga panganib; katulad ng maling paggamit ng mga pondo ng gumagamit, panloloko, etc. Kung pagpaparisin, ang desentralisadong pagpapalit ay walang moral na panganib, ngunit ang karanasan ng gumagamit ay hindi mabuti, at magkakaroon ng higit pang bottleneck sa pagganap. Mayroon bang isang paraan upang mapagsama ang parehong mga solusyon at makamit ang pinakamahusay sa parehong mundo?

Ang pag-superconduct ng mga transaksyon ay isang mekanismo na maaaring makakagawa nito; Ang mga gumagamit ay hindi na kailangang magdeposito ng mga asset, kung saan sila ay maaaring gumamit ng kanilang sariling mga asset sa blockchain sa kalakalan. Ang kasunduan ng transaksyon na nakumpleto sa blockchain, ngunit ang proseso ng pagtutugma ng mga order ay ay nagaganap sa off-chain, gamit ang isang sentral na pagpapalit na nagbibigay ng pagtutugma na mga serbisyo. Dahil ang pagtutugma ay nagaganap sa off-chain, ang kahusayan nito ay katulad ng sentralisadong mga pagpapalitan, ngunit ang mga asset na nananatiling nasa ilalim ng kontrol ng gumagamit. Ang mga pagpapalitan ay gumagamit ng pangkalakal na layunin ng gumagamit upang maisakatuparan ang pagpapatupad ng mga serbisyo, nang walang moral na mga panganib na kasangkot, katulad ng maling paggamit ng mga pondo ng gumagamit, panloloko, etc.

Sa kasalukuyan, sa loob ng kumunidad ng NEO, ang pag-develop ng mga smart na kontrata upang makamit ang pag-superconduct ng blockchain na mga transaksyon ay lumitaw, katulad ng OTCGO.

### 8.2 Matalinong Pondo

Ang mga matalinong pondo ay nakabatay sa pagkakaroon ng benepisyo ng blockchain bilang desentralisado, bukas at madaling maunawaan, nagtataglay ng isang mas mataas na antas ng seguridad at kalaay kumpara sa tradisyonal na mga pondo. Ang mga matalinong pondo na ito ay cross-border at bukas rin sa mga mamumuhunan sa buong mundo, kung saan ang mga tanyag na proyekto ay maaaring pondohan gamit ang kapital mula sa lahat sa buong mundo.

Ang Nest ay isang nakabase sa NeoContract na matalinong pondo na proyekto, na sobrang katulad sa TheDAO na proyekto batay sa Ethereum, kung saan ang pinabuting mga panukala sa seguridad ay kinakailangan upang maiwasan ang mga pagkakamali ng TheDAO (mga hacker).

### 8.3 Cross-chain Interoperability

Sa nakikinitang hinaharap, magkakaroon ng maraming mga publikong chain at libu-libong mga alyansa ng chain o mga pribadong chain na iiral sa buong mundo. Ang mga magkahiwalay na mga blockchain na sistemang ito ay mga isla ng halaga at impormasyon, na hindi interoperable sa isa't isa. Gamit ang cross-chain interoperability na mekanismo, maraming magkahiwalay na mga blockchain ang maaaring iugnay, upang ang mga halaga sa magkaibang mga blockchain ay maaaring ipagpalit sa isa't sa, upang makamit ang tunay na halaga ng Internet.

Ang NeoContract ay nagbibigay ng suporta para sa implementasyon ng cross-chain interoperability, sinisigurado ang pakakaalinsunod sa loob ng cross-chain asset na pagpapalitan, cross-chain na ibinahaging mga transaksyon, at pagpapatupad ng mga smart na kontrata sa magkaibang mga blockchain.

### 8.4 Orakulo na mga Makina

Ang konsepto ng mga orakulo sa katutubong kuwento ay nakabatay sa abilidad ng isang tiyak na sobrenatural na katauhan na maaaring sumagot sa isang partikular na hanay ng mga tanong. Sa blockchain, ang orakulo na mga makina ay bukas na pinto sa panlabas na mundo para sa mga smart na kontrata, ginagawang posible para sa mga smart na kontrata ang paggamit ng tunay na mundong impormasyon bilang isang kondisyon para sa pagpapatupad ng kontrata.

Ang NeoContract ay hindi nagbibigay ng abilidad upang direktang mag-access ng panlabas na datos, tulad ng access sa mga resource sa Internet, dahli ito ay magpapakilala ng non-deterministic na pagkilos, nagreresulta sa mga hindi pagkakaalinsunod sa pagitan ng mga node habang nagpapatupad ng kontrata. Ang pagpapatupad ng orakulo na makina sa NeoContract ay nangangailangan na ang panlabas na datos ay napadala sa blockchain gamit ang isang inaasahang pangatlong partido, pinagsasama ng mga data feed na ito bilang parte ng blockchain ledger, sa gayon ay tinatanggal ang non-determinism.

Ang kapani-paniwala pangatlong partido na binanggit sa itaas, maaaring isang tao o institusyon na pinagkatiwalaan sa parehong partido sa kontrata, o isang desentralisadong data provider na garantisado ng mga pang-ekonomiyang insentibo. Sa ganitong paraan, ang NeoContract ay maaaring gamitin sa implementasyon ng ganitong mga Orakulong makina.

### 8.5 Ethereum DAPP

Ang Bitcoin na ay gumawa ng kapanahunan ng mga blockchain at elektronikong salapi, at ang Ethereum ay gumawa ng kapanahunan ng mga smart na kontrata. Ang Ethereum, ang tagapanguna ng smart na kontrata sa blockchain, ay nakagawa ng dakilang mga kontribusyon sa disenyong ideya, ekonomikong modelo at teknolohikal na pagsasakatuparan ng smart na kontratang sistema. Sa parehong panahon, ang Ethereum na plataporma ay nakakita ng maraming mga DAPP (distributed applications), kung saan ang mga functionality ay nagsasama ng: mga kasunduan sa pagsusugal, mga digita asset, elektronikong ginto, plataporma sa paglalaro, medikal na insurance, pangkasal na plataporma, na kalat na kalat na paggamit sa maraming industriya. Sa teorya, ang lahat ng mga DAPP na ito ay maaaring madaling mailipat sa NeoContract na plataporma, bilang isang NEO na aplikasyon.
