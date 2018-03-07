# NEO White Paper

A distributed network for the Smart Economy

## NEO design goals: Smart Economy

NEO is the use of blockchain technology and digital identity to digitize assets, the use of smart contracts for digital assets to be self-managed, to achieve "smart economy" with a distributed network.

### Digital Assets

Digital assets are programmable assets that exist in the form of electronic data. With blockchain technology, the digitization of assets can be decentralized, trustful, traceable, highly transparent, and free of intermediaries. On the NEO blockchain, users are able to register, trade, and circulate multiple types of assets. Proving the connection between digital and physical assets is possible through digital identity. Assets registered through a validated digital identity are protected by law.

NEO has two forms of digital assets: global assets and contract assets. Global assets can be recorded in the system space and can be identified by all smart contracts and clients. Contract assets are recorded in the private storage area of the smart contract and require a compatible client to recognize them. Contract assets can adhere to certain standards in order to achieve compatibility with most clients.

### Digital Identity

Digital identity refers to the identity information of individuals, organizations, and other entities that exist in electronic form. The more mature digital identity system is based on the PKI (Public Key Infrastructure) X.509 standard. In NEO, we will implement a set of X.509 compatible digital identity standards. This set of digital identity standards, in addition to compatible X.509 level certificate issuance model, will also support Web Of Trust point-to-point certificate issuance model. Our verification of identity when issuing or using digital identities includes the use of facial features, fingerprint, voice, SMS and other multi-factor authentication methods. At the same time, we will also use the blockchain to replace the Online Certificate Status Protocol (OCSP) to manage and record the X.509 Certificate Revocation List (CRL).

### Smart Contract

The smart contract was first proposed by the cryptographer Nick Szabo in 1994, only five years after the creation of the World Wide Web. According to Szabo's definition: When a pre-programmed condition is triggered, the smart contract will execute the corresponding contract terms. Blockchain technology provides us with a decentralized, tamper-resistant, highly reliable system in which smart contracts are very useful. NEO has an independent smart contract system: NeoContract.

The NeoContract smart contract system is the biggest feature of the seamless integration of the existing developer ecosystem. Developers do not need to learn a new programming language but use C#, Java and other mainstream programming languages in their familiar IDE environments (Visual Studio, Eclipse, etc.) for smart contract development, debugging and compilation. NEO's Universal Lightweight Virtual Machine, NeoVM, has the advantages of high certainty, high concurrency, and high scalability. The NeoContract smart contract system will allow millions of developers around the world to quickly carry out the development of smart contracts. NeoContract will have a separate white paper describing the implementation details.

### Application and Ecosystem

Ecosystem is the vitality of the open source community. In order to achieve the goal of an intelligent economic network, NEO will be committed to the development of its ecosystem, providing mature development tools, improving development of documents, organizing education and training activities, and providing financial support. We plan to support the following NEO-based applications and ecology and to reward improvements to the design of the experience:

🔹 **Node Program**

- A fully functioning Full node PC program

- A light node PC program with a better user experience

- Web / Android / iOS clients that do not need to synchronize with the blockchain

- Hardware wallet

🔹 **Blockchain Explorer**

🔹 **SDK Development Kit**

- Support Java / Kotlin, .NET C # / VB, JavaScript / Typescript, Python, Go

🔹 **Smart Contract Compiler and IDE Plugin**

- C# / VB.Net / F#, Visual Studio

- Java / Kotlin, Eclipse

- C / C++ / GO

- JavaScript / TypeScript

- Python / Ruby

🔹 **Decentralized Applications**

- Smart fund

- AI-assisted legal smart contract

- Social networking

- Automated tokens liquidity providers

- Decentralized exchange

- Secure communication protocol

- Data exchange market

- Intellectual property trading market

- Prediction market

- Advertising market

- Hashpower market

- NeoGas market

## NEO Management Model

### Economic Model

NEO has two native tokens, NEO (abbreviated symbol NEO) and NeoGas (abbreviated symbol GAS).

NEO, with a total of 100 million tokens, represents the right to manage the network. Management rights include voting for bookkeeping, NEO network parameter changes, and so on. The minimum unit of NEO is 1 and tokens cannot be subdivided.

GAS is the fuel token for the realization of NEO network resource control, with a maximum total limit of 100 million. The NEO network charges for the operation and storage of tokens and smart contracts, thereby creating economic incentives for bookkeepers and preventing the abuse of resources. The minimum unit of GAS is 0.00000001.

In the genesis block of the NEO network, 100 million NEOs are generated, GAS has not yet been generated. 100 million GAS, corresponding to the 100 million NEO, will be generated through a decay algorithm in about 22 years time to address holding NEO. If NEO is transferred to a new address, the subsequent GAS generated will be credited to the new address.

The NEO network will set a threshold by voting to exempt GAS from a certain amount of transfer transactions and smart contract operations to enhance the user experience. When a large amount of spam transactions occur, NeoID can be used to prioritize transactions and smart contracts with qualified identities. Transactions and smart contracts with no qualifying digital identities can get priority by paying GAS.

### Distribution Mechanism

NEO distribution:

NEO's 100 million tokens is divided into two portions. The first portion is 50 million tokens distributed proportionally to supporters of NEO during the crowdfunding. This portion has been distributed.

The second portion is 50 million NEO managed by the NEO Council to support NEO's long-term development, operation and maintenance and ecosystem. The NEO in this portion has a lockout period of 1 year and is unlocked only after October 16, 2017. This portion will not enter the exchanges and is only for long-term support of NEO projects. The plans for it are as below:

🔹 10 million tokens (10% total) will be used to motivate NEO developers and members of the NEO Council

🔹 10 million tokens (10% total) will be used to motivate developers in the NEO ecosystem

🔹 15 million tokens (15% total) will be used to cross-invest in other block-chain projects, which are owned by the NEO Council and are used only for NEO projects

🔹 15 million (15% total) will be retained as contingency

🔹 The annual use of NEO in principle shall not exceed 15 million tokens

GAS distribution:

GAS is generated with each new block. The initial total amount of GAS is zero. With the increasing rate of new block generation, the total limit of 100 million GAS will be achieved in about 22 years. The interval between each block is about 15-20 seconds, and 2 million blocks are generated in about one year.

Each year around 2 million blocks will be generated and the initial generation will be 8 GAS per block. There will be an annual reduction of 1 GAS per block, per year, to coincide with the passing of every 2 million blocks. The reduction will continue down to just 1 GAS per block and will be held at that rate for around 22 years. After the 44 millionth block the total GAS generated will have reached 100 million and from this point there will be no further generation of GAS from new blocks.

Ayon sa release curve na ito, 16% sa GAS ay malilikha sa unang taon, 52% sa GAS ay malilikha sa unang apat na taon, at 80% sa GAS ay malilikha sa unang 12 taon. Ang mga GAS na ito ay proporsyonal na ibabahagi na nakaalinsunod sa NEO holding ratio, na itinala sa nararapat na mga address. Ang mga NEO holder ay maaaring simulan ang pang-angkin na transaksyon sa anumang oras at angkinin itong mga GAS token sa kanilang mga holding address.

### Mekanismo sa pamamahala

Chain na pamamahala: Ang mga NEO token holder ay ang mga may-ari at tagapamahala ng network, namamahala ng network sa pamamagitan ng pagboto sa network, gamit ang nabuo ng GAS mula sa NEO upang magamit ang mga punsyon sa network. Ang mga NEO token ay maaaring ilipat.

Off-chain na pamamahala: Ang Konseho ng NEO ay binubuo ng mga founding na miyembro ng NEO na proyekto, sa ilalim kung saan ang komite ng pamamahala, teknikal na komite at ang secretariat, ayon sa pagkakabanggit, ay responsable para sa estratehikong paggawa ng desisyon, teknikal na paggawa ng desisyon at tiyak na implementasyon. Ang Konseho ng NEO ay reponsable sa komunidad ng NEO para sa promosyon at kaunlaran ng NEO na ecosystem bilang pangunahing layunin nito.

## Implementasyon ng NEO na teknolohiya

### Consensus na mekanismo: dBFT

Ang dBFT ay tinatawag ng Delegated Byzantine Fault Tolerant, isang Byzantine fault-tolerant consensus na mekanismo na pinapagana ang malakihang partisipasyon sa pinagkasunduan sa pamamagitan ng proxy na pagboto. Ang holder ng NEO token ay maaaring, sa pamamagitan ng pagboto, pumili ng bookkeeper na sinusuportahan nito. Ang napiling grupo ng mga bookkeeper, gamit ang BFT na algoritmo, ay maabot ang isang pikakasunduan at bubuo ng bagong mga bloke. Ang pagboto sa NEO network ay magpapatuloy sa real time, sa halip na umalinsunod sa isang nakapirming termino.

Ang dBFT ay magbibigay ng fault tolerance of f = ⌊ (n-1) / 3 ⌋ para sa isang consensus na sistema na binubuo ng n na mga consensus node. Ang fault tolerance na ito ay nagsasama rin ng parehong seguridad at availability, lumalaban sa pangkalahatan at Byzantine na mga kabiguan, at naaangkop sa anumang network environment. Ang dBFT ay may magandang pagtatapos, nangangahulugan na kapag ang mga kumpirmasyon ay huli na, ang bloke ay hindi na maaaring i-bifurcate, at ang transaksyon ay hindi na mababawi o maibabalik.

Sa NEO dBFT consensus na mekanismo, na tatagal ng halos 15 hanggang 20 segundo upang bumuo ng isang bloke, ang transaksyon na throughput ay masusukat sa halos 1,000TPS, na isang mahusay na pagganap bukod sa publikong mga chain. Sa pamamagitan ng angkop na optimisasyon, may potensyal na aabot ng 10,000TPS, papayagan itong sumuporta ng malakihang komersyal na mga aplikasyon.

Ang dBFT ay pagsasamahin ang digital identity na teknolohiya, nangangahulugan na ang mga bookkeeper ay maaaring isang tunay na pangalan ng indibidwal o institusyon. Kaya naman, posible itong i-freeze, bawiin, manahin, kunin, at lipatan ng pagmamay-ari dahil sa mga desisyon ng hudisyal sa mga ito. Pinapadali nito ang pagpaparehistro ng mga compliant financial asset sa NEO na network. Ang NEO network ay nagpaplano na sumuporta tulad nitong mga operasyon kapag kinakailangan.

### Sistema ng matalinong kontrata: NeoContract

Ang sistema ng matalinong kontrata ng NEO ay binubuo ng tatlong bahagi:

**NeoVM - Universal Block Chain Virtual Machine:**

Ang NeoVM ay isang magaan, pangkalahatang layunin na birtwal na makina na may arkitektura na napakalapit sa JVM at .NET Runtime, katulad sa isang birtwal na CPU na nagbabasa at nagpapatupad ng mga instruksyon sa kontrata nang magkakasunod, gumaganap ng prosesong kontrol batay sa functionality ng instruksyon na mga operasyon, mga lohikang operasayon at iba pa. Ito ay may isang magandang bilis ng start-up at kagalingan, napakaangkop para sa maliliit na mga programa katulad ng mga matalinong kontrata, maaari ring i-port sa non-blockchain na mga sistema, o i-integrate sa IDE upang magbigay ng isang pinakamainam na karanasan sa pag-develop. Ang functionality ng NeoVM ay maaaring mapalawak, katulad ng pagpapakilala sa isang JIT (real-time na compiler) na mekanismo, sa gayon ay nagpapaunlad ng kahusayan ng implementasyon.

**InteropService - Interoperable na mga Serbisyo:**

Ginagamit upang i-load ang blockchain ledger, mga digital asset, digital na pagkakakilanlan, matiyagang storage area, NeoFS, at iba pang pinagbabatayang mga serbisyo. Sila ay katulad ng mga birtwal na makina na binigay para sa mga birtwal na makina, pinapayagan ang mga matalinong kontrata na mag-access sa mga serbisyong ito sa run time upang makamit ang ilang advanced na functionality. Sa pamamagitan nitong low-coupling na disenyo, **ang NeoVM ay maaaring i-port sa anumang blockchain o kahit non-blockchain na sistemang ginamit, pinapataas ang kahalagahan ng mga matalinong kontrata.**

**DevPack - Compiler and IDE na plugin:**

Ang DevPack ay nagsasama ng mataas na lebel na language compiler at ng IDE na plug-in. Dahil ang arkitektura ng NeoVM ay sobrang katulad sa JVM at .NET Runtime, ang mga compiler sa DevPack ay maaaring mag-compile ng Java byte code at .NET MSIL sa instruction set ng NeoVM. Ang mga developer ng Java / Kotlin, C# ay hindi kailangang matuto ng bagong mga lengguwahe at pwede kaagad magsimulang mag-develop ng mga matalinong kontrata sa VS, Eclipse at ibang pamilyar na mga IDE environment. **Lubha nitong binabawasan ang mga learning curve para sa pag-develop ng mga matalinong kontrata, pinapayagan tayong madaling bumuo ng isang buhay na buhay na komunidad sa paligid ng NeoContract.**

Ang NeoContract ay maaaring lumikha ng isang matalinong kontrata na call tree gamit ang static analysis bago magpatakbo ng isang matalinong kontrata. **Gamit ang deterministic na call tree, ang NEO node ay maaaring dinamikang i-fragment ang matalinong kontrata upang makamit ang batay sa teoryang walang limitasyong pagpapalawak**, na dinadaig ang "jamming effect" na sanhi ng static fragmentation ng ibang mga sistema ng block chain.

### Cross-chain interoperability na kasunduan: NeoX

Ang NeoX ay isang protokol na nagpapatupad ng cross-chain interoperability. Ang NeoX ay nakahati sa dalawang bahagi: "cross-chain assets exchange na protokol" at "cross-chain distributed transaction na protokol."

**Cross-chain assets exchange na kasunduan:**

Ang NeoX ay pinalawak sa umiiral na double-stranded na atomikong mga asset ng mga exchange protocol upang pahintulutan ang maramihang kalahok na magpalitan ng mga asset sa kabuuan ng magkaibang mga chain at upang siguraduhin na matagumpay ang lahat ng mga hakbang sa buong proseso ng transaksyon o sabay-sabay na mabigo. Upang makamit ang punsyon na ito, kailangan nating gumamit ng NeoContract na punsyon upang lumikha ng isang account na kontrata para sa bawat kalahok. Kung ang ibang mga blockchain ay hindi tumutugma sa NeoContract, sila ay maaaring magkatugma sa NeoX hangga't sila ay maaaring magbigay ng simpleng matalinong kontratang functionality.

**Cross-chain distributed transaction na protokol:**

Ang cross-chain distributed na mga transaksyon ay nangangahulugan na ang maramihang hakbang ng isang transaksyon ay nakakalat sa kabuuan ng magkaibang mga blockchain at ang pagkakaalinsunod sa buong transaksyon ay natiyak. Ito ay isang ekstensyon ng cross-chain assets na pagpapalitan, pinapalawak ang pag-uugali ng assets na pagpapalitan sa arbitrary na pagkilos. Sa madaling salita, ang NeoX ay ginagawang posible para sa cross-chain na mga matalinong kontrata kung saan ang isang matalinong kontrata ay maaaring gumanap na magkaibang parte sa maramihang chain, alinman ay kasunod o pagpapanumbalik sa pangkabuuan. Nagbibigay ito ng mahusay na mga posibilidad para sa cross-chain na mga kolaborasyon at sinisiyasat namin ang mga pangyayari ng cross-chain na matalinong kontratang aplikasyon.

### Ibinahaging Storage Protocol: NeoFS

Ang NeoFS ay isang ibinahaging storage protocol na gumagamit ng Distributed Hash Table (DHT) na teknolohiya. Ang mga NeoFS ay nag-iindex nga datos gamit ang file content (Hash) sa halip ng file path (URI). Ang mga malaking file ay maaaring hatiin sa pirming laking datos na mga bloke na ibinahagi at nakaimbak sa iba't ibang mga node.

Ang pangunahing problema sa ganitong uri ng sistema ay ang pangangailangan ng paghahanap ng isang balanse sa kalabisan at pagkamaaasahan. Ang NeoFS ay nagpaplanong lutasin ang kontradiksyong ito sa pamamagitan ng mga token na insentibo at ang pagtatatag ng mga backbone node. Ang mga gumagamit ay maaaring pumili sa pagkamaaasahang mga kinakailangan ng file. Ang mga file na may mababang pagkamaaasahang mga kinakailangan ay maaaring iimbak at i-access nang libre o halos libre. Ang matatag at maaasahang mga serbisyo para sa mga file na may mataas na pagkamaaasahang mga kinakailangan ay ibibigay ng mga backbone node.

Ang NeoFS ay magsisilbi bilang isa sa mga InteropService interoperability na serbisyo sa ilalim ng NeoContract na sistema, pinapayagan ang mga matalinong kontrata na mag-imbak ng malaking mga file sa blockchain at magtakda ng access para sa mga file na iyon. Sa karagdagan, ang NeoFS ay maaaring isama sa digital na pagkakakilanlan upang ang mga digital na sertipiko na ginagamit ng mga digital na pagkakakilanlan ay maaaring itinalaga, ipadala, at bawiin nang walang isang sentral na server na mamamahala sa kanila. Sa hinaharap, ang lumang block na datos ay maaaring iimbak sa NeoFS, upang ang karamihan sa buong mga node ay maaaring maglabas ng lumang datos para sa mas mabuting scalability at sa parehong pagkakataon, siguraduhin ang integridad ng makasaysayang datos.

### Anti-quantum cryptography na mekanismo: NeoQS

Ang paglitaw ng mga quantum na kompyuter ay pumupwesto ng isang pangunahing pagsubok sa RSA at ECC na nakabaseng kriptograpikong mga mekanismo. Ang mga quantum na kompyuter ay maaaring maglutas ng mataas na bilang ng decomposition na mga problema (na inaasahan ng RSA) at ang elliptic curve discrete na algoritmo (na inaasahan ng ECC) sa isang pinakamaikling panahon. Ang NeoQS (Quantum Safe) ay isang lattice-based cryptographic na mekanismo. Sa kasalukuyan, ang mga quantum na kompyuter ay walang abilidad na madaling maglutas ng Shortest Vector Problem (SVP) at ang Closest Vector Problem (CVP), na isinasaalang-alang bilang pinakamaaasahang algoritmo para sa paglaban ng mga quantum na kompyuter.

## Buod

Ang NEO ay isang ibinahaging network na nagsasama ng mga digital asset, ang mga digital an pagkakakilanlan at mga matalinong kontrata. Ang NEO na sisteam ay gagamit ng DBFT, NeoX, NeoFS, NeoQS at marami pang ibang orihinal na mga teknolihiya, bilang imprastraktura para sa matalinong ekonomiya ng hinaharap.
