# Streams

Streams في QUIC بتوفر abstraction خفيف ومرتب للbyte-stream.

في نوعين أساسيين من stream في QUIC:

- Unidirectional streams بتحمل بيانات في اتجاه واحد: من اللي بدأ الstream لطرفه التاني.

- Bidirectional streams بتسمح بإن البيانات تتبعت في الاتجاهين.

أي نوع من الstream يقدر يتعمل من أي endpoint، يقدر يبعت بيانات متداخلة مع streams تانية في نفس الوقت، ويقدر يتلغي.

عشان نبعت بيانات على QUIC connection، stream واحد أو أكتر بيتستخدم.

## Flow control

Streams معمولها flow control منفرد، ده بيسمح للendpoint إنه يحدد memory commitment ويطبق back pressure. إنشاء الstreams برضو معمولها flow control، مع كل peer بيعلن أقصى stream ID مستعد يقبله في وقت معين.

## Stream Identifiers

Streams بتتعرف برقم 62-bit unsigned integer، واللي بيتسمى Stream ID. أقل bitين مهمين في Stream ID بيستخدموا عشان يعرفوا نوع الstream (unidirectional ولا bidirectional) ومين اللي بدأ الstream.

أقل bit مهم (0x1) في Stream ID بيعرف مين اللي بدأ الstream. Clients بيبدأوا streams أرقام زوجي (اللي فيها أقل bit مهم = 0)؛ servers بيبدأوا streams أرقام فردي (مع الbit = 1).

تاني أقل bit مهم (0x2) في Stream ID بيفرق بين unidirectional streams و bidirectional streams. Unidirectional streams دايماً الbit ده = 1 و bidirectional streams الbit ده = 0.

## Stream concurrency

QUIC بيسمح بعدد streams عشوائي يشتغل concurrently. Endpoint بيحدد عدد الstreams الactive الداخلة عن طريق تحديد أقصى stream ID.

أقصى stream ID مخصوص لكل endpoint ويتطبق بس على الpeer اللي بيستقبل الإعداد.

## إرسال واستقبال البيانات

Endpoints بتستخدم streams عشان تبعت وتستقبل بيانات. ده آخر حاجة هدفها الأساسي. Streams هي ordered byte-stream abstraction. بس streams منفصلة مش بالضرورة توصل بالترتيب الأصلي.

مثال مصري: فكر في الstreams زي خطوط التليفون في السنترال. كل خط (stream) له رقم مميز، وممكن يشتغل في اتجاه واحد (زي الراديو) أو اتجاهين (زي التليفون العادي). السنترال (QUIC) بيقدر يدير خطوط كتيرة في نفس الوقت.

## Stream Prioritization

Stream multiplexing له تأثير كبير على أداء الapplication لو الموارد المخصصة للstreams اتحددت أولوياتها صح. التجربة مع بروتوكولات multiplexed تانية، زي HTTP/2، بتوري إن استراتيجيات prioritization الفعالة لها تأثير إيجابي كبير على الأداء.

QUIC نفسه مابيوفرش إشارات لتبادل معلومات prioritization. بدلاً من كده بيعتمد على استقبال معلومات priority من الapplication اللي بيستخدم QUIC. البروتوكولات اللي بتستخدم QUIC تقدر تعرف أي prioritization scheme يناسب application semantics بتاعها.

Extensible Prioritization Scheme لـ HTTP ([RFC 9218](https://www.rfc-editor.org/rfc/rfc9218.html)) ممكن يتستخدم لـ HTTP/3. بيعرف إشارات ويقدم scheduling guidance. المخطط ده أبسط من الأصلي المعرف لـ HTTP/2.