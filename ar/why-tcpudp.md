## TCP ولا UDP

لو مانقدرش نصلح head-of-line blocking جوا TCP، في النظرية المفروض نقدر نعمل بروتوكول نقل جديد جنب UDP و TCP في network stack. أو ممكن حتى نستخدم [SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol) اللي هو بروتوكول نقل معايرة بواسطة IETF في [RFC 4960](https://tools.ietf.org/html/rfc4960) مع عدة من الخصائص المرغوب فيها.

بس، في السنين الأخيرة مجهودات إنشاء بروتوكولات نقل جديدة تقريباً اتوقفت خالص بسبب صعوبات نشرها على الإنترنت. نشر بروتوكولات جديدة بيتعرقل بواسطة firewalls كتيرة و NATs و routers و middle-boxes تانية اللي بتسمح بس بـ TCP أو UDP ومنتشرة بين المستخدمين والسيرفرات اللي محتاجين يوصلولها. تقديم بروتوكول نقل تاني بيخلي N% من الconnections تفشل لأنها بتتحجب بواسطة boxes بتشوفها مش UDP أو TCP وبالتالي شر أو غلط بطريقة ما. معدل الفشل N% بيتعتبر عالي أوي إن المجهود ميستحقش.

بالإضافة لده، تغيير حاجات في طبقة بروتوكول النقل في network stack عادة يعني بروتوكولات مطبقة بواسطة kernels نظام التشغيل. تحديث ونشر kernels جديدة لنظم التشغيل عملية بطيئة تتطلب مجهود كبير. تحسينات TCP كتيرة معايرة بواسطة IETF مش منتشرة أو مستخدمة على نطاق واسع لأنها مش مدعومة بشكل واسع.

## ليه مش SCTP-over-UDP

SCTP بروتوكول نقل موثوق بـ streams، ولـ WebRTC في حتى implementations موجودة بتستخدمه على UDP.

ده ماتعتبرش كويس كفاية كبديل لـ QUIC لأسباب عدة، منها:

- SCTP مايحلش مشكلة head-of-line-blocking للstreams
- SCTP بيتطلب عدد الstreams يتحدد في connection setup  
- SCTP مالوش قصة TLS/security قوية
- SCTP عنده 4-way handshake، QUIC بيقدم 0-RTT
- QUIC bytestream زي TCP، SCTP message-based
- QUIC connections تقدر تنتقل بين IP addresses بس SCTP مايقدرش

للتفاصيل أكتر عن الفروق، شوف [A Comparison between SCTP and QUIC](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00).

مثال مصري: فكر في الوضع زي إنك عايز تعمل نوع نقل جديد في الشوارع. TCP زي الأتوبيس - بطيء بس موجود في كل حتة. UDP زي التوك توك - سريع بس مش مضمون. SCTP كان زي الميكروباص - أحسن من الأتوبيس بس مش كل الشوارع تقبله. QUIC زي إنك تاخد التوك توك وتديله مميزات الأتوبيس - سرعة مع أمان.