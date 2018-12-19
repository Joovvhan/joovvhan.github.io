---

title: "Sound Classification"

---

## 서론
개인적으로 보기에 Speech Recognition, Voice Synthesis, Sound Classification, Music Sytle Transfer 
네 가지 과제를 난이도 순으로 나열하면 다음과 같다. 

```yaml

Music Style Transfer > Voice Synthesis > Speech Recognition > Sound Classification

```

여기서 Sound는 모든 종류의 소리를 의미하고, 나머지는 단어 그대로 각각 발화, 발성, 음악을 의미한다.
소리를 분류한다는 것은 새소리와 자동차 소리를 구분하는 등의 작업을 의미한다.

발화를 인식한다는 것은 사람이 내는 발화를 텍스트로 변환하는 작업(Speech-to-Text, STT)을 의미한다.

Speech Recognition은 어찌보면 Sound Classification의 한 종류로 볼 수 있을 것이다.

물론 Sound Classification이 Speech Recognition과 다른 데이터 환경에서 좀 더 고도화된 결과물을 요구하기도 한다.

몇 가지 예를 들자면 Speech Recognition 과정에 요구되는 데이터는 비교적 확실히 레이블 되어 있는 반면, 
Sound Classification에서는 여러 가지 소리가 공존할 수 있어, 이 부분에 대한 레이블링 문제가 존재한다. 
예를 들어 새 지저귐과 자동차 엔진 소리가 같이 녹음된 소리는 어떤 레이블을 가져야 하는가 하는 문제가 있다.

Voice Synthesis는 STT 과정의 역과정으로 텍스트를 발화로 변환하는 작업(Text-to-Speech, TTS)이다.

기존에는 보이스 웨어를 이용한 비교적 불완전한 음성 합성을 이루어왔지만, 최근 딥러닝을 적용하여 자연스러운 음성을 합성하고 있다.

Music Sytle Transfer가 사람 음성에 적용된 경우가 Voice Style Transfer라고 볼 수 있을 것이다.

최근 Voice Synthesis 분야에서 이미 많은 성과를 보여줬으므로, Voice Style Transfer가 불가능하지 않음은 쉽게 유추할 수 있다.
TTS와 STT 모두 가능하니, 우선 음성을 텍스트로 바꾸고, 특정 인물의 음성으로 다시 그 텍스트를 발음하게 하는 것은 가능하기 때문이다.
Music Style Transfer도 마찬가지로 먼저 음악을 악보로 변환하고, 그 악보를 학습된 악기 모델로 연주하게 하는 것은 가능할지도 모른다.

이런 관계성을 생각해보았을 때, 개인적으로 매긴 난이도는 위와 같다.

흥미로운 점은, Sound Classification은 비교적 쉬운 문제인 것처럼 보임에도 불구하고 학계에서 뛰어난 결과물을 찾아보기 어렵다는 점이다.

## Dataset

[**UrbanSound8K**](https://urbansounddataset.weebly.com/): [**Freesound**](https://freesound.org/)에서 제공하는 음향 데이터에 레이블을 붙인 것이다.

[**ESC**](https://github.com/karoldvl/ESC-50): 마찬가지로 [**Freesound**](https://freesound.org/)에서 제공하는 음향 데이터에 레이블을 붙인 것이다.
50개의 클래스와 10개의 클래스를 가진 ESC-50과 ESC-10 두 종류의 데이터가 존재한다. 레이블링 작업자는 Karol J. Piczak.

## Challenges

DCASE: [**DCASE 2018**](http://dcase.community/challenge2018/index)

## 현황

다양한 방법론이 존재하지만, 결국 Sound Classification은 소리를 시주파수 데이터(예: MFCC(Mel-frequency Cepstrum Coefficient))로 변환하여, 
CNN 모델에 적용하는 것이 일반적이다. 개인적인 경험상 이 부분에 대해서는 큰 변화가 없다. 물론 더 많은 논문을 조사할 필요가 있다. 
어쨌든, 참조할 모델에는 큰 차이가 없다는 전제하에 우선적으로 Dataset을 조사하기로 했다.

현재 UrbanSound8K 데이터와 ESC-50 데이터를 확보했다.

```
전체 주파수 범위가 224 등분 되도록 Spectrogram의 nsc를 448로 설정
Spectrogram의 시간 축 방향에서, 중심의 224 픽셀을 선택하여 224x224 이미지 생성
Keras의 Pretrained Xception, VGG-16 모델에 적용
&rarr; 전혀 분류 못하고 있음
&rarr; Spectrogram 확인 결과, 이미지 상에서는 어느 정도 차이가 남
&rarr; 여전히 원인 불명
```

```
지나치게 느린 연산 &rarr; GPU 가속기를 켜지 않았었음 &rarr; 해결됨
클래스와 일치하지 않는 부분이 있음(예: 새 소리로 분류된 음성 중 새 소리가 나지 않는 부분이 있음)
전혀 분류 못하고 있음 &rarr; 원인 불명
```

## 조치해야 할 부분

1. Karol J. Piczak의 논문을 참조하여 같은 방식으로 분류 시도.
&rarr; MFCC를 사용하는 방식임. 굳이 따라할 필요가 있을까 고민이 됨.

2. librosa 패키지에 대해 공부

3. 다른 DCASE 사례들을 찾아볼 필요성을 느낌.
&rarr; DCASE 대회 이력에 대해서 정리하면 좋을 듯 함.







