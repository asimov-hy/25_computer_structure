<!-- p3 -->

# Intro

마이크로프로세서는 많은 과학적 혁신을 뒷받침하고 통신, 연산, 스토리지가 거의 무료에 가까운 디지털 세상을 만드는데 기여를 함

- 현대 컴퓨터 역사는 100녀이 안됨
  - 1930, 1940에 최초의 전자기계 및 밸브 기반 기계를 생산 -> 현대 컴퓨터는 더 빠르고, 전력 소모가 적고, 안정적

<br><br><br>

<!-- p5 -->

<div style="text-align: center;">

# 추상화 수준(Levels of Abstraction)

</div>

## Architecture

프로세서의 전반적인 구조와 기능을 정의

- 개발자가 소프트웨어 및 펌웨어를 작성할 수 있도록 하는 일련의 사양
- 명령어 세트(Instruction Set), Data type, processor mode, addressing mode 등이 포함

## Micro-architecture

컴퓨터 내부 구조의 논리적 구성(회로 디자인)

- 특정 아키텍처를 실제로 구현하는 세부적인 구조와 설계를 의미
  - 파이프라인 디자인, 캐시 메모리 구조, 분기 예측 등 최적화 기술

<br>
전체적인 디자인과 성능 vs 성능이 프로세서 내부에서의 실제 동작 기획

## Hardware or Implementation

물리적 구현

<br>

<!-- p6 -->

## Computer Architecture vs. Organization

<div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 20px;">

<!-- Text (Left) -->
<div style="flex: 1; min-width: 500px;">

두 개는 관련이 있지만 컴퓨터 사이언스 분야에서는 **구분되는 개념**

| **Computer Architecture**                                                     | **Computer Organization**                                        |
| ----------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| 컴퓨터가 수행하는 작업                                                        | 컴퓨터가 수행하는 방법                                           |
| 프로그래머가 볼 수 있는 시스템 구조와 기능                                    | 시스템 구현을 위한 하드웨어 구성                                 |
| 명령어 세트, 레지스터, 데이터 유형, 메모리, 주소 지정 모드와 같은 논리적 기능 | 회로 설계, 논리 회로, 제어 장치, 연산 장치 등과 같은 물리적 단위 |

- **Computer Architecture**는 하드웨어가 구현해야 할 것을 먼저 정의

<div style="text-align: center;"><strong>Computer Architecture ➡ Computer Organization</strong></div>

</div>

<!-- Image (Right) -->
<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images/02-1\02-1(Computer_System).png" alt="Computer System Diagram" style="max-width: 50%; height: auto;">
</div>

</div>

<!-- p7 -->

## 아키텍처 사양 (Archtecture Specification)

- 아키텍처는 하드웨어와 소프트웨어가 서로 문제없이 작동할 수 있도록, 명확하게 정해 놓은 둘 사이의 연결 방식과 규칙
  - 전력 소비, 비용, 면적, 성능 목표 등을 충족하기 위해 다양한 호환 프로세서 가능
- 소프트웨어가 아키텍처 사양을 잘 따르면, 다른 하드웨어에서도 문제없이 실행

<br>
<br>

<br>
<br>
<div style="text-align: center;">

# Computer Architecture

</div>

단순한 명령어 정의를 넘어서, HW/SW가 효과적으로 연결되도록 전체 구조를 설계하는 것

- 몇 가지 기본 개념 위에 구축 -> 새로운 해법을 끊임없이 찾아야 함
- 전력, 자원 등 제한된 조건 속에서 전력, 비용, 면적, 성능 등 종합해서 높은 효율, _최선_ 을 추구 (최선은 상황과 목적에 따라 달라짐)
  - 과거 기술과 워크로드에만 의존하지 않고 미래의 변화도 함께 고려
  - 설계는 실험과 검증을 통해 신중하게 결정

<br><br><br>

## What shapes computer architecture?

<div style="text-align: center;">
  <img src="images\02-1\02-1(Com_arch_arena).png" style="max-width: 60%; height: auto;">
</div>

## Design Goal

- **Function(기능)**  
  시스템이 수행해야 하는 역할과 동작

  - 수정이 어려움
  - 검증은 설계 과정에서 가장 많은 비용이 듬 (칩 제조 후에 많은 비용이 들기 때문에 설계 단계에서 신중한 고려가 필요)

- **Performance(성능)**  
  시스템이 얼마나 빠르고 효율적으로 작업을 수행하는지

  - 작업 목적(작업 부하)에 따라 요구 성능이 다름 -> 절대적 최선이 없음

- **Power(전력)**  
  시스템이 사용하는 에너지의 양

  - 제일 먼저 고려되는 제약 조건 중 하나 - 시스템 성능을 제한/결정을 함

- **Security(보안)**
  민감한 데이터와 시스템 제어권을 보호하는 기능 - 악의적 입력이나 외부 접근으로부터 프로세서를 **안전하게 보호**

- **Cost(비용)**
  시스템을 설계·생산하는 데 드는 자원 - 설계 복잡도, 다이 크기, 패키징 등

- **Reliability(신뢰성)**
  시스템이 얼마나 오류 없이 안정적으로 동작하는가 - 작동 중 오류를 감지/허용하는가?

## Markets and Features

각 목표 시장마다 전력 소비, 비용, 면적, 성능, 보안, 신뢰성 등의 측면에서 서로 다른 절충안이 필요
<br>

> **Arm의 몇가지 프로세서 클래스 예시**
>
> - Cortex-A: 고성능 애플리케이션 프로세서
>   - 예: 휴대폰용
> - Cortex-R: 결정론적 실시간 성능 (deterministic real-time performance)
>   - 오류 감지 (fault detection), 내성 (tolerance) 기능 포함
> - Cortex-M: 에너지 효율적인 임베디드 디바이스
>   - '마이크로컨트롤러' 클래스 코어
> - Neoverse: 단일 칩의 확장 가능한 프로세서 네트워크
>   - 예: 8, 16, 64 또는 128코어
>   - 데이터센터, 엣지 서버, 스토리지 등에 사용
>
> **Smartphone**
>
> - has many processor cores, each optimized for different roles using different Arm Cortex series (A, R, M)
> <br><br>
>   ![alt text](<images\02-1\02-1(smartphone).png>)

<br><br><br>

<div style="text-align: center;">

# Historical Performance Gains

</div>

1985년에 하나의 다이(die) 또는 칩(chip)에 완전한 마이크로프로세서를 통합
기술 향상: 트랜지스터의 크기가 작아지면서 단일 코어의 성능이 빠르게 향상
거의 20년 동안 매년 52%의 비율로 성능이 향상 (SPEC 벤치마크 데이터 - 베스크톱, 서버 프로세서 기준)

## 1. Clock Period

클럭 주파수는 1985년과 2002년에 800배 성능 향상상

<div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 20px;">

<div style="flex: 1; min-width: 500px;">

Clock Period (클럭 주기)에서 약 100배 단축

- 더 빨라진 트랜지스터 -> ~10배
- 파이프라이닝(pipelining) & 회로수준(circuit-level) 발전 -> ~10배

더 빠르고 저전력인 트렌지스터 제공

> **프로세서의 철의 법칙 (Iron Law)**  
> 시간 = 실행된 명령어 × 명령어당 클럭(CPI) × 클럭 주기
>
> > CPI: _Cycles Per Instruction_ (낮을수록 좋음)  
> > IPC: _Instructions Per Cycle_ (높을수록 좋음)
> >
> > $\displaystyle \text{CPI} = \frac{1}{\text{IPC}}$  
> > <br>

</div>
  <div style="flex: 1; min-width: 100px; text-align: center;">
    <img src="images\02-1\02-1(clock).png" alt="Computer System Diagram" style="max-width: 50%; height: auto;">
  </div>
</div>

## 2. Clock Per Instruction (CPI)

1. 초기 컴퓨터는 트랜지스터 수가 제한 ➡ 명령을 실행하는 데 여러 클럭 사이클이 필요 (CPI ≫ 1)

2. 트랜지스터 예산(budget)이 향상 ➡ CPI ≈ 1 가능

   > 클럭 주파수 자체에 신경 쓰지 않는다면 CPI 낮추는 건 비교적 쉬움
   >
   > 하지만 **CPI가 낮은 고주파(high-frequency) 설계**는 어려움  
   >  &nbsp;&nbsp;(고성능 프로세서를 계속 바쁘게 유지해야 함 → 다양한 기술, 많은 트랜지스터/면적/전력이 필요)

3. 클럭 사이클당 여러개의 명령어를 가져옴 ➡ CPI < 1

- 종종 IPC로 참조
- 명령어가 동시에 실행되려면 독립적이어야함
- 트랜지스터 예산 증가 ➡ 명령어 수준 병렬 처리 (ILP: Instruction-Level Parallelism)

## 3. Pipelining

하나의 명령어를 여러 단계로 나누고, 각 단계를 병렬로 처리하여 여러 명령어를 겹쳐 실행함으로써 처리 속도를 높이는 방식 <br><br>

<div style="text-align: center;">
  <img src="images\02-1\02-1(Pipelining).png" alt="Pipelining" style="max-width: 80%; height: auto;">
</div>

## 4. IPC and Instruction Count

800배 성능 향상(1985~2002)

- 100배: 클럭 주파수 개선
- 8배: 명령어수 감소, 컴파일러 최적화 개선, IPC 개선선

(오른쪽 그래프는 이러한 개선 사항을 표시. 이 그래프는 성능(시간 대비 인첼 프로세서서의 MHz당 SpecInt2000 벤치마크 성능)을 표시)

<div style="text-align: center;">
  <img src="images\02-1\02-1(SpecInt2000pMHz).png" alt="SpecInt2000pMHz" style="max-width: 80%; height: auto;">
</div>

## Shorter Critical Path
<div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 20px;">
<div style="flex: 1; min-width: 500px;">

- 임계 경로의 게이트 수를 줄이는 방법
- 추가 레지스터를 삽입 -> 복잡한 로직을 여러 파이프라이 단계로 나누기
- 회로 수준의 설계 기술도 발전
> 임계 경로의 길이가 약 10배 감소

</div>
<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images\02-1\02-1(Crit_Path).png" alt="Crit path" style="max-width: 50%; height: auto;">
</div>

</div>  

### Moore's Law
동일한 비용으로 칩에 통합할수 있는 트랜지스터의 수가 2년마다 두배로 증가
- 마이크로 아키텍쳐 복잡해짐 ➡ 프로세서 트랜지스터 예산은 빠르게 증가
<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images\02-1\02-1(Moore's Law).png" alt="Moore's Law" style="max-width: 50%; height: auto;">
</div>

## Better Performance and Lower Power
<br>
<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images\02-1\02-1(p26).png" alt="p26  " style="max-width: 80%; height: auto;">
</div>

## Slower Single-core Performance Gains
- 연간 최고 성능 향상 -> 52% 에서 21% 로
  - 파이프라이닝 한계
  - ILP 한계
  - 전력 소비
  - 온칩 와이어의 성능
<br><br><br>

# Multiple Processors

- 2005년 설계 대새 / 전환 증가
- 클럭 주파수는 더 천천히 증가
- 개별 코어는 가능한 높은 전력 효율이 되도록 설계
  
한계:
- 전력 소비로 인해 성능 제한 가능성
- 병렬 프로그램 작성 필요, 충분한 병렬 스레드 찾지 못할수 있음
- 온칩, 오프칩 통신이 성능 향을 제한 (대역폭 제한 -> 코어 스로틀(throttle))

## Specialization
설계 목표를 달성하기 위해 유연성과 효율성을 맞바꿈
- 좁은 워크로드(narrow workload), 심지어 단일 알고리즘을 위한 설계
- 이러한 가속기는 전력과 성능 면에서 범용 솔루션보다 10~1000배 더 우수함

## Today's SoC(system on a chip) Designs
최신 휴대폰 SoC에는 70억개 이상의 트랜지스터가 포함될 수 있다
- 여러개의 프로세서 코더, GPU, 다수의 특수 가속기, 대량의 온침 메모리, 오프칩 메모리에 대한 고대역폭 인터페이스

<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images\02-1\02-1(soc design).png" alt="soc design" style="max-width: 50%; height: auto;">
</div>

### Trends in Computer Architecture


<div style="flex: 1; min-width: 100px; text-align: center;">
  <img src="images\02-1\02-1(trends).png" alt="trends" style="max-width: 80%; height: auto;">
</div>
<br><br><br><br><br><br><br><br><br>

### The Future -- The end of Moore's Law
최근 몇년 동안 스테일링 속도가 느려졌지만 트랜지스터 밀도는 계속 향상
- 결국 2D 스케일링의 속도도 느려질수 밖에 없음(원자의 크기에 의해 제한)
다음 단계:
- 3D: 여러 층의 트랜지스터
- 더 나은 패키징
- 새 유형의 메모리
- 새 재료 및 장치