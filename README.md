# facial-detection


### 프로젝트의 목적
개, 고양이, 사람을 구분해 주는 웹사이트 구축 프로젝트를 해 봄으로써 실제 서비스에서 고비용의 GPU를 사용하지 않고 효율적인 시스템을 구축하는 방법을 고안해 본다.


### 사전학습

10분 딥러닝 유튜브 학습
https://www.youtube.com/watch?v=8DjIJc7xH5U

허훈의 YOLO 논문 리뷰
https://www.youtube.com/watch?v=Ae-p7QVOdbA
https://curt-park.github.io/2017-03-26/yolo/


YOLO v1, v2, v3 논문 리뷰
https://www.youtube.com/watch?v=cNFpo7kDf-s


딥러닝 기반의 유명한 회사
https://deepsystems.ai/reviews

윈도우에서 YOLO v4 설치
https://www.youtube.com/watch?v=5pYh1rFnNZs

YOLO에서 추가적인 학습방법
https://m.blog.naver.com/PostView.nhn?blogId=hhd4136&logNo=221304645344&proxyReferer=https:%2F%2Fwww.google.com%2F
https://pgmrlsh.tistory.com/6?category=766787

아마존에서 실행하기
https://kinocoder.tistory.com/13

mac에서 개발 준비하기
https://www.arunponnusamy.com/deep-learning-setup-macos.html

이미지 학습학기

https://j-remind.tistory.com/64
https://blog.francium.tech/custom-object-training-and-detection-with-yolov3-darknet-and-opencv-41542f2ff44e
https://github.com/tzutalin/labelImg




### YOLO Site
https://pjreddie.com/darknet/yolo/


### YOLO Test
```
sudo apt-get install build-essential
sudo apt-get install git

git clone https://github.com/pjreddie/darknet.git
cd darknet
make

wget https://pjreddie.com/media/files/yolo-tiny.weights

./darknet detect cfg/yolov1-tiny.cfg yolo-tiny.weights data/dog.jpg
```

### 테스트 결과
GCP에서 테스트 - n1-standard-1(vCPU 1개, 3.75GB 메모리)
- coco data set의 경우
./darknet detector test cfg/coco.data cfg/yolov1.cfg yolo.weights data/dog.jpg

<table>
  <tr>
   <td>```


   </td>
   <td>V1
   </td>
   <td>V2
   </td>
   <td>V3
   </td>
   <td>V4
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>8.74 sec/1 frame
   </td>
   <td>13.93 sec/1 frame
   </td>
   <td>33.09 sec/1 frame
   </td>
   <td> sec/1 frame
   </td>
  </tr>
  <tr>
   <td>dog
   </td>
   <td>X
   </td>
   <td>82%
   </td>
   <td>100%
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>truck
   </td>
   <td>55%
   </td>
   <td>64%
   </td>
   <td>92%
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>bicycle
   </td>
   <td>X
   </td>
   <td>85%
   </td>
   <td>99%
   </td>
   <td>
   </td>
  </tr>
</table>

- VOC data set의 경우
./darknet detector test cfg/voc.data cfg/yolov1.cfg yolov1.weights data/dog.jpg

<table>
  <tr>
   <td>```


   </td>
   <td>V1
   </td>
   <td>V2
   </td>
   <td>V3
   </td>
   <td>V4
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>8.74 sec/1 frame
   </td>
   <td>14.75 sec/1 frame
   </td>
   <td>32.44 sec/1 frame
   </td>
   <td> sec/1 frame
   </td>
  </tr>
  <tr>
   <td>dog
   </td>
   <td>X
   </td>
   <td>82%(sheep)
   </td>
   <td>100%(sheep)
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>truck
   </td>
   <td>55%(car)
   </td>
   <td>64%(cat)
   </td>
   <td>92%(cat)
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>bicycle
   </td>
   <td>X
   </td>
   <td>85%
   </td>
   <td>99%
   </td>
   <td>
   </td>
  </tr>
</table>

- Tiny Model
** 도메인을 변경해서 맥에서 하든, 우분투에서 하든 결과가 동일하다.
```
./darknet detect cfg/yolov1-tiny.cfg yolov1-tiny.weights data/dog.jpg
wget https://pjreddie.com/media/files/yolo-tiny.weights
wget https://pjreddie.com/media/files/yolov2-tiny.weights
wget https://pjreddie.com/media/files/yolov3-tiny.weights

./darknet detect cfg/yolov1-tiny.cfg yolo-tiny.weights data/dog.jpg
./darknet detect cfg/yolov2-tiny.cfg yolov2-tiny.weights data/dog.jpg
./darknet detect cfg/yolov3-tiny.cfg yolov3-tiny.weights data/dog.jpg
```

<table>
  <tr>
   <td>```


   </td>
   <td>V1
   </td>
   <td>V2
   </td>
   <td>V3
   </td>
   <td>V4
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>8.74 sec/1 frame
   </td>
   <td>1.3 sec/1 frame
   </td>
   <td>1.38 sec/1 frame
   </td>
   <td> sec/1 frame
   </td>
  </tr>
  <tr>
   <td>dog
   </td>
   <td>X
   </td>
   <td>82%
   </td>
   <td>57%
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>truck
   </td>
   <td>X
   </td>
   <td>74%
   </td>
   <td>52%
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>bicycle
   </td>
   <td>X
   </td>
   <td>59%
   </td>
   <td>56%
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
   <td>62%(car)
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
   <td>59%(bicycle)
   </td>
   <td>
   </td>
  </tr>
</table>


### 기본 YOLO 검토 결과
- 맥과 GCP, AWS에서 플랫폼이 다르고, CPU수와 메모릭가 다르지만, 버전마다 비슷한 mAP와 FPS를 보인다
- 기본 YOLO 모델은 NO GPU에서는 버전이 오를 수록 느려지지만, 정확도는 높아졌다.
- Tiny YOLO는 V2 이후 1.3 sec/frame대의 성능을 보였다
- 코코데이터셋이 VOC보다 정확도가 높았다
