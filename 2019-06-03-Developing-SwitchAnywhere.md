# 아무나 내 방의 불을 끌 수 있는 프로그램 Switch Anywhere

드라마 <빅뱅이론>에 나온 농담에서 영감을 받아 만들었습니다.

### 이 프로그램을 사용하는 상황

*Moonhyuk* : 제 방의 불을 끌 수 있는 사이트를 공개합니다! http://www.switchAnywhere.com 여기 들어오셔서 아무나 버튼을 눌러보세요!
*User* : 오 한번 꺼볼까.. *[사이트 접속 후]* '끄기' 눌렀는데 꺼졌겠지?
*Moonhyuk* : 방금 중국에서 내 방 불을 껐어!!

----

## Iteration 과정
1. 이  프로그램을  사용하는  상황과  필수  요소, 제약  조건  등을  정합니다. “내가  이  프로그램을  쓴다면?”이라고  가정하면  더  쉬울  수  있습니다.
2. 이  프로그램에  무엇을  입력했을  때  어떤  결과가  나와야  하는지  유형을  분류하고  구체적인  사례를  찾아  봅니다.
3. 어디까지  구현할  건지, 무엇이  가장  중요한지, 어떤  순서대로  진행해야  할지  결정합니다.
4. 프로그램을  구현합니다.
5. 프로그램을  공유합니다.
6. 결과를  확인하고  추가로  배운  점을  적용해 1로  돌아가서  다듬습니다.

1~6을  매일  진행함으로써  점진적으로  개선시킵니다. 특히 1과 2를 구체적으로 적습니다. 프로토타입을 만들어보니 필요 없는 기능인 것 같으면 과감하게 목표를 수정해도 됩니다.


### 1. 필수요소
 - 방의 스위치를 물리적으로 누를 수 있는 장치(디바이스)
 - 유저들이 전구의 On과 Off를 조작할 수 있는 웹 프론트엔드
	 - 켜기 / 끄기 버튼
	 - 전구 이미지
 - 디바이스에게 요청을 전달할 웹서버
 - On/Off 요청을 받아 물리적 장치를 작동시킬 수 있고, 현재 상태를 웹사이트에 업데이트 시킬 수 있는 프로그램

### 2. 제약사항
- 유저는 전구를 켜는 행위와 끄는 행위에 대해서만 요청을 보낼 수 있다.
- 디바이스는 스위치를 물리적으로 누르는 행위만 할 뿐 실제로 켜졌는지 알 수 없다.


### 3. 입력과 출력
입력 : On / Off 버튼 클릭
출력 :
- 전구 Off / On 이미지로 바뀜
- 스위치 장치에 신호를 보냄
- ip를 추적해 어느 나라에서 누른건지 서버에 로그를 남김

### 4. 어디까지 구현할 것인가
프로토타입으로 방 전구가 아니라 라즈베리파이에 연결된 LED에 대해 조작을 할 것입니다.

**오늘 당장 할 수 있는 것**
- [x] 켜기/끄기 버튼과 전구 이미지가 있는 Front page를 vue.js로 구현한다.

**구현 할 순서**
~~ - [ ] 라즈베리파이에 들어갈 프로그램 구현 ~~
	- IoT를 위한 경량 프로토콜인 CoAP 프로토콜을 사용한다.
	- 요청을 받아 LED를 켜고 끄는 것을 처리한다.
	- 현재 상태와 성공/실패 여부를 응답한다.
- [ ] Web Backend Server 구현
	- http 프로토콜을 CoAP 프로토콜로 변환하여 라즈베리 파이에 전달.


	- IP를 추적해 어느 나라에서 요청했는지 서버에 로그를 남김
~~ - [ ] web 서버 Cloud에 배포 ~~
- [ ] 모드를 추가한다.
Club mode : 미친듯이 껐다 켜졌다 반복
모스부호 mode : 유저가 텍스트를 입력하면 모스부호로 번역되어 반짝거리게 한다.
- [ ] 실제 스위치를 누를 수 있는 디바이스를 만든다.(모터로)
- [ ] 라즈베리 파이에 들어가는 프로그램을 수정한다.
	- LED 조작 함수를 없애고 스위치 조작 함수로 바꾼다.

6일간 웹서버를 배포하는 것 까지 구현하는 것을 목표로 합니다.

**2019-06-03 수정**
- [ ] webiopi.js파일을 vue.js의 형식에 맞게 프론트 페이지에 import
켜기/끄기 버튼에 webiopi의 함수를 불러올 수 있도록 method 정의 후 @click=""에 넣어줌.
- [ ] 라즈비안os에서 webiopi 설치 후 모터를 컨트롤 하는 python file 작성
- [ ] 라즈베리파이 GPIO 핀번호 23,24번에 모터 연결
- [ ] python file 실행 후 버그 수정
- [ ] config 경로에 HTML file과 python file 넣고 라즈베리파이에서 웹서버 동작시킴.
- [ ] HTML 파일은 vue 에서 npm run build 후 dis 폴더 내의 파일만 넘긴다
- [ ] 모터의 각도 조절 함수를 사용하여 on일때 각도, off 일때 각도를 정해준다.
- [ ] 실제 스위치를 누를 수 있는 디바이스를 모터로 만든다.
- [ ] UI 수정 다른 모드의 버튼 추가


WebIOPI documentation
([http://webiopi.trouch.com/](http://webiopi.trouch.com/))
Python tutorial documentation
[https://webiopi.trouch.com/Tutorial_Basis.html](https://webiopi.trouch.com/Tutorial_Basis.html)
WebIOPI 파이썬으로 모터 조작
[https://m.blog.naver.com/cosmosjs/220676648986](https://m.blog.naver.com/cosmosjs/220676648986)
이어서)
[https://m.blog.naver.com/cosmosjs/220672296511](https://m.blog.naver.com/cosmosjs/220672296511)
라즈베리파이 GPIO 핀 번호
[https://m.blog.naver.com/pcmola/220797340767](https://m.blog.naver.com/pcmola/220797340767)
javascript 코드까지 있는 webiopi 실습 
[https://m.blog.naver.com/cosmosjs/220729784491](https://m.blog.naver.com/cosmosjs/220729784491)
서보블라스터 - 여러개의 모터 사용할 때
[http://blog.naver.com/cosmosjs/220665404570](http://blog.naver.com/cosmosjs/220665404570)
javascript 함수 export 방법
[https://medium.com/@zachgavin/module-exports-and-loading-es5-to-es6-a33ac592989c](https://medium.com/@zachgavin/module-exports-and-loading-es5-to-es6-a33ac592989c)
 


