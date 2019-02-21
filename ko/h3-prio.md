<!--
# HTTP/3 Prioritization

One of the HTTP/3 stream frames is called `PRIORITY`. It is used to set
priority and dependency on a stream in a way similar to how it works in
HTTP/2.

The frame can set a specific stream to depend on another specific stream and
it can set a "weight" on a given stream.

A dependent stream should only be allocated resources if either all of the
streams that it depends on are closed or it is not possible to make progress
on them.

A stream weight is value between 1 and 256 and it is specified that streams
with the same parent **should** be allocated resources proportionally based on
their weight.
-->

# HTTP/3 우선순위 정하기

HTTP/3 스트림 프레임 중에는 `PRIORITY`라는 프레임이 있다.
이 프레임은 HTTP/2에서 동작한 방식과 비슷하게 스트림의 우선순위와 의존성을 설정하는 데 사용한다.

이 프레임은 특정 스트림이 다른 스트림에 의존하도록 설정할 수 있고
해당 스트림에 "가중치"를 설정할 수 있다.

종속된 스트림은 의존하는 스트림이 모두 닫혔을 때만 리소스가 할당받아야 하고
아니면 진행될 수 없다.

스트림 가중치는 1부터 256 사이의 값을 가지며 같은 부모를 가진 스트림은
**반드시** 가중치에 따라 리소스를 할당받아야 한다.
