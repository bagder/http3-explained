## مستوى النقل والتطبيق

بروتوكول IETF QUIC بروتوكول نقل، يقدر يتستخدم فوقه بروتوكولات طبقة application تانية. بروتوكول application layer الأولي هو HTTP/3 (h3).

طبقة النقل بتدعم connections و streams.

نسخة Google القديمة من QUIC كان النقل و HTTP ملزقين مع بعض في واحد single do-it-all وكان أكتر special-purpose send-http/2-frames-over-udp protocol.

مثال مصري: فكر في QUIC زي شاحنة نقل (transport) تقدر تحمل حاجات مختلفة. HTTP/3 زي البضاعة اللي راكبة عليها. النسخة القديمة من Google كانت زي عربية مخصوصة للخضار بس، النسخة الجديدة زي شاحنة تقدر تشيل أي حاجة.