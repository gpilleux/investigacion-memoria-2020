# [An Empirical Study of Zero-Day Attacks In The Real World](https://users.ece.cmu.edu/~tdumitra/public_documents/bilge12_zero_day.pdf)

## TL-DR / Conclusion  
Systematic study of zero-day attacks between 2008–2011
Technique for identifying and analyzing zero-day attacks from the data available through the Worldwide Intelligence Network Environment (WINE)

* We propose a method for identifying zero-day attacks from data collected on real hosts and made available to the research community via the WINE platform.
* We conduct a systematic study of the characteristics of zero-day attacks. Our findings are summarized in Table 1.
* We compare the impact of zero-day vulnerabilities before and after their public disclosure, and we discuss the implications for the policy of full disclosure

## Key Concepts  
  1. Zero-day attack is a cyber attack exploiting a vulnerability that has not been disclosed publicly.

### Challenges  
Zero-day attacks are difficult to prevent because they exploit unknown vulnerabilities, for which there are no patches and no anti-virus or intrusion-detection signatures.
  

## Specifics  
In this paper, we consider only exploits that have been used in real-world attacks before the corresponding vulnerabilities were disclosed. 
Focus on data that highlights the presence and propagation rate of malware on the Internet

### Data
  1. Common Vulnerabilities and Exposures (CVE). Database with extensive information about vulnerabilities, including technical details and the disclosure dates, that is a widely accepted standard for academia, governmental organizations and the cyber security industry.
  2. Google search the history of binary reputation submissions for these malicious files
  3. WINE platform. Two datasets: anti-virus telemetry and binary reputation.
  4. [21] Open Source Vulnerability Database (OSVDB)
  5. [38] Symantec’s Threat Explorer
  6. [1, 19] Microsoft and Adobe Security Bulletins
  
## Methodology  
  1. Building the ground truth
	  * Collect the discovery, disclosure, exploit release date and patch release dates from CVE.
	  * Threat Explorer lookup on these CVEs to identify threat that exploits it.
  2. Identifying exploits in executables
	  * Identify exploits that are detected by each *virus_id* to search in binary reputation data.
  3. Identifying executables dropped after exploitation (optional)
	  * Mapping of threats to malicious files
  4. Analyzing the presence of exploits on the Internet
  5. Identifying zero-day attacks
	  * If at least one of the file hash ids of a threat was downloaded before the disclosure date of $cve id_i$, it means that $cve id_i$ is a zero-day vulnerability and that $virus id_i$ performed a zero-day attack.
  

## Related Work  
1. [12] Three exploit archives, popular in the hacker community. [32] larger data set.
2. [16] 2010 Hydraq trojan, also known as the “Aurora” attack that aimed to steal information from several companies.
3. [11] 2010 Stuxnet worm, which combined four zeroday vulnerabilities to target industrial control systems.
4. [27] 2011 attack against RSA.
