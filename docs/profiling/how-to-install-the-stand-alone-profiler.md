---
title: "Практическое руководство. Установка изолированного профилировщика | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "средства повышения производительности, установка изолированного профилировщика"
  - "средства профилирования, самостоятельный профилировщик"
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Практическое руководство. Установка изолированного профилировщика
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предусмотрен изолированный профилировщик для запуска из командной строки, который может выполняться без установки интегрированной среды разработки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Подобная ситуация возникает в том случае, если для установки среды разработки на компьютере нет необходимости или возможности.  Например, не следует устанавливать среду разработки на производственном веб\-сервере.  
  
> [!NOTE]
>  При использовании автономного профилировщика для сбора данных о производительности для веб\-сайта ASP.NET, средство командной строки [Средство VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) предпочтительнее средства [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### Установка изолированного профилировщика  
  
1.  Найдите установщик изолированного профилировщика \(vs\_profiler.exe\) на установочном носителе [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в каталоге, включающем папки \\Standalone Profiler, и запустите его.  
  
2.  Добавьте в системный путь пути для файлов vsintr.exe и msdis150.dll.  
  
    > [!NOTE]
    >  При установке [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] по умолчанию файлы vsinstr.exe и msdis150.dll расположены в папке \\Program Files\\Visual Studio 9\\Team Tools\\Performance Tools.  
  
3.  В командной строке введите **VSInstr**.  
  
    > [!NOTE]
    >  Если отображаются сведения об использовании файла vsinstr.exe, установка выполнена правильно.  Если выводится сообщение об ошибке, в котором указывается, что файл vsinstr.exe или одна из его зависимостей не найдены, следует проверить правильность установки пути, как описано на шаге 2.  
  
4.  Настройте серверов символов, задав для переменной **\_NT\_SYMBOL\_PATH** значение **symsrv\*symsrv.dll\*c:\\localcache\*http:\/\/msdl.microsoft.com\/download\/symbols**  
  
5.  После установки сервера символов с помощью системных переменных среды запустите средства профилирования из нового окна командной строки.  Это позволит активировать новые переменные среды.  В окне командной строки введите следующую команду:  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  Подробные инструкции по настройке пакета сервера символов см. в разделе [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Для сериализации символов в файл данных профилирования \(VSP\) используется средство [VSPerfReport](../profiling/vsperfreport.md):  Следует использовать переключатели **VSPerfReport \/summary:all \/packsymbols**.  Если добавление символов в файл данных не была выполнено, убедитесь, что переменная среды \_NT\_SYMBOL\_PATH установлена.  
  
## См. также  
 [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Пошаговое руководство. Профилирование из командной строки с помощью выборки](../Topic/Walkthrough:%20Command-Line%20Profiling%20Using%20Sampling.md)   
 [Пошаговое руководство. Профилирование из командной строки с помощью метода инструментирования](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)