---

title: "Voice Synthesis"

---

## 서론
음성 합성은 이미 연구된 내용도 많고, 다양한 개발자들이 구현해놓은 코드가 이미 존재한다. 
우선 GPU 서버에 소스와 데이터를 받아 실제 음성 합성을 실험하는 중이다.

## 관련 데이터
* [**LJ Speech**](https://keithito.com/LJ-Speech-Dataset/)
* [**Blizzard**](http://www.cstr.ed.ac.uk/projects/blizzard/2012/phase_one)

## 관련 논문
* Tacotron
* Tacotron2
* WaveNet
* DeepVoice

## 코드 참조
* [**Keith Ito**](https://github.com/keithito/tacotron)
* [**Taehoon Kim**](https://github.com/carpedm20/multi-speaker-tacotron-tensorflow)
* [**Ryuichi Yamamoto**](https://github.com/r9y9)

## 해야할 일
* 관련 논문을 싹 다 읽고 *용어*와 *관련 기술* 정리
* 작동하는 코드의 흐름을 line-by-line으로 분석

## 해결해야 할 점
* Docker에서 연 Jupyter Notebook 포트를 외부에서 제대로 접속할 수 있도록 만드는 것
* 한글 텍스트 관련 에러의 원인 분석
