> # Week_2
# Color
## RGB란?
-------------------
+ RGB컬러는 빛의 혼합으로 모니터와 액정의 빛을 이용한 제품 색상에 기초해 색을 구현하는 모드이다.
+ 색을 섞을수록 밝아지기 때문에 '가산혼합'이라고 한다.　　　
+ 일반적으로 RGB는 웹디자인과 화면용 이미지, CD-ROM, 모니터, 조명 등에 사용된다.
## CMYK란?
------------------
+ CMYK는 Cyan, Magenta, Yellow(청록색, 자홍색, 노란색) 3가지를 혼합해 색을 만들어낸다．　　　　　
+ CMYK는 더하면 더할수록 어두워져 최종적으로 Black이 되는 '감산혼합'을 의미한다. 
+ RGB가 나타낼 수 있는 색상 수보다 CMYK가 나타낼 수 있는 색상 수는 적다.
+ CMYK의 색을 모니터에서는 구현할 수 있지만 RGB의 색은 인쇄물에서 구현할 수 없다.

## 빛의 3원색   
 ![image](https://wowpress.co.kr/wow2.0/w_guide/assets/img/g2_2_01.jpg)   
+ 빨강 - ( R )
+ 초록 - ( G )
+ 파랑 - ( B )   
 ![image](https://wowpress.co.kr/wow2.0/w_guide/assets/img/g2_2_02.jpg)
+ 시안( C )   
+ 마젠타( M )   
+ 노랑( Y )   
+ 검정( k )

## 
### 1. Bit
* 데이터를 나타내는 최소 단위이다. 0과 1의 조합으로 구성된다.
### 2. Vector
+ vector2 (x,y) vector3 (x,y,z) vector4 (x,y,z,w)
### 4. Integer
+ 정수
### 5. Float
+ 부동 소수점
### 6. Boolean
+ 참(1)과 거짓(0)
### 7. Alpha
+ 알파란 투명도를 나타낸다.   
+ 1이면 불투명 0이면 투명이다.
### 8. Color space   
   
> # Week_3
## Gamma란?
-------------------
+ gamma란 이미지를 제작했을때 프린터나 스캐너의 밝기의 크기를 나타내는 용어이다.
+ 영상의 휘도 간 상관 관계를 결정하는 수치이다.　　
+ 감마값에 따라 같은 화면이라도 표현되는 밝기 톤의 차이가 느껴진다.
+ 모니터들이 가장 많이 사용하는 color space는 sRGB(non-linear, 8bit, gamma 2.2) 안에서 이뤄진다. sRGB안에서는 gamma correction이라는 것이 작용하는데, 이는 우리가 본 luminance값을 비디오나 사진에서 암호화, 해독하던 방식을 말한다.   

    ![image](https://news.samsungdisplay.com/wp-content/uploads/2017/05/1-32.jpg)   
### - Gamma가 3D 프로그램에서 어떻게 적용될까?
 

HDR을 제외한 텍스쳐 이미지들이나 컬러 피커가 스크린에서 바르게 보일 수 있는 이유는 감마값이 미리 적용되어 있기 때문이다. 하지만 렌더 엔진들은 linear에서 작용하고 있다.
    
그렇기 때문에 텍스쳐 이미지들의 gamma 수치를 없애지 않고 linear로 작용하는 엔진에서 렌더한다면 감마가 섞인 결과물이 나오게 될 것이다. 최종 결과물인 텍스쳐 이미지에는 감마가 두배로 적용이 되는 것이다. 내가 예상했던 이미지와 다른 결과물이 나오게 될 것이다.
## Linear Workflow
------------------

+ 실제 세상의 빛은 linear로 작용, 우리가 보는 빛의 양은 광원들의 빛의 양을 합친 값이다. 즉, 실제 세상에서는 input이 output과 일정, 동등하다. 이를 linear라고 한다.
+ linear workflow는 씬 안의 모든 라이트, 텍스쳐, 머터리얼이 렌더할 때 같은 color space에서 존재함을 보장한다.．　　　　　
+ 이미지를 저장할 때 중요하다.


# aces    

![image](http://www.oscars.org/sites/oscars/files/aces_share2.png)
(https://youtu.be/DX5tQix9NbY)
+ aces란 색상 관리 및 이미지 교환 시스템이다.
+ ACES는 16bit, 32bit, 25stop 이상의 규격을 가지고 있어 현존하는 모든 카메라의 다이내믹 레인지와 컬러 영역을 커버할 수 있다.
+ 이 과정은 IDT, ACES, RRT+ODT 과정을 
거치게 된다.   

> # Week_4   
# Merge
-------------------
atop Ab+B(1-a)   
average (A+B)/2   
color-dodge brighten B towards A   
conjoint-over A+B(1-a)/b,A if a>b   
copy A
difference abs(A-B)   
disjoint-over A+B(1-a)/b, A+B if a+b<1   
divide A/B, 0 if A<0 and B<0   
exclusion A+B-2AB   
from B-A   
geometric 2AB/(A+B)   
hard-light multiply if A<.S, screen if A>.5   
hypot diagonal sqrt(A * A+B * B)   
in Ab   
mask Ba   
matte Aa+B(1-a) (unpremultiplied over)   
max max(A,B)   
min min(A,B)   
minus A-B   
multiply AB, A if A<0 and B<0    
out A(1-b)   
over A+B(1-a)   
overlay multiply if B<.5, screen if B>.5    
plus A+B   
screen A+B-AB if A and B between 0-1, else A if A>B else B    
soft-light B(2A+B(1-AB))) if AB<1, 2AB otherwise(less extreme than hard-light)   
stencil B(1-a)   
under A(1-b)+B   
xor A(1-b)+B(1-a)   

+ A=Input A
+ a=alpha of A
+ B=input B
+ b=alpha of B   

## Rotoscoping
------------
로토스코핑('roto'라고도 함)은 애니메이션 및 실사 프로젝트 모두에 대한 그래픽 자산을 생성하는 프레임별로 실사 푸티지를 추적하는 것과 관련된 애니메이션 기술이다.

 ![image](https://www.foundry.com/sites/default/files/paragraphs/hero-images/Header_nuke_rotoscoping.jpg)

+  Zoom in to it on frame 1
+ Go to the draw tool – roto node (‘O’ on the keyboard) – don’t need to drop it in quite yet
+ To the left of the viewer you have additional tools relating to the roto node – selection/points/curve type
+ Choose bezier here, most control
+ We want a closed shape – bezier – click drag a point to change the curve tangent
+ CTRL click only moves 1 handle
+ Move to the end frame 70 (little blue markers indicate a key frame)
+ Select all – draw a box around the roto
+ On frame 70 – LMB into position
+ Zoom in on the bits that don’t match and move into position
Play it and check it!  

> # Week_5
# Chroma key
### - What is Chromakey and how does if work?
-------------------
The essentials: What is chroma key and how does it work?
One of the most-used and time-honored visual effects techniques is chroma key. Simply put, chroma key involves shooting a subject against a solid-color background, and then removing that background in post-production, replacing it with transparency. Then, the subject can be placed in front of any new background.

In other words, chroma key is a method to replace a predefined color, the socalled key color, in filmed material – and insert (digital) content such as graphs, maps and animations or combine it with material from another shot.

The most common key colors used are green and blue. Why these two colors? They are in opposite contrast to the color of the human skin.
# Explaining the chroma key effect
크로마 키는 녹색 또는 파란색 화면을 사용하거나 녹색 또는 파란색 페인트를 사용하여 얻을 수 있는 원하는 효과와 가장 관련이 있는 용어이다.
### 크로마 키 정의
크로마키 기술이란?
크로마 키 기술은 이미지에서 특정 색상을 제거하여 이미지의 해당 부분을 교체하는 프로세스이다. 색상은 단색일 수 있으며 가장 일반적으로 파란색 또는 녹색이다. Chroma keying은 이미지에서 단색을 제거하는 곳에서 사용된다.이 기술은 "키잉" 또는 "키아웃"이라고도 한다.

![image](https://i.ytimg.com/vi/r3kpyTVcc64/maxresdefault.jpg)   
(https://www.youtube.com/watch?v=r3kpyTVcc64&ab_channel=learninglab)

### 크로마 키는 어떻게 작동할까?
크로마 어려워 보일 수 있지만 실제로는 가장 풀기 쉬운 VFX 중 하나라고 한다.

- 참고 동영상
(https://www.youtube.com/watch?v=Cw3aXn1lvhM&ab_channel=%EC%98%A4%ED%95%8CTV_OPIM_VFX)

> # Week_6   
## Keying   
-'Keying'이란 비디오 편집 소프트웨어를 사용하여 포스트 프로덕션에서 그린 스크린 배경을 제거하는 프로세스이다. 녹색 화면 배경에 키가 지정되면 완전히 투명해진다. 그런 다음 투명한 영역을 다른 이미지나 비디오로 채울 수 있다.   

-Ctrl/Cmd+Shift+Alt로 사각형을 파란색 픽셀 위로 드래그하여 이미지에서 직접 화면 색상을 선택한다. 
선택한 픽셀의 평균값이 사용된다.   

 ![image](https://assets.rocketstock.com/uploads/Color-Key-Featured-Image-1000x576.jpg) 
### Tip
1. 색상을 샘플링할 때 Alt를 누르면 Nuke는 사용자가 보고 있는 것과 관계없이 항상 소스 이미지를 샘플링한다. 즉, 매트 상태나 합성상태에서도 블루 스크린 색상을 선택할 수 있다.

2. 뷰어에서 Ctrl/Cmd+마우스 오른쪽 버튼을 클릭하여 샘플링된 픽셀을 버릴 수 있다.

3. 최상의 결과를 도출하려면 화면의 다른 부분에서 선택하는 것이 좋다.

4. ScreenColor를 선택하면 배경 위에 전경을 합성하는 데 사용되는 스크린 매트가 생성된다.
또한 ScreenBalance를 설정하고(아직 수동으로 설정하지 않은 경우) 전경을 despill한다.   

> # Week_7   
## Tracking
-----------
Tracking은 비디오 영상에서 특정 대상의 위치 변화를 추적하는 것이다.

Tracking은 포인트들을 파악하는 것이 중요하다.
밝고 어두운 부분이 확실하게 대비되는 반점, 가장자리 모서리 부분들이 포인트가 될 수 있다.
그렇게 Tracking을 해주면 포인트들이 트랙들을 분석하여 2D나 3D공간을 재현해 낼 수 있다.

### Tracking하는 방법 요약정리.   
-------------
 ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FSL9IA%2FbtqFJqTqUxF%2FpTUV5Snoa1S8gKjhVRVNo1%2Fimg.png)

1. Tracker를 불러와 add track을 해서 기준이 될 수 있는 부분에 놓는다.   

 ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbqmMYl%2FbtqFOYJy4u0%2Fe5Tsu3aWKaFjSQJaq45dk1%2Fimg.png)

2. 위 재생버튼을 눌러 트래킹을 해준다.

 ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbv897F%2FbtqFRBNbcKo%2FgAgeyVQ2PBp6cncZ2Rc541%2Fimg.png)

3. 사용할 프레임에 Roto를 만들고 control 누른 상태로 traker의 translate부분을 클릭 드레그 하여 roto의 tramlate에 드롭해준다.   


### Denoise
-------------
노이즈 제거 노드이다. 이 노드는 Footage에서 노이즈 또는 그레인을 제거하는데 효율적이다.
이미지 품질을 잃지 않고 노이즈를 제거할 수 있다.
 ![image](https://www.tombolphoto.com/wp-content/uploads/schden.jpg)

### Spill
-----------
녹색 화면에서 피사체로 다시 반사되는 빛이다. 녹색 화면이 밝게 켜져 있을 때 빛은 실제로 해당 색상을 피사체에 다시 반사할 수 있다.

# Week_9

## Matte Painting
---------------------
Matte Painting은 디지털 또는 전통적인 페인팅으로 영화 제작을 위한 가상 또는 사실적인 세트를 만드는 것이다. 카메라가 담을 수 없는 가상 공간을 만들 수 있다. 

1800년대에 등장했으며 영화 전체가 촬영된 후 검은색으로 칠해진 유리 스크린에 배경 요소를 통합하는 방식으로 이루어졌다.
현대 디지털 매트 페인팅은 2D 페인팅을 만들기 위해 photoshop및 clip studio Paint와 같은 소프트웨어가 일반적으로 사용된다. Maya 및 3ds Max는 일반적으로 3D 프로젝트에 사용되며 Nuke는 합성 프로세스에 사용된다. 

### Matte painting tutorial (Tips)
 [Youtube_Matte Painting Tutorial](https://www.youtube.com/watch?v=1EU7Om5utlM)

# Week_10
