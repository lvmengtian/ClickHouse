---
machine_translated: true
machine_translated_rev: d734a8e46ddd7465886ba4133bff743c55190626
toc_priority: 31
toc_title: "\u0645\u0639\u0631\u0641\u06CC \u0634\u0631\u06A9\u062A"
---

# ورود خانواده موتور {#log-engine-family}

هنگامی که شما نیاز به سرعت نوشتن بسیاری از جداول کوچک (تا حدود 1 میلیون ردیف) و بعد به عنوان یک کل خواندن این موتور برای حالات توسعه داده شد.

موتورهای خانواده:

-   [خط زدن](stripelog.md)
-   [ثبت](log.md)
-   [جمع شدن](tinylog.md)

## ویژگیهای مشترک {#common-properties}

موتورها:

-   ذخیره داده ها بر روی یک دیسک.

-   اضافه کردن داده ها به پایان فایل هنگام نوشتن.

-   قفل پشتیبانی برای دسترسی همزمان داده ها.

    در طول `INSERT` نمایش داده شد, جدول قفل شده است, و دیگر نمایش داده شد برای خواندن و نوشتن داده ها هر دو منتظر جدول برای باز کردن. اگر هیچ نمایش داده شد نوشتن داده ها وجود دارد, هر تعداد از نمایش داده شد خواندن داده ها را می توان به صورت همزمان انجام.

-   پشتیبانی نمی کند [جهش](../../../sql-reference/statements/alter.md#alter-mutations) عملیات.

-   هنوز شاخص را پشتیبانی نمی کند.

    این به این معنی است که `SELECT` نمایش داده شد برای محدوده داده ها موثر نیست.

-   هنوز داده نوشتن نیست اتمی.

    شما می توانید یک جدول با داده های خراب اگر چیزی می شکند عملیات نوشتن, مثلا, خاموش کردن سرور غیر طبیعی.

## تفاوت {#differences}

این `TinyLog` موتور ساده ترین در خانواده است و فقیرترین قابلیت ها و کمترین بهره وری را فراهم می کند. این `TinyLog` موتور از خواندن داده های موازی با چندین موضوع پشتیبانی نمی کند. این اطلاعات کندتر از موتورهای دیگر در خانواده است که خواندن موازی را پشتیبانی می کند و تقریبا به عنوان بسیاری از توصیفگرها به عنوان `Log` موتور به دلیل ذخیره هر ستون در یک فایل جداگانه. در حالات کم بار ساده استفاده کنید.

این `Log` و `StripeLog` موتورهای پشتیبانی خواندن داده های موازی. هنگام خواندن داده ها, تاتر با استفاده از موضوعات متعدد. هر موضوع یک بلوک داده جداگانه را پردازش می کند. این `Log` موتور با استفاده از یک فایل جداگانه برای هر ستون از جدول. `StripeLog` ذخیره تمام داده ها در یک فایل. در نتیجه `StripeLog` موتور با استفاده از توصیف کمتر در سیستم عامل, اما `Log` موتور فراهم می کند بهره وری بالاتر در هنگام خواندن داده ها.

[مقاله اصلی](https://clickhouse.tech/docs/en/operations/table_engines/log_family/) <!--hide-->
