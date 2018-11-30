## ユーザースペース

ユーザースペースにおけるトランスポートプロコトルの実装は、 開発の推進と素早いプロコトルのイテレーションを助長しました。それ以来 Google にとって、操作の両端で実行し、ユーザーにとても頻繁に新機能をつかってもらうことは**簡単**でした。

もはやそのプロトコルが、OS のカーネルによって実装、提供され続けることを妨げざるを得ないでしょう。そして将来、誰かが良い案を見つけるべきです。

### 多数の実装

1つの自明な、 新しいトランスポートプロコトルの実装 影響 主にユーザースペースに住む

One obvious effect of implementing a new transport protocol that primarily lives in user-space 

is that we see many independent implementations and we can look forward to applications running with this rather big and complicated transport protocol stack in them going forward and different applications using different not only HTTP/3 but also QUIC stacks. It will for sure bring new challenges.