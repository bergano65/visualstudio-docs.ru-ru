---
title: "Поддержка Visual Basic 6.0 оператор | Документы Microsoft"
ms.date: 08/28/2017
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs: VB
helpviewer_keywords:
- VB6 support
- Visual Basic 6.0 support
ms.assetid: ffc5ba4d-44d7-4ef7-a3f6-38a8738bf127
author: paulyuk
ms.author: paulyuk
ms.workload: paulyuk
ms.openlocfilehash: a8977aad735a115089685ed0032b3d358d8b89c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="support-statement-for-visual-basic-60-on-windows"></a>Информация о поддержке для Visual Basic 6.0 в Windows


## <a name="executive-summary"></a>Резюме администрации

Команды Visual Basic фиксируется «Он просто работает» совместимость для приложений Visual Basic 6.0 на поддерживаемых операционных системах Windows: 

- Windows 10
- Windows 8.1
- Windows 7
- Windows Server 2016
- Windows Server 2012, включая R2
- Windows Server 2008, включая R2

Команды Visual Basic цель состоит в приложениях Visual Basic 6.0 продолжают работать в поддерживаемых версиях Windows. Как описано в этом документе выполнения core Visual Basic 6.0 будет поддерживается для полное время поддерживаемых версий Windows, который имеет пять лет Основная фаза поддержки следуют пять лет расширенной поддержки (http://support.microsoft.com/gp/lifepolicy). Поддержка панель будет сокращено до серьезных регрессий и важных проблемах безопасности для существующих приложений.

## <a name="technical-summary"></a>Технические сведения

Visual Basic 6.0 состоит из этих ключевых результатов:
- Visual Basic 6.0 IDE (интегрированной среде разработки).
- Среда выполнения Visual Basic 6.0: базовый библиотеки и подсистема выполнения, используемые для запуска приложений VB 6.0.
- Файлы расширенной среды выполнения Visual Basic 6.0: выбранные файлы OCX элементов управления ActiveX, библиотеки и средства доставки со носителя IDE и при выпуске в Интернете.

## <a name="the-visual-basic-60-ide"></a>Visual Basic 6.0 IDE

Интегрированная среда разработки Visual Basic 6.0 больше не поддерживается 8 апреля 2008 г. Кроме того, команды Windows и Visual Basic протестированы интегрированная среда разработки Visual Basic 6.0 на Windows Vista, Windows 7, Windows Server 2008, Windows 8 и Windows 8.1 для понимания и уменьшения (если применимо) проблемы совместимости на 32-разрядные версии Windows (см. [64-разрядной версии Windows](#62-bit-windows) ниже, в разделе для получения дополнительных сведений о 64-разрядных систем). Это объявление не изменяет политику поддержки для интегрированной среды разработки.

## <a name="the-visual-basic-60-runtime"></a>Среда выполнения Visual Basic 6.0

Среда выполнения Visual Basic 6.0 определен как скомпилированный двоичный файл, изначально включенных в список распространения для Visual Basic 6.0. Эти файлы были отмечены как распространяемый в оригинальная лицензия Visual Basic 6.0. Эти файлы примеры библиотеки времени выполнения Visual Basic 6.0 (`msvbvm60.dll`), элементов управления (т. е. `msflxgrd.ocx`) вместе с среды выполнения поддерживает файлы для других основных функциональных областей (т. е. MDAC).

Среда выполнения состоит из трех групп:

- Поддерживаемые файлы среды CLR--доставке в операционной системе

   Файлы среды выполнения Visual Basic 6.0 ключ, используемый в большинстве сценариев приложений, входящим в и поддерживается в течение времени существования поддерживаемых версий Windows. Это время жизни — пять лет Основная фаза поддержки и пять лет расширенной поддержки от времени, который поставляется в данной версии Windows. Эти файлы были протестированы на совместимость как часть наших тестирования приложений Visual Basic 6.0, под управлением поддерживаемых версий Windows. 

   > [!NOTE]
   > Все поддерживаемые версии Windows содержать почти те же список файлов и redist требования для приложений, содержащих эти файлы должны быть практически идентичны. Это одно из основных отличий `TriEdit.dll` был удален из Windows Vista и более поздних версиях.

- Поддерживаемые файлы среды выполнения —-дополнительные файлы для распространения с приложением

   Этот расширенный список состоит из ключевых элементов управления, библиотек и средств, устанавливаемых с компакт-диска интегрированной среды разработки или на сайте Microsoft.com на компьютере разработчика. Как правило VB6 IDE по умолчанию устанавливается эти элементы управления на компьютере разработчика. Разработчику по-прежнему необходимо повторно распространить эти файлы с приложением. Поддерживаемая версия файла доступна в центре загрузки Майкрософт (http://go.microsoft.com/fwlink/?LinkID=142927).

- Файлы среды CLR не поддерживается

   Некоторые файлы, либо находятся за пределами основной поддержки или никогда не были включены в составе redist среды выполнения (например, они были включены в `\Tools` папки на носителе интегрированной среды разработки для поддержки прежних версий приложений VB4/VB5, или они были сторонние элементы управления). Эти файлы не поддерживаются в Windows. Вместо этого они подвержены независимо от поддержки соглашение действует для носителе, с которого они поставляются с. Это подразумевает каких-либо гарантий вокруг поддержки и обслуживания. В некоторых случаях более поздних версиях эти библиотеки поддерживаются. Ниже приведены сведения об обратной совместимости и миграции для поддерживаемых версий.

Сведения о файлах, включенных в каждой группы поддержки см. в разделе [определение среды выполнения](#runtime-definition) разделе ниже.

## <a name="the-visual-basic-60-support-lifetime"></a>Время существования поддержку Visual Basic 6.0

Поддержка и/или доставки в поддерживаемых версиях Windows двоичных файлов среды выполнения Visual Basic 6.0 не изменить политику поддержки интегрированная среда разработки Visual Basic 6.0 или Visual Studio 6.0 IDE в целом. Эти продукты выходят из расширенной поддержкой 8 апреля 2008 г.

Сведения о жизненном цикле поддержки продуктов корпорации Майкрософт можно найти на http://support.microsoft.com/gp/lifepolicy. В рамках этого жизненного цикла поддержки Майкрософт будет продолжать поддержки среды выполнения Visual Basic 6.0 в поддерживаемых версиях Windows для поддержки время существования этих операционных систем. Это означает, например, что среда выполнения Visual Basic 6.0 будет поддерживаться в Windows Server 2003 до июня 2008 г. для поддержки и июня 2013 г. для расширенной поддержки.
Дополнительные сведения о жизненном цикле поддержки или подробные сведения о Дополнительные варианты поддержки посетите нашу страницу поддержки в http://www.microsoft.com/support.

## <a name="64-bit-windows"></a>64-разрядной версии Windows

Файлы среды выполнения Visual Basic 6.0, 32-разрядной. Эти файлы поставляются в 64-разрядных операционных системах Windows ссылки в следующей таблице. в среде эмуляции WOW только поддерживаются VB6 32-разрядных приложений и компонентов. 32-разрядные компоненты также должна быть размещена в процессы 32-разрядное приложение.

Интегрированная среда разработки Visual Basic 6.0 никогда не предлагают в собственный 64-разрядной версии, а также 32-разрядных интегрированной среды разработки поддерживается на 64-разрядной версии Windows. Не VB6 разработки на 64-разрядной версии Windows или любой собственного архитектуры, отличные от 32-разрядной и не будут поддерживаться.

## <a name="windows-7"></a>Windows 7

С момента первоначального выпуска данное заявление о поддержке операционной системы Windows 7 был освобожден. Этот документ был обновлен для уточнения поддержки корпорации Майкрософт для VB6 на Windows 7.

Среда выполнения VB6 будет поставляться и будут поддерживаться в течение времени существования операционной системы в Windows 7. Продолжать использовать только 32-разрядных файлов среды выполнения Visual Basic 6.0, и все компоненты должны размещаться в процессах 32-разрядное приложение.

## <a name="windows-81"></a>Windows 8.1

С момента первоначального выпуска данное заявление о поддержке операционной системы Windows 8.1 был освобожден. Этот документ был обновлен для уточнения поддержки корпорации Майкрософт для VB6 на Windows 8.1.

Среда выполнения VB6 будет поставляться и будут поддерживаться в течение времени существования операционной системы в Windows 8.1. Продолжать использовать только 32-разрядных файлов среды выполнения Visual Basic 6.0, и все компоненты должны размещаться в процессах 32-разрядное приложение. Могут считать, что статьи поддержки для Windows 8.1 одинаково как для Windows 7.

## <a name="windows-10"></a>Windows 10

С момента первоначального выпуска данное заявление о поддержке операционной системы Windows 10 был освобожден. Этот документ был обновлен для уточнения поддержки корпорации Майкрософт для VB6 в Windows 10.

Среда выполнения VB6 будет поставляться и будут поддерживаться в течение времени существования операционной системы в Windows 10. Продолжать использовать только 32-разрядных файлов среды выполнения Visual Basic 6.0, и все компоненты должны размещаться в процессах 32-разрядное приложение. Могут считать, что статьи поддержки для Windows 10 одинаково как для Windows 8.1.

## <a name="windows-server-2008"></a>Windows Server 2008

С момента первоначального выпуска данное заявление о поддержке операционной системы Windows Server 2008 был освобожден. Этот документ был обновлен для уточнения поддержки корпорации Майкрософт для VB6 на Windows Server 2008.

Среда выполнения VB6 будет поставляться и будут поддерживаться в течение времени существования операционной системы в Windows Server 2008. Продолжать использовать только 32-разрядных файлов среды выполнения Visual Basic 6.0, и все компоненты должны размещаться в процессах 32-разрядное приложение.

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

С момента первоначального выпуска данное заявление о поддержке операционной системы Windows Server 2008 R2 была снята. Этот документ был обновлен для уточнения поддержки корпорации Майкрософт для VB6 на Windows Server 2008 R2.

Среда выполнения VB6 будет поставляться и будут поддерживаться в Windows Server 2008 R2 в течение времени существования операционной системы. Продолжать использовать только 32-разрядных файлов среды выполнения Visual Basic 6.0, и все компоненты должны размещаться в процессах 32-разрядное приложение. Могут считать, что статьи поддержки для Windows Server 2008 R2 одинаково как для Windows Server 2008.

## <a name="windows-server-2012"></a>Windows Server 2012

С момента первоначального выпуска данное заявление о поддержке операционной системы Windows Server 2012 был освобожден. Этот документ был обновлен для уточнения поддержки корпорации Майкрософт для VB6 на Windows Server 2012.

Среда выполнения VB6 будет поставляться и будут поддерживаться в течение времени существования операционной системы в Windows Server 2012. Продолжать использовать только 32-разрядных файлов среды выполнения Visual Basic 6.0, и все компоненты должны размещаться в процессах 32-разрядное приложение. Могут считать, что статьи поддержки для Windows Server 2012 одинаково как для Windows Server 2008 R2.

## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

С момента первоначального выпуска данное заявление о поддержке операционной системы Windows Server 2012 R2 был освобожден. Этот документ был обновлен для уточнения поддержки корпорации Майкрософт для VB6 на Windows Server 2012 R2.

Среда выполнения VB6 будет поставляться и будут поддерживаться в Windows Server 2012 R2 в течение времени существования операционной системы. Продолжать использовать только 32-разрядных файлов среды выполнения Visual Basic 6.0, и все компоненты должны размещаться в процессах 32-разрядное приложение. Могут считать, что статьи поддержки для Windows Server 2012 R2 одинаково как для Windows Server 2012.

## <a name="windows-server-2016"></a>Windows Server 2016

С момента первоначального выпуска данное заявление о поддержке операционной системы Windows Server 2016 был освобожден. Этот документ был обновлен для уточнения поддержки корпорации Майкрософт для VB6 на Windows Server 2016.

Среда выполнения VB6 будет поставляться и будут поддерживаться в течение времени существования операционной системы в Windows Server 2016. Продолжать использовать только 32-разрядных файлов среды выполнения Visual Basic 6.0, и все компоненты должны размещаться в процессах 32-разрядное приложение. Могут считать, что статьи поддержки для Windows Server 2016 одинаково как для Windows Server 2012 R2.

## <a name="supported-windows-operating-system-versions"></a>Поддерживаемые версии операционной системы Windows

Дополнительные сведения об операционных системах, которые содержат определенный уровень поддержки для VB6. 

|Операционная система Windows|VB6 Поддерживаемые среды выполнения</br>Файлы, входящим в Windows имеется поддержка?|VB6 Поддерживаемые Rutime</br>Дополнительные файлы</br>для распространения с приложением поддерживают?| Интегрированная среда разработки VB6 имеет поддержку?|
|---|---|---|---|
|Все 32-разрядных выпусков Windows 10|Да *|Да *|Нет|
|Windows 10, все 64-разрядные выпуски (WOW)|Да * </br> 32-разрядных приложений, работающих в режиме WOW только|Да* </br> 32-разрядных приложений, работающих в режиме WOW только|Нет|
|Windows 8.1, все 32-разрядные версии|Да *|Да *|Нет|
| Windows 8.1, все 64-разрядные выпуски (WOW)|Да * </br> 32-разрядных приложений, работающих в режиме WOW только|Да* </br> 32-разрядных приложений, работающих в режиме WOW только|Нет|
|Все 32-разрядные выпуски Windows 7|Да *|Да *|Нет|
|Windows 7, все 64-разрядные выпуски (WOW)|Да * </br> 32-разрядных приложений, работающих в режиме WOW только|Да * </br> 32-разрядных приложений, работающих в режиме WOW только|Нет|
|Windows Server 2016 все 64-разрядные выпуски (WOW)|Да* </br> 32-разрядных приложений, работающих в режиме WOW только|Да* </br> 32-разрядных приложений, работающих в режиме WOW только|Нет|
|Все 64-разрядные выпуски (WOW) для Windows Server 2012 R2<br>Windows Server 2012, все 64-разрядные выпуски (WOW)|Да* </br> 32-разрядных приложений, работающих в режиме WOW только|Да* </br> 32-разрядных приложений, работающих в режиме WOW только|Нет|
|Windows Server 2008 R2, x64 все выпуски (WOW)</br>Windows Server 2008, все x64 выпуски (WOW)|Да * </br> 32-разрядных приложений, работающих в режиме WOW только|Да * </br> 32-разрядных приложений, работающих в режиме WOW только|Нет|
|Все 32-разрядные выпуски Windows Server 2008,|Да *|Да *|Нет|


> [!NOTE]
> &#42;  Поддержка среды выполнения VB6 ограничивается жизненный цикл поддержки Windows.  Например если целевой ОС расширенная поддержка, VB6 не может иметь более высокий уровень поддержки, чем расширенная поддержка.  [Таблицы фактов жизненного цикла поддержки Windows](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet) содержит жизненного цикла Дополнительные сведения о предыдущих и текущих версий Windows.

## <a name="visual-basic-60-runtime-usage-inside-vba-and-office"></a>Использование среды выполнения Visual Basic 6.0 внутри VBA и Office

Visual Basic для приложений или VBA, является различных технологий обычно используются для автоматизации приложения и макросы внутри других приложений, чаще всего в приложениях Microsoft Office. VBA поставляется как часть Office, и поэтому поддержка VBA регулируется политика поддержки для Microsoft Office. Однако существуют ситуации, когда используется VBA для вызова или разместить двоичных файлов среды выполнения Visual Basic 6.0 и элементы управления. В таких ситуациях Visual Basic 6.0 поддерживается файлов среды выполнения в операционной системе и список расширенных файлов также поддерживаются, если используются в среде поддерживаемых VBA.

Для сценариев среды выполнения VB6 поддерживаться внутри VBA все следующие должны выполняться условия.

- Версия операционной системы узла среда выполнения VB. по-прежнему поддерживается.
- Версия узла Office для VBA по-прежнему поддерживается.
- Одни файлы среды выполнения по-прежнему поддерживаются.

## <a name="visual-basic-script-vbscript"></a>Скрипт Visual Basic (VBScript)

VBScript не связан с Visual Basic 6.0 и данное заявление о поддержке. Однако VBScript в настоящее время поставляется как часть Windows 7, Windows 8.1, Windows 10, Windows Server 2008 R2, Windows Server 2012 R2 и Windows Server 2016 включая и регулируется жизненный цикл поддержки операционной системы.

## <a name="third-party-components"></a>Компоненты сторонних разработчиков

Корпорация Майкрософт не может для обеспечения поддержки сторонних компонентов, таких как элементы управления OCX и ActiveX. Пользователям, рекомендуется связаться с исходной поставщиком управления сведения о поддержке для этих компонентов.

## <a name="reporting-issues-with-vb-60-applications-running-on-windows"></a>Сообщить о возникших проблемах с приложениями VB 6.0, работающей под управлением Windows

Разработчики, которые планируется использовать Visual Basic 6.0 с помощью одного из перечисленных операционных систем Windows установите этой операционной системы и начать тестирования совместимости приложений с помощью исходного приложения приемочного тестирования.

Если проблемы с приложением Visual Basic 6.0, запущенной на одном из перечисленных операционных систем Windows, выполните на обычные каналы технической поддержки, чтобы сообщить о проблеме.

## <a name="supported-and-shipping-in-windows"></a>Поддерживаемые и доставки в Windows

| | | | |
|---|---|---|---|
|ATL.dll|         msadcor.dll|     msorcl32.dll|   ole2.dll|
|Asycfilt.dll|    Msadcs.dll|      Msvbvm60.dll|   Ole32.dll|
|Comcat.dll|      msadds.dll|      Msvcirt.dll|    Oleaut32.dll|
|версия|     msaddsr.dll|     Msvcrt.dll|     Oleaut32.dll|
|dbnmpntw.dll|    msader15.dll|    Msvcrt40.dll|   Oledb32.dll|
|DCOMCNFG.exe|    Msado15.dll|     Mtxdm.dll|      oledb32r.dll|
|Dllhost.exe|     msador15.dll|    MtxOCI.dll|     oledlg.dll|
|Ds16gt.dll|      msadrh15.dll|    Odbc16gt.dll|   olepro32.dll|
|ds32gt.dll|      mscpxl32.dll|    Odbc32.dll|     olethk32.dll|
|expsrv.dll|      msdadc.dll|      Odbc32gt.dll|   Regsvr32.exe|
|hh.exe|          Msdaenum.dll|    Odbcad32.exe|   rpcns4.dll|
|Hhctrl.ocx|      msdaer.dll|      Odbccp32.cpl|   Rpcrt4.dll|
|IMAGEHLP.dll|    MSDAORA.dll|     Odbccp32.dll|   Scrrun.dll|
|iprop.dll|       msdaosp.dll|     ODBCCR32.dll|   Secur32.dll|
|Itircl.dll|      msdaprst.dll|    odbccu32.dll|   simpdata.tlb|
|Itss.dll|        MSDAPS.dll|      odbcint.dll|    SQLOLEDB.dll|
|mfc40.dll|       msdasc.dll|      odbcji32.dll|   Sqlsrv32.dll|
|Mfc42.dll|       MSDASQL.dll|     odbcjt32.dll|   stdole2.tlb|
|mfc42enu.dll|    msdasqlr.dll|    Odbctrac.dll|   stdole32.tlb|
|msadce.dll|      msdatsrc.tlb|    oddbse32.dll|   Storage.dll|
|msadcer.dll|     msdatt.dll|      odexl32.dll|    VBAJET32.dll|
|msadcf.dll|      Msdfmap.dll|     odfox32.dll|    vfpodbc.dll|
|msadcfr.dll|     Msdfmap.ini|     odpdx32.dll|                |
|Msadco.dll|      msjtes40.dll|    odtext32.dll|               |

## <a name="supported-runtime-files-to-distribute-with-your-application"></a>Поддерживаемые среды выполнения файлы для распространения с приложением

| | | | |
|---|---|---|---|
|comct232.ocx |msbind.dll   |msdbrptr.dll  |msstdfmt.dll| 
|comct332.ocx |mscdrun.dll  |msflxgrd.ocx  |Msstkprp.dll| 
|Comctl32.ocx |Mschrt20.ocx |mshflxgd.ocx  |mswcrun.dll|  
|COMDLG32.ocx |mscomct2.ocx |mshtmpgr.dll  |Mswinsck.ocx| 
|dbadapt.dll  |MSCOMCTL.ocx |MSINET.ocx    |picclp32.ocx| 
|dbgrid32.ocx |mscomm32.ocx |Msmapi32.ocx  |richtx32.ocx| 
|dblist32.ocx |msdatgrd.ocx |Msmask32.ocx  |sysinfo.ocx|  
|mci32.ocx    |msdatlst.ocx |msrdc20.ocx   |tabctl32.ocx| 
|msadodc.ocx  |msdatrep.ocx |Msrdo20.dll

## <a name="unsupported-but-supported-and-compatible-updates-or-upgrades-are-available"></a>Не поддерживается, поддерживаемых и совместимый обновления доступны, но

| | | | |
|---|---|---|---|
|dao350.dll|   msexch35.dll| msjter35.dll| msrepl35.dll|
|Mdac_typ.exe| msexcl35.dll| msjtor35.dll| Mstext35.dll|
|MSChart.ocx|  msjet35.dll|  msltus35.dll| msxbse35.dll|
|msdaerr.dll|  msjint35.dll| Mspdox35.dll| odbctl32.dll|
|msdatl2.dll|  msjt4jlt.dll| msrd2x35.dll| oledb32x.dll|

## <a name="unsupported-runtime-files"></a>Файлы среды CLR не поддерживается

| | | | |
|---|---|---|---|
|anibtn32.ocx| spin32.ocx|   rpcltscm.dll|  rdocurs.dll|
|graph32.ocx|  gauge32.ocx|  rpcmqcl.dll|   vbar332.dll|
|keysta32.ocx| gswdll32.dll| rpcmqsvr.dll|  visdata.exe|
|autmgr32.exe| ciscnfg.exe|  RPCSS.exe|     vsdbflex.srg|
|autprx32.dll| Olecnv32.dll| dbmsshrn.dll|  threed32.ocx|
|racmgr32.exe| rpcltc1.dll|  dbmssocn.dll|  MSWLess.ocx|
|racreg32.dll| rpcltc5.dll|  windbver.exe|  tlbinf32.dll|
|grid32.ocx|   rpcltccm.dll| msderun.dll|   TriEdit.dll|
|msoutl32.ocx| rpclts5.dll|  odkob32.dll|

## <a name="localization-support-binaries"></a>Двоичные файлы для поддержки локализации

Следующие двоичные файлы необходимы для поддержки приложений Visual Basic 6.0, работающих в локализованных версиях операционной системы Windows. Они поддерживаются, но не поставляются в Windows. Эти файлы должны прилагаться к установке приложения.

### <a name="supported-runtime-files-to-distribute-with-your-application"></a>Поддерживаемые среды выполнения файлы для распространения с приложением

|JPN|KOR|CHT|CHS|
|---|---|---|---|
|mfc42jpn.dll|  mfc42kor.dll|  mfc42cht.dll|  mfc42chs.dll|
|scrrnjp.dll|   scrrnko.dll|   scrrncht.dll|  scrrnchs.dll|
|vb6jp.dll|     vb6ko.dll|     vb6cht.dll|    vb6chs.dll|
|cmct2jp.dll|   cmct2ko.dll|   cmct2cht.dll|  cmct2chs.dll|
|cmct3jp.dll|   cmct3ko.dll|   cmct3cht.dll|  mscc2chs.dll|
|mscc2jp.dll|   mscc2ko.dll|   mscc2cht.dll|  cmct3chs.dll|
|cmctljp.dll|   cmctlko.dll|   cmctlcht.dll|  cmctlchs.dll|
|cmdlgjp.dll|   cmdlgko.dll|   mscmccht.dll|  mscmcchs.dll|
|mscmcjp.dll|   mscmcko.dll|   cmdlgcht.dll|  cmdlgchs.dll|
|dbgrdjp.dll|   dbgrdko.dll|   dbgrdcht.dll|  dbgrdchs.dll|
|dblstjp.dll|   dblstko.dll|   dblstcht.dll|  dblstchs.dll|
|mcijp.dll|     mciko.dll|     mcicht.dll|    mcichs.dll|
|msadnjp.dll|   msadnko.dll|   msadncht.dll|  msadnchs.dll|
|adodcjp.dll|   adodcko.dll|   adodccht.dll|  adodcchs.dll|
|mschtjp.dll|   mschtko.dll|   mschtcht.dll|  mschtchs.dll|
|msch2jp.dll|   msch2ko.dll|   msch2cht.dll|  msch2chs.dll|
|mscomjp.dll|   mscomko.dll|   mscomcht.dll|  mscomchs.dll|
|datgdjp.dll|   datgdko.dll|   datgdcht.dll|  datgdchs.dll|
|datlsjp.dll|   datlsko.dll|   datlscht.dll|  datlschs.dll|
|datrpjp.dll|   datrpko.dll|   datrpcht.dll|  datrpchs.dll|
|dbrprjp.dll|   dbrprko.dll|   dbrprcht.dll|  dbrprchs.dll|
|flxgdjp.dll|   flxgdko.dll|   flxgdcht.dll|  flxgdchs.dll|
|mshfgjpn.dll|  mshfgkor.dll|  mshfgcht.dll|  mshfgchs.dll|
|htmprjp.dll|   htmprko.dll|   htmprcht.dll|  htmprchs.dll|
|inetjp.dll|    inetko.dll|    inetcht.dll|   inetchs.dll|
|msmpijp.dll|   msmpiko.dll|   msmpicht.dll|  msmpichs.dll|
|msmskjp.dll|   msmskko.dll|   msmskcht.dll|  msmskchs.dll|
|rdc20jp.dll|   rdc20ko.dll|   rdc20cht.dll|  rdc20chs.dll|
|rdo20jp.dll|   rdo20ko.dll|   rdo20cht.dll|  rdo20chs.dll|
|stdftjp.dll|   stdftko.dll|   stdftcht.dll|  stdftchs.dll|
|mswcrjp.dll|   mswcrko.dll|   mswcrcht.dll|  mswcrchs.dll|
|winskjp.dll|   winskko.dll|   winskcht.dll|  winskchs.dll|
|pcclpjp.dll|   pcclpko.dll|   pcclpcht.dll|  pcclpchs.dll|
|rchtxjp.dll|   rchtxko.dll|   rchtxcht.dll|  rchtxchs.dll|
|sysinjp.dll|   sysinko.dll|   sysincht.dll|  sysinchs.dll|
|tabctjp.dll|   tabctko.dll|   tabctcht.dll|  tabctchs.dll|

|ITA|FRA|ESP|DEU|
|---|---|---|---|
|mfc42ita.dll|  mfc42fra.dll|  mfc42esp.dll|  mfc42deu.dll|
|scrrnit.dll|   scrrnfr.dll|   scrrnes.dll|   scrrnde.dll|
|vb6it.dll|     vb6fr.dll|     vb6es.dll|     vb6de.dll|
|cmct2it.dll|   cmct2fr.dll|   cmct2es.dll|   cmct2de.dll|
|mscc2it.dll|   mscc2fr.dll|   mscc2es.dll|   mscc2de.dll|
|cmct3it.dll|   cmct3fr.dll|   cmct3es.dll|   cmct3de.dll|
|cmctlit.dll|   cmctlfr.dll|   cmctles.dll|   cmctlde.dll|
|mscmcit.dll|   mscmcfr.dll|   mscmces.dll|   mscmcde.dll|
|cmdlgit.dll|   cmdlgfr.dll|   cmdlges.dll|   cmdlgde.dll|
|dbgrdit.dll|   dbgrdfr.dll|   dbgrdes.dll|   dbgrdde.dll|
|dblstit.dll|   dblstfr.dll|   dblstes.dll|   dblstde.dll|
|mciit.dll|     mcifr.dll|     mcies.dll|     mcide.dll|
|msadnit.dll|   msadnfr.dll|   msadnes.dll|   msadnde.dll|
|adodcit.dll|   adodcfr.dll|   adodces.dll|   adodcde.dll|
|mschtit.dll|   mschtfr.dll|   mschtes.dll|   mschtde.dll|
|msch2it.dll|   msch2fr.dll|   msch2es.dll|   msch2de.dll|
|mscomit.dll|   mscomfr.dll|   mscomes.dll|   mscomde.dll|
|atgdit.dll|    datgdfr.dll|   datgdes.dll|   datgdde.dll|
|datlsit.dll|   datlsfr.dll|   datlses.dll|   datlsde.dll|
|datrpit.dll|   datrpfr.dll|   datrpes.dll|   datrpde.dll|
|dbrprit.dll|   dbrprfr.dll|   dbrpres.dll|   dbrprde.dll|
|flxgdit.dll|   flxgdfr.dll|   flxgdes.dll|   flxgdde.dll|
|mshfgit.dll|   mshfgfr.dll|   mshfges.dll|   mshfgde.dll|
|htmprit.dll|   htmprfr.dll|   htmpres.dll|   htmprde.dll|
|inetit.dll|    inetfr.dll|    inetes.dll|    inetde.dll|
|msmpiit.dll|   msmpifr.dll|   msmpies.dll|   msmpide.dll|
|msmskit.dll|   msmskfr.dll|   msmskes.dll|   msmskde.dll|
|rdc20it.dll|   rdc20fr.dll|   rdc20es.dll|   rdc20de.dll|
|rdo20it.dll|   rdo20fr.dll|   rdo20es.dll|   rdo20de.dll|
|stdftit.dll|   stdftfr.dll|   stdftes.dll|   stdftde.dll|
|mswcrit.dll|   mswcrfr.dll|   mswcres.dll|   mswcrde.dll|
|winskit.dll|   winskfr.dll|   winskes.dll|   winskde.dll|
|pcclpit.dll|   pcclpfr.dll|   pcclpes.dll|   pcclpde.dll|
|rchtxit.dll|   rchtxfr.dll|   rchtxes.dll|   rchtxde.dll|
|sysinit.dll|   sysinfr.dll|   sysines.dll|   sysinde.dll|
|tabctit.dll|   tabctfr.dll|   tabctes.dll|   tabctde.dll|

