![image](https://github.com/user-attachments/assets/428aed66-f78c-438a-93ad-875fb8eb5a4c)# [STM32] 세탁기 구현

## 프로젝트 소개

**1. 수행기간 : 2023. 09.13 ~ 2023. 10.13 **

**2. 수행목표 : NonOS 상태에서 타이머를 활용한 동시성 확보 **
  
**3. 개발보드 : STM32(STM32F429ZI)  **

**4. 개발언어 : C  **

**5. Tools n Peripheral
- GPIO (LED)
- Interrupt (Button, 초음파센서)
- One-wire 통신 (온습도 센서)
- I2C (LCD)
- PWM 제어 (모터 드라이버, Buzzer)
- PWM을 활용하여 밝기 조절 (FND)

## 동작 사양
![image](https://github.com/user-attachments/assets/5ffc61c5-bc7f-4926-956b-727b04119ef4)

![image](https://github.com/user-attachments/assets/14bf5e6b-7f0f-4d87-bd5e-8fb0e26d08db)

동작 사양 설명

  1. Control
   : [선택, 상, 하, 좌, 우] 버튼을 통한 Display 조작

  2. Display
Mode Select : 세탁, 헹굼, 탈수 모드 선택가능
Mode Select이 완료 되면, Mode에 대한 시간 설정
시간 설정 완료 후 Total Running Time을 Display하며 세탁, 행군, 탈수 동작을 순차적으로 진행

  3. 부가 기능
온습도센서를 통해 세탁기 내부 습도를 감지하여 세탁기 문 잠금(Servo Motor) 제어
Emergency Stop 버튼을 지원하여 동작 중 긴급정지 가능
Motor Driver를 통한 DC Motor 제어로 Mode 별 동작 알고리즘 분기
모든 Process가 종료 되면 Buzzer를 통해 세탁 종료 알림


## 시현 영상
[![](https://img.youtube.com/vi/lyeTFwmIuKs/0.jpg)](https://youtu.be/lyeTFwmIuKs?t=0s)

<br>


## 설계 과정
### 데이터 시트 기반 Clock Configure
![image](https://github.com/user-attachments/assets/7745b4f7-67c7-4f79-87ae-e7375e31e378)

![image](https://github.com/user-attachments/assets/24602ecd-061e-4d77-ba5a-2d272f9c9d80)

### FND 클럭 동기화 / 레지스터 제어
![image](https://github.com/user-attachments/assets/850686ae-5a76-419d-8c7e-e47b9f342bfb)

![image](https://github.com/user-attachments/assets/a286d7ed-17e5-44a4-ab83-9891efb62faf)

#### Sample code
![image](https://github.com/user-attachments/assets/3bff5cc3-f40c-4186-ae26-c1eb7d92b49e)


<br>


## 검증
### 스코프와 로직분석기를 통한 데이터 검증
![image](https://github.com/user-attachments/assets/039a4b6e-5edb-4f8f-876e-159ee6bed3dd)

![image](https://github.com/user-attachments/assets/54c102a3-eced-4ec3-aead-9c9d7e2ff5b7)


<br>
