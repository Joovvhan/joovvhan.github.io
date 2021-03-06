---

title: "Twitch Video Clipper"

---

## 서론
자기 개발을 위한 공부만 계속하면 금방 질린다. 항상 재밌는 일과 공부를 병행해야 성과가 오르는 법인 듯 하다. 
여러가지 해보고 싶은 일이 있지만, 그 중에서도 가장 쉬워보이는 Twitch Video Clipper를 먼저 시도해보려고 한다.

논문 심사가 끝날 때쯤 되어 Twitch 방송을 시청하게 되었다. 최근에는 침착맨의 침대펄 엄근진 토론을 시청했다. 
방송이 끝나고 나면, 각종 커뮤니티 사이트에 방송 캡쳐본이 돌아다니는 것을 볼 수 있고, Youtube에서는 비디오 하이라이트 부분이 클립되어 올라온다. 
Twitch 방송에 들어가보니 시청자들이 하이라이트 부분을 수작업으로 오려내어 등록하는 것으로 보인다. 
이 과정을 자동화할 수 없을까? 이 의문에서 출발한 것이 바로 Twitch Video Clipper이다.

개인적으로 생각해봤을 때, 이 작업은 무척이나 단순할 것이다. Twitch에는 채팅이라는 명백한 하이라이트 지표가 존재하기 때문에, 
시간대별로 채팅 횟수를 추적한다면 상대적으로 흥미로운 구간을 잡아낼 수 있을 것으로 추측한다.

우선 다음과 같은 두 가지 목표를 달성하려고 한다.

1. 해당 구간을 잘라내어 실제로 하이라이트라고 부를만한지 주관적으로 평가한다.
2. 해당 구간 채팅으로부터 키워드를 추출한다.

## Prerequisites
```
* FFmpeg (영상 편집)
* Twitch Leecher (영상 다운로드)
* RechatTool (채팅 로그 다운로드)
```

## 진행 상황
FFmpeg를 사용하는 방법을 익혔다. 우선 [**Github에 공유된 코드**](https://github.com/c0decracker/video-splitter)를 기반으로 FFmpeg를 사용했는데, 
자체 작성 코드로 옮기도록 한다. 키워드 추출은 어떤 알고리즘을 참조하면 좋을지 고민 중이다. 
또, Jupyter Notebook에서 FFmpeg를 호출하면 Notebook이 뻗어버리는 현상도 확인 필요하다.
Voice Synthesis를 공부할 겸 jamo도 공부해볼까 고민 중이다. 
그리고 마지막으로 채팅 로그에서 하이라이트 구간을 좀 더 엄밀하게 정의할 필요가 있다.
