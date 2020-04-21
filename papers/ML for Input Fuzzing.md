# [Learn&Fuzz: Machine Learning for Input Fuzzing](https://arxiv.org/pdf/1701.07232.pdf)
## TL-DR / Conclusion
Automatically generating input grammars for grammar-based fuzzing

## Key Concepts
1. Fuzzing is the process of finding security vulnerabilities in input-parsing code by
repeatedly testing the parser with modified, or fuzzed, inputs.
2. Epoch. Iteration of the learning algorithm to go over the complete training dataset

## Abstract
Detailed case study with a complex input format (PDF) and a large complex security-critical parse

Tension between conflicting learning and fuzzing goals
1. Learning wants to capture the structure of well-formed inputs
2. Fuzzing wants to break that structure in order to cover unexpected code paths and find bugs.

New algorithm which uses a learnt input probability distribution to intelligently guide where to fuzz inputs.

### Challenges
1. Automate grammar-based fuzzing.
2. How to learn and then generate diverse well-formed inputs in order to maximize parser-code coverage, while still injecting enough ill-formed input parts in order to exercise unexpected code paths and error-handling code.

## Specifics
The **SampleFuzz** algorithm introduces unexpected characters in objects only in places where the model is highly confident, in order to trick the PDF parser.

No bugs were found on normal tests. However, during a longer experiment with Sample+Random, they found a **stack-overflow bug** which triggers an unexpected recursion in the parser.

Three types of fuzzing
1. Blackbox random fuzzing [27]
	* Automatic
	* Effective at finding security vulnerabilities in binary-format file parsers 
2. Whitebox constraint-based fuzzing [12]
	* Automatic
	* Effective at finding security vulnerabilities in binary-format file parsers 
3. Grammar-based fuzzing [23, 27], which can be viewed as a variant of model-based testing [28].
	* Not fully automatic
	* Requires input grammar of input format

### Neural-network-based statistical learning techniques
Use of recurrent neural networks (seq-to-seq [5, 26]) for learning a statistical input model that is also generative: it can be used to generate new inputs based on the probability distribution of the learnt model
Use of unsupervised learning for model learning

**LSTM model** [15] (a variant of RNN) with 2 hidden layers, where each layer consists of 128 hidden states.

## Methodology


## Related Work
[27] Grammar-based fuzzing. Peach3 and SPIKE4, most popular blackbox random fuzzers. Whitebox fuzzing [19, 11].
[2] Learning grammars for grammar-based fuzzing. Generate new inputs for fuzzing.

