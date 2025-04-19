# Simple Processor
간단한 프로세서 구성 요소
- 메모리: 프로그램(명령어)과 데이터를 저장장
- 레지스터 파일: 명령어는 레지스터 파일에서 피연산자를 읽고 그 결과를 레지스터 파일에 기록
- 레지스터, ALU 및 가산기
- 디코딩 및 제어 로직

## Simple(32-bit) Processor
모든 명령어가 32 bit로 인코딩 된 것으로 가정
  - (ex: 레지스터와 데이터 경로(datapath): 32비트 폭, 메모리: 32 비트로 주소 악세스, 데이터 반환)
- 프로세서에 32개의 레지스터가 있는 것으로 가정하면 특정 레지스터를 식별하는데 5비트를 사용(2^5 = 32)

<br><br><br><br>

<div style="text-align: center;">

# Processor Datapath 

</div>

## Encoding Instructions
<div style="text-align: center; font-size: 1.2em;">
    ><strong> Instruction Rd, Rs, Operand2 </strong><
</div>

(Operand 2 는 레지스터 또는 즉치값일 수 있음)
<br>

명령어를 인코딩하는데 32비트가 주어진다면 프로세서를 위한 두가지 간다한 명령어 인코딩 형식을 만들 수 있음

<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images\02-2\32bit_instruction.png" alt="32bit instruction" style="max-width: 60%; height: auto;">
</div>

## PC and Instruction Memory

<div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 20px;">

<!-- Text (Left) -->
<div style="flex: 1; min-width: 500px;">

**PC(프로그램 카운터)**: 현재 메모리에서 가져오는(fetch) 명령어의 주소를 저장

- 매 사이클마다 PC(주소)를 4(바이트)씩 증가시미켜 각 32비트 명령어를 차례로 읽음
&nbsp;&nbsp;&nbsp;(실제 동작은 다른 곳에서)
</div>

<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images\02-2\pc&instruction_memory.png" alt="pc&instruction_memory" style="max-width: 50%; height: auto;">
</div>

</div>

## Add mux to allow Jump/Branch

<div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 20px;">

<!-- Text (Left) -->
<div style="flex: 1; min-width: 500px;">

**Mux(multiplexer)**: selects one of several input signals and forwards it to a single output.

- 멀티플랙서(multiplexer)를 추가하여 브랜치 대상 주소(branch target address), 즉 가져온 브랜치 다음 PC 값을 제공할수 있도록 함

</div>

<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images\02-2\add mux.png" alt="add mux" style="max-width: 50%; height: auto;">
</div>

</div>

## Add a Register File and ALU

<div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 10px;">

<!-- Text (Left) -->
<div style="flex: 1; min-width: 500px;">

**Register File**: 연산에 필요한 데이터를 임시로 저장하고 빠르게 읽고 쓸 수 있는 고속 저장 장치
**ALU(Arithmetic Logic Unit)**: 산술 및 논리 연산을 수행하는 계산 회로

- 간단한 ALU 연산 시퀀스를 실행할 수 있다. 하지만 아직 데이터 메모리에 엑세스할 수 없고 분기할 수 없다.
- 명령어에서 정보를 추출하는 디코딩 로직을 추가
  - 소스 레지스터: RS1, RS2
  - 대상 레지스터: RD
  - 수행해야할 ALU function

</div>

<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images\02-2\alu&regFile.png" alt="alu & regfile" style="max-width: 80%; height: auto;">
</div>

</div>

## Loading from Data Memory

<div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 10px;">


<div style="flex: 1; min-width: 500px;">

**Data Memory**: 프로그램이 사용하는 실제 데이터가 저장된 공간

- 데이터를 메모리에서 읽어오는 load 명령어를 실행할 수 있도록, 기존의 데이터 경로에 데이터 메모리 접근 경로를 추가
- 메모리 주소는 보통 두 개의 레지스터 값을 더해서 계산 가능

</div>

<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images\02-2\load from dataMem.png" alt="load from data mem" style="max-width: 80%; height: auto;">
</div>

</div>

## Storing to Data Memory

<div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 10px;">


<div style="flex: 1; min-width: 500px;">

메모리에 저장하기 위해 쓸 주소와 데이터를 모두 제공  
+즉치 값을 추출하여 ALU 연산이나 주소 계산에 사용할 수 있는 기능 추가

</div>

<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images\02-2\storing to dataMem.png" alt="storing to data memory" style="max-width: 80%; height: auto;">
</div>

</div>

## Supporting Branch Instruction

<div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 10px;">


<div style="flex: 1; min-width: 500px;">

조건 분기(branch) 명령을 처리할 수 있도록 확장

- 브랜티 대상 주소는 PC를 기준으로 계산. 모든 명령어가 32비트 이므로 즉치(offset)은 왼쪽으로 2 shift(= 곱하기 4)

</div>

<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images\02-2\support branch Instr.png" alt="images\02-2\support branch Instr.png" style="max-width: 80%; height: auto;">
</div>

</div>

<div style="text-align: center;">

# The Fundamentals of Computer Design

</div>

**Architecture**: 개발자가 소프트웨어 및 펌웨어를 작성할 수 있도록 하는 사양 집합, 명령어 세트 포함

**Microarchitecture**: 컴퓨터 내부 구조의 논리적 구성

**Hardware or Implementation**: 구현 또는 물리적 구조

<br><br><br>

## Amdahl's Law
How to assign resources?
암달의 법칙은 컴퓨터 시스템의 요소를 개선하여 얻을수 있는 성능 향상을 계산하는 간단한 방법을 제공

>**Speedup** is calculated as:
> $$
> \text{speedup} = \frac{time_{without\_enhancement}}{time_{with\_enhancement}} = 
> \frac{1}{(1 - \text{Fraction}_{enhanced}) + \frac{\text{Fraction}_{enhanced}}{\text{Speedup}_{enhanced}}}
> $$
> $$
> \text{speedup} = \frac{1}{(1 - P) + \frac{P}{N}}
> $$
> <br>

<br>
- S는 시스템의 성능 향상 비율
- Fraction_enhanced는 성능향상 비율
- Speedup_enhanced는 성능향상 부분이 전과 비교해서 몇 배가 되는 지에 대한 계수
- P 는 전체 작업 중 병렬화 가능한 비율
- N은 병렬로 처리할 수 있는 프로세서의 수
- (1-P)는 순차적인 부분의 비율로, 병렬화되지 않는 코드 부분


- 성능 개선의 한계
  - 설계의 한 부분만 개선하면 얻을 수 있는 속도 향상은 개선이 이루어질수록 점차 감소
  > <br>
  >
  > $$  \frac{1}{1 - \text{Fraction}_{\text{enhanced}}} \quad \text{한계에 도달}$$
  > <br>

<br>
단일 최적화에 집중하면 하드웨어 투자에 따른 성능 개선⬇. 이는 각 최적화를 적용한 후 개선할 부분을 신중하게 재평가하고 하드웨어를 투자


## Complexity
일반적으로 단순하고 우아한 솔루션을 찾음
- 복잠성은 설계 및 검증 비용을 증가
- 구축한 것을 이해하고 어떻게 작동할지 예측을 해야함

## Making the Common-case fast
모두 성능이 아니라 **흔히 사용하는** 성능 위주로 개선
- 모든 성능 개선 단점:
  - 최적화 설계, 검증, 구현 하는데 리소스 소모
  - 복잡한 작업 가속화 ➡ cycle-time 연장 ➡ 모든 작업 속도 느려짐
  - 리소스가 덜 중요한 기능으로 리다렉션이 됨

<br>

- 실현 방법
  - 지역성: 자주 접근하는 데이터를 가까이
  - 추측: 결과를 미리 예상하여 계산을 앞당김 (**실행 경로**를 정하는 것)
  - 예측: 조건 분기 등의 결과를 미리 예측해 지연을 최소 (**실제 계산**을 먼저 해보는 것)
  - 방향성: 간접 참조를 통해 유연한 구조와 재사용성 (ex: 변수 값 대신 주소/포인터 이용)
    - 유연성: 구조를 바꾸지 않고도 동작을 쉽게 변경 (가상 함수 → 코드 수정 없이 다른 클래스의 동작으로 대체 가능)
    - 확장성: 새 동작 추가나 변경이 간편 (가상 메모리 시스템에서 실제 물리 메모리는 계속 바뀌어도 가상 주소는 그대로)
  - 병렬 처리: 여러 작업을 동시에 수행
  - 전문화: 특정 작업에 최적화된 전용 하드웨어