# Hyundai NGV Simulation Model Customization 2026

이 저장소는 Hyundai NGV Smart Factory Track의 **제조물류 시뮬레이션 모델 커스터마이징** 수업 보조 자료입니다. 수업은 이산사건 시뮬레이션(DES)의 기본 구조를 이해하고, Python과 SimPy로 이벤트 중심 모델을 구현한 뒤, 현장 데이터에서 도착/서비스 시간 분포를 추정해 모델에 반영하는 흐름으로 구성됩니다. 이후 시뮬레이션 결과를 KPI로 정리하고 시각화하며, 스케줄링 규칙이나 병목 처리 로직을 바꾸어 제조/물류 프로세스 개선안을 비교하는 데 초점을 둡니다.

## Notebook Summary

### `input_modeling_output_analysis.ipynb`

실제 또는 예제 데이터를 불러와 기초 통계량, 히스토그램, 경험적 CDF를 확인하고 여러 확률분포를 적합하는 입력 모델링 노트북입니다. AIC/BIC, KS 통계량, Q-Q plot 등을 통해 후보 분포를 비교하고, 선택한 분포가 시뮬레이션 입력으로 어떻게 쓰일 수 있는지 보여줍니다. 뒤쪽에서는 독립 반복 신뢰구간, sequential replication rule, paired comparison, SMORE plot처럼 시뮬레이션 출력 분석에 필요한 통계 절차도 함께 다룹니다.

### `plotting_metric_analysis.ipynb`

단순 작업 처리 시스템의 예시 시뮬레이션 결과를 만들고, Throughput, WIP, Lead Time, 납기 준수율, Tardiness 같은 주요 운영 KPI를 계산/시각화하는 노트북입니다. 제품군별 요약표, 시간 구간별 처리량, WIP 추이, Lead Time 분포, 납기 초과 작업 분석, Little's Law 점검 등을 통해 시뮬레이션 결과를 의사결정용 지표로 바꾸는 방법을 보여줍니다. 마지막에는 다중 replication 결과를 요약해 평균과 신뢰구간 기반으로 KPI를 해석하는 흐름까지 포함합니다.

### `jobshop_scheduling_rule_simulation.ipynb`

A/B/C 타입의 job이 M1, M2, M3 기계를 서로 다른 순서로 거치는 stochastic job shop을 SimPy로 구현한 노트북입니다. 같은 난수 시나리오를 FCFS, SPT, LPT, EDD, RANDOM 같은 스케줄링 규칙에 공통 적용하여 공정하게 비교하고, 단일 실행의 event log와 Gantt chart로 모델 동작을 확인합니다. 반복실험을 통해 makespan, throughput, flow time, waiting time, tardiness, machine utilization 등을 평균/표준편차/신뢰구간으로 비교하며 병목과 우선순위 규칙의 영향을 해석합니다.

## Files

- `input_modeling_output_analysis.ipynb`: 입력 데이터 분포 적합과 시뮬레이션 출력 통계 분석
- `plotting_metric_analysis.ipynb`: 시뮬레이션 KPI 계산, 시각화, 대시보드식 결과 해석
- `jobshop_scheduling_rule_simulation.ipynb`: job shop DES 모델 구현과 스케줄링 규칙 비교 실습
