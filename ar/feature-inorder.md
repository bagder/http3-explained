## ‎توصيل مرتب

QUIC بيضمن in-order delivery للstreams، بس مش بين الstreams. ده يعني إن كل stream هيبعت بيانات ويحافظ على ترتيب البيانات، بس كل stream ممكن يوصل للمقصد بترتيب مختلف عن اللي الapplication بعته!

مثلاً: stream A و B بيتنقلوا من سيرفر لclient. Stream A يبدأ الأول وبعدين stream B. في QUIC، packet ضائع بيأثر بس على الstream اللي الpacket الضائع ينتمي له. لو stream A فقد packet بس stream B مفقدش، stream B ممكن يكمل نقله ويخلص بينما stream A الpacket الضائع بتاعه يتبعت تاني. ده مكانش ممكن مع HTTP/2.

مرسوم هنا بstream أصفر وstream أزرق متبعتين بين اتنين QUIC end-points على connection واحد. هما مستقلين وممكن يوصلوا بترتيب مختلف، بس كل stream بيوصل للapplication بشكل موثوق مرتب.

مثال مصري: فكر في الموضوع زي إنك طلبت وجبتين مختلفتين من مطعمين مختلفين (streamين). لو الطلب الأول اتأخر، الطلب التاني ممكن يوصل الأول ومتستناش الأول. بس كل طلب جوا نفسه مرتب - الفراخ قبل الرز قبل السلطة.

![two QUIC streams between two computers](../images/quic-chain-streams.png)