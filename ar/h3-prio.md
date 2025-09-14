# HTTP/3 Prioritization

مواصفة HTTP/3 الأساسية مابتعرفش prioritization بنفسها. طريقة HTTP/2 لل prioritization اتشافت معقدة أوي ومهجورة بواسطة آخر مراجعة لمواصفة HTTP/2 [RFC 9113](https://www.rfc-editor.org/rfc/rfc9113.html). بديل أبسط، Extensible Prioritization Scheme لـ HTTP ([RFC 9218](https://www.rfc-editor.org/rfc/rfc9218.html))، اتنشر منفصل، ويقدر يتستخدم في HTTP/2 و HTTP/3.

في HTTP/3، إشارات priority بتتبعت في شكل Priority header field و/أو PRIORITY_UPDATE frame متبعت على HTTP/3 Control Stream. السيرفرات تقدر تتعامل مع الإشارات دي عشان تجدول إرسال محتوى HTTP response. [RFC 9218](https://www.rfc-editor.org/rfc/rfc9218.html) بيقدم scheduling guidance مقصود إنه يحسن أداء تطبيق الويب للclient.

مثال مصري: فكر في prioritization زي نظام الأولويات في المستشفى. الطوارئ لها أولوية أعلى من الكشف العادي. HTTP/3 بيقول للسيرفر إيه الأهم يوصل الأول - الصور المهمة في الصفحة ولا الإعلانات في الجنب.