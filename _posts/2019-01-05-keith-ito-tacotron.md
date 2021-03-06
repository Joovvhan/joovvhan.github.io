---
title: "Keith Ito's Tacotron Review"
---

### 이 포스트에서는 Keith Ito라는 분이 구현한 Tacotron 코드를 분석한다.
코드의 흐름을 처음부터 끝까지 분석하여 이를 구현하기 위해 공부해야 할 부분을 정리하려고 한다.

### hParam.py 
각종 하이퍼 파라미터를 기록, 전체 흐름을 이해하는데 도움이 됨.

### preprocessing.py
[x] argparse: argparse package를 활용한 argument를 넘겨 받는 일반적인 방식에 관하여

[x] LJSpeech와 Billizard Dataset: Dataset의 구조

[x] metadata: train.txt를 이용하여 데이터를 관리하는 방식, 이후 DataFeeder로 이어짐.

### datasets/ljspeech.py
[-] lambda: tqbm을 lambda 문법으로 넘겨주는 이유

[-] ProcessPoolExecutor, partial: 병렬 처리 문법

### util/audio.py
librosa 패키지의 wrapper라고 볼 수 있음.
[-] _preemphasis: 초기 필터, a, b parameter를 직접 집어 넣어서 정확히 몇 Hz에 해당하는 필터인지 분석 필요

[x] _stft: librosa.stft를 수행할 뿐 

[x] _istft: librosa.istft를 수행할 뿐

[x] spectrogram: 필터링 수행 후 STFT 적용, abs 적용하고(이 시점에서 데이터가 복소수가 아니게 된다), ref_level_db=20 빼주고, db로 변환

[-] melspectrogram: spectrogram 함수에서 log 취하기 이전에 mel-frequency 가중치를 생성하고 곱하는 것으로 파악. [**librosa.filters.mel**](https://librosa.github.io/librosa/generated/librosa.filters.mel.html) 함수 분석 필요.

[x] _amp_to_db: 주어진 array에 20 * log10 수행. -inf를 방지하지 위해 최소값은 1e-5로 대체.

[x] _db_to_amp: (1/20 * x) ^ 10, _amp_to_db의 정확한 역변환.

[x] _normalize: S에 min_level_db 빼고, min_level_db로 나누고, np.clip을 이용하여 0과 1 사이 값으로 자르기. spectrogram, melspectrogram 양쪽에 활용.

[-] _stft_parameters: hparams 클래스에서 STFT 변수를 호출, n_fft와 hparms.num_freq 사이의 관계식 파악 필요.

[-] _grinffin_lim: spectrogram을 원신호로 복원하는 알고리즘, inverse STFT에 비해 갖는 장점을 아직 파악하지 못함. [원본 논문](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.306.7858&rep=rep1&type=pdf)



### train.py
[-] [subprocess.check_output](https://docs.python.org/3/library/subprocess.html#subprocess.check_output): 하위 프로세스를 생성하는 코드.

[-] [tf.train.Coordinator](https://www.tensorflow.org/api_docs/python/tf/train/Coordinator?hl=ko): Thread coordinator. 

[x] tf.variable.scope: Tensorflow 변수의 scope를 정의, with as 문법으로 주로 사용하는 듯.

[x] models/__init__.create_model: Tacotron class를 생성.

### tacotron.py
Tacotron class를 포함하고 있는 실제 tacotron 모델을 생성하는 코드, 어려움

[-] tensorflow.contrib.rnn: GRUCell, MultiRNNCell, OutputProjectionWrapper, ResidualWrapper, RNN 공부 필요...

[-] tensorflow.contrib.seq2seq: BasicDecoder, BahdanauAttention, AttentionWrapper, 이론적으로 공부해야 함... 어려움. Attention 공부 필요.

[-] 

### models/modules.py
Tacotron 논문에서 언급된 주요 module, Tacotron Class에서 호출되며, Tacotron을 구성하는 핵심 요소.

[x] prenet:

[x] encoder_cbhg:

[x] post_cbhg:

[x] cbhg:

[x] highwaynet:

[x] conv1d:




