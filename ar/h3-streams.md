# QUIC streams و HTTP/3

HTTP/3 مصمم لـ QUIC فهو بيستغل streams بتاع QUIC بالكامل، بينما HTTP/2 كان لازم يصمم مفهوم stream و multiplexing بتاعه بنفسه على TCP.

طلبات HTTP المعمولة على HTTP/3 بتستخدم مجموعة محددة من streams.

## HTTP/3 frames

HTTP/3 يعني إعداد QUIC streams وإرسال مجموعة من frames للطرف التاني. في عدد قليل ثابت (فعلاً تسعة في 18 ديسمبر 2018!) من frames المعروفة في HTTP/3. الأهم فيها على الأرجح:

- HEADERS، اللي بيبعت HTTP headers مضغوطة
- DATA، بيبعت محتويات بيانات binary
- GOAWAY، من فضلك اقفل الconnection ده

## HTTP Request

الclient بيبعت HTTP request بتاعه على *bidirectional* QUIC stream مبدوء من الclient.

الrequest يتكون من HEADERS frame واحد وممكن اختيارياً يتبعه frame واحد أو اتنين تانيين: سلسلة من DATA frames وممكن HEADERS frame أخير للtrailers.

بعد بعت request، الclient بيقفل الstream للإرسال.

## HTTP Response

السيرفر بيبعت HTTP response بتاعه على bidirectional stream. HEADERS frame، سلسلة من DATA frames وممكن HEADERS frame أخير.

مثال مصري: فكر في HTTP/3 streams زي نظام الأرقام في البنك. كل عميل (client) ياخد رقم (stream) ويبعت طلبه (request) للموظف، والموظف (server) يرد عليه على نفس الرقم (response). لكن عكس البنك، ممكن عدة عملاء يتكلموا مع الموظف في نفس الوقت على أرقام مختلفة.

## QPACK headers

HEADERS frames بتحتوي على HTTP headers مضغوطة باستخدام خوارزمية QPACK. QPACK شبيه في الأسلوب لضغط HTTP/2 المسمى HPACK ([RFC 7541](https://httpwg.org/specs/rfc7541.html))، بس متعدل عشان يشتغل مع streams موصلة out of order.

QPACK نفسه بيستخدم اتنين إضافيين unidirectional QUIC streams بين النقطتين. بيتستخدموا لحمل معلومات dynamic table في أي اتجاه.