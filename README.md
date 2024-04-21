# Malware Checker

<p align="center"><img src="https://github.com/kookmin-sw/capstone-2023-21/assets/39542937/e2ebce95-c45d-4d75-a38d-2c42cf9a38ca"></p>  

**악성 파일 여부** 및 **파일 정보**를 알려주는 웹 서비스  
**Github Page** : [https://kookmin-sw.github.io/capstone-2023-21/](https://kookmin-sw.github.io/capstone-2023-21/)

## 📖 프로젝트 소개

우리는 현재 디지털 시대를 살고 있으며, 인터넷과 컴퓨터를 사용하는 일상생활이 빈번하게 일어나고 있습니다. 그러나 인터넷 상에서 다운로드 받거나 받은 파일을 실행하다 보면 악성코드에 감염될 가능성이 있습니다.

이에 대비하여, 사용자들이 소유한 파일이 악성코드인지 아닌지를 쉽게 확인할 수 있도록 도와주는 웹 서비스를 개발하려고 합니다.

---

## 📝 프로젝트에 기여한 부분
- Spring을 활용하여 Front & Back-End의 설계 및 구축
  - Frontend 의 기본적인 틀 제공
  - Backend 의 전체적인 설계 및 구현
    - API 작업 ( 파일 업로드 및 전처리 API, DB 관리 Etc) 
  - 데이터 베이스 관리
    - Mysql을 활용한 데이터 베이스 관리 
    - Mybatis, JDBC, JPA, Hibernate를 사용하여 구현
       
- Deep Learning을 활용한 악성 파일 탐지 모델 구현
  - 파일의 바이너리 값을 이미지화
  - 이미지 인식 모델로 악성 파일 분류
  - 패킹 탐지 기술과 접목하여 정확도 향상

---

## 🔧 주요 기술

<p align="center"><img src="https://github.com/kookmin-sw/capstone-2023-21/assets/39542937/3dab7f3a-cf5b-4200-adbc-e1109c1e06b6"></p>

### 1. **패킹 파일 탐지**

악성 파일들의 대부분은 탐지 회피 및 효율적인 배포를 위해 파일을 패킹되어 있고 패킹이 되어 있다면 파일의 데이터를 올바른 값으로 읽어 들일 수 없기 때문에 파일의 패킹 유무를 확인해야합니다.

<p align="center"><img src="https://github.com/kookmin-sw/capstone-2023-21/assets/39542937/b16bf5ed-1fee-451f-b41b-48960dd4a4c6"></p>

패킹 탐지 기술은 **진입점 섹션**의 패킹의 필수적인 특징인 **'write'속성**과 **엔트로피 통계**를 이용하여 구현하였습니다.

</br>

### 2. **악성코드 탐지 및 분류**

CNN 딥러닝을 사용하여 악성 파일을 검사하였습니다. 학습 데이터 셋으로는 Kaggle의 Microsoft Malware Classification Challenge (BIG 2015)의 데이터를 사용하였습니다. 데이터의 내용은 PE파일에서 header를 제외하고, 파일의 바이너리 값을 16진수로 변환하였습니다. 각 악성 파일마다 레이블이 매겨져 있으며 레이블은 총 9개의 악성 파일 클래스로 나뉘어져 있습니다.


|       Name       |         Type       |
| :--------------: | :----------------: |
|     `Ramnit`     |           Worm        |
|    `Lollipop`    |          Adware       |
|  `Kelihos_ver3`  |         Backdoor      |
|     `Vundo`      |           Trojan       |
|     `Simda`      |          Backdoor      |
|     `Tracur`     |     Trojan Downloader  |
|  `Kelihos_ver1`  |         Backdoor      |
| `Obfuscator.ACY` |   Obfuscated malware |
|     `Gatak`      |        Backdoor      |


</br>


**PE 파일 분석에서 CNN을 적용한 이유**
- 파일은 헤더, 코드 섹션, 데이터 섹션 등과 같이 여러 구성 요소로 이루어진 바이너리 데이터의 파일입니다. 이러한 구성 요소는 하나의 이미지로 볼 수 있습니다.
- PE 파일을 이미지로 변환하고, CNN 모델을 통해 각각의 이미지를 분류하고 분석할 수 있습니다.
- CNN을 사용하여 PE 파일을 분석하면, 이미지 처리와 마찬가지로 지역성과 통계적 균일성을 활용하여 PE 파일의 특징을 추출하고 분류하는 데 효과적입니다.

</br>

### **시스템 흐름도**

<p align="center"><img src="https://github.com/kookmin-sw/capstone-2023-21/assets/39542937/7b7ba380-9cd9-4057-9e49-520db13ce00d"></p>


---

## 💻 웹 페이지 구성

|Main Page|Upload Page|Receive Page|
|:-:|:-:|:-:|
|![image](https://github.com/kookmin-sw/capstone-2023-21/assets/39542937/f66b3399-7134-4283-9a7d-d46f089d19fa)|![image (2)](https://github.com/kookmin-sw/capstone-2023-21/assets/39542937/00360df0-9dbe-4c4b-b392-f527ed47fb0c)|![image (1)](https://github.com/kookmin-sw/capstone-2023-21/assets/39542937/06a07347-377f-4d97-a693-3796d9dc25f1)|

---

## 👍 기대효과

1. 직관적으로 파일 분석 결과 확인 가능
2. 다른 종류의 악성코드 데이터를 추가 학습하여 성장 가능

---

## 👫 팀 소개

팀 : 21조 (kookmin-sw/capstone-2023-21)

직급 | 이름 | 학번 | 메일 | 역할 |
---|---|---|---|---|
팀장 | 유남규 | ****2842 | 20152842@kookmin.ac.kr | AI, Malware detection
팀원 | 김용호 | ****1588 | dydgh0608@kookmin.ac.kr | Frontend, Backend, PE file analyze

---


