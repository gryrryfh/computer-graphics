# faceApi를 이용한 미용 프로그램 팀프로젝트
## 팀원 : 이재경, 김기찬, 추승범, 엄재웅
## 소스코드 
``` java script

let img, parts;
let options = {withLandmarks: true, withDescriptors: false};
let button;
let colorPicker;
let Eb = 1;

function preload() {
  img = loadImage('face1.jpg');
}

function setup() {
  createCanvas(img.width, img.height);
  colorPicker = createColorPicker('#ed225d');
  button = createButton('Eyebrow');
  background(255); 
  noLoop();
}

function draw(){
  image(img, 0, 0);
  faceapi = ml5.faceApi(options, modelReady);
  button.mousePressed(Ebf);
}

function Ebf(){
  Eb *= -1;
}

function mousePressed(){
  redraw();//화면클릭하면 1번더실행
}

function modelReady() {
  faceapi.detectSingle(img, gotResults);
}

function gotResults(err, results) {
  if (err) {
    console.error(err);
    return;
  }
  console.log(results);
  parts = results.parts;
  stroke(0, 0, 255);
  strokeWeight(2);
  drawmouth();
  if(Eb > 0){
    draweyebrow();
  }
}

function drawmouth() {
  stroke(0);
  fill(colorPicker.color());
  beginShape();
  for(let i=0; i<parts.mouth.length; i++){
    vertex(parts.mouth[i]._x, parts.mouth[i]._y);
  }
    vertex(parts.mouth[0]._x, parts.mouth[0]._y);
  endShape();   
}

function draweyebrow(){ 
  stroke(255,0,255);
  noFill();
  beginShape();
  for(let i=0; i<parts.leftEyeBrow.length; i++){
    vertex(parts.leftEyeBrow[i]._x, parts.leftEyeBrow[i]._y);
  }
  endShape();

  beginShape();
  for(let i=0; i<parts.rightEyeBrow.length; i++){
    vertex(parts.rightEyeBrow[i]._x, parts.rightEyeBrow[i]._y);
  }
  endShape();
}
```

## 실행 결과
![1](image/facedetection.mp4)

## 변형내용
* 입술의 화장과 눈썹을 강조하기 위해 나머지 눈, 코와 관련된 내용들을 삭제했다.
* createColorPicker를 사용해 입술색을 원해는 모든 색으로 바꿀 수 있게 했다.
* createButoon을 사용해 눈썹이 버튼을 누르면 없어지고 다시 생기고를 할 수 있게 했다.
* 사진과 미용프로그램 구현내용을 합쳐 조금 더 사용자가 모습을 잘 확인 할 수 있게 했다.

## 소감
* 김기찬 
>이번 과제를 통해서 평소에도 관심을 가지고 있던 인공지능에 대해 직접적으로 체험해 볼 수 있었고 팀원들과 함께 입술과 눈썹을 변형하는 코드를 구상하면서 새로운 함수나 기능들을 찾아볼 수 있는 시간이 되었습니다. 알고리즘이나 유연한 사고의 필요성을 느끼게 되는 즐거운 과제였던 것 같습니다.

* 이재경 
>인공지능과 관련된 과제를 간단하게나마 공부해보고 알아보면서 관련 내용에 흥미를 많이 가졌습니다. 아직 진로를 확실히 정하지 않았는데 이번 팀프로젝트를 계기로 인공지능, 머신러닝과 관련된 공부를 더 해보고싶다는 생각이 들었습니다. 코드들이 간단해보여도 변형하는데 시간이 좀 걸렸습니다. 앞으로 그래픽스에 열정을 가지고 공부하면서 관련분야에 전문가가 되보고싶습니다.

* 추승범 
>팀원들과 함께 고민하며 머신 러닝을 공부하게 되어서 너무 재밌는 시간이었습니다. 처음 사용해보는 머신 러닝은 활용도가 높고 실생활에서 유용하게 사용할 수 있어 보였습니다. 코딩을 잘하는 팀원에게 코딩을 배우며 머신 러닝과 자바스크립트를 한층 더 알아가는 팀프로젝트였습니다.  더 열심히 공부해서 머신 러닝을 잘 다룰 수 있도록 노력하겠습니다.

* 엄재웅 
>팀원들과 디스코드에서 모여 회의 후 각자의 아이디어를 정해 자바 스크립트에 실현시켜보는 방식으로 진행을 하였습니다.
입술과 눈썹을 변형시키기 좋은 방법이 버튼을 추가하여 버튼을 통해 색들을 바꾸는 것이라 생각하였고 직접 만들어 보기도 하였습니다.
중간중간에 입술과 눈썹의 위치들도 바꿔보는등 여러가지 수정도 해보며 페이스 마스크를 만드는 코드를 더 익힐 수 있는 좋은 시간이 되었습니다.
