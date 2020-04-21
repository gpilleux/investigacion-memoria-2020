# Google OSS-Fuzz

**Hacen fuzzing de código estático de proyectos OPEN SOURCE**

[Fuzzing glossary](https://github.com/google/fuzzing/blob/master/docs/glossary.md).

Supports [llvm/LibFuzzer](http://llvm.org/docs/LibFuzzer.html) (tutorial [here](https://github.com/google/fuzzing/blob/master/tutorial/libFuzzerTutorial.md)), [AFL](https://lcamtuf.coredump.cx/afl/) fuzzing engines, [Sanitizers](https://github.com/google/sanitizers) as well as [Google/Clusterfuzz](https://github.com/google/clusterfuzz) a distributed fuzzer execution environment and reporting tool. 

**LLVM supports Ruby**

Useful [docs](https://github.com/google/fuzzing/tree/master/docs).

## LLVM/LibFuzzer
Permite ejecutar fuzzers para CVE's específicos.
Permite ejecución en paralelo

## Seed Corpus
Initial set of inputs. Allows more code coverage.
## Competing bugs
Sometimes there is one shallow (easy to find) bug in the target that prevents you from finding more bugs. The best approach in such cases is to fix the shallow bug(s) and restart fuzzing. However you can move forward a bit by simply re-starting libFuzzer many times. `-jobs=1000` will do this for you.

## Sanitizer
AddressSanitizer is a fast memory error detector. It consists of a compiler instrumentation module and a run-time library. The tool can detect the following types of bugs:

-   Out-of-bounds accesses to heap, stack and globals
-   Use-after-free
-   Use-after-return (runtime flag  ASAN_OPTIONS=detect_stack_use_after_return=1)
-   Use-after-scope (clang flag  -fsanitize-address-use-after-scope)
-   Double-free, invalid free
-   Memory leaks (experimental)

## Distributed Fuzzing
What if I want to fuzz one specific target on more CPUs than any single VM has? That's easy: you may store the corpus on some cloud storage system and synchronize it back and forth.

## Continuous fuzzing

One-off fuzzing might find you some bugs, but unless you make the fuzzing process  **continuous**  it will be a wasted effort.

A simple continuous fuzzing system could be written in < 100 lines of bash code. In an infinite loop do the following:

**AUTOMATIZACIÓN DE FUZZING CON CI**

-   Pull the current revision of your code.
-   Build the fuzz target
-   Copy the current corpus from cloud to local disk
-   Fuzz for some time.
    -   With libFuzzer, use the flag  `-max_total_time=N`  to set the time in seconds).
-   Synchronize the updated corpus back to the cloud
-   Provide the logs, coverage information, crash reports, and crash reproducers via e-mail, web interface, or cloud storage.

## [LeakSanitizer](http://clang.llvm.org/docs/LeakSanitizer.html)
LeakSanitizer is a run-time memory leak detector

# Advanced Fuzzing - libFuzzer plugins
## [Structure-Aware Fuzzing](https://github.com/google/fuzzing/blob/master/docs/structure-aware-fuzzing.md)
Generation-based fuzzers usually target a single input type, generating inputs according to a pre-defined grammar.

With some additional effort, however, libFuzzer can be turned into a grammar-aware (i.e. **structure-aware**) fuzzing engine for a specific input type.

Es **util** en los casos en que una función muta los datos (por ejemplo una función que recibe un archivo comprimido y lo descomprime, PNG, Protocol Buffers [protobufs])


## [Protocol Buffers As Intermediate Format](https://github.com/google/fuzzing/blob/master/docs/structure-aware-fuzzing.md#protocol-buffers-as-intermediate-format)

Protobufs provide a convenient way to serialize structured data, and LPM provides an easy way to mutate protobufs for structure-aware fuzzing. Thus, it is tempting to use libFuzzer+LPM for APIs that consume structured data other than protobufs.

Un **ejemplo** es SQLite. Se pueden crear distintos SQL statements que sería complicado sin protobufs.

## Fuzzing Stateful APIs
An API may not consume data directly at all, and it could consist of many functions that work only when the API is in a certain state. Such **stateful APIs** are common for e.g. networking software. Fuzzing with protobufs could be useful here as well.

## Conclusions

Structure-aware fuzzing is one of the "next big things" in program state exploration and vulnerability discovery. Probably as big as coverage-guided fuzzing has been since the early 2000s. Admittedly, structure-aware fuzzing, at least as described in this document, requires substantial manual work for every input type. Finding ways to automate structure-aware fuzzing further is becoming a hot research topic.
