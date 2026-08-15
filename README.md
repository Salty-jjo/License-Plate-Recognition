# 🚗 License Plate Recognition

CCTV 영상에서 차량과 번호판을 인식하고, 추출된 차량 번호를 데이터베이스와 비교하여 **도난 차량을 탐지하는 시스템**입니다.

대학교 프로젝트로 진행했으며, Computer Vision 기반 객체 탐지부터 OCR을 통한 문자 인식, Database 연동까지 하나의 파이프라인으로 구현했습니다.

## 📌 Project Overview

CCTV 영상에서 차량 정보를 사람이 직접 확인해야 하는 기존 방식의 불편함을 개선하기 위해 시작한 프로젝트입니다.

전체 처리 과정은 다음과 같습니다.

**CCTV Video → Vehicle Detection → License Plate Detection → OCR → Database Search**

1. CCTV 영상 입력
2. YOLOv3를 이용한 차량 객체 탐지
3. OpenCV를 이용한 차량 및 번호판 영역 이미지 처리
4. Tesseract OCR을 이용한 차량 번호 문자 추출
5. 인식된 차량 번호를 Database에서 검색
6. 도난 차량 여부 확인 및 결과 출력

## 🛠 Tech Stack

### Language

* Python

### Computer Vision

* OpenCV
* YOLOv3

### OCR

* Tesseract OCR

### Database / Cloud

* MySQL
* AWS RDS

## 🔍 Implementation

### 1. Vehicle Detection

YOLOv3를 이용하여 CCTV 영상에서 차량 객체를 탐지했습니다.

영상 프레임을 입력받아 차량에 해당하는 객체를 검출하고, 이후 번호판 인식을 수행할 차량 영역을 추출합니다.

### 2. License Plate Detection

검출된 차량 이미지에서 번호판 영역을 찾기 위해 OpenCV 기반 이미지 처리를 수행했습니다.

번호판 후보 영역을 추출한 뒤 OCR을 수행할 수 있도록 이미지 전처리를 진행했습니다.

### 3. License Plate Recognition

추출된 번호판 이미지에 **Tesseract OCR**을 적용하여 차량 번호를 문자열 데이터로 변환했습니다.

이미지 형태의 정보를 실제 검색 가능한 데이터로 변환하여 이후 Database 조회에 사용할 수 있도록 구현했습니다.

### 4. Stolen Vehicle Search

차량 및 도난차량 정보를 관리하기 위해 **AWS RDS에 MySQL Database를 구축**했습니다.

OCR을 통해 인식한 차량 번호를 Database의 도난차량 정보와 비교하여 일치 여부를 확인하고, 검색 결과를 프로그램에서 확인할 수 있도록 구현했습니다.

## 💡 What I Learned

이 프로젝트를 통해 이미지 데이터가 실제 서비스에서 활용되기까지의 전체 과정을 경험했습니다.

* OpenCV를 활용한 이미지 전처리
* YOLOv3 기반 Object Detection
* Tesseract를 활용한 OCR
* Python과 MySQL Database 연동
* AWS RDS를 활용한 Database 구축
* Computer Vision 결과를 실제 서비스 로직과 연결하는 과정

단순히 AI 모델을 실행하는 것에 그치지 않고,

**영상 데이터 → 객체 탐지 → 이미지 처리 → 문자 데이터 추출 → Database 조회**

과정을 하나의 시스템으로 연결해 보았다는 점에서 의미가 있었던 프로젝트입니다.

## 📚 Project Information

* University Project
* Topic: CCTV-based Stolen Vehicle Detection
* Role: Development
