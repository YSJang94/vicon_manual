# VICON 사용법

## 목차
0. Prerequisite
1. 바이컨 보정하기
2. 새로운 물체 등록하기
3. ROS로 바이컨 토픽 받기
4. 영상 튜토리얼

## 0. Prerequisite
   데스크탑 켜고 밑에 바이컨 컨트롤러 ON  
   바탕화면의 Vicon Tracker 1.3.1 클릭  
   asus 라우터 켜기 (바이컨 통신용)  
   ROS 가능한 노트북  

## 1. 바이컨 보정하기
   카메라가 제대로 잡히면 프레임이 초록색으로 바뀜  
   마우스 우클릭으로 줌, 좌클릭으로 뷰포인트 바꾸기, 동시 클릭해서 translation  
* 카메라 보정하기
  1. CALIBRATE CAMERS 탭에서START 눌러 보정 시작
  2. WAND를 카메라 앞에서 흔들어서 보정
  3. WAND COUNT 최소 4000 넘겨야,  이상적으로는 10000 이상 (중요)
  4. 3D 뷰, 카메라 뷰(지정된 카메라에 찍히는 마커) 등을 선택할 수 있음
  5. STOP 누르기
* 원점 정하기
  1. WAND에 나타난 +x, +z와 원하는 좌표축과 정렬 (원점은 실험실 한 가운데 X표시)
  2. SET VOLUME ORIGIN 탭에서 START 눌러서 원점 기준 잡기

## 2. 새로운 물체 등록하기
* 마커 붙이는 요령
  1. 웬만하면 4개 이상의 마커 사용, 많을수록 좋음  
  2. 보통 3~4개로 한 평면 구성 (비대칭적으로 부착해야함), 나머지 1개는 평면에 수직인 곳에 부착  
  *평면의 무게중심에 object 원점이 잡힘(?), yaw는 물체 등록 시 놓인 방향을 기준으로 설정됨*  
* 등록하기
  1. 원하는 물체의 바이컨 마커를 CTRL 클릭해서 선택  
  2. OBJECT 탭에서 물체 등록 (이름 설정하고 확인)  
  3. OBJECT 탭에서 check 표시 토글해서 원하는 물체의 pose만 읽을 수 있음  

## 3. ROS로 바이컨 토픽 받기
* ROS 설정하기
  1. 와이파이 (icsl2.4/5) 또는 이더넷 케이블로 노트북과 연결 (인터넷 안되는 내부망)  
  2. ETH에서 제공하는 vicon_bridge.git을 catkin_ws로 클론하고 catkin_make 실행  
  (https://github.com/icsl-Jeon/vicon_bridge.git, 아마도 추가적인 dependency 필요할 수 있음)  
   *필요에 따라 launch 파일을 수정해야됨 (IP 주소, 포트 등)*  
   *필요에 따라 .bashrc를 수정하여 ROS_IP 등을 등록해야 될 수 있음*  
* 바이컨 연결하기
  1. roslaunch vicon_bridge 명령으로 ros node 실행
  2. rostopic list로 바이컨에서 쏘는 TF 토픽을(vicon/<object_name>/) 찾고 rostopic <topic_name> echo로 실시간 확인이 가능함 (id,t,x,y,z,qx,qy,qz,qw – 위치랑 쿼터니언 등 제공)  
   *(optional) txt나 rosbag으로 저장해서 추후 가공*  

## 4. 영상 튜토리얼
<a href="http://www.youtube.com/watch?feature=player_embedded&v=YOUTUBE_VIDEO_ID_HERE
" target="_blank"><img src="http://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg" 
alt="바이컨 영상 튜토" width="240" height="180" border="10" /></a>
