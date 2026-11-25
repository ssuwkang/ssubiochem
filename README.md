# ssubiochem
This repository contains coursework, lecture notes, problem sets, and laboratory materials for an undergraduate student in the Department of Chemistry at Soongsil University.

# 🧬 Boltz-2 원클릭 단백질 구조 및 결합 친화도 예측기 (`Boltz-2.ipynb`)

숭실대학교 화학과 실습 및 구조생물학 학습용으로 구성된 **Boltz-2** Google Colab 노트북입니다.  
단백질(단일 또는 복합체) 서열과 저분자 리간드 SMILES를 입력하면 구조 예측과 결합 친화도(Affinity) 추정, 3D 구조 시각화, 결과 ZIP 압축/다운로드까지 한 번에 실행합니다.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ssuwkang/ssubiochem/blob/main/Boltz-2.ipynb)

---

## 📌 주요 기능

1. **원클릭 환경 점검 및 자동 설치:** GPU 연결 상태를 확인하고 `boltz[cuda]`, `py3Dmol`, `pyyaml` 설치 여부를 자동으로 확인·설치합니다.
2. **YAML 입력 자동 생성:** 단백질 서열(`:` 구분자로 다중 사슬 지원, 최대 26개 엔티티)과 리간드 SMILES를 바탕으로 Boltz-2 입력 YAML을 자동 생성합니다.
3. **구조 및 결합 친화도 예측:** `--use_msa_server`와 `--use_potentials` 옵션을 적용해 구조 예측을 수행하고 신뢰도 지표(`pTM`, `ipTM`, `Complex pLDDT`)와 결합 예측치(`Binding Probability`, `log10(IC50)`, `pIC50`, 근사 `ΔG`)를 출력합니다.
4. **3D 시각화 및 결과 저장:** 예측된 1순위 `.cif` 구조를 `py3Dmol`로 시각화하며, 선택 시 전체 결과 폴더를 `.zip`으로 묶어 다운로드합니다.

---

## 🚀 실행 방법

1. 위 **Open In Colab** 배지를 눌러 노트북을 엽니다.
2. Colab 상단 메뉴에서 **[런타임] → [런타임 유형 변경]**을 열고 하드웨어 가속기를 **T4 GPU**로 설정합니다.
3. 노트북 폼에서 아래 항목을 입력하거나 기본 예시(`EGFR.Lazertinib`)를 확인합니다.
   * `jobname`: 작업 폴더 및 출력 파일 이름 접두사
   * `protein_sequences`: 단백질 아미노산 서열 (복합체는 `:` 기호로 사슬 구분)
   * `ligand_smiles`: 저분자 리간드 SMILES (선택 사항; 비워두면 단백질 구조만 예측)
   * `predict_affinity`: 리간드 입력 시 결합 친화도 예측 포함 여부 (`True` / `False`)
   * `auto_download`: 예측 완료 후 `<jobname>_boltz2_results.zip` 자동 다운로드 여부
4. 셀 좌측의 **재생 버튼(`▶`)**을 클릭해 실행합니다.

> **소요 시간 안내:** 패키지 설치 및 약 6 GB 모델 가중치 다운로드는 런타임당 최초 1회 진행되며, 서열 길이에 따라 전체 실행에 수 분에서 10분 이상 걸릴 수 있습니다. 긴 서열이나 복합체에서 GPU 메모리(VRAM) 부족 오류가 발생하면 도메인 단위로 서열을 나누어 테스트해 보세요.

---

## ⚠️ 해석 및 활용 시 주의사항

* **계산적 추정치:** 결합 확률 및 친화도(`log10(IC50)`, `pIC50`, 근사 `ΔG`)는 AI 모델 기반 예측치이며, 실제 생화학·구조생물학 실험 결과를 대체하지 않습니다.
* **교육·연구 목적 활용:** 본 노트북과 저장소 자료는 수업 및 학술·연구 학습 목적으로 제공됩니다. 외부 MSA 서버 조회 및 모델 가중치 다운로드 시 해당 서비스와 원본 도구의 이용 조건을 따릅니다.
* **출처 표기:** Boltz-2를 활용한 분석 결과를 과제·발표·연구에 활용할 경우 Boltz-2 공식 저장소 및 관련 문헌을 함께 인용해 주세요.

---

## 📄 라이선스

본 저장소의 노트북 및 실습 안내 자료는 저장소에 명시된 라이선스(예: MIT License)를 따르며, 포함된 오픈소스 소프트웨어(`Boltz-2`, `py3Dmol`, `PyYAML` 등)는 각 프로젝트의 라이선스를 따릅니다.
