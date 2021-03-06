### Kafka 2.8 문서 번역

## 1. 시작하기  
### 1.1 소개
#### 이벤트 스트리밍이란?

이벤트 스트리밍은 인체의 중추 신경계의 디지털 버전이다. 이벤트 스트리밍은 비즈니스가 점점 소프트웨어 정의 및 자동화 된 소프트웨어의 사용자가 더 많은 소프트웨어인 '상시 접속' 세계의 기술적 기반입니다.

기술적으로 말하면, 이벤트 스트리밍, 데이터베이스, 센서, 모바일 장치, 클라우드 서비스, 소프트웨어 응용 프로그램 등의 이벤트 소스에서 이벤트 스트림의 형식으로 데이터를 실시간으로 캡처하는 방법입니다. 나중에 검색 할 수 있도록 이러한 이벤트 스트림을 영구적으로 저장합니다. 실시간 및 소급 이벤트 스트림을 조작, 처리 및 반응한다. 필요에 따라 이벤트 스트림을 다양한 대상 기술에 라우팅합니다. 따라서 이벤트 스트리밍은 데이터의 지속적인 흐름 해석이 보장 된 적절한 정보를 적절한 장소에 적절한 시간에 배치됩니다.
</br></br>

#### 이벤트 스트리밍은 무엇에 사용할 수 있어요?

이벤트 스트리밍은 다양한 산업 및 조직의 [다양한 사례](https://kafka.apache.org/powered-by)에 적용됩니다. 그 많은 예는 다음과 같습니다.
- 증권 거래소, 은행, 보험 등으로 지불 및 금융 거래를 실시간으로 처리하기 위하여.
- 물류 및 자동차 산업 등으로 자동차, 트럭, 함대 및화물을 실시간으로 추적하고 모니터링하는.
- 공장이나 윈드 파크 등 IoT 장치 및 기타 장비에서 센서 데이터를 지속적으로 캡처하고 분석하기 위하여.
- 소매, 호텔, 여행 업계, 모바일 애플리케이션 등 고객과의 상호 작용이나 주문을 수집하고 즉시 대응하기 위하여.
- 병원에서 환자를 모니터링하고 상태의 변화를 예측하여 긴급 적시에 치료를 보장합니다.
- 회사의 다른 부서에서 생성 된 데이터를 연결, 저장 및 이용 가능하게하는 것.
- 데이터 플랫폼, 이벤트 기반 아키텍처 및 마이크로 서비스의 기반 역할을합니다.
</br></br>

#### Apache Kafka®는 이벤트 스트리밍 플랫폼입니다. Apache Kafka® 뜻? 
Kafka는 세 가지 주요 기능을 결합하므로 단일 전투 테스트 솔루션을 사용하여 end-to-end 이벤트 스트리밍 [사용 사례](https://kafka.apache.org/powered-by)를 구현할 수 있습니다.
다른 시스템에서 데이터를 지속적으로 가져오기/내보내기를 포함하여 이벤트 스트림을 게시(쓰기) 및 구독(읽기)합니다.
이벤트 스트림을 원하는 만큼 내구성 있고 안정적으로 저장합니다.
이벤트 스트림을 발생 시 또는 소급하여 처리합니다.
그리고 이 모든 기능은 분산되고 확장성이 뛰어나고 탄력적이며 내결함성이 있으며 안전한 방식으로 제공됩니다. Kafka는 베어 메탈 하드웨어, 가상 머신, 컨테이너, 온프레미스 및 클라우드에 배포할 수 있습니다. Kafka 환경을 자체 관리하거나 다양한 공급업체에서 제공하는 완전 관리형 서비스를 사용할 수 있습니다.
</br></br>

#### Kafka는 한마디로 어떻게 작동해요? 
Kafka는 고성능 TCP 네트워크 프로토콜을 통해 통신하는 서버와 클라이언트로 구성된 분산 시스템입니다. bare-metal 하드웨어, 가상 머신, 온프레미스 및 클라우드 환경의 컨테이너에 배포 할 수 있습니다.

서버 : Kafka는 여러 데이터 센터 또는 클라우드 지역에 걸쳐 하나 이상의 서버 클러스터로 실행됩니다. 이러한 서버 중 일부는 브로커라는 스토리지 계층을 형성합니다. 해당 서버는 Kafka Connect를 실행하여 이벤트 스트림으로 데이터를 지속적으로 가져오고 내보내고 Kafka를 관계형 데이터베이스 및 기타 Kafka 클러스터와 같은 기존 시스템과 통합합니다. mission-critical 사용 사례를 구현할 수 있도록 Kafka 클러스터는 확장성이 뛰어나고 내결함성이 있습니다. 서버 중 하나에 장애가 발생하면 다른 서버가 작업을 인계받아 데이터 손실 없이 지속적인 운영을 보장합니다.

클라이언트 : 이를 통해 네트워크 문제나 시스템 장애가 발생한 경우에도 이벤트 스트림을 병렬로 대규모로 내결함성 방식으로 읽고, 쓰고, 처리하는 분산 애플리케이션 및 마이크로서비스를 작성할 수 있습니다. Kafka에는 Kafka 커뮤니티에서 제공하는 수십 개의 클라이언트가 포함된 일부 클라이언트가 포함되어 있습니다. 클라이언트는 상위 수준 Kafka Streams 라이브러리를 포함하여 Java 및 Scala, Go, Python, C/C++ 및 기타 여러 프로그래밍 언어와 REST API에 사용할 수 있습니다.
</br></br>

#### 주요 개념 및 용어
이벤트는 세계 또는 귀하의 비즈니스에서 "무언가 발생"했다는 사실을 기록합니다. 문서에서는 기록 또는 메시지라고도 합니다. Kafka에서 데이터를 읽거나 쓸 때 이벤트 형식으로 이 작업을 수행합니다. 개념적으로 이벤트에는 키, 값, 타임스탬프 및 선택적 메타데이터 헤더가 있습니다. 다음은 이벤트의 예입니다.
- Event key: "Alice"
- Event value: "Made a payment of $200 to Bob"
- Event timestamp: "Jun. 25, 2020 at 2:06 p.m."

**Producers** 는 Kafka에 이벤트를 게시(쓰기)하는 클라이언트 응용 프로그램이고, **consumers** 는 이러한 이벤트를 구독(읽기 및 처리)하는 응용 프로그램입니다. Kafka에서 생산자와 소비자는 완전히 분리되고 서로 불가지론적이며, 이는 Kafka가 잘 알려진 높은 확장성을 달성하기 위한 핵심 설계 요소입니다. 예를 들어 생산자는 소비자를 기다릴 필요가 없습니다. Kafka는 이벤트를 정확히 한 번 처리하는 기능과 같은 다양한 보장을 제공합니다.

이벤트는 **topics**에 구성되고 영구적으로 저장됩니다. 매우 단순화된 주제는 파일 시스템의 폴더와 유사하고 이벤트는 해당 폴더의 파일입니다. 주제 이름의 예는 "결제"일 수 있습니다. Kafka의 토픽은 항상 다중 생성자 및 다중 구독자입니다. 주제에는 이벤트를 작성하는 0개, 1개 또는 많은 생성자와 이러한 이벤트를 구독하는 0개, 1개 또는 많은 소비자가 있을 수 있습니다. 주제의 이벤트는 필요한 만큼 자주 읽을 수 있습니다. 기존 메시징 시스템과 달리 이벤트는 소비 후 삭제되지 않습니다. 대신 주제별 구성 설정을 통해 Kafka가 이벤트를 유지해야 하는 기간을 정의한 후 이전 이벤트가 삭제됩니다. Kafka의 성능은 데이터 크기와 관련하여 사실상 일정하므로 데이터를 장기간 저장하는 것이 완벽합니다.

토픽은 분할됩니다. 즉, 토픽은 다른 Kafka 브로커에 있는 여러 "버킷"에 분산됩니다. 데이터의 분산 배치는 클라이언트 응용 프로그램이 동시에 많은 브로커에서 데이터를 읽고 쓸 수 있도록 하기 때문에 확장성에 매우 중요합니다. 새 이벤트가 주제에 게시되면 실제로 해당 주제의 파티션 중 하나에 추가됩니다. 이벤트 키가 동일한 이벤트(예: 고객 또는 차량 ID)는 동일한 파티션에 기록됩니다. 그리고 Kafka는 주어진 토픽 파티션의 모든 소비자가 항상 작성된 것과 정확히 동일한 순서로 해당 파티션의 이벤트를 읽도록 보장합니다.

![image](https://user-images.githubusercontent.com/66021792/129522151-5a4c1ae5-c0cf-484e-a6af-c4674b8ee582.png)
*그림: 이 예제 항목에는 4개의 파티션 P1–P4가 있습니다. 두 개의 서로 다른 생산자 클라이언트가 네트워크를 통해 주제의 파티션에 이벤트를 기록하여 서로 독립적으로 새 이벤트를 주제에 게시하고 있습니다. 동일한 키를 사용하는 이벤트(그림에서 색상으로 표시)는 동일한 파티션에 기록됩니다. 적절한 경우 두 생산자 모두 동일한 파티션에 쓸 수 있습니다.*

데이터 내결함성 및 고가용성을 만들기 위해 모든 주제를 지리적 지역 또는 데이터 센터에 걸쳐 복제할 수 있기 때문에 문제가 발생하거나 브로커에 대한 유지 관리 등을 수행하려는 경우에 대비하여 데이터 복사본이 있는 여러 브로커가 항상 있도록 합니다. 일반적인 프로덕션 설정은 3의 복제 팩터입니다. 즉, 항상 3개의 데이터 복사본이 있습니다. 이 복제는 주제 파티션 수준에서 수행됩니다.

이 입문서는 소개용으로 충분해야 합니다. 문서의 디자인 섹션에서는 관심이 있는 경우 Kafka의 다양한 개념을 자세히 설명합니다.
</br></br>

#### Kafka APIs
