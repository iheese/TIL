[2023년 5월 09일 (화)]

규칙 1: 한 메서드에 오직 한 단계의 들여쓰기만 한다.
규칙 2: else 예약어를 쓰지 않는다.
규칙 3: 모든 원시값과 문자열을 포장한다.
규칙 4: 한 줄에 점을 하나만 찍는다.
규칙 5: 줄여쓰지 않는다(축약 금지).
규칙 6: 모든 엔티티를 작게 유지한다.
규칙 7: 2개 이상의 인스턴스 변수를 가진 클래스를 쓰지 않는다.
규칙 8: 일급 콜렉션을 쓴다.
규칙 9: 게터/세터/프로퍼티를 쓰지 않는다.

https://developerfarm.wordpress.com/2012/02/03/object_calisthenics_summary/

레디스 캐시

redis는 별도의 서버를 띄워야 하기에(Global Cache), 네트워크 지연이나 단절 등 네트워크 상에서 생길 수 있는 문제가 발생할 가능성이 생긴다. 또한 redis는 풍부한 자료구조, pub/sub, 싱글 쓰레드를 통한 정합성 유지 등 다양한 기능들을 제공한다.

Ehcache :스프링에서 간단하게 사용할 수 있는 Java 기반 오픈 소스 캐시 라이브러리
 별도의 데몬을 가지지 않고, Spring 내부적으로 동작한다. 이 말은 프로세스 라이프 사이클을 Spring Application과 동일하게 가져간다는 뜻이다. 즉, 스프링이 죽으면 EHcache도 죽는다는 말.
Ehcache는 직렬화된 데이터 객체를 저장하는 메모리 블럭이다. Ehcache는 프로세스 내 캐싱에서 테라바이트 크기의 캐쉬와 함께 프로세스 내/프로세스 외 혼합 구현으로 확장된다.
Ehcache는 아래 세 가지의 공간에 데이터를 저장할 수 있다. [ Memory / OffHeap / Disk ]
* Memory Tier : In - Memory
* OffHeap Tier : Memory Heap 외부에 저장. java GC가 적용 X. 바이트 단위의 매우 큰 캐시를 생성.
* Disk Tier : File 캐시와 유사. CacheManager를 이용하여 여러 디스크 저장소 경로를 구성 할 수 있다.

Ehcache는 LRU(Least Recent Used), LFU (Least Frequency Used), FIFO(First In First Out) 세가지 제거 알고리즘을 제공한다.
스프링은 캐시 추상화 (Cache Abstraction)을 통해 편리한 캐싱 기능을 지원하고 있다. (cache를 사용할 때, 추상화 인터페이스를 통해서 ehcache, redis 와 같은 다른 캐싱 인프라 간의 전환을 손쉽게 할 수 있다.)

- memcached
memcached는 같은 로컬환경에서 실행될 수 있지만(Local Cache), Spring Application과는 별도로 구동해야한다. 어차피 라이프 사이클이 분리된다는 말이다.
