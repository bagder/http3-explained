# 詳解HTTP/3

この本の試みは2018年3月に始まりました。HTTP/3 と、その根幹のプロトコルである QUIC を文書化することがその目的です。
どうして、どのようにして動作するのか、プロトコルの詳細、その実装など。

この本は完全に無償で提供され、援助したいと考えるすべての人を巻き込んだ共同作品です。

## 前提条件

この本の読者は、TCP/IP ネットワーキングの基礎や、HTTP、Web の基本を理解しているものとみなされます。
HTTP/2 に関する詳細や特徴については、[http2 explained](https://daniel.haxx.se/http2/) を最初に読むことを推奨しています。

## 著者

この本は [Daniel Stenberg](https://daniel.haxx.se/) によって作成されました。
Daniel は、HTTP クライアントソフトウェアとして世界中で最も幅広く使われている [curl](https://curl.haxx.se/) の作者であり、リードデベロッパーです。
Daniel は20年以上にわたり HTTP やインターネットのプロトコルに関して取り組んでおり、 [http2 explained](https://daniel.haxx.se/http2/) の著者でもあります。

訳者:

- [inductor](https://github.com/inductor)
- [ebiiim](https://github.com/ebiiim)
- [kousukekikuchi1984](https://github.com/kousukekikuchi1984)
- [MATTENN](https://github.com/MATTENN)
- [beagle](https://github.com/beagleworks)
- [MakTak](https://github.com/take114514)
- [akihirok2k2](https://github.com/akihirok2k2)
- [OldBigBuddha](https://github.com/OldBigBuddha)
- [hidesuke](https://github.com/hidesuke)
- [ichika](https://github.com/ichika5259)
- [peacock](https://github.com/peacock0803sz)
- [gim_kondo](https://github.com/gimKondo)
- [hykw](https://github.com/hykw)
- [misato8310](https://github.com/misato8310)

## ホームページ

この本のホームページは [daniel.haxx.se/http3-explained](https://daniel.haxx.se/http3-explained) にあります。

## ヘルプ！

本文書に関する誤字脱字やあからさまな間違いを見つけた場合は、修正した状態の文書を送っていただければ、改訂版を作成します。
助けていただいたすべての方に、適切なクレジットを提供します！ 時間をかけてこの文書を良くしていければと思っています。

よろしければ、[誤字の指摘](https://github.com/bagder/http3-explained/issues)
または[プルリクエスト](https://github.com/bagder/http3-explained/pulls)を本の GitHub ページに送ってください。

## License

この文書およびすべてのコンテンツは、[Creative Commons
Attribution 4.0 license](https://creativecommons.org/licenses/by/4.0w/) のライセンスにて使用許諾されています。
