# [Tiresias: Predicting Security Events Through Deep Learning](https://seclab.bu.edu/people/gianluca/papers/tiresias-ccs2018.pdf)
## TL-DR / Conclusion
Leverages Recurrent Neural Networks (RNNs) to predict future events on a machine, based on previous observations with a precision of up to 0.93.


## Key Concepts


## Abstract


### Challenges
Existing prediction systems have two main limitations. 
1. They only focus on predicting events with a binary outcome (e.g., whether an attack or a data breach will happen) but do not provide any insights on the techniques and the modus operandi that will be followed by attackers.
2. Second, these systems need labeled data to build a model and be able to make a decision, and it is not always easy to obtain such labeled data at a scale that allows to train an accurate model. 
3. One additional issue is that attackers operate changes to their modus operandi over time, and therefore both feature engineering and binary detection systems themselves need to be updated and retrained to keep performing accurate detections [20].

## Specifics
* Predict the exact actions that will be taken by an attacker when performing a computer attack.
* Predict which particular CVE will be used by an attacker when mounting a multi-step attack against a server
* We believe that a predictive system should be capable of understanding and making predictions given variable-length event sequences as the contexts

* Long short-term memory (LSTM) and variants such as gated recurrent units (GRU) are the most popular recurrent neural network models for sequential tasks, such as in character-level language modeling [13]. 
* One common approach to deal with complex sequential data is using a stacked RNNs architecture. **major setback**: require vigorous evaluation and may not 
adapt well to the new data at run time

**Data**. Symantec’s intrusion prevention product.

## Methodology
1. Architecture Overview
	2.1 Data collection and preprocessing
	2.2 Model training & validation
		* Recurrent memory cells
	2.3 Security event prediction
		* Predicts probability of $e_{i+1}  | e_0 : e_i$ which returns each event with its respective probability of appearance.
		* Get the maximum probability and say "that's the most likely event to happen"
	2.4 prediction performance monitoring
		* Retrains model if Precision, Recall and F1 are below normal
2. Recurrent Memory Array
	* recurrent memory array by Rocki [27]
	* modifying LSTM architectures


## Related Work
Attackers use multiple steps to reach their targets [3, 33]
privilege escalation exploits [25].
encrypting the victim’s data and holding it hostage [12, 14].
stealing sensitive information [6, 31]
log prediction [22]
function type recovery [4].

