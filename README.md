# Implementation of Dynamic Memory Networks for QA System using Tensorflow  
  
#### cuteboydot@gmail.com  
  
#### reference  
1. [Ask Me Anything:Dynamic Memory Networks for Natural Language Processing](https://arxiv.org/pdf/1506.07285.pdf)  
  
#### data reference  
1. [bAbI, facebook](https://research.fb.com/downloads/babi/)  
  
### 1. Dynamic Memory Networks 
<img src="./img/dymemnn.png" width="90%">  
  
Dynamic Memory Networks는 크게 input module, question module, memory module, answer module로 구성되어 있다.  
input module은 word의 조합으로 구성된 sentence를 RNN(GRU)의 output을 통해 하나의 context vector로 생성한다.  
question module은 question word들을 GRU의 state로 vector로 생성한다.  
memory module은 input context c_t, momory m, question module q 등을 이용하여 attention을 구하고,  
GRU(c_t, e)를 통해 memory를 업데이트 한다. 이때 episode e에서 e0는 question module로 시작한다.  

### 2. Test result  
본 프로젝트는 총 20종류의 데이터 중, 10번(indefinite-knowledge)과 11번(basic-coreference) 내용을 사용하였다.  
실험 환경은 다음과 같다.  
- python 3.6  
- tensorflow 1.3  
- data size for train : 10,000 (qa10, qa11 각각)  
- data size for test : 1,000 (qa10, qa11 각각)  
- number of hop : 4  
- embedding dim : 20  
- RNN state dim : 30  
- attention dim : 30
- total epochs : 150  
- batch size : 75  
- learngin rate : 0.005  
  
#### qa10 : indefinite knowledge  
<img src="./img/qa10_result_gru.png" width="100%">  
<img src="./img/qa10_acc.png" width="80%">  
  
#### qa11 : basic coreference  
<img src="./img/qa11_result_gru.png" width="100%">  
<img src="./img/qa11_acc.png" width="80%">  
  
#### Tensorflow Graph  
<img src="./img/dymemnn_graph.png" width="80%">  
