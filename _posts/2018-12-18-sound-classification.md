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





