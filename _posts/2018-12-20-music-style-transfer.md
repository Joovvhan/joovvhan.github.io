---

title: "Music Style Transfer"

---

## 서론
이 연구는 딥러닝에 대해서 아는 것이 하나도 없을 때부터 진행해보고 싶었던 것이다. 
이미지 영역에서 Style Transfer가 가능하다는 것은 이미 식상할 정도로 많은 딥러닝 참고 자료에서 보았다. 
그렇다면 소리의 영역에서도 Style Transfer가 가능한가? 
이 부분에 대해서는 아직 명확한 예시가 없는 것 같다.

본인이 8-bit 스타일의 음악을 좋아하고, K-pop이 지속적으로 인기를 끌면서 다음과 같은 데이터를 접할 수 있게 되었다.

<iframe width="427" height="240" src="https://www.youtube.com/embed/Fm5iP0S1z9w" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> 
-----
<iframe width="427" height="240" src="https://www.youtube.com/embed/YkLaNh1F_w8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
-----

원곡과 8-bit 스타일의 편곡된 음악이 쌍으로 존재한다면, 마치 [**vid2vid**](https://github.com/NVIDIA/vid2vid)처럼 
Music Style Transfer가 가능할 것이라는 것이 본인의 추측이다.

단, 이를 구현하기 위해서는 기존 소리 영역에서의 딥러닝 방법론을 먼저 숙지하는 것이 우선일 것이다.

## 참고 문헌 
* [**TimbreTron**](https://www.cs.toronto.edu/~huang/TimbreTron/index.html)

## 진행 상황
* 악보를 생각해보자. 특정 악기의 음색으로 주어진 악보대로 연주를 합성해내는 것은 이미 오래 전부터 가능하다.
* 원곡 &rarr; 악보 &rarr; 8-bit 편곡: 쉽지만, End-to-end Approach라고 보기에는 무리가 있다.
* 음색 &rarr; 악보, 악보 &rarr; 음색: 이 두 가지가 가능한가? Music Style Transfer보다는 상대적으로 쉬울 것 같다.

## 추후 진행 사항
* Music Style이라는 것이 무엇을 의미하는지 엄밀하게 정의하기
* Music Style을 정의하기 위해 음악 처리 쪽에서 쓰이는 단어와 먼저 익숙해지기
