# 反対意見

## UDPが使えない

大企業、運用者、組織はUDPを使った53番ポート（主にDNSとして利用されている）
の外部通信をブロックしていたり、帯域制限をかけている。この利用制限の理由は、攻撃に
悪用されがちだからだ。なぜなら、攻撃者がDNSを利用し、ターゲットに対して大規模な
外部トラフィックを生み出すことが可能であるためだ。そのために、既存のUDPプロトコルや
UDPで頻繁に用いられるサーバー上の実装はDNSアンプ攻撃に対して脆弱である。

これに対して、QUICではアンプ攻撃に対して軽減する方法が備わっている。サーバーから受け取る
最初のパケットは最低でも1,200バイトを要求するとともに、クライアントレスポンスのパケットを
受け取っていない場合では、クライアントサーバーは3回以上のそれをレスポンスを送ってはならない、
とプロトコル上で明記されている。

## UDPはカーネル内で遅い

UDPがカーネル内で遅い点は正しいのように思われる、少なくとも2018年では。ただし、
この関して明確な理由を主張することができない。なぜなら、カーネルでの遅さは
どのように発生しているのか、どれだけUDPの転送パフォーマンスによる遅さであるかは、
開発者にとってはここ数年間はあまり興味がないからだ。

そのために、ほとんどのクライアントでは、この「遅さ」は気づくことはないだろう。

## QUICはCPU使用量が高すぎる

先述の「UDPは遅い」と同様であるが、CPU使用量が高すぎる点に関してもあまり当てはまらない。
なぜならTCPとTLSを利用する際にはハードウェアレベルでのアシストがあるまでに進化し、熟成している。

もちろん、時間を経るごとに、こういった改善が見込める。問題は利用者がどれだけ
余剰なCPU使用の増加を気にしなければならないかだ。

## これはGoogleの規格でしょ？

これはGoogleの規格でない。Googleは広大なインターネット規模でUDPを用いたQUIC同様の規格が
正しく動き、良いパフォーマンスであることを確認してから、最初の仕様をIETFに送っただけに
すぎない。

その時から、会社や組織から参加している個人もGoogleのUDPを用いたHTTP規格から離れた
トランスポート・プロトコルの規格をまとめるためにベンダー・ニュートラルなIETFで
働いている。ここにもちろんGoogleの従業員も参加しているが、Mozilla, Fastly, Cloudflare,
Akamai, Microsoft, Facebook, Appleといった会社から参加している人が大多数を占め、
インターネットのトランスポート・プロトコルをまとめている。

## This is too small of an improvement

That is not really a critique but an opinion. Maybe it is, and maybe it is too
little of an improvement so close in time since HTTP/2 was shipped.

HTTP/3 is likely to perform much better in packet loss-ridden networks, it
offers faster handshakes so it will improve latency both as perceived and
actual. But is that enough of benefits to motivate people to deploy HTTP/3
support on their servers and for their services? Time and future performance
measurements will surely tell!
