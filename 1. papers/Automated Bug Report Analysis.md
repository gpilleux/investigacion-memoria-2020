
#  [Understanding and Securing Device Vulnerabilities through Automated Bug Report Analysis](https://www.eecis.udel.edu/~hnw/paper/security19.pdf)

## TL-DR / Conclusion
1. 90% of malicious attacks exploit the **known vulnerabilities**.
2. 96% of the IoT attacks use the **same** or similar **scripts** included in the vulnerability reports.
3. IoT vulnerability specific signature generation system for **intrusion detection**
4. Uses **key knowledge retrieval** to generate vulnerability-specific signatures which are used for intrusion detection.

## Key Concepts
An intrusion detection system (IDS) monitors a network or a system for malicious activities or policy violations.
1. *Signature-based detection* leverages known patterns (signatures) of malicious code or operations to identify malicious activities
2. *Anomaly-based detection* captures deviations from a system’s normal profile.
3. *Vulnerability-specific signature*. It models the vulnerability itself. Provides comprehensive protection against all related attacks on the weakness. Created through manual analysis of a vulnerability but it can be leveraged to **automatically** generate such a signature using NLP techniques.

**This paper focuses on providing automatic signature generation for the signature-based detection systems.**

## Abstract
Study based on a large number of real-world attack traces collected from honeypots, attack tools purchased from the underground, and information collected from high-profile IoT attacks.

This study sheds new light on the device vulnerabilities of today's IoT systems and their security implications:  
* Ongoing cyber attacks heavily rely on **known vulnerabilities** and the attack code released through their reports. 
* Reliance on **known vulnerabilities** can be used against *adversaries*.
* The same bug reports that enable the development of an attack can also be leveraged to extract vulnerability-specific features that help **stop** the attack.

Using *Natural Language Processing (NLP)* to **automatically collect and analyze** more than 7,500 **security reports** (with 12,286 security critical IoT flaws in total) scattered across **bug-reporting blogs, forums, and mailing lists on the Internet**. We show that **signatures** can be **automatically generated** through an *NLP-based report analysis*, and used by intrusion detection or firewall systems to effectively mitigate the threats from today's IoT-based attacks.

### Challenges
1. Many vulnerability report *sources* with *different structure*. It is difficult to identify IoT vulnerability reports from other documents.
2. Vulnerability reports written in *natural language*.  Difficult large-scale discovery of vulnerability information .
3. Identifying critical elements for a signature requires *domain-specific knowledge* to carefully distinguish between exploit-specific information and vulnerability-specific information.


## Specifics
* Four popular attack toolkits [Table 4](https://www.eecis.udel.edu/~hnw/paper/security19.pdf#page=5&zoom=100,72,88).
* Attacks almost exclusively use known vulnerabilities for exploitation.
* Known [IoT Botnets](https://www.eecis.udel.edu/~hnw/paper/security19.pdf#page=5&zoom=100,72,213)
* List of [vulnerability reporting websites](https://www.eecis.udel.edu/~hnw/paper/security19.pdf#page=6&zoom=100,424,337)
* IoTShield, automatically evaluates the content of vulnerability reports published at different sources. using NLP, extracting key knowledge from these reports to automatically generate vulnerability-specific signatures, which can be used by existing intrusion detection systems (IDSes) or web application firewalls (WAFs).
* From the same sources adversaries use to build their exploits, vulnerability signatures can be automatically generated using NLP, and be quickly deployed to shield IoT devices from malicious attacks.
* About 80% of IoT vulnerability reports are released together with exploitable methods, which can be readily utilized by hackers.
* IoTShield achieves a high precision (above 97%) and a very low false positive rate with minor performance impact

## NLP
* A [*spell-checking*](https://www.abisource.com/projects/enchant/) is used to filter out documents irrelevant to IoT.
* *Regular expression based pattern matching* is utilized to identify the vulnerability reports related to IoT
* *Semantic consistency analysis* is used to examine the extracted IoT *entities*.
* *Grammatical dependency parser*. Provides a representation of grammatical relations between words in a sentence. Used to to generate a vulnerability specific signature.

*Vulnerability extractor* to remove irrelevant content and identify key information of security flaws. 

*Semantics extractor* of vulnerability descriptions and other structured information (e.g., attack scripts). The descriptions provide information about all circumstances under which a vulnerability can be exploited (e.g., all related parameters and locations), which enables us to leverage the attack surface observed from an attack script or other structured information like traffic logs to stop other attacks

## Threat Model
We consider an adversary who attempts to exploit the security flaws disclosed in a vulnerability report to compromise remote, Internet-connected IoT devices. For this purpose, the adversary can compromise the remote IoT devices and use them to launch malicious attacks.
Accordingly, adversaries can exploit those devices’ security flaws remotely, and gain unauthorized control of those vulnerable devices (compromised IoT device may become a botnet node).

## Honeypots
We deployed eight vulnerable IoT devices (three routers and five cameras) as honeypots from May 2018 to June 2018.
They record the request packets from the IP and their timestamps before sending back “200 OK” and redirecting all HTTP requests to our main page.
All of our simulators are indexed as real IoT devices in Shodan (so they seem real).


## Methodology
### Automated Vulnerability-specific Signature Generation
The **attack scripts** are often publicly **available** in the vulnerability reports, making those known vulnerabilities **easy to exploit**.
The quality is determined by the comprehensiveness of the reports.

*(1) report crawler, (2) vulnerability extractor, and (3) rule generator*
1. Overview and Data
2. IoT Vulnerability Extraction
	* Preprocessing
		* Manually crawl specific pages
		* Remove irrelevant *information* from websites
	* Corpora quality analyzer
		* Filter irrelevant *documents* using *% of dictionary words* + *# of hyperlinks*
	* IoT vulnerability recognition
		* Recognize IoT key information (device type, vendor name, product name, vulnerability type) modeled as entity recognition problem in NLP (keywords + regular expression based matching [Table 7](https://www.eecis.udel.edu/~hnw/paper/security19.pdf#page=7&zoom=100,424,88))
		* Entity Checker: Google search for extracted entities and calculate cosine similarity for the title of search results. If < 0.08 then it's non-IoT device
	3. Automatic Defense Rule Generation
	* Report clustering
		* Different blogs can describe same vulnerability from different aspects. Need to cluster to form a complete report before rule generation. Cluster based on the entities (device type, vendor name, product name, vulnerability type).
		* Supplements missing information of a vulnerability report.
	* Semantic and structured information retrieval
		* [51] Dependency Tree to parse sentence and extract noun as target term and check relationship with keywords. [Example](https://www.eecis.udel.edu/~hnw/paper/security19.pdf#page=9&zoom=100,424,402)
	* Signature generation
		* Vulnerability location + "file.suffix" + parameters

## Related Work
* [46]**Vulnerability-specific signature generation (data patch)** for an unknown vulnerability, given a zero-day attack instance.
* [45] proposed to automatically mine parameter configuration rules of network control systems (e.g., BACnet-based building automation systems) from system specifications
* [50] presented a novel technique for automatic Indicator-of-Compromise extraction from **unstructured text**.
* [54] used NLP techniques to analyze Android APP descriptions and API documents for determining **unnecessary permissions**.
* [55] explored the vulnerability-related information disseminated on Twitter and provided an early warning for the existence of **real-world exploits by tweets**.
* [61]. proposed leveraging vulnerability-related text (CVE reports and Linux git logs) to guide Linux kernel **vulnerability fuzzing**
* [62] mined Android documents and security literature to generate features for Android **malware detection**


