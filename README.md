# 대학생 학업 중단 / 졸업 예측

## :alarm_clock: 개발 기간: 2024년 2월 1일(목) ~ 2024년 3월 6일(수)
## 개발환경:
|IDE|프로그래밍<br/>언어|
|------|---|
|![Coalb](https://img.shields.io/badge/Colab-F9AB00?style=for-the-badge&logo=googlecolab&color=525252)|![PYTHON](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)|

## :people_holding_hands: 멤버구성 및 역할
천진원(조장)

김민근, 주현수, 허영민

: 전체 과정 함께 진행

## :bulb: 기획 선정 및 배경
한국교육개발원의 고교 졸업자의 대학진학률 현황 분석에 따르면 2021년 기준 한국의 대학 진학률은 등록자 기준 73.7%이고, 각 나이대별 취학률 또한 OECD 평균 보다 높은 수치를 기록하고 있습니다.

그러나 현실적으로는 다양한 요인으로 인해 학업을 중단하는 경우가 있습니다. 한국교육개발원의 학업 중단율 분석에 따르면 2021년 기준 전문대학과 대학을 포함한 학업 중단율은 13%에 달하는 높은 수치를 기록하고 있습니다.

이러한 학업 중단 현상은 개인의 미래를 저해하고 국가 차원의 중요한 고급 인력을 잃는 결과를 초래할 수 있습니다. 따라서 이를 해결하고 예방하기 위해 학업 중단의 원인 분석 및 예측 조기 대응 시스템을 마련하는 것이 필요합니다.

그러므로 저희는 학업 중단의 원인을 다각도로 분석하고, 예측 모델을 설계해 학생들의 학업 중단을 최소화하고, 국가 발전을 위한 고급 인력을 유지할 수 있는 방안을 모색하기 위해 해당 주제를 선정했습니다.

## :robot: 모델 개발
> ### EDA
1. Json 파일을 DataFrame으로 변환 후 각종 정보를 확인했습니다.

각 이미지 데이터의 라벨링, 나이, 성별, 배경정보, Bounding Box 정보 등 각종 정보가 처리되어 있습니다.
![image](https://github.com/DPTure/Team5/assets/155731578/3a5cbfc6-8756-4f12-a58d-1ef9186dd7bf)

2. 기초 통계 정보를 확인했습니다.

3. 간단한 시각화를 통해 데이터의 분포를 확인했습니다. 감정에 대한 데이터 불균형은 존재하지 않습니다.
![image](https://github.com/DPTure/Team5/assets/155731578/695528c1-6612-4e9c-83d9-92f7e9ab0669)
![image](https://github.com/DPTure/Team5/assets/155731578/80930595-dadf-401e-a41a-486d11f59671)
![image](https://github.com/DPTure/Team5/assets/155731578/463d0ce4-4755-4953-adb3-fe37ae62503b)
![image](https://github.com/DPTure/Team5/assets/155731578/a30529cf-c8e3-406f-8069-e866085fec4a)
![image](https://github.com/DPTure/Team5/assets/155731578/984407c3-a7ea-4f16-bb7c-d51094314ade)


> ### Preprocessing
1. 사진 데이터 crop & crop+seg 작업을 진행했습니다.

crop


![image](https://github.com/DPTure/Team5/assets/155731578/3350fccc-2835-42a8-b102-d6a2d609bb3a)


crop & seg


![image](https://github.com/DPTure/Team5/assets/155731578/7ec94f04-92f7-486a-89d3-4d68ca533953)


2. array 변환, 차원 추가 및 resize 전처리 작업을 수행했습니다.

> ### Modeling & Model ensemble

ConvNeXt, ResNet v2, DenseNet, MobileNet v2/v3, Inception v3, BEIT, SWIN, YOLO v8 모델을 돌려보고 loss 및 acc를 측정하였고,
모델 앙상블을 진행했습니다.

모든 모델들의 loss와 acc를 측정한 결과, 단일 모델인 BEIT가 loss 0.5846, acc 87.33%로 가장 높은 성능을 보였습니다. 따라서 BEIT를 감정 분석 모델로 선정했습니다.
> ### Prerequisites

Before using the library or REST API, you must sign up on the suno.ai website and obtain your cookie as shown in this screenshot.
You can find cookie from the Web Browser's Developer Tools -> Network Tab -> Filter: _clerk_js_version

Music Face에서 사용되는 모델의 경우 용량이 큰 관계로 구글 드라이브 링크를 첨부해드립니다. Submission/Models 폴더 내에 있는 best_model.pt, swinv2_ages.pt, swinv2_gender.pt 파일을 다운받아 이용해주세요.

[Google Drive](https://drive.google.com/drive/u/0/folders/1BNF7E2JYfD7p42UU6ymU-nXpWdB1cFyD)

![prerequisites](https://github.com/Jinwonie/music_face/assets/155731578/20586ae8-c1d7-434e-be6e-6e5bf57b8b0f)

> ### Input your cookie 
```
cookies='Your Cookie'
```

> ### 기타
이 비공식 API는 Suno AI 서비스와 상호 작용하는 편리한 방법을 제공하지만 생성된 음악에 대한 소유권이나 권리를 주장하지 않습니다. 플랫폼을 사용할 때 Suno AI의 서비스 약관을 존중하십시오.
