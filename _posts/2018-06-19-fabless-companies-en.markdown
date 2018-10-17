---
layout: post
title:  "[ENG] Hardware Trojans - Attack Models"
date:   2018-06-19 08:38:12 +0200
categories: jekyll update
---

Whenever I am involved in a discussion about Hardware Trojans most questions are focused on the following topics / problems:

1.      what would a professional attack look like?

2.      how realistic is the attack by interfering with an integrated circuit?

3.      and finally, is it even a real threat?

 These questions will be discussed in that order. The Trojan-related attack models for integrated circuits are closely linked to the supply chain and the contractors in the silicon production process. Currently, microelectronics uses the so-called foundry model, which separates the production of chips (silicon) from the design of integrated circuits. The manufacturing is carried out by separate companies or business units within the same organization. This model takes its name from a similar process in the automotive industry (and heavy industry) where the design of the vehicle (machine) is done by companies and institutions other than steelworks and foundries. Sometimes a very large car company can afford to buy a steelwork, or a steelwork has shares of a car company. An example of analogy in the world of electronics would be Intel, which does both, designs and manufactures integrated circuits.

The foundry model divides microelectronics companies in two: those which have silicon production capacity and those which must subcontract silicon production. The following tables present a list of the largest companies in both categories. While the companies that do not produce silicon are mostly well recognized, those which do produce silicon are mostly unknown. This is analogous to the situation in the car market, where we recognize vehicle brands but not steel mills or foundries where the parts have been physically made.



Silicone-free companies (fabless), 2017 data based on IC Insights [report](https://www.design-reuse.com/news/43336/2017-top-10-fabless-system-ic-companies.html).

| Position | Company       | Country  |
| -------- | ------------- | -------- |
| 1        | Qualcomm      | USA      |
| 2        | Broadcom Ltd. | Singapur |
| 3        | Nvidia        | USA      |
| 4        | MediaTek      | Taiwan   |
| 5        | Apple         | USA      |
| 6        | AMD           | USA      |
| 7        | HiSilicon     | China    |
| 8        | Xilinx        | USA      |
| 9        | Marvell       | USA      |
| 10       | Unigroup      | China    |

The world biggest silicon foundries, [source.](https://www.electronicsweekly.com/news/business/top-ten-foundries-2017-2017-12/)


| Position | Company         | Country     | Market Share |
| -------- | --------------- | ----------- | ------------ |
| 1        | TSMC            | Taiwan      | 55,9 %       |
| 2        | Globalfoundires | USA         | 9,4 %        |
| 3        | UMC             | Taiwan      | 8,5 %        |
| 4        | Samsung         | South Korea | 7,7 %        |
| 5        | SMIC            | Taiwan      | 5,4 %        |
| 6        | TowerJazz       | Israel      | 2,4 %        |
| 7        | Powerchip       | Taiwan      | 1,8 %        |
| 8        | VIS             | Taiwan      | 1,4 %        |
| 9        | Hua Hong Semi   | China       | 1,4 %        |
| 10       | Dongbu Hitek    | South Korea | 1,2 %        |



In microelectronics, the division into fabs and fabless companies leads to the specification of the following entities in the production process:

- IP provider (3PIP 3rd party IP provider) - a company producing specific elements of the chip, e.g. memory controllers, data buses, networks on the chip (network chip), interfaces, etc. The software analogy is the provider of libraries e.g. graphics engine, API, or compression.
- System integrator/developer (SoC designer) - a company that integrates elements into one system, which often also has its own production of IP components.
- Silicon foundry - the company responsible for the production process of silicon

Using this classification as a basis, seven attack models can be identified. This classification  uses the “confidence” or “control” of different actors involved in the production process as the main criterion, see the Table below.:

| Model | Description                                            | IP provider | **System Integrator** | Foundry   |
| ----- | ------------------------------------------------------ | ----------- | --------------------- | --------- |
| 1     | Unreliable supplier                                    | Untrusted   |                       |           |
| 2     | Unsupervised integrator                                |             | Untrusted             |           |
| 3     | Untrusted foundry                                      |             |                       | Untrusted |
| 4     | Commercially available product                         | Untrusted   | Untrusted             | Untrusted |
| 5     | Unsupervised design office                             | Untrusted   | Untrusted             |           |
| 6     | Logical design without silicon production capabilities | Untrusted   |                       | Untrusted |
| 7     | Unreliable supplier using trusted components           |             | Untrusted             | Untrusted |

Description of individual attack models:

1.      Unreliable supplier: in most systems, components are sourced from different suppliers, e.g. USB interfaces, network interfaces or memory cards and processors. If we do not have control over their design process, we get a “close sourced” product. As a result, we know what that module is doing but not how it is done, i.e. largely unknown principles of work. This allows hardware trojans within the selected IPs.
2.      Unsupervised integrator - introduction of trojan can happen at the synthesis level of integrated circuits and/or through component integration and bonding.
3.      Untrusted foundry: most electronics companies do not have the technology to produce silicon wafers. Therefore, they must outsource this part of production to other companies. This leads to a loss of control over the final stage of production, i.e. the digestion of silicon wafers (change of masks, improper transistors). You may find more about this when looking for “doping trojans” as keywords e.g. [source](https://www.emsec.rub.de/media/crypto/veroeffentlichungen/2015/03/19/beckerStealthyExtended.pdf).

4.      Commercially available product: here, as a customer, we only have access to the finished product. Trojan deployment can happen at every stage of production. The process of its detection is costly, time consuming and difficult, more about this topic in [my presentation from Confidence 2018 conference. ](https://adamkostrzewa.github.io/jekyll/update/2018/06/06/prezentacja-confidence-2018.html)

5.      Unsupervised design office: the company has control over the silicon production process, but modification may occur in the process of component design or system integration.
6.      Logical design without silicon production capabilities: the integrator has no control over part of the components of the designed system, as well as over the silicon production process. Most of US companies currently operating on the market are in this situation.
7.      Unreliable supplier using trusted components: a supplier of components (e.g. HDL libraries) may lose control of its own product during integration or production in silicon. This is a difficult situation, because to prove its innocence, the supplier must reveal the source of the product/component.

**Exemplary Attack**

Let us describe the threat by means of a theoretical example of an attack inspired by recent press reports, e.g. CClenear or DELL's motherboards. First of all, due to the specificity of the problem, we must take into account the high level of sophistication of the attacker, i.e. technical experience and resources. Therefore, we assume that the operation plan is prepared with the cooperation of a “Far East” manufacturer of electronic components. The attacker has a professional team of engineers and financial resources allowing to spread the whole project over several years. The first step will be to bring infected equipment into the market. Large companies, such as HUAWEI or Samsung, can build it into their products straightforwardly  - at the first logical stage of the design. However, this entails a high risk of losing customer confidence if the attack gets detected. In addition, once modified, products cannot be withdrawn from the market. That is why the attacker decides to implement an alternative plan: the introduction of a Trojan in the module provided by the subcontractor. This can be done in cooperation with the subcontractor at the first or second stage of production (logical design or synthesis of electrical circuits) or without the subcontractor's knowledge or agreement at the second or third stage of the production (creation of masks for silicon production, chip digestion). An example of such attack is the story associated with [DELL’s statement ](http://www.theregister.co.uk/2010/07/21/dell_server_warning/) which warned users that some products (motherboards) contain a hardware trojan most likely introduced by a subcontractor. To provide additional security in case of detection, the attacker designs a functionality so that it can be considered a design error. A famous example of this are [dynamically changing AMD's microcodes](https://www.realworldtech.com/forum/?threadid=35566&curpostid=35566)  which, according to the manufacturer, were supposed to be used to patch (path) a working processor. However, it turned out that they allow the attacker to introduce the CPU backdoor in the process of updating and bypass the hardware protection system, causing a lot of speculation and controversy. Of course, AMD considered the case as a design error.

The finished product is then distributed on the market. The attacker at this stage does not activate the Trojan but waits and allows users to enjoy the basic functionality of the module. After a certain period of time, e.g. from half a year to two years, the market is saturated. The product appears naturally (as a result of purchase, warranty repairs, replacement or temporary replacement of equipment) in selected facilities, e.g. banks, factories, government institutions.

Then the malicious company can start the attack. There are many ways to activate and communicate with Trojans: through the backdoor within a communication protocol, through protocol manipulation, through side-channel attack, or through errors. Protocol backdoors are one of the most popular methods which consists in embedding Trojan control in the already existing communication using watermarks or stegano techniques, i.e. selected and known only to the attacking fragments of the transmission are used to give commands to the malicious system or to receive data.

Our attacker is therefore choosing this method. A triggering signal (data) can be provided as part of the driver installation/update process. Connection to the manufacturer's servers is then made with the knowledge and consent of the user. Furthermore, it is worth taking into account more sophisticated forms of attack. For instance, it is possible to purchase product rights for software designed by a third-party company not directly related to the attacker. The recent CCleaner scandal is an excellent example. The well-known and popular CCleaner program has infected millions of users' computers for almost a month (from 15 August to 12 September, when the next update removed vulnerability). Researchers from Talos, who were the first to describe the attack publicly, published a report on the objectives of the attack, mentioning for instance Samsung's factory in Poland.

 Detecting a hardware/software combination attack would be even more difficult than detecting a CCleaner attack. First of all, as we described earlier, all the functionality used to bypass the system's security features is made in the hardware. As shown by the [results](https://danluu.com/cpu-backdoors/) obtained by the researchers in the domain of hardware security, e.g. backdoors in processors, the software layer is practically defenseless against such malicious manipulations. Most security mechanisms since the [1970s](http://www.multicians.org/protection.html) are based on the assumption that the equipment the programmer is using behaves according to the rules strictly defined in the specification, e.g. the processor's protection rings.  

As a result, the attacker only needs to mask the communication with the Trojan for infiltration or exfiltration. Cryptographic techniques, e.g. stegano or watermarks, prove that it can be done without arousing suspicion. As proven by modern cryptography, without knowing the communication protocol during a stegano approach, it is extremely difficult to detect the course and purpose of the connection. As a result, the attacker can exfiltrate data of his interest and control it the way he wants, e.g. by means of diagnostic data sent with the user's knowledge and consent.

**Real stories**

Two good examples are Chinese companies Huawei and ZTE, which, after a wave of criticism accusing them of using hardware and software trojans in telecommunication products [1], [2], [3] , found themselves in the sight of the USA congress. In 2012, the congress managed to exclude the Huawei company from public tenders in the (safety-critical) telecommunication domain [4],[5]. The headlines of the American press ["The US Congress Panel considers Huawei and ZTE to be a threat to national security"](http://www.nytimes.com/2012/10/09/us/us-panel-calls-huawei-and-zte-national-security-threat.html) and the German public television channel Arte "[Huawei spy from China](http://info.arte.tv/de/huawei-der-spion-aus-china)" tells the whole story.



    [1] http://www.nytimes.com/2012/10/09/us/us-panel-calls-huawei-and-zte-national-security-threat.html
    [2] https://www.theguardian.com/technology/2012/oct/08/china-huawei-zte-security-threat
    [3] https://www.forbes.com/forbes/welcome/?toURL=https://www.forbes.com/sites/simonmontlake/2012/10/08/u-s-congress-flags-chinas-huawei-zte-as-security-threats
    [4] http://www.spiegel.de/netzwelt/netzpolitik/us-kongress-will-chinas-telekom-firmen-huawei-und-zte-aussperren-a-860014.html
    [5] http://info.arte.tv/de/huawei-der-spion-aus-china
