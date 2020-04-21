# Smart Fuzzing

Fuzzing is the art of **automatic bug finding**, and it’s role is to find software implementation faults, and identify them if possible.
Fuzzing is particularly useful for exposing bugs like memory leaks, control flow issues, and race conditions

Creator Professor Barton Miller at University of Wisconsin Madison 1989. Work found [here](http://www.cs.wisc.edu/~bart/fuzz/).

## [OWASP - Fuzzing](https://owasp.org/www-community/Fuzzing)

Fuzzing a web app: urls, forms, user-generated content, RPC requests, etc
**Protocol fuzzing**. A protocol fuzzer sends forged packets to the tested application, or eventually acts as a proxy, modifying requests on the fly and replaying them.
**File format fuzzing**. A file format fuzzer generates multiple malformed samples, and opens them sequentially. When the program crashes, debug information is kept for further investigation.
One can attack:
-   the parser layer (container layer): file format constraints, structure, conventions, field sizes, flags, …
-   the codec/application layer: lower-level attacks, aiming at the program’s deeper internals

## Web Apps Fuzzer
* [Automating Web Apps Input Fuzzing via Burp Macros](https://blog.securelayer7.net/automating-web-apps-input-fuzzing-via-burp-macros/). Limited for community usage.
* [Wfuzz](https://github.com/xmendez/wfuzz). Web app modular framework fuzzer.
* [Msiavashi/web-browser-fuzzer](https://github.com/Msiavashi/web-browser-fuzzer). Written in node.js

## Fuzzing Frameworks
* [Sulley Fuzzing Framework](https://github.com/OpenRCE/sulley)
* [boofuzz](https://github.com/jtpereyda/boofuzz)
* [BFuzz](https://github.com/RootUp/BFuzz)


## Fuzzers from OWASP
* [zzuf](https://github.com/samhocevar/zzuf) is a transparent application input fuzzer. Changes random bits in the program's input.
* [Hachoir](https://github.com/vstinner/hachoir) is used by computer butchers to divide binary files into fields.
* [American Fuzzy Lop Wrapper](https://github.com/shellphish/fuzzer).
* [Google/oss-fuzz](https://github.com/google/oss-fuzz). Continuous Fuzzing for Open Source Software. [A new chapter for OSS-Fuzz](https://security.googleblog.com/2018/11/a-new-chapter-for-oss-fuzz.html). 
* [Radamsa](https://gitlab.com/akihe/radamsa) un-guided test mutation
* [Google Honggfuzz](https://github.com/google/honggfuzz)

* [OWASP-WebScarab](https://github.com/OWASP/OWASP-WebScarab)
* [JBroFuzz](https://wiki.owasp.org/index.php/JBroFuzz): a web application fuzzer. Download from [Sourceforge](https://sourceforge.net/projects/jbrofuzz/). [Github link](https://github.com/twilsonb/jbrofuzz).
* [WSFuzzer](https://owasp.org/www-community/WSFuzzer "wikilink"): real-world manual SOAP pen testing tool

## Open Source
**Mutational Fuzzers**
* [Radamsa - a flock of fuzzers](https://github.com/aoh/radamsa)

**Domain-Specific Fuzzers**
* [Microsoft SDL MiniFuzz File Fuzzer](https://www.microsoft.com/download/en/details.aspx?id=21769)
* [Microsoft SDL Regex Fuzzer](https://www.microsoft.com/download/en/details.aspx?id=20095)
* [ABNF Fuzzer](https://github.com/nradov/abnffuzzer)
* [Sloth Fuzzer](https://github.com/mfontanini/sloth-fuzzer). Smart File Fuzzer


**Commercial products**
* [Codenomicon’s product suite](http://www.codenomicon.com/products/all.shtml)
* [Peach Fuzzing Platform](http://peachfuzzer.com/)
* [Spirent Avalanche NEXT](http://www.spirent.com/Products/AvalancheNEXT)
* [Beyond Security’s beSTORM product](http://www.beyondsecurity.com/bestorm_overview.html)
* [Microsoft Security Risk Detection API Samples](https://github.com/Microsoft/msrd-rest-samples)

**File System Fuzzer**
* [FSfuzzer](https://www.ee.oulu.fi/research/ouspg/fsfuzzer)

**Kernel Fuzzer**
[Google/syzkaller](https://github.com/google/syzkaller)

**History of Fuzzing (Fuzzers timeline)**
[The smart fuzzer revolution](https://blog.trailofbits.com/2017/02/16/the-smart-fuzzer-revolution/)

[foospidy/payloads](https://github.com/foospidy/payloads). A collection of web attack payloads.

## FuzzBench - Fuzzer Benchmarking as a Service
[Fuzzer Benchmarking as a Service](https://security.googleblog.com/2020/03/fuzzbench-fuzzer-benchmarking-as-service.html)
[Google/FuzzBench](https://github.com/google/FuzzBench)
FuzzBench provides a framework for painlessly evaluating fuzzers in a reproducible way.
[Google/Fuzzer-test-suite](https://github.com/google/fuzzer-test-suite)
