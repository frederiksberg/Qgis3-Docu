QGIS Installation
===========================

Først trin er at installere Qgis 3 hos brugerne. Der skal ikke ændres nogen instillinger under installationen.

# Konfigurering 

Der er på forhånd opsat en profil til brugeren. Denne profil skal kopieres til brugers computer under ```C:\qgis ``` 

#### Projekt filer

For at Qgis bruger den profil som vi har oprettet, når man åbner en projekt fil. Skal der ændres i filen 

```qgis.bat (C:\Program Files\QGIS 3.0\bin) ```
```batch
@echo off
call "%~dp0\o4w_env.bat"
call qt5_env.bat
call py3_env.bat
@echo off
path %OSGEO4W_ROOT%\apps\qgis\bin;%PATH%
set QGIS_PREFIX_PATH=%OSGEO4W_ROOT:\=/%/apps/qgis
set GDAL_FILENAME_IS_UTF8=YES
rem Set VSI cache to be used as buffer, see #6448
set VSI_CACHE=TRUE
set VSI_CACHE_SIZE=1000000
set QT_PLUGIN_PATH=%OSGEO4W_ROOT%\apps\qgis\qtplugins;%OSGEO4W_ROOT%\apps\qt5\plugins
start "QGIS" /B "%OSGEO4W_ROOT%\bin\qgis-bin.exe" {--profiles-path C:\qgis} %* <---- det i tuborg tegn skal tilføjes
```
#### Shortcut

Herefter skal der også ændres i shortcut til Qgis 3, hvor der skal tilføjes det samme som i .bat filen.

```"C:\Program Files\QGIS 3.0\bin\qgis-bin.exe" --configpath "C:\Users\nibr02\Documents"```
