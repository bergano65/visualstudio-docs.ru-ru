---
title: "Средства производительности в приложениях Windows 8 и Windows Server 2012 | Документы Майкрософт"
ms.custom: 
ms.date: 06/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: baf12bba10dfba15f10d75fd1f7a4cdc4000e441
ms.openlocfilehash: a5d885f8604bdb52907adae4f231b41e0881017f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/21/2017

---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Средства производительности в приложениях Windows 8 и Windows Server 2012
Возможности расширенной безопасности, появившиеся в Windows 8 и Windows Server 2012, требовали значительных изменений в способе, которым средства производительности Visual Studio собирают данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. Этот раздел описывает изменения средств производительности, начиная с платформ Windows 8 и Windows Server 2012.
  
> [!NOTE]
>  Средства производительности в других поддерживаемых версиях Windows (Windows 7, Windows Server 2008 R2) не изменились.
  
##  <a name="BKMK_In_this_topic"></a> Содержание раздела  
 [Сбор данных в приложениях для Магазина Windows из интегрированной среды разработки Visual Studio](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Сбор данных в приложениях, выполняющихся на рабочем столе в Windows 8 или в Windows Server 2012, из интегрированной среды разработки Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
-   [Сбор данных в приложениях, выполняющихся на рабочем столе в Windows 8 или в Windows Server 2012, с помощью выборки из интегрированной среды разработки Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
 [Профилирование из командной строки](#BKMK_Profiling_from_the_command_line)  
  
 [Сбора данных уровневого взаимодействия (TIP)](#BKMK_Collecting_tier_interaction__TIP__data)  
  
##  <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a> Сбор данных в приложениях для Магазина Windows из интегрированной среды разработки Visual Studio  
 При профилировании приложения для Магазина Windows, написанного на языке JavaScript и HTML 5, собираются данные инструментирования для кода javascript. При профилировании приложения для Магазина Windows или компонента, написанного на Visual C++, Visual C# или Visual Basic, собираются данные выборки для машинного и управляемого кода. Вы можете профилировать приложение локально или на удаленном компьютере.  
  
 Эти функции и параметры профилирования не поддерживаются при профилировании приложений для Магазина Windows:  
  
-   Профилирование приложений JavaScript с помощью метода выборки.  
  
-   Профилирование управляемого и машинного кода с помощью метода инструментирования.  
  
-   Профилирование параллелизма  
  
-   Профилирование памяти .NET  
  
-   Профилирование уровневого взаимодействия (TIP)  
  
-   Параметры выборки, например установка интервала времени и события выборки, а также сбор дополнительных данных счетчика производительности.  
  
-   Параметры инструментирования, такие как сбор данных производительности и счетчиков Windows, или указание дополнительных параметров командной строки.  
  
 Дополнительные сведения о профилировании приложений для Магазина Windows см. в следующих разделах.  
  
 [Запуск приложений для Магазина Windows на локальном компьютере](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
 [Запуск приложений Магазина Windows на удаленном компьютере](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
 [Средства профилирования](profiling-tools.md)  
  
-   [Память JavaScript](../profiling/javascript-memory.md)
  
-   [Профилирование кода Visual C++, Visual C# и Visual Basic в приложениях для Магазина Windows на локальном компьютере](http://msdn.microsoft.com/en-us/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
-   [Профилирование кода Visual C++, Visual C# и Visual Basic в приложениях для Магазина Windows на удаленном устройстве](http://msdn.microsoft.com/en-us/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
-   [Анализ данных о производительности кода Visual C++, Visual C# и Visual Basic в приложениях для Магазина Windows](http://msdn.microsoft.com/en-us/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a> Сбор данных в приложениях, выполняющихся на рабочем столе в Windows 8 или в Windows Server 2012, из интегрированной среды разработки Visual Studio  
 Профилирование с помощью метода инструментирования не изменено для Windows 8.  
  
 Профилирование уровневого взаимодействия (TIP) с помощью метода выборки не поддерживается.  
  
###  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a> Сбор данных в приложениях, выполняющихся на рабочем столе в Windows 8 или в Windows Server 2012, с помощью выборки из интегрированной среды разработки Visual Studio  
 Эти функции и параметры профилирования не поддерживаются при профилировании приложения Windows 8 для настольных систем или приложения Windows Server 2012 с помощью метода выборки:
  
-   Профилирование уровневого взаимодействия (TIP). Поддерживается сбор данных TIP с помощью метода инструментирования.
  
-   Параметры выборки, например установка интервала времени и события выборки, а также сбор дополнительных данных счетчика производительности.  
  
##  <a name="BKMK_Profiling_from_the_command_line"></a> Профилирование из командной строки  
 Используйте две следующие программы командной строки для сбора данных профилирования на устройствах Windows 8 и Windows Server 2012, в том числе тех, на которых не установлен Visual Studio.  
  
|Имя программы|Описание|  
|---------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|Сбор данных профилирования из приложений Магазина Windows и сбор примерных данных профилирования из приложений Windows 8 для настольных систем и приложений Windows Server 2012.|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|Сбор данных профилирования инструментирования, параллелизма и уровневого взаимодействия из приложений, которые выполняются на рабочем столе Windows 8 или Windows Server 2012. Сбор всех типов данных профилирования из предыдущих версий Windows.|  
  
 Обе программы устанавливаются с помощью Visual Studio для использования на локальном компьютере.  
  
 Для профилирования приложений на устройствах, на которых не установлен Visual Studio, выполните одно из следующих действий.  
  
-   Загрузите программы командной строки как часть инструментов удаленной отладки для Visual Studio с [веб-сайта MSDN](http://go.microsoft.com/fwlink/?LinkID=219549).  
  
-   Скопируйте и запустите программу установки инструментов автономного профилировщика с компьютера Visual Studio. Программы установки находятся в папке *%VSInstallDir%* **\Team Tools\Performance Tools\Setups** . Выберите программу установки для операционной системы удаленного компьютера (x86 или x64).  
  
> [!NOTE]
>  Для сбора данных профилирования TIP необходимо установить автономный профилировщик с компьютера с Visual Studio на удаленный компьютер.  
  
 Следующие функции и параметры профилирования не поддерживаются при профилировании приложений Windows 8 Windows Server 2012 из командной строки.  
  
-   Сбор данных из веб-приложений Windows 8 и Windows Server 2012 с помощью метода выборки с [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).  
  
-   Сбор данных выборки с помощью VsPerfCmd.exe.  
  
-   Параметры выборки, например установка интервала времени и события выборки, а также сбор дополнительных данных счетчика производительности.  
  
##  <a name="BKMK_Collecting_tier_interaction__TIP__data"></a> Сбора данных уровневого взаимодействия (TIP)  
 Профилирование уровневого взаимодействия позволяет получить дополнительные сведения о времени выполнения функций многоуровневых приложений, взаимодействующих с базой данных посредством служб ADO.NET. Данные собираются только для синхронных вызовов функций.  
  
 **Выпуски Visual Studio**  
  
 Данные профилирования уровневого взаимодействия можно собирать с помощью [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]или [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)]. Однако данные профилирования уровневого взаимодействия можно просматривать только в [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] и [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
 **Windows 8 или Windows Server 2012**  
  
1.  Чтобы собрать данные об уровневом взаимодействии из приложений, выполняющихся на рабочем столе Windows 8 или Windows Server 2012, необходимо использовать метод инструментирования.  
  
2.  Вы не можете собрать данные об уровневом взаимодействии для приложений для Магазина Windows.  
  
3.  Данные об уровневом взаимодействии можно включить во все методы профилирования на других поддерживаемых версиях Windows.  
  
 **Мастер производительности и обозреватель производительности**  
  
 Необходимо добавить параметр коллекции данных об уровневом взаимодействии в сеанс профилирования из обозревателя производительности. Необходимо также добавить проект, исполняемый файл или веб-сайт к узлу целевого объекта в "Обозревателе производительности". См. раздел [Сбор данных взаимодействия уровней](../profiling/collecting-tier-interaction-data.md).  
  
 **Сбор данных об уровневом взаимодействии на удаленном компьютере**  
  
 Чтобы собрать данные об уровневом взаимодействии на удаленном компьютере, необходимо скопировать файл **vs_profiler_***\<Платформа>***_***\<Язык>***.exe** из папки *%VSInstallDir%***\Team Tools\Performance Tools\Setups** на компьютере с Visual Studio на удаленный компьютер и установить его. Нельзя использовать средства профилирования в пакете загрузки [Удаленная отладка](../debugger/remote-debugging.md).  
  
 Для сбора данных профилирования можно использовать [VSPerfCmd](../profiling/vsperfcmd.md) или [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) .  
  
 **Отчеты TIP**  
  
 Данные об уровневом взаимодействии можно просматривать только в [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] или [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] IDE. Получение отчетов об уровневом взаимодействии (TIP) на основе файлов с помощью [VSPerfReport](../profiling/vsperfreport.md) недоступно.  
  
## <a name="see-also"></a>См. также  
 [Обозреватель производительности](../profiling/performance-explorer.md)   
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)
