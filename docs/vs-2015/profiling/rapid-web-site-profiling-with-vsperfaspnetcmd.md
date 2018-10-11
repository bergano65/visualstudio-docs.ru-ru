---
title: Быстрое профилирование веб-сайтов с помощью средства VSPerfASPNETCmd | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a16bef2afa14d992300649d4ec9ffd9752def099
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880686"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Быстрое профилирование веб-сайтов с помощью средства VSPerfASPNETCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Быстрое профилирование веб-сайтов с помощью средства VSPerfASPNETCmd](https://docs.microsoft.com/visualstudio/profiling/rapid-web-site-profiling-with-vsperfaspnetcmd).  
  
Средство командной строки **VSPerfASPNETCmd** позволяет без труда профилировать веб-приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. У этой программы меньше параметров по сравнению с программой командной строки [VSPerfCmd](../profiling/vsperfcmd.md), в ней не нужно задавать переменные среды и не требуется перезагрузка компьютера. Средство **VSPerfASPNETCmd** предпочтительнее использовать для профилирования с помощью отдельного профилировщика. Дополнительные сведения см. в разделе [Практическое руководство. Установка изолированного профилировщика](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
>  Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. См. статью [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 В некоторых сценариях, например при сборе данных о параллелизме или в случае приостановки и возобновления профилирования, более предпочтительным методом профилирования является использование **VSPerfCmd**.  
  
> [!NOTE]
>  Программы командной строки средств профилирования расположены в подкаталоге \Team Tools\Performance Tools каталога установки [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. На 64-разрядных компьютерах следует использовать средство VSPerfASPNETCmd, расположенное в 32-разрядном каталоге \Team Tools\Performance Tools. Для использования средств командной строки профилировщика необходимо добавить путь к этим средствам в переменную среды PATH окна командной строки или указать этот путь при вызове команды. Дополнительные сведения см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="profiling-an-aspnet-application"></a>Профилирование приложения ASP.NET  
 Для профилирования веб-приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] введите одну из команд, описанных в следующих разделах. Будет запущен веб-сайт, и профилировщик начнет собирать данные. Запустите приложение, а затем закройте браузер. Чтобы остановить профилирование, нажмите клавишу ВВОД в окне командной строки.  
  
> [!NOTE]
>  По умолчанию командная строка после команды **vsperfaspnetcmd** не возвращается. Для принудительного возврата командной строки можно воспользоваться командой **/nowait**. См. раздел [Использование параметра /nowait](#UsingNoWait).  
  
## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Сбор статистики приложения с помощью метода выборки  
 Выборка — это метод профилирования, используемый по умолчанию в средстве **VSPerfASPNETCmd**, который не нужно задавать в командной строке. Следующая командная строка позволяет собрать статистику для заданного веб-приложения:  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Сбор подробных данных о времени с помощью метода инструментирования  
 С помощью следующей командой строки можно собрать подробные данные о времени в динамически компилируемом веб-приложении [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]:  
  
 **vsperfaspnetcmd /trace**  *websiteUrl*  
  
 Для профилирования статически скомпилированных DLL-файлов в веб-приложении следует инструментировать файлы с помощью средства командной строки [VSInstr](../profiling/vsinstr.md). Команда/trace vsperfaspnetcmd позволит включить данные из инструментированных файлов.  
  
## <a name="to-collect-net-memory-data"></a>Сбора данных об использовании памяти .NET  
 Параметр **/Memory** позволяет собирать данные о выделении объектов в памяти .NET, а также сведения о времени существования этих объектов. Сбор данных о выделении — это режим, используемый по умолчанию для параметра данных **/Memory**, который не нужно задавать в командной строке.  
  
 **vsperfaspnetcmd /memory** *websiteUrl*  
  
 Чтобы в дополнение к данным о выделении собрать данные о времени существования объекта, воспользуйтесь параметром **Lifetime**:  
  
 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*  
  
 Кроме того, можно воспользоваться параметром **/Trace** для включения подробных данных о времени вместе с данными о памяти .NET:  
  
 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`  
  
## <a name="to-collect-tier-interaction-data"></a>Сбор данных взаимодействия уровней  
  
> [!WARNING]
>  Данные профилирования уровневого взаимодействия можно собирать с помощью [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] или [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Однако данные профилирования уровневого взаимодействия можно просматривать только в [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] и [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
>   
>  Для сбора данных TIP в Windows 8 или Windows Server 2012 необходимо использовать параметр инструментирования (**/trace**).  
  
 Чтобы собрать данные об уровневом взаимодействии вместе с данными выборки, воспользуйтесь командной строкой:  
  
 **vsperfaspnetcmd /tip** `websiteUrl`  
  
 Чтобы собрать данные об уровневом взаимодействии вместе с данными инструментирования, воспользуйтесь командной строкой:  
  
 **vsperfaspnetcmd /trace /tip** *websiteUrl*  
  
 Чтобы собрать данные об уровневом взаимодействии вместе с данными о памяти .NET, воспользуйтесь командной строкой:  
  
 **vsperfaspnetcmd /memory**[**:lifetime**] **/tip**_websiteUrl_  
  
##  <a name="UsingNoWait"></a> Использование параметра /nowait  
 По умолчанию командная строка после команды **vsperfaspnetcmd** не возвращается. Для принудительного возврата командной строки можно воспользоваться следующим синтаксисом. Затем в окне командной строки можно выполнить другие операции. Для завершения профилирования воспользуйтесь параметром **/shutdown** в отдельной команде **vsperfaspnetcmd**.  
  
 Чтобы начать профилирование, воспользуйтесь следующей командной строкой:  
  
 **vsperfaspnetcmd** [*/Options*] **/nowait**_websiteUrl_  
  
 Для завершения профилирования воспользуйтесь следующей командной строкой:  
  
 **vsperfaspnetcmd /shutdown** *websiteUrl*  
  
## <a name="additional-options"></a>Дополнительные параметры  
 Во все команды, перечисленные ранее в этом разделе, за исключением команды **vsperfaspnetcmd/shutdown**, можно добавить любой из следующих параметров.  
  
|Параметр|Описание:|  
|------------|-----------------|  
|**/Output:** `VspFile`|По умолчанию файл данных профилирования (VSP) создается в текущем каталоге с именем файла **PerformanceReport.vsp**. Параметр /output позволяет задать другое расположение, имя файла или и то, и другое.|  
|**/PackSymbols:Off**|По умолчанию VsPerfASPNETCmd встраивает символы (имена функций и параметров и т. п.) в VSP-файл. Встраивание символов может привести к существенному увеличению файла данных профилирования. При обращении к PDB-файлам, содержащим такие символы, в процессе анализа данных следует воспользоваться параметром /packsymbols:off, чтобы отключить встраивание символов.|



