---
layout: post
title: 데이터 통신 2015 - 기말
date: 2018-06-12 +0300
img: learn.jpg
category: data_communication
tags: [데이터통신, CSMA]
---

## 1. 다음 용어에 관하여, 최대한 알기 쉽고 자세하게 기술하라.
### 가) FCS :
데이터를 전송할 때 에러를 검출하기 위한 방법 중 CRC 기법이 있는데, 보낼 k개의 데이터 블럭 비트 뒤에 k 데이터 블럭과 Gernerate divisor 비트 값으로 나눠 만들어지는 FCS(Frame Check Sequence)라는 에러 검사를 위한 r개의 비트를 붙인다. 그래서 총 보내는 데이터는 k + r이 된다.<br/>
<br/>
### 나) PAP   in PPP:
PPP(Point to Point Protocol)은 두 컴퓨터 사이의 통신을 담당하는 프로토콜이다.
PPP에는 보안을 위해 PAP와 CHAP 2가지 프로토콜이 있다.
그 중 PAP는 가장 간편하면서도 일반적인 패스워드 확인법이다.
암호화 되지않는 비밀번호를 네트워크 상으로 전달해 안전하지 않다.
2 way handshake 방식으로 클라이언트가 사용자 이름과 비번을 전송하면, 서버가 인증 ack/nack을 보낸다.
<br/>
<br/>
### 다) USN:
Ubiquitous Sensor Network의 줄임말로 어디에나 있는 센서 네트워크란 뜻이다. 사물의 인식 정보나 주위의 환경 정보 등을 탐지하는 센서들끼리의 통신을 하기 위해 구성된 네트워크이다.
<br/>
<br/>
### 라) Authentication 과 encryption:
Authentication: 특정한 개인 정보나 제 3자는 읽을 수 없는 데이터를 접근할 때 자신이 허가된 자라고 인증하는 것
encryption: 인증된 자를 제외하고 제 3자는 읽을 수 없도록 평문을 부호화하여 암호문으로 만드는 것.

_ _ _

<br/>
## 2. Consider the delay of pure ALOHA versus slotted ALOHA at low load. Which one is less? Explain your answer.
pure ALOHA는 스테이션이 준비되는 즉시 데이터 프레임을 보내고 충돌하면 패킷을 모두 무시하고 일정시간 후에 재전송하는 방식이고,
slotted ALOHA는 시간을 slot 단위로 나눠 각 스테이션이 그 slot에 맞춰 전송하는 방식이다.
그래서 pure ALOHA는 바로 보내는 데에 반해 slotted ALOHA는 프레임 전송이 모두 끝나도 slot이 끝날때까지 대기해 delay가 더 길다.

_ _ _

<br/>

## 3. Imgae that PC1 sends an Ethernet frame to PC2, but PC3 and PC4 also get a copy of the frame. How does PC3 know to ignore the data in the frame?

ethernet FramePC1이 보내는 프레임을 PC2, PC3, PC4가 브로드캐스트로 모두 받게된다.
PC1이 보낸 프레임에는 Destination address가 적혀있는데, 누구한테 이 프레임이 전달되어야하는지를 알려준다.
PC2, PC3, PC4는 PC1의 프레임을 받으면 먼저 Destination address를 검사해 자신의 MAC 과 Destination address가 맞는지 확인하고 다르다면 프레임을 모두 폐기한다.

_ _ _

<br/>

## 4. IEEE 802.11 wireless LAN에서 CSMA/CA 기반의 DCF 모드에서 멀티미디어 데이터를 실시간으로 전송할 때의 문제점에 관하여 알기 쉽고 자세하게 기술하라.
DCF 방식은 항상 전송 시작 전에 각 스테이션은 매체가 사용중인지 알아보고, 사용중이면 충돌 회피를 하기 위해 (정해진 시간+난수값)만큼 전송을 연기한다. 무선 매체가 사용중이면 점차 그 간격을 늘려가며 재시도한다.
실시간 전송은 정해진 시간안에 꼭 데이터가 보내져야하기 때문에 난수값만큼 지연되는 DCF 방식에서는 불가능하다.