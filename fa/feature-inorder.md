## توزیع منظم

پروتکل QUIC تحویل/توزیع منظم و کامل جریان‌ها را تضمین می‌کند، اما نه
مابین جریان‌ها. بدین معنا که هر جریان داده را با حفظ ترتیب آن ارسال
می‌کند، اما هر جریان ممکن است که با ترتیبی متفاوت از آنچه که نرم‌افزار
فرستاده است به مقصد رسد!

به‌طور مثال: جریان‌های A و B از یک سرور به یک کارخواه منتقل
شده‌اند. جریان A نسبت به جریان B تقدم دارد. در QUIC، یک بستهٔ گمشده تنها
همان جریانی را که به آن تعلق دارد تحت تأثیر قرار می‌دهد. اگر جریان A یک
بسته را گم کند اما جریان B خیر، جریان B می‌تواند انتقال خود را ادامه دهد و
تکمیل کند در حالی که بستهٔ گمشدهٔ جریان A دوباره فرستاده می‌شود. چنین چیزی در
HTTP/2 مقدور نبود.

در تصویر زیر یک جریان زرد و یک جریان آبی مابین دو پایانهٔ QUIC بر روی یک اتصال
فرستاده شده است. آنها مستقل هستند و می‌توانند با ترتیبی متفاوت برسند، اما
هر جریان دقیقاًً منظم به نرم‌افزار تحویل داده می‌شود.

![two QUIC streams between two computers](../images/quic-chain-streams.png)
