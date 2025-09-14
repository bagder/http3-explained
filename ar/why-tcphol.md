## TCP head of line blocking

HTTP/2 بيشتغل على TCP ومع TCP connections أقل بكتير من لما نستخدم نسخ HTTP الأقدم. TCP هو بروتوكول للنقل الموثوق وممكن تفكر فيه زي سلسلة وهمية بين جهازين. اللي بيتحط على الشبكة في ناحية هيوصل للناحية التانية، بنفس الترتيب - في الآخر. (أو الconnection ينقطع.)

![a TCP chain between two computers](../images/tcp-chain.png)

مع HTTP/2، المتصفحات العادية بتعمل عشرات أو مئات من النقل المتوازي على TCP connection واحد.

لو packet واحد وقع، أو ضاع في الشبكة في أي مكان بين النقطتين اللي بتتكلم HTTP/2، ده معناه إن كل TCP connection يتوقف بينما الpacket الضائع يتبعت تاني ويلاقي طريقه للمكان المطلوب. بما إن TCP هو "السلسلة" دي، ده معناه إن لو حلقة واحدة ضاعت فجأة، كل حاجة كانت هتيجي بعد الحلقة الضائعة لازم تستنى.

رسم توضيحي باستخدام استعارة السلسلة لما نبعت streamين على connection ده. stream أحمر وstream أخضر:

![the chain showing links in different colors](../images/tcp-chain-streams.png)

ده بيبقى TCP-based head of line block!

كلما معدل فقدان الpackets يزيد، HTTP/2 يشتغل أسوأ وأسوأ. عند فقدان 2% من الpackets (اللي هو جودة شبكة وحشة جداً، خد بالك)، التجارب أثبتت إن مستخدمين HTTP/1 عادة يكونوا أحسن - لأنهم عادة عندهم لغاية ستة TCP connections يوزعوا الpackets الضائعة عليها. ده معناه إن مع كل packet ضائع الconnections التانية تقدر تكمل.

إصلاح المشكلة دي مش سهل، لو أصلاً ممكن، مع TCP.

مثال مصري: فكر في TCP زي قطار واحد طويل. لو عربة واحدة في النص عطلت، كل القطار يوقف لحد ما العربة دي تتصلح، حتى لو العربيات اللي ورا كانت شغالة كويس.

## Independent streams بتتجنب الblock

مع QUIC لسه في connection setup بين النقطتين اللي بيخلي الconnection آمن ونقل البيانات موثوق.

![a QUIC chain between two computers](../images/tcp-chain.png)

لما نعمل streamين مختلفين على connection ده، بيتعاملوا بشكل مستقل بحيث إن لو أي حلقة ضاعت لواحد من الstreams، بس الstream ده، السلسلة المعينة دي، اللي هتتوقف وتستنى الحلقة المفقودة تتبعت تاني.

مرسوم هنا بstream أصفر وstream أزرق متبعتين بين نقطتين.

مثال مصري: QUIC زي إن عندك شارعين منفصلين بدل من شارع واحد. لو حصل زحمة في شارع، الشارع التاني يفضل شغال عادي.

![two QUIC streams between two computers](../images/quic-chain-streams.png)