# Zynq Embedded Performance Labs
Embedded system and performance optimization labs using Xilinx Zynq-based Zybo board

Xilinx Zynq 기반 Zybo 보드를 활용하여 임베디드 시스템의 I/O 제어부터 메모리 및 연산 성능 최적화까지 단계적으로 실습했습니다. GPIO를 통해 Push Button, DIP Switch, LED를 제어하고 AXI 기반 하드웨어 구조와 Memory-Mapped I/O의 동작을 이해하였습니다. 이후 행렬 곱셈에 Loop Tiling을 적용하여 Cache 설정과 Tile Size에 따른 실행 시간 변화를 비교하였습니다. 마지막으로 DFT/FFT를 C 및 Assembly로 구현하고 Compiler Optimization과 Data Cache 설정에 따른 성능 차이를 분석하였습니다. 이를 통해 하드웨어와 소프트웨어의 상호작용이 전체 시스템 성능에 미치는 영향을 실습 중심으로 학습하였습니다.

# 🛠️ 1. GPIO & I/O Peripheral Control
Zybo 보드의 Push Button, DIP Switch, LED 등의 On-board I/O Peripheral을 C 프로그램에서 제어하는 실험입니다. Vivado의 Block Design을 통해 Zynq Processing System과 AXI Interconnect, AXI GPIO의 연결 구조를 확인하고, XGpio API를 이용하여 Memory-Mapped I/O 방식으로 입력과 출력을 제어하였습니다. 실습에서는 기본 gpiotest.c를 수정하여 Stopwatch 형태의 상태 기반 프로그램을 구현했습니다. Push Button 입력에 따라 RUN, STOP/RESUME, RECORD, DISPLAY, RESET 상태가 전환되고, 측정된 값은 LED 및 UART 출력으로 확인하도록 구성되어 있습니다.
<img width="1000" height="600" alt="image" src="https://github.com/user-attachments/assets/037d25f4-8a11-4378-9205-385ba09fd542" />

# 🛠️ 2. Cache Optimization & Loop Tiling
행렬 곱셈 프로그램을 이용하여 Cache와 Loop Tiling이 프로그램 실행 성능에 미치는 영향을 분석하는 실험입니다. 먼저 일반적인 행렬 곱셈을 수행하는 mat_mul()과 Tile 단위로 행렬을 처리하는 mat_mul_tiling()을 직접 구현하고 두 결과가 동일한지 검증했습니다. 이후 Tile Size를 변경하면서 실행 시간을 측정하고, L1 Data Cache를 Enabled/Disabled한 경우를 각각 비교하였습니다. 평가 조건에서는 컴파일러 최적화 -O2를 사용하고, Tiling 미적용 및 Tile Size 2, 4, 8, 16, 32에 대해 각각 10회 실행 후 평균 실행 시간을 측정하여 Cache와 데이터 접근 지역성의 관계를 분석했습니다. 이를 통해 메모리 접근 패턴이 CPU 성능에 어떤 영향을 주는지 알 수 있었다.

# 🛠️ 3. FFT Implementation & Optimization
DFT와 FFT 알고리즘을 구현하고 C 및 Assembly 수준에서 실행 성능을 최적화하는 실험입니다. FFT는 OFDM과 같은 통신 시스템에서 시간 영역 신호를 주파수 영역으로 변환하는 핵심 연산이며, 일반 DFT는 N^2개의 곱셈이 필요한 반면 FFT는 중간 연산을 재사용하여 계산량을 크게 줄이는 구조를 사용합니다. 실습에서는 먼저 C로 DFT를 구현하고 프로그램을 실행·디버깅한 뒤, FFT를 C 구현과 Assembly 구현으로 최적화했습니다. 또한 Compiler Optimization Level과 Data Cache 설정을 변경하면서 세 가지 FFT 구현의 normalized execution time을 비교하고, 생성된 Assembly Code를 분석하여 성능 향상의 원인을 확인했습니다.
