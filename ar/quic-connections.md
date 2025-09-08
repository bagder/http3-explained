# Connections

QUIC connection هو محادثة واحدة بين طرفين من QUIC endpoints. إعداد connection في QUIC بيجمع version negotiation مع cryptographic و transport handshakes عشان يقلل latency إعداد الـ connection.

عشان تبعت داتا فعلاً على connection زي ده، لازم تعمل stream واحد أو أكتر وتستخدمه.

## Connection ID

كل connection عنده مجموعة من connection identifiers، أو connection IDs، وكل واحد منهم يقدر يعرف الـ connection. Connection IDs بتتختار بشكل مستقل من endpoints؛ كل endpoint بيختار connection IDs اللي الطرف التاني هيستخدمها.

الوظيفة الأساسية للـ connection IDs دي هي التأكد إن تغييرات العناوين في طبقات البروتوكول الأقل (UDP, IP, وتحت) متخليش packets بتاعة QUIC connection توصل للمكان الغلط.

باستغلال connection ID، connections تقدر كده تنتقل بين IP addresses وشبكات مختلفة بطرق TCP مكانش يقدر يعملها أبداً. مثلاً، migration يخلي download شغال ينتقل من شبكة موبايل لwifi أسرع لما المستخدم ياخد جهازه لمكان فيه wifi. وبنفس الطريقة، الـ download يقدر يكمل على شبكة الموبايل لو الwifi بقى مش متاح.

## Port numbers

QUIC مبني على UDP، فـ 16 bit port number field بتستخدم عشان تميز بين connections الجاية.

## Version negotiation

QUIC connection request اللي جاي من client هيقول للسيرفر أي نسخة QUIC protocol عايز يتكلم بيها، والسيرفر هيرد بقائمة النسخ المدعومة عشان الـ client يختار منها.

مثال مصري: فكر في Connection ID زي رقم الموبايل بتاعك. حتى لو غيرت مكانك من البيت للشغل أو من wifi للموبايل، رقمك نفسه وأي حد عايز يكلمك يقدر يوصلك. ده عكس TCP اللي زي التليفون الأرضي - لازم تكون في مكان معين عشان حد يقدر يكلمك.