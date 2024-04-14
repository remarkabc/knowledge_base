# modify mkv in mkvtoolnix batch
```powershell
chcp 65001
@echo off
echo "modify mkv in batch"
setlocal enableDelayedExpansion
FOR /l %%N in (90,1,90) do (
    set "n=000%%N"
    ECHO S01.E!n:~-3!.mkv
    rem D:\Tool\mkvtoolnix\mkvmerge.exe --ui-language en --priority lower --output ^"\\192.168.123.10\Video01\TV\Saint Seiya ^(1986^)\圣斗士星矢 S01\nosub.S01.E!n:~-3!.mkv^" --no-subtitles ^"^(^" ^"\\192.168.123.10\Video01\TV\Saint Seiya ^(1986^)\圣斗士星矢 S01\S01.E!n:~-3!.mkv^" ^"^)^" --title S01.E!n:~-3!
    rem D:\Tool\mkvtoolnix\mkvmerge.exe --ui-language en --priority lower --output ^"\\192.168.123.10\Video01\TV\Saint Seiya ^(1986^)\圣斗士星矢 S01\new.S01.E!n:~-3!.mkv^" --audio-tracks 1,6 --no-subtitles --language 0:und --display-dimensions 0:1440x1080 --language 1:zh --default-track-flag 1:yes --language 6:ja ^"^(^" ^"\\192.168.123.10\Video01\TV\Saint Seiya ^(1986^)\圣斗士星矢 S01\S01.E!n:~-3!.mkv^" ^"^)^" --title S01.E!n:~-3! --track-order 0:0,0:1,0:6
    D:\Tool\mkvtoolnix\mkvmerge.exe --ui-language en --priority lower --output ^"\\192.168.123.10\Video01\TV\Saint Seiya ^(1986^)\圣斗士星矢 S01\new.S01.E!n:~-3!.mkv^" --audio-tracks 1,5 --language 0:und --display-dimensions 0:1440x1080 --language 1:zh --default-track-flag 1:yes --language 5:ja ^"^(^" ^"\\192.168.123.10\Video01\TV\Saint Seiya ^(1986^)\圣斗士星矢 S01\nosub.S01.E!n:~-3!.mkv^" ^"^)^" --title S01.E!n:~-3! --track-order 0:0,0:1,0:5
)
```