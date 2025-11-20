- - -
يشتغل مع VegasPro15 لسبب ما...
أنصح تقرأ النوته بـobsidian عشان تقرأ براحتك!

كتبت: 2025/11/19
آخر تعديل كان: 2025/11/19

## عن طريق متصفح الملفات
أفتح متصفح ملفاتك وروح لذا المكان
`C:\Program Files\VEGAS\VEGAS Pro 16.0`
أنصحك تستخدم [Everything](https://www.voidtools.com/)، بيساعد كثير.
ملاحظة: عشان تلغي ملف، غير أسمهم لأي شي، عن نفسي أغير أسمهم لكذا `example.dll.backup`

1. so4compoundplug.dll
   يصلح مشاكل الصوت (إن صادفت واحد)
   %%ما يخلي Vegas يعيد تصييغ الملفات بكيفه، خصيصا ملفات الصوت%%
   - بكيفك:
	   ألغي أي **.dll** يبدأ بـ**so4**
	   مثل `so4mediainfolib.Dll`,`So4Reader.dll`...لآخره

2. compoundplug.dll
	يصلح مشاكل ضغط الألوان على `draft preview`

## داخل Vegas pro
علق على **shift** ثم روح لـ**Options** و اضغط على **Preferences**

### داخل خانة الـinternal
أبحث و غير التالي:
1. openCL/GL Interop = false
2. memory needed by Vegas = 4096[^1]
3. memory needed by vegas-64 = 4096[^1]
4. opencl memory size filter = 2048[^1]
5. Enable Legacy (Mainconcept AVC/AAC and Intel HEVC) Render Plugins = True
	هذا يغير في خانة الـ render، لأن حق Magix يكرش بدون سبب.
	بتلاقيها باسم `MainConcept AVC/AAC`
	الخايس اسمه `Magix AVC/ACC`

و أنت هناك يمديك تاخذ نظره عن الـ`trackview`! (اختياري)

### داخل خانة الـGeneral
%%بيطول معك xD%%
أي شيء مذكور هنا تأكد فعِّله، عداه ألغيه:
- Automatically open last project on startup
- Confirm media file deletion when still in use
- Save active prerenders on project dose
- Enable autosave[^2]
- Prompt to adjust project settings to match first media added to timeline
- Check project file type associations at startup
- Render large Wave files as Wave64
- Allow Wave renders up to 4 GB
- Ignore fact chunk when opening compressed Wave files
- Allow pulldown removal when opening 24p DV
- AAF Export - I-Ise frame unit for audio
- Enable no-recompress rendering
- Allow legacy GPIJ rendering
- Prompt to keep files after recording
- Create undos for FX parameter changes
- Keep bypassed FX running (to avoid pause on bypass/enable)
- Favor audio sync when playing Variable Frame Rate (VFR) media
- Automatically name regions and markers if not playing
- use linear scrub range
- Make spacebar and F 12 Play/Pause instead of Play/Stop
- Always draw marker lines
- Allow edit cursor to be dragged

## لكروت إنفيديا
روح للمتحكم ( أي control panel) ثم لـ**Manage 3D settings** تحت خانه *3d Settings*
دور على **OpenGL GDI compatiblitly** و حطه **Prefer Compatiblte**

## كيف احفظ/ابدل اعدادات الواجهه و اللوح
روح للموقع
`C:\Users\<اسمك>\AppData\Roaming\VEGAS Pro\16.0`

وااااا بدلهم و عدلهم مثل ماتبي!

### مثال
انسخ التالي و حطه داخل ملف text **وصيغه** `keyboard.ini` بالتمام، غير هذا ماراح يشتغل
تذكر قبل لا تبدل ملف `keyboard.ini` انك تحفظ نسخه منه

```
[SfKeyMap]
Name=[Default]
[Global]
Tools.BuildRAMPreview=Ctrl+Alt+B;F13
Null.0=Shift+F12
[TrackView]
Edit.Group.DeleteAll=A
Edit.Ripple.All=F
Null.0=Ctrl+F
Null.1=Ctrl+Shift+F
Null.2=Shift+Play
[Trimmer]
Null.0=Shift+Play
```

## هدايااااا
سوي نص و حط بيه
```
del /s /f /q *.sfk
```
و صيغه إلى **.bat** و بوووووم!
صار عندك أمر يحذف ملفات **.sfk** الخايسه! (يحذف من الجذر فقط)

بعض الإضافات *المجانيه* [هنا](https://github.com/RatinFX/VegasProFlow)، شيك عليهم!
بس قبلها تأكد أنك مثبت
[.net 4.8](https://dotnet.microsoft.com/en-us/) أو أعلى

# ملاحظة:
إذا أستخدمت VisualStudioCode 2024 أو أعلى، ممكن تواجه كراشات غريبه.
والحمدلله فيه حل للموضوع، تحتاج ملف اسمه `vcomp140.dll` و لازم تاخذه من ويندوز ما قد تثبت فيه VSC2024 أو أعلى
بعض المعلومات عنه
- file version: `14.44.35211.0`
- product version: `14.44.35211.0`
- file size: `188KB`

حمله/انسخه إلى جذر vegas و حطه هناك
`C:\Users\<Your User Name>\AppData\Roaming\VEGAS Pro\16.0`
ثم إفتح vegas عادي

# خلصنا!

[^1]:  [Mega Bytes](https://en.wikipedia.org/wiki/Binary_prefix).
ويندوز يفصل بين الوحدات كل 1024، عكس يونيكس و أشباهه يحول لكل 1000

[^2]:  ملاحظة! **طبيعيا** Vegas يحفظ المشروع كل 5 دقايق بصايغه 300,000 جزء ثانية
يمديك تغيره في خانه الـinternal و تبحث عن `msAutoSaveInterval` (اكتب save يكفي)
و غير القيمه! أنصح تحطه 60,000 جزء أي دقيقه.