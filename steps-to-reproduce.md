# Find deps
 * watch in cspropj files for additional lib or include (Paths)
  * found: libsndfile, muparserx, fftw3
 * try find this deps
  1) using vcpkg
```shell
> vcpkg search fft
    clfft                    2.12.2#6         clFFT is an OpenCL 1.2 accelerated Fast Fourier Transform library.
    dlib[fftw3]                               fftw3 support for dlib
    fftw3                    3.3.10#5         FFTW is a C subroutine library for computing the discrete Fourier transfor...
    fftw3[avx]                                Builds part of the library with avx, sse2, sse
    fftw3[avx2]                               Builds part of the library with avx2, fma, avx, sse2, sse
    fftw3[openmp]                             Builds openmp enabled lib
    fftw3[sse]                                Builds part of the library with sse
    fftw3[sse2]                               Builds part of the library with sse2, sse
    fftw3[threads]                            Enable threads in fftw3
    fftwpp                   2019-12-19#2     FFTW++ is a C++ header/MPI transpose for Version 3 of the highly optimized...
    itk[cufftw]                               Use CUDA FFTW
    kissfft                  2021-11-14       A Fast Fourier Transform (FFT) library that tries to Keep it Simple, Stupid
    matplotplusplus[fftw]                     fftw3 support for Matplot++
    pffft                    2021-10-09#1     PFFFT, a pretty fast Fourier Transform.
    simple-fft               2020-06-14#1     Header-only C++ library implementing fast Fourier transform of 1D, 2D and ...
    vkfft                    1.2.17           Vulkan/CUDA/HIP/OpenCL/Level Zero Fast Fourier Transform library
    xtensor-fftw             2019-11-30#2     FFTW bindings for the xtensor C++14 multi-dimensional array library
> vcpkg install fftw3[avx]:x64-window
    Computing installation plan...
    The following packages will be built and installed:
        fftw3[avx,core]:x64-windows -> 3.3.10#5
    Detecting compiler hash for triplet x64-windows...
    Restored 0 package(s) from C:\Users\dominic\AppData\Local\vcpkg\archives in 910.2 us. Use --debug to see more details.
    Installing 1/1 fftw3:x64-windows...
    Building fftw3[avx,core]:x64-windows...
    -- Downloading https://www.fftw.org/fftw-3.3.10.tar.gz -> fftw-3.3.10.tar.gz...
    -- Extracting source E:/c-cpp/vcpkg/downloads/fftw-3.3.10.tar.gz
    -- Applying patch omp_test.patch
    -- Applying patch patch_targets.patch
    -- Applying patch fftw3_arch_fix.patch
    .....
    Total install time: 1.199 min
    fftw3 provides CMake targets:

    # this is heuristically generated, and may not be correct
    find_package(FFTW3 CONFIG REQUIRED)
    target_link_libraries(main PRIVATE FFTW3::fftw3)

    find_package(FFTW3f CONFIG REQUIRED)
    target_link_libraries(main PRIVATE FFTW3::fftw3f)

    find_package(FFTW3l CONFIG REQUIRED)
    target_link_libraries(main PRIVATE FFTW3::fftw3l)

> vcpkg search muparserx
The result may be outdated. Run `git pull` to get the latest results.
If your port is not listed, please open an issue at and/or consider making a pull request.    -  https://github.com/Microsoft/vcpkg/issues

> vcpkg search sndfile
    fluidsynth[sndfile]                       Enable rendering to file and SF3 support
    gstreamer[sndfile]                        Enable support for the SndFile file reader/writer
    libsndfile               1.1.0#1          A library for reading and writing audio files
    libsndfile[experimental]                  Enable experimental code
    libsndfile[external-libs]                 Enable FLAC, Vorbis, and Opus codecs
    libsndfile[mpeg]                          Enable MPEG codecs
    libsndfile[regtest]                       Build regtest
    simage[sndfile]                           Use libsndfile to load/save sampled sound
    sndfile                  0#1              x Library to read, write and manipulate many soundfile types.
    sndfile[external-libs]                    Support Ogg Vorbis and FLAC audio files

> vcpkg install libsndfile:x64-windows
    Computing installation plan...
    The following packages will be built and installed:
      * libflac[core]:x64-windows -> 1.3.4#1
      * libogg[core]:x64-windows -> 1.3.5
        libsndfile[core,external-libs,mpeg]:x64-windows -> 1.1.0#1
      * libvorbis[core]:x64-windows -> 1.3.7#2
      * mp3lame[core]:x64-windows -> 3.100#10
      * mpg123[core]:x64-windows -> 1.29.3
      * opus[core]:x64-windows -> 1.3.1#9
      * yasm[core,tools]:x64-windows -> 1.3.0#5
      * yasm-tool-helper[core]:x64-windows -> 2020-03-11#1
    Additional packages (*) will be modified to complete this operation.
    Detecting compiler hash for triplet x64-windows...
    Restored 0 package(s) from C:\Users\dominic\AppData\Local\vcpkg\archives in 1.732 ms. Use --debug to see more details.
    Installing 1/9 libogg:x64-windows...
    Building libogg[core]:x64-windows...
    -- Using cached xiph-ogg-v1.3.5.tar.gz.
    -- Cleaning sources at E:/c-cpp/vcpkg/buildtrees/libogg/src/v1.3.5-1a4243fef9.clean. Use --editable to skip cleaning for the packages you specify.
    -- Extracting source E:/c-cpp/vcpkg/downloads/xiph-ogg-v1.3.5.tar.gz
    -- Using source at E:/c-cpp/vcpkg/buildtrees/libogg/src/v1.3.5-1a4243fef9.clean
    -- Found external ninja('1.11.0').
    -- Configuring x64-windows
    -- Building x64-windows-dbg
    -- Building x64-windows-rel

    Elapsed time to handle libsndfile:x64-windows: 16 s
    Total install time: 1.508 min
    libsndfile provides CMake targets:

        # this is heuristically generated, and may not be correct
        find_package(SndFile CONFIG REQUIRED)
        target_link_libraries(main PRIVATE SndFile::sndfile)

```

  * missing muparserx
    * https://github.com/beltoforion/muparserx/releases
  * create dir 3rd-party
  * extract  muparserx
  * add Project-Include Path (All Settings/All Builds)(VC++-Verzeichnisse/Externe Includeverzeichnisse): `$(SolutionDir)\3rd-party\muparserx-4.0.11\parser`
```
  * compile
  > LNK1181	Eingabedatei "muparserx.lib" kann nicht geöffnet werden.	EqualizerAPO	E:\c-cpp\equalizerapo\EqualizerAPO\LINK	1
```
  * `\3rd-party\muparserx-4.0.11\`contains cmake file
    * build muparserx MSVS Projectfiles using cmake:
```
> cd \3rd-party\muparserx-4.0.11
> cmake.exe "-DCMAKE_TOOLCHAIN_FILE=e:\c-cpp\vcpkg\scripts\buildsystems\vcpkg.cmake" -G "Visual Studio 17 2022" -Ax64 -Bbuild/win64 -H.

    -- Selecting Windows SDK version 10.0.22000.0 to target Windows 10.0.19045.
    -- The CXX compiler identification is MSVC 19.34.31935.0
    -- Detecting CXX compiler ABI info
    -- Detecting CXX compiler ABI info - done
    -- Check for working CXX compiler: C:/Program Files/VisualStudio/2022/Community/VC/Tools/MSVC/14.34.31933/bin/Hostx64/x64/cl.exe - skipped
    -- Detecting CXX compile features
    -- Detecting CXX compile features - done
    -- Building muparserx version: 4.0.11
    -- Using install prefix: C:/Program Files/muparserx
    -- Configuring done
    -- Generating done
    -- Build files have been written to: E:/c-cpp/equalizerapo/3rd-party/muparserx-4.0.11/build/win64
```
  * use generated muparserx.sln file to compile muparserx:
    * get vc++ environment using vswhere to get path to vcvars.bat (or similar) to access msbuild via cli:
```
> FOR /F "tokens=*" %g IN ('"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vswhere" -products * -property installationPath') do (SET vspath=%g)
> echo %VSPATH%
    C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools
> call "%vspath%\Common7\Tools\VsDevCmd.bat"
    **********************************************************************
    ** Visual Studio 2022 Developer Command Prompt v17.4.2
    ** Copyright (c) 2022 Microsoft Corporation
    **********************************************************************
```
> cd build\win64
> msbuild /p:PreferredToolArchitecture=x64 /p:configuration=MinSizeRel muparserx.sln
    MSBuild version 17.4.0+18d5aef85 for .NET Framework
    Die Projekte in dieser Projektmappe werden nacheinander erstellt. Um eine parallele Erstellung zu ermöglichen, müssen Sie den Schalter "-m" hinzufügen.
    Der Buildvorgang wurde am 15.12.2022 16:56:07 gestartet.
    Projekt "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\build\win64\muparserx.sln" auf Knoten "1" (Standardziele).
    ValidateSolutionConfiguration:
      Die Projektmappenkonfiguration "MinSizeRel|x64" wird erstellt.
    ValidateProjects:
      Das Projekt "INSTALL" ist in der Projektmappenkonfiguration "MinSizeRel|x64" nicht zum Erstellen ausgewählt.
    Das Projekt "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\build\win64\muparserx.sln" (1) erstellt "E:\c-cpp\equaliz
    erapo\3rd-party\muparserx-4.0.11\build\win64\ALL_BUILD.vcxproj.metaproj" (2) auf Knoten "1" (Standardziele).
    PrepareForBuild:
      Das Verzeichnis "muparserx.dir\MinSizeRel\" wird erstellt.
      Das Verzeichnis "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\build\win64\MinSizeRel\" wird erstellt.
      Das Verzeichnis "muparserx.dir\MinSizeRel\muparserx.tlog\" wird erstellt.
    InitializeBuildStatus:
      "muparserx.dir\MinSizeRel\muparserx.tlog\unsuccessfulbuild" wird erstellt, da "AlwaysCreate" angegeben wurde.
    CustomBuild:
      Building Custom Rule E:/c-cpp/equalizerapo/3rd-party/muparserx-4.0.11/CMakeLists.txt
    VcpkgTripletSelection:
      Not using Vcpkg because VcpkgEnabled is "false"
    ClCompile:
      C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Tools\MSVC\14.34.31933\bin\HostX64\x64\CL.exe /c /I
      "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser" /nologo /W3 /WX- /diagnostics:column /MP /O1 /Ob1 /D _MBCS
      /D WIN32 /D _WINDOWS /D NDEBUG /D "CMAKE_INTDIR=\"MinSizeRel\"" /Gm- /EHsc /MD /GS /fp:precise /Zc:wchar_t /Zc:forSco
      pe /Zc:inline /GR /Fo"muparserx.dir\MinSizeRel\\" /Fd"E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\build\win64\Mi
      nSizeRel\muparserx.pdb" /external:W3 /Gd /TP /errorReport:queue "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\par
      ser\mpError.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpFuncCmplx.cpp" "E:\c-cpp\equalizerapo\3rd
      -party\muparserx-4.0.11\parser\mpFuncCommon.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpFuncMatri
      x.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpFuncNonCmplx.cpp" "E:\c-cpp\equalizerapo\3rd-party\
      muparserx-4.0.11\parser\mpFuncStr.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpICallback.cpp" "E:\
      c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpIOprt.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\p
      arser\mpIOprtBinShortcut.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpIPackage.cpp" "E:\c-cpp\equa
      lizerapo\3rd-party\muparserx-4.0.11\parser\mpIToken.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpI
      ValReader.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpIValue.cpp" "E:\c-cpp\equalizerapo\3rd-part
      y\muparserx-4.0.11\parser\mpIfThenElse.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpOprtBinAssign.
      cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpOprtBinCommon.cpp" "E:\c-cpp\equalizerapo\3rd-party\m
      uparserx-4.0.11\parser\mpOprtBinShortcut.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpOprtCmplx.cp
      p" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpOprtIndex.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparse
      rx-4.0.11\parser\mpOprtMatrix.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpOprtNonCmplx.cpp" "E:\c
      -cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpOprtPostfixCommon.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparse
      rx-4.0.11\parser\mpPackageCmplx.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpPackageCommon.cpp" "E
      :\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpPackageMatrix.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparser
      x-4.0.11\parser\mpPackageNonCmplx.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpPackageStr.cpp" "E:
      \c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpPackageUnit.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4
      .0.11\parser\mpParser.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpParserBase.cpp" "E:\c-cpp\equal
      izerapo\3rd-party\muparserx-4.0.11\parser\mpParserMessageProvider.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0
      .11\parser\mpRPN.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpScriptTokens.cpp" "E:\c-cpp\equalize
      rapo\3rd-party\muparserx-4.0.11\parser\mpTest.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpTokenRe
      ader.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpValReader.cpp" "E:\c-cpp\equalizerapo\3rd-party\
      muparserx-4.0.11\parser\mpValue.cpp" "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpValueCache.cpp" "E:\c
      -cpp\equalizerapo\3rd-party\muparserx-4.0.11\parser\mpVariable.cpp"
      mpError.cpp
      mpFuncCmplx.cpp
      mpFuncCommon.cpp
      mpFuncMatrix.cpp
      mpFuncNonCmplx.cpp
      mpFuncStr.cpp
      mpICallback.cpp
      mpIOprt.cpp
      mpIOprtBinShortcut.cpp
      mpIPackage.cpp
      mpIToken.cpp
      mpIValReader.cpp
      mpIValue.cpp
      mpIfThenElse.cpp
      mpOprtBinAssign.cpp
      mpOprtBinCommon.cpp
....

    "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\build\win64\muparserx.sln" (Standardziel) (1) ->
    "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\build\win64\ALL_BUILD.vcxproj.metaproj" (Standardziel) (2) ->
    "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\build\win64\example.vcxproj.metaproj" (Standardziel) (4) ->
    "E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\build\win64\example.vcxproj" (Standardziel) (7) ->
      E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\sample\example.cpp(262,72): warning C4996: 'localtime': This function or variable may be unsafe.
      Consider using localtime_s instead. To disable deprecation, use _CRT_SECURE_NO_WARNINGS. See online help for details. [E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\build\win64\example.vcxproj]
      E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\sample\example.cpp(318,17): warning C4996: 'fopen': This function or variable may be unsafe. Consider using fopen_s instead. To disable deprecation, use _CRT_SECURE_NO_WARNINGS.
      See online help for details. [E:\c-cpp\equalizerapo\3rd-party\muparserx-4.0.11\build\win64\example.vcxproj]
    16 Warnung(en)
    0 Fehler
    Verstrichene Zeit 00:00:04.30

````
  * add Project-Lib Path (All Settings/All Builds) (VC++-Verzeichnisse/Bibliothekspfade): `$(SolutionDir)\3rd-party\muparserx-4.0.11\build\win64\MinSizeRel`

```
> msbuild /p:PreferredToolArchitecture=x64 /p:configuration=MinSizeRel muparserx.sln

Fehler	LNK1181	Eingabedatei "libsndfile-1.lib" kann nicht geöffnet werden.	EqualizerAPO	E:\c-cpp\equalizerapo\EqualizerAPO\LINK	1

```
 * fix libsndfile-1.lib to sndfile.lib (as found in vcpkg installed/windows-x64/...) in EqualizerAPO Project -> Linker/Zusätzliche Abhängigkeiten (first reset to Debug / x86)
 * build
 ```
 > msbuild /p:PreferredToolArchitecture=x64 /p:configuration=MinSizeRel muparserx.sln
  Fehler	LNK1181	Eingabedatei "libfftw3f-3.lib" kann nicht geöffnet werden.	EqualizerAPO	E:\c-cpp\equalizerapo\EqualizerAPO\LINK	1
```
  * same here...change to fftw3f.lib


