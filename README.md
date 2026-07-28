# Zynq Embedded Performance Labs
Embedded system and performance optimization labs using Xilinx Zynq-based Zybo board

Xilinx Zynq 기반 Zybo 보드를 활용하여 임베디드 시스템의 I/O 제어부터 메모리 및 연산 성능 최적화까지 단계적으로 실습했습니다. GPIO를 통해 Push Button, DIP Switch, LED를 제어하고 AXI 기반 하드웨어 구조와 Memory-Mapped I/O의 동작을 이해하였습니다. 이후 행렬 곱셈에 Loop Tiling을 적용하여 Cache 설정과 Tile Size에 따른 실행 시간 변화를 비교하였습니다. 마지막으로 DFT/FFT를 C 및 Assembly로 구현하고 Compiler Optimization과 Data Cache 설정에 따른 성능 차이를 분석하였습니다. 이를 통해 하드웨어와 소프트웨어의 상호작용이 전체 시스템 성능에 미치는 영향을 실습 중심으로 학습하였습니다.

# 🛠️ GPIO & I/O Peripheral Control
Zybo 보드의 Push Button, DIP Switch, LED 등의 On-board I/O Peripheral을 C 프로그램에서 제어하는 실험입니다. Vivado의 Block Design을 통해 Zynq Processing System과 AXI Interconnect, AXI GPIO의 연결 구조를 확인하고, XGpio API를 이용하여 Memory-Mapped I/O 방식으로 입력과 출력을 제어하였습니다. 실습에서는 기본 gpiotest.c를 수정하여 Stopwatch 형태의 상태 기반 프로그램을 구현했습니다. Push Button 입력에 따라 RUN, STOP/RESUME, RECORD, DISPLAY, RESET 상태가 전환되고, 측정된 값은 LED 및 UART 출력으로 확인하도록 구성되어 있습니다.
<img width="1420" height="900" alt="image" src="https://github.com/user-attachments/assets/037d25f4-8a11-4378-9205-385ba09fd542" />
