# computer graphics

## Video texture 구현
`Reference`와 `WebGL Tutorial`을 참고하여 `Video texuture`를 구현했습니다.

### 기능

1. Video 영상을 play/pause 할 수 있습니다.
2. HTML에서 비디오를 화면에 띄우고 id를 javascript로 호출하여 비디오 객체를 하나 더 생성하여 화면에 현재 재생중인 영상을 추가했고 Mapping된 영상과 동시에 pause,start 기능이 가능하도록 설정했습니다.
```html
<html> :<video id="ing" video src="b.mp4" width="480" height="270" autoplay="autoplay">현재 재생중인 영상</video>
<javascript>const current = document.getElementById("ing");
var pauseVideo = document.getElementById('pause');
  pauseVideo.addEventListener('click', function() {
    video.pause(); 
    current.pause();
  
  }, true);
  
  var playVideo = document.getElementById('play');
  playVideo.addEventListener('click', function() {
      video.play(); 
      current.play();
  }, true);
```

3. 큐브 회전을 반대로 하거나 deltaTime 변수를 조작하여 속도를 변경할 수 있습니다.
```js
function cuberotate(){
  if(speed >= 1.0){
    speed = -1.0;
  }else{
    speed = 1.0;
  }
}
function cubestartstop(){
  if(speed == 0.0){
    speed = 1.0;
  }else{
    speed = 0.0;
  }
}

function cubefast(){
  if(speed >= 1.0){
    speed += 0.1;
  }else if(speed == 0.0){
    speed = 0.0;
  }else{
    speed -= 0.1;
  }
  
}

function cubeslow(){
  if(speed > 0 ){
    speed -= 0.1;
  }else{
    speed += 0.1;
  }
}
now *= 0.001; 
    const deltaTime = (now - then) *speed;
    then = now;
```

### 이벤트리스너
버튼 6개를 구현하였고 비디오 관련된 버튼은 getElementById로 호출 받아서 입력했고, 큐브 관련 버튼은 버튼클릭시 함수가 호출됩니다.
```html
<button id="play">영상 다시시작</button>
<button id="pause">영상 일시정지</button>
<button onclick="cuberotate()">큐브 방향전환</button>
<button onclick="cubestartstop()">큐브 시작/정지</button>
<button onclick="cubefast()">큐브 속도up</button>
<button onclick="cubeslow()">큐브 속도down</button>
```

### 시연 영상
![1](project.gif)

## Reference
1. https://developer.mozilla.org/ko/docs/Web/API/WebGL_API/Tutorial/Animating_textures_in_WebGL

2. https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video#Events

3. https://www.youtube.com/watch?v=O1mYw-3Wl_Q

4. https://www.youtube.com/watch?v=gMC6VaNdhuo

5. https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/pause_event

6. 비디오 파일 저작권 x https://www.learningcontainer.com/mp4-sample-video-files-download/