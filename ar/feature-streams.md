## ‎Streams متعددة جوا الconnections

زي SCTP و SSH و HTTP/2، QUIC عنده streams منطقية منفصلة جوا الconnections الفيزيائية. عدد من الstreams المتوازية اللي تقدر تنقل بيانات في نفس الوقت على connection واحد من غير ما تأثر على الstreams التانية.

Connection هو setup متفاوض عليه بين نقطتين زي ما TCP connection بيشتغل. QUIC connection بيتعمل لـ UDP port و IP address، بس بعد ما يتعمل الconnection بيتربط بـ "connection ID" بتاعه.

على connection متعمل، أي ناحية تقدر تعمل streams وتبعت بيانات للناحية التانية. Streams بتوصل in-order وهي reliable، بس streams مختلفة ممكن توصل out-of-order.

QUIC بيقدم flow control على الconnection والstreams.

شوف تفاصيل أكتر في أجزاء [connections](quic-connections.md) و [streams](quic-streams.md)

مثال مصري: فكر في QUIC زي بناية فيها شقق كتيرة (streams). كل شقة (stream) مستقلة عن التانية - لو واحدة فيها مشكلة، باقي الشقق تشتغل عادي. بس كلها في نفس البناية (connection الواحد).