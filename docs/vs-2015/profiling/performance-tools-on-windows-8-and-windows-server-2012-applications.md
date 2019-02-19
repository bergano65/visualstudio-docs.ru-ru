---
title: Средства производительности в приложениях Windows 8 и Windows Server 2012 | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c13472fc1322701fefada53ee3e94156f35e8072
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757975"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Средства производительности в приложениях Windows 8 и Windows Server 2012
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым средства производительности Visual Studio собирают данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. В этом разделе описаны изменения средств производительности на платформах Windows 8 и Windows Server 2012.  
  
> [!NOTE]
>  Средства производительности в других поддерживаемых версиях Windows (Windows 7, Windows Server 2008 R2) не изменились.  
  
##  <a name="BKMK_In_this_topic"></a> Содержание раздела  
 [Сбор данных в приложениях для Магазина Windows из интегрированной среды разработки Visual Studio](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Сбор данных в приложениях, выполняющихся на рабочем столе в Windows 8 или в Windows Server 2012, из интегрированной среды разработки Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
- [Сбор данных в приложениях, выполняющихся на рабочем столе в Windows 8 или в Windows Server 2012, с помощью выборки из интегрированной среды разработки Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
  [Профилирование из командной строки](#BKMK_Profiling_from_the_command_line)  
  
  [Сбора данных уровневого взаимодействия (TIP)](#BKMK_Collecting_tier_interaction__TIP__data)  
  
##  <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a> Сбор данных в приложениях для Магазина Windows из интегрированной среды разработки Visual Studio  
 При профилировании приложения для Магазина Windows, написанного на языке JavaScript и HTML 5, собираются данные инструментирования для кода javascript. При профилировании приложения для Магазина Windows или компонента, написанного на Visual C++, Visual C# или Visual Basic, собираются данные выборки для машинного и управляемого кода. Вы можете профилировать приложение локально или на удаленном компьютере.  
  
 Эти функции и параметры профилирования не поддерживаются при профилировании приложений для Магазина Windows:  
  
- Профилирование приложений JavaScript с помощью метода выборки.  
  
- Профилирование управляемого и машинного кода с помощью метода инструментирования.  
  
- Профилирование параллелизма  
  
- Профилирование памяти .NET  
  
- Профилирование уровневого взаимодействия (TIP)  
  
- Параметры выборки, например установка интервала времени и события выборки, а также сбор дополнительных данных счетчика производительности.  
  
- Параметры инструментирования, такие как сбор данных производительности и счетчиков Windows, или указание дополнительных параметров командной строки.  
  
  Дополнительные сведения о профилировании приложений для Магазина Windows см. в следующих разделах центра разработчиков Windows:  
  
  [Запуск приложений для Магазина Windows на локальном компьютере](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
  [Запуск приложений Магазина Windows на удаленном компьютере](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
  [Анализ производительности приложений](http://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)  
  
- [Время выполнения функций JavaScript](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03)  
  
- [Время выполнения функций JavaScript на удаленном устройстве](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
  
- [Анализ данных о времени выполнения функций JavaScript](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
  
- [Профилирование кода Visual C++, Visual C# и Visual Basic в приложениях для Магазина Windows на локальном компьютере](http://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
- [Профилирование кода Visual C++, Visual C# и Visual Basic в приложениях для Магазина Windows на удаленном устройстве](http://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
- [Анализ данных о производительности кода Visual C++, Visual C# и Visual Basic в приложениях для Магазина Windows](http://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
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
  
 Данные профилирования уровневого взаимодействия можно собирать с помощью [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]или [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Однако данные профилирования уровневого взаимодействия можно просматривать только в [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] и [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **Windows 8 или Windows Server 2012**  
  
1. Чтобы собрать данные об уровневом взаимодействии из приложений, выполняющихся на рабочем столе Windows 8 или Windows Server 2012, необходимо использовать метод инструментирования.  
  
2. Вы не можете собрать данные об уровневом взаимодействии для приложений для Магазина Windows.  
  
3. Данные об уровневом взаимодействии можно включить во все методы профилирования на других поддерживаемых версиях Windows.  
  
   **Мастер производительности и обозреватель производительности**  
  
   Необходимо добавить параметр коллекции данных об уровневом взаимодействии в сеанс профилирования из обозревателя производительности. Необходимо также добавить проект, исполняемый файл или веб-сайт к узлу целевого объекта в "Обозревателе производительности". См. раздел [Сбор данных взаимодействия уровней](../profiling/collecting-tier-interaction-data.md).  
  
   **Сбор данных об уровневом взаимодействии на удаленном компьютере**  
  
   Чтобы собирать сведения об уровневом взаимодействии на удаленный компьютер, необходимо скопировать и установить файл **vs\_profiler\_**_\<платформа>_**\_**_\<язык>_**.exe** из папки _%VSInstallDir%_**\Team Tools\Performance Tools\Setups**, расположенный на компьютере с Visual Studio. Невозможно использовать средства профилирования в пакете загрузки [Инструменты удаленной отладки для Visual Studio](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) .  
  
   Для сбора данных профилирования можно использовать [VSPerfCmd](../profiling/vsperfcmd.md) или [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) .  
  
   **Отчеты TIP**  
  
   Данные об уровневом взаимодействии можно просматривать только в [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] или [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] IDE. Отчеты об уровневом взаимодействии на основе файлов с помощью [VSPerfReport](../profiling/vsperfreport.md) недоступны.  
  
## <a name="see-also"></a>См. также раздел  
 [Обозреватель производительности](../profiling/performance-explorer.md)   
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)
