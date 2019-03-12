<!--
# HTTP/3 Server push

HTTP/3 server push is similar to what is described in HTTP/2 ([RFC
7540](https://httpwg.org/specs/rfc7540.html)), but uses different mechanisms.

A server push is effectively the response to a request that the client never
sent!

Server pushes are only allowed to happen if the client side has agreed to
them. In HTTP/3 the client even sets a limit for how many pushes it accepts
by informing the server what the max push stream ID is. Going over that limit
will cause a connection error.

If the server deems it likely that the client wants an extra resource that it
hasn't asked for but ought to have anyway, it can send a `PUSH_PROMISE` frame
(over the request stream) showing what the request looks like that the push is
a response to, and then send that actual response over a new stream.

Even when pushes have been said to be acceptable by the client before-hand,
each individual pushed stream can still be canceled at any time if the client
deems that suitable. It then sends a `CANCEL_PUSH` frame to the server.

## Problematic

Ever since this feature was first discussed in the HTTP/2 development and
later after the protocol shipped and has been deployed over the Internet, this
feature has been discussed, disliked and pounded up in countless different
ways in order to get it to become useful.

Pushing is never "free", since while it saves a half round-trip it still uses
bandwidth. It is often hard or impossible for the server-side to actually know
with a high level of certainty if a resource should be pushed or not.
-->

# HTTP/3 서버 푸시

HTTP/3 서버 푸시는 HTTP/2에서 설명된
내용([RFC 7540](https://httpwg.org/specs/rfc7540.html))과 비슷하지만
다른 메커니즘을 사용한다.

서버 푸시는 클라이언트가 보낸 적이 없는 요청에 대한 효율적인 응답이다!

서버 푸시는 클라이언트 쪽에서 서버 푸시에 동의했을 때만 발생할 수 있다. HTTP/3에서는
클라이언트가 최대 푸시 스트림의 ID가 무엇인지 서버에게 알려주어 클라이언트가 얼마나 많은
푸시를 받을지를 제한한다. 이 제한을 초과하면 연결 오류가 발생할 것이다.

클라이언트가 요청하지는 않았지만 어쨌든 서버가 받아야 하는 추가 리소스가 있다고 판단하면,
(요청 스트림을 통해) 서버가 요청에 푸시로 응답한 것처럼 보이는 `PUSH_PROMISE` 프레임을
보낼 수 있다. 그다음 실제 응답은 새로운 스트림을 통해 보낸다.

클라이언트가 미리 푸시를 받을 수 있다고 말했더라도, 클라이언트가 적합하다고 판단하면
푸시된 개별 스트림을 언제든 취소할 수 있다. 그리고 서버에 `CANCEL_PUSH` 프레임을 보낸다.

## 문제점

이 기능은 HTTP/2 개발에서 처음 논의된 이후 HTTP/2 프로토콜이 나오고 인터넷에 배포된 뒤,
이 기능을 유용하게 만들기 위해 셀 수 없이 다양한 방법으로 논의되고, 싫어하게 했으며, 두들겨 맞았다.

라운드 트립의 절반을 줄일 수 있지만, 여전히 대역폭을 사용하기 때문에 푸시는 결코 "공짜"가 아니다.
실제로 리소스가 푸시되어야 하는지 아닌지를 서버 측에서 확실하게 알기가 어렵거나 불가능하다.
