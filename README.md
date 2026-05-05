# 🛠️ 베어링 불량 예측 및 품질 검수 시스템 (AI Bearing QC System)

[cite_start]고속 자동화 라인에 즉시 투입 가능한 **실시간 베어링 객체 탐지 및 다단계(2-Stage) 결함 분석 시스템**입니다. [cite: 4] [cite_start]단순한 모델 학습을 넘어, 금속 광택 및 배경 노이즈 등 실제 제조 현장에서 발생하는 기술적 과제를 소프트웨어적으로 해결하는 데 집중했습니다. [cite: 13, 25]

## 📌 프로젝트 개요
- [cite_start]**배경**: 실물 테스트가 용이한 베어링을 대상으로 전환하여 데이터 부족 문제 해결 및 실무 적용성 강화 [cite: 3]
- [cite_start]**목적**: 실시간 객체 탐지 및 정밀 결함 분류 파이프라인 구축 [cite: 4]
- **핵심 성과**: 
  - [cite_start]OpenCV CLAHE 전처리를 통한 미세 균열 선명도 확보 [cite: 13]
  - [cite_start]원형도(Circularity) 검증 로직을 통한 비정형 오탐체 필터링 [cite: 13]
  - [cite_start]라벨링 없는 배경 학습을 통한 오탐율 감소 [cite: 26]

## ⚙️ 기술 스택 및 환경
| 구분 | 상세 내용 |
| :--- | :--- |
| **AI 모델** | [cite_start]YOLOv8n (탐지용), YOLOv8s (결함 분류용) [cite: 6] |
| **전처리/로직** | [cite_start]OpenCV (CLAHE), 원형도 검증 알고리즘 [cite: 13] |
| **연산 장치** | [cite_start]Tesla T4 GPU (학습), 로이체 웹캠 (테스트) [cite: 6] |
| **데이터 규모** | [cite_start]결함 이미지 301장 (659개 객체) 등 [cite: 6] |

## 📊 성능 분석
### 주요 결함별 판별 능력 (mAP50)
- [cite_start]**공식/구멍 (Pitted Surface)**: 0.941 (최상) [cite: 19]
- [cite_start]**패치/얼룩 (Patches)**: 0.905 (우수) [cite: 20]
- [cite_start]**이물질 혼입 (Inclusion)**: 0.637 [cite: 21]
- [cite_start]**미세 균열 (Crazing)**: 0.214 (웹캠 사양 한계) [cite: 22]

### 환경별 테스트 결과
- [cite_start]**표준 환경 (흰색 배경)**: 정확도 약 **95% 이상** [cite: 16]
- [cite_start]**저조도/어두운 배경**: 정확도 약 50~60% (대비 저하로 인한 인식 저하) [cite: 17]

## 💡 주요 해결 과제 (Troubleshooting)
- [cite_start]**금속 광택 및 반사**: OpenCV CLAHE 전처리 적용으로 해결 [cite: 13]
- [cite_start]**경계선 오차**: DFL(Distribution Focal Loss) 분석 및 적용으로 박스 밀착도 향상 [cite: 11, 13]
- [cite_start]**배경 노이즈**: 2-Stage 파이프라인 구조화를 통해 오탐지 대폭 감소 [cite: 13]

## 📝 결론
[cite_start]본 프로젝트를 통해 **"코드뿐만 아니라 테스트 환경의 표준화가 AI 성능을 완성한다"**는 점을 체득했습니다. [cite: 27] [cite_start]향후 고성능 검수를 위해 물리적 조명 환경(돔 조명 등) 보완이 필요함을 확인했습니다. [cite: 25]
