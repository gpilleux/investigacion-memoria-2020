# [SemFuzz: Semantics-based Automatic Generation of Proof-of-Concept Exploits](https://homes.luddy.indiana.edu/xw7/papers/p2139-you.pdf)
## TL-DR / Conclusion

* First semantics-based, intelligent fuzzer that automatically recovers vulnerability-related knowledge from text reports and uses it to guide systematic construction of test cases for triggering a known or related unknown flaw.
* Demonstrates that non-code textual bug descriptions (e.g., CVE, Linux git logs) are valuable information sources for reconstructing exploits on known vulnerabilities.

## Key Concepts
1. PoC. Proof-of-concept.
2. CoFG. Context-Free Grammar

## Specifics
* Based on the state-of the-art Linux system call fuzzer, called Syzkaller [4].
* Automatic PoC generation through vulnerability related text using information extraction and a semantics-based fuzzing.
* Indicates that more complicated flaws can also be automatically attacked.
* SemFuzz creates a call sequence reaching the vulnerable function, and then iteratively “mutates” the parameters of individual calls to move towards the patched code inside the function, until the target vulnerability is triggered.
* Patches are also exposing information of the vulnerabilities at the same time

### NLP
* Uses Part-of-Speech (POS) Tagging, Phrase Parsing and Syntactic Parsing.
* Tool pyStatParser [18] to get the CoFG.
* Uses Linux Programmer Manual (LPM) to correlate system calls and parameters.

KCOV (kernel code coverage) [3], designed to track the executed code in Linux kernel.

## Methodology
1. Setting up the Testing Environment
2. Generating Seed Input
	* From CVE extract affected version, vulnerability type, vulnerable functions, critical variables and system calls.
	* With retrieved system calls (along with the parameters) are put together as an incomplete seed input.
	* If the parameter is a structure, fill each field in the structure. For enumeration fields, fill them with the related enumeration values learned from LPM. For other fields, populate them with random values compatible with their types.
	* Correlates other system calls with the retrieved ones, and puts them into the seed input
3. Coarse-level Mutation
	* Adds and mutates system calls. Leverages 
	* Distance between the vulnerable functions and the execution trace of the fuzzing instance. The input corresponding to the shortest distance is chosen as a new seed input for another round of fuzzing until any vulnerable function is reached
4. Fine-grained Mutation
	* Does not add new system calls or delete any existing system calls in the input. What it does is to mutate the values of the system call parameters, and to repeat existing system calls.
	* Distance between basic blocks.
	* Chooses the input that has the highest value for further fuzzing.

## Related Work
1. **[28] Automatically reverse-engineer a patch to generate an exploit for the vulnerability meant to be fixed by the patch.**
2. **[24, 35] Automatically generating exploits for SQLI and XSS attacks on web applications.**
3. [39] Leverages symbolic execution of Android framework for vulnerability discovery and exploit generation.
4. [56] uses a data-driven seed generation approach, which leverages the knowledge learned from the vast amount of existing samples to generate well-distributed seed inputs for fuzzing.
5. [49, 27] Leverage static control-flow and data-flow analysis to prioritize deep paths and de-prioritize frequent paths when mutating the inputs.
6. [32] Dynamically discovers likely memory layouts to guide the fuzzing process.
