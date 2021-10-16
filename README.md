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
# Croma key
### - What is Cromakey and how does if work?
-------------------
The essentials: What is chroma key and how does it work?
One of the most-used and time-honored visual effects techniques is chroma key. Simply put, chroma key involves shooting a subject against a solid-color background, and then removing that background in post-production, replacing it with transparency. Then, the subject can be placed in front of any new background.

In other words, chroma key is a method to replace a predefined color, the socalled key color, in filmed material – and insert (digital) content such as graphs, maps and animations or combine it with material from another shot.

The most common key colors used are green and blue. Why these two colors? They are in opposite contrast to the color of the human skin.
