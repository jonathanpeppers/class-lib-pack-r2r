# class-lib-pack-r2r

A sample to include ReadyToRun compiled assemblies in a NuGet/class library.

To try it:

```dotnetcli
> dotnet pack -c Release
...
  Successfully created package 'C:\src\class-lib-pack-r2r\bin\Release\class_lib_pack_r2r.win-x86.1.0.0.nupkg'.
  Successfully created package 'C:\src\class-lib-pack-r2r\bin\Release\class_lib_pack_r2r.win-arm64.1.0.0.nupkg'.
  Successfully created package 'C:\src\class-lib-pack-r2r\bin\Release\class_lib_pack_r2r.win-x64.1.0.0.nupkg'.
```

The files packed inside are ~16kb R2R assemblies:

```powershell
> 7z l .\bin\Release\class_lib_pack_r2r.win-x64.1.0.0.nupkg

7-Zip 22.01 (x64) : Copyright (c) 1999-2022 Igor Pavlov : 2022-07-15

Scanning the drive for archives:
1 file, 4051 bytes (4 KiB)

Listing archive: C:\src\class-lib-pack-r2r\bin\Release\class_lib_pack_r2r.win-x64.1.0.0.nupkg

--
Path = C:\src\class-lib-pack-r2r\bin\Release\class_lib_pack_r2r.win-x64.1.0.0.nupkg
Type = zip
Physical Size = 4051

   Date      Time    Attr         Size   Compressed  Name
------------------- ----- ------------ ------------  ------------------------
2022-11-28 14:56:30 .....          520          294  _rels\.rels
2022-11-28 14:56:30 .....          408          255  class_lib_pack_r2r.win-x64.nuspec
2022-11-28 20:56:30 .....        16384         2156  lib\net7.0\class-lib-pack-r2r.dll
2022-11-28 14:56:30 .....          465          214  [Content_Types].xml
2022-11-28 14:56:30 .....          641          376  package\services\metadata\core-properties\933e69ad2ea842fab6ae4fc73dd579bd.psmdcp
------------------- ----- ------------ ------------  ------------------------
2022-11-28 20:56:30              18418         3295  5 files
```

While regular assemblies are more like ~3.5kb:

```powershell
ls .\bin\Release\net7.0\win-arm64\*.dll
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        11/28/2022   2:56 PM           3584 class-lib-pack-r2r.dll
```
