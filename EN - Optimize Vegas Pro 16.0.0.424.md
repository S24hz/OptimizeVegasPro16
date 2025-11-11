- - -
works also with Vegas 15 too if you use it for some reason...
use obsidian/notepad++ for better reading experience!

Created in: 09/11/2025 - dd/mm/yyyy
last time updated in: 11/11/2025 - dd/mm/yyyy
## in the file explorer
you can find those files on this path
`C:\Program Files\VEGAS\VEGAS Pro 16.0`
i recommend you to use [Everything](https://www.voidtools.com/) for this process
to disable it you need to open Vegas file location and rename it, personally i rename it like this `example.dll.backup`

1. so4compoundplug.dll
   fix audio problems in Vegas (if you faced some)
   %%it does not let Vegas to change the files format especially audio ones unnecessarily%%
   - optional:
	   disable any **.dll** that contain  **so4**
	   like `so4mediainfolib.Dll`,`So4Reader.dll`...etc
2. compoundplug.dll
	fix color compression on draft preview
## inside Vegas pro
hold **shift** then go to **Options** and click **Preferences**
go to internal:
and
### inside the Internal tap
1. openCL/GL Interop = false
2. memory needed by Vegas = 4096[^1]
3. memory needed by vegas-64 = 4096[^1]
4. opencl memory size filter = 2048[^1]
5. Enable Legacy (Mainconcept AVC/AAC and Intel HEVC) Render Plugins = True
   this one affect the render page, because the Magix renderer crash randomly for no reason
   you will find it under the name of `MainConcept AVC/AAC`
   the bad one is named `Magix AVC/ACC`

while you there take a shot and search about `trackview`! (optional)
### inside the General tap
anything *written* here is an option checked!
pleas make sure to **uncheck** any option it name not mentioned!
%%this one will be the long one xD%%
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
- Make spacebar and F12 Play/Pause instead of Play/Stop
- Always draw marker lines
- Allow edit cursor to be dragged
  
## GPU: NV - Control Panel
open the control panel and go to **Manage 3D settings** under *3d Settings*
find **OpenGL GDI compatiblitly** and make it **Prefer Compatiblte**

## How to Backup/Replace your layout and keyboard shortcuts
Go to this location
`C:\Users\<Your User Name>\AppData\Roaming\VEGAS Pro\16.0`

then go and backup/replace them!

### Example:
copy the following text, then put it into a text file and **save them as** `keyboard.ini`, it must be 1:1
remember to **backup** the original `keyboard.ini` file!

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
## LAST THINGS GIFET!!!
make a text file and past this
```
del /s /f /q *.sfk
```
then **save it as** .bat file
what it does is make sure to **clean any** .sfk file in your folder!

some cool *free* plugins [here](https://github.com/RatinFX/VegasProFlow), check them out!
and before you go to the installation process, make sure you have *at least* [.net 4.8](https://dotnet.microsoft.com/en-us/) or higher

# Done!

[^1]:  [Mega Bytes](https://en.wikipedia.org/wiki/Binary_prefix).
WindowsNT uses 1024 as a unit prefix base, unlike other systems (like Mac/Unix) that use 1000.

[^2]:  Tip! by **default** Vegas save the project file every 5min or in other words 300,000ms
and you can change that by going in the internal tap and write `msAutoSaveInterval` (just write save)
and change it! i recommend to change it to 60,000ms aka 1min.
