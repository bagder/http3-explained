<!--
# Streams

Streams in QUIC provide a lightweight, ordered byte-stream abstraction.

There are two basic types of stream in QUIC:

 - Unidirectional streams carry data in one direction: from the initiator of the stream to its peer.

 - Bidirectional streams allow for data to be sent in both directions.

Either type of stream can be created by either endpoint, can concurrently send
data interleaved with other streams, and can be canceled.

To send data over a QUIC connection, one or more streams are used.

## Flow control

Streams are individually flow controlled, allowing an endpoint to limit memory
commitment and to apply back pressure. The creation of streams is also flow
controlled, with each peer declaring the maximum stream ID it is willing to
accept at a given time.

## Stream Identifiers

Streams are identified by an unsigned 62-bit integer, referred to as the
Stream ID. The least significant two bits of the Stream ID are used to
identify the type of stream (unidirectional or bidirectional) and the
initiator of the stream.

The least significant bit (0x1) of the Stream ID identifies the initiator of
the stream. Clients initiate even-numbered streams (those with the least
significant bit set to 0); servers initiate odd-numbered streams (with the bit
set to 1).

The second least significant bit (0x2) of the Stream ID differentiates between
unidirectional streams and bidirectional streams. Unidirectional streams
always have this bit set to 1 and bidirectional streams have this bit set to
0.

## Stream concurrency

QUIC allows for an arbitrary number of streams to operate concurrently. An
endpoint limits the number of concurrently active incoming streams by limiting
the maximum stream ID.

The maximum stream ID is specific to each endpoint and applies only to the
peer that receives the setting.

## Sending and Receiving Data

Endpoints use streams to send and receive data. That is after all their
ultimate purpose. Streams are an ordered byte-stream abstraction. Separate
streams are however not necessarily delivered in the original order.

## Stream Prioritization

Stream multiplexing has a significant effect on application performance if
resources allocated to streams are correctly prioritized. Experience with
other multiplexed protocols, such as HTTP/2, shows that effective
prioritization strategies have a significant positive impact on performance.

QUIC itself does not provide frames for exchanging prioritization information.
Instead it relies on receiving priority information from the application that
uses QUIC. Protocols that use QUIC are able to define any prioritization
scheme that suits their application semantics.

When HTTP/3 is used over QUIC, the prioritization is done in the HTTP layer.
-->

# 스트림

QUIC 스트림은 경량이면서 순서가 있는 바이트 스트림 추상화를 제공한다.

QUIC에는 두가지 기본 스트림 타입이 있다.

 - 단방향 스트림은 한쪽으로 데이터를 전달한다. 즉, 스트림을 시작한 쪽에서 피어로 전달된다.

 - 양방향 스트림은 양쪽으로 데이터를 보낼 수 있다.

두 엔드포인트가 두 타입의 스트림을 모두 만들 수 있고 스트림은 다른 스트림과 상호배치된 데이터를
동시에 보낼 수 있고 취소할 수도 있다.

QUIC 연결을 통해 데이터를 보낼 때 하나 이상의 스트림을 사용한다.

## 흐름 제어

스트림은 개별적으로 흐름 제어가 되므로 엔드포인트가 메모리 사용을 제한할 수 있고
백프레셔(back pressure)를 적용할 수도 있다. 스트림의 생성도 흐름 제어가 되고
각 피어는 일정 시간 동안 받고자 하는 최대 스트림 ID를 정의할 수 있다.

## 스트림 식별자

스트림 ID라고 부르는 부호없는 62비트 정수로 스트림을 식별한다. 스트림 ID의 최하위 2비트를
스트림(단방향이나 양방향이나)의 타입과 스트림을 시작한 쪽을 식별하는 데 사용한다.

스트림 ID의 최하위 비트(0x1)는 누가 스트림을 시작했는지를 식별한다. 클라이언트는
짝수의 스트림(최하위 비트가 0으로 설정된 스트림)을 초기화 하고 서버는
홀수의 스트림(최하위 비트가 1으로 설정된 스트림)을 초기화한다.

스트림 ID의 두 번째 하위 비트(0x2)는 단방향 스트림과 양방향 스트림을 구분한다.
단방향 스트림을 항상 이 비트를 1로 설정하고 양방향 스트림은 이 비트를 0으로 설정한다.

## 스트림 동시성

QUIC에서는 임의의 스트림이 다수 동시에 동작할 수 있다. 엔드포인드는 최대 스트림 ID를 제한해서
동시에 받아들이는 활성 스트림의 수를 제한한다.

엔드포인트마다 최대 스트림 ID를 설정하고 설정을 받는 피어에만 적용된다.

## 데이터 보내기와 받기

엔드포인트는 스트림을 사용해서 데이터를 보내고 받고 이는 스트림의 원래 목적이다.
스트림은 순서가 맞는 바이트 스트림 추상화다. 하지만 별도의 스트림은 원래 순서대로 전달되지 않는다.

## 스트림의 우선순위

스트림에 할당된 리소스의 우선순위가 제대로 설정되면 스트림 멀티플렉싱은 애플리케이션 성능에
상당한 영향을 준다. HTTP/2 같은 멀티플렉싱을 지원하는 다른 프로토콜의 경험에서 상당히
긍적적인 성능 효과를 보여주는 효율적인 우선순위 전략을 볼 수 있다.

QUIC 자체에서 우선순위를 결정하는 정보를 교환하는 프레임을 제공하지는 않는다. 대신 QUIC을 사용하는
애플리케이션에서 우선순위 정보를 받는데 의존한다. QUIC을 사용하는 프로토콜은 애플리케이션의 의미에
적합한 우선순위 스키마를 정의할 수 있다.

QUIC을 통해 HTTP/3을 사용할 때 우선순위는 HTTP 계층에서 동작한다.
