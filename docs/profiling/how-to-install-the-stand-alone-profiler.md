---
title: "Практическое руководство. Установка автономного профилировщика | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0799a5da2b1596c79a57a6960283c62fca709a8a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Практическое руководство. Установка изолированного профилировщика
В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предусмотрен автономный профилировщик для запуска из командной строки, который может выполняться без установки интегрированной среды разработки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Подобная ситуация возникает в том случае, если для установки среды разработки на компьютере нет необходимости или возможности. Например, среду разработки не следует устанавливать на рабочем веб-сервере.  
  
> [!NOTE]
>  При использовании автономного профилировщика для сбора данных по производительности веб-сайта ASP.NET программа командной строки [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) предпочтительнее программы [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-install-the-stand-alone-profiler"></a>Установка автономного профилировщика  
  
1.  Найдите установщик автономного профилировщика (vs_profiler.exe) на установочном носителе [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в каталоге, включающем папки \Standalone Profiler, и запустите его.  
  
2.  Добавьте пути к файлам vsintr.exe и msdis150.dll в системный путь.  
  
    > [!NOTE]
    >  При установке [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] по умолчанию файлы vsinstr.exe и msdis150.dll находятся в папке \Program Files\Visual Studio 10\Team Tools\Performance Tools.  
  
3.  В командной строке введите **VSInstr**.  
  
    > [!NOTE]
    >  Если отображаются сведения об использовании файла vsinstr.exe, установка выполнена правильно. Если выводится сообщение об ошибке, в котором указывается, что файл vsinstr.exe или одна из его зависимостей не найдены, проверьте правильность задания путей, как описано в шаге 2.  
  
4.  Настройте сервер символов, присвоив переменной **_NT_SYMBOL_PATH** значение **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols**.  
  
5.  После настройки сервера символов с помощью системных переменных среды запустите средства профилирования из нового окна командной строки. Это позволит применить новые переменные среды. В окне командной строки введите следующую команду:  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  Подробные инструкции по настройке пакета сервера символов см. в разделе [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Для сериализации символов в файл данных профилирования (VSP) используется средство [VSPerfReport](../profiling/vsperfreport.md). Следует использовать параметры **VSPerfReport /summary:all /packsymbols**. Если символы в файл данных не вставлены, убедитесь в том, что переменная среды _NT_SYMBOL_PATH задана.  
  
## <a name="see-also"></a>См. также  
 [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Пошаговое руководство. Профилирование из командной строки с помощью выборки](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Пошаговое руководство. Профилирование из командной строки с помощью метода инструментирования](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)