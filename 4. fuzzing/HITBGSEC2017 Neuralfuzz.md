# [#HITBGSEC 2017](https://www.youtube.com/results?search_query=%23HITBGSEC)  Neuralfuzz: Neural Networks For Fuzzing Web Apps 
> Speaker: Ivan Novikov

[Neuralfuzz github](https://github.com/wallarm)

## Main Problem of Fuzzing
Send the HTTP request with the payload inside.

### 1. Where should you put the payload?
* Crawling
* Units/regressions/functional coverage
* DPI (deep packet inspection): JSON, XML, Base64, GZIP, matryoshkas
* Custom encodings/encryption
* App logic understanding. Models other than request-response

### 2. What is the payload?
* Known vectors - **vuln scanners**
* Unexpected data/random/anything - **fuzzers**

### 3. How to identify an exception?
* Sensors implementation (logging, hooks, traps)
* Anomalies detection
* Reproducibility

## This video is about the WHAT
* Collect all requests by unit/manual tests
* Apply fuzzing policies
* Generate new unit tests
* Run all of them

**Top 6 fuzzing techniques**
1. Last byte modification: `?username=admi%00`
2. Random byte modification: `?username=ad%00in`
3. Add payload to the end: `?username=admin%27`
4. Parameters from other requests (password to logout)
5. Numbers increasing/decreasing: `/user/100001/status`
6. Filenames by fuzz.txt (check Github)

## Fuzzing with Neural Networks
Uses Recurrent Neural Networks. It's a way to put unrestricted the data size inside a NN.

[UGRNN](https://arxiv.org/pdf/1611.09913.pdf): Update Gate RNN. 

### Train sets
[SecList/Fuzzing](https://github.com/danielmiessler/SecLists/tree/master/Fuzzing)

### Analyzing Results
Exclude 5XX HTTP code, 1+ms response

## Whats Next?
* Solving result analysis problem with NN
* Connect to Python-based proxy to automate everything
* Make it smarter by connection with a response. AI-sqlmap is possible!



