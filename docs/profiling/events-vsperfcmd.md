---
title: "Параметр Events (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Параметр Events (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметр **Events** программы VSPerfCmd.exe позволяет управлять ведением журнала трассировки событий Windows.  Данные трассировки событий Windows сохраняются в ETL\-файле, который отличается от файла данных профилировщика.  Эти данные можно просмотреть в отчете с помощью команды [VSPerfReport](../profiling/vsperfreport.md) \/summary:etw.  
  
 Параметр **Events** можно использовать в любой момент времени перед вызовом команды **Shutdown** программы VSPerfCmd для остановки профилирования.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### Параметры  
 **On**&#124;**Off**  
 Запускает или останавливает сбор данных события.  
  
 `Guid`  
 Идентификатор GUID элемента управления поставщика.  
  
 `ProviderName`  
 Имя поставщика, созданного с помощью инструментария управления Windows \(WMI\).  
  
 `Flags`  
 Значение флагов с префиксом "0x", заданное поставщиком событий.  
  
 `Level`  
 Задает количество собранных данных.  `Level` определяется поставщиком событий.  
  
 Параметр **Events** распознает в качестве имен поставщиков следующие ключевые слова ядра.  
  
 **Process**  
 События процесса  
  
 **Thread**  
 События потока  
  
 **Image**  
 События загрузки и выгрузки образов  
  
 **Disk**  
 События ввода\-вывода на диске  
  
 **File**  
 События ввода\-вывода в файле  
  
 **Hardfault**  
 Ошибки страниц физической памяти  
  
 **Pagefault**  
 Ошибки страниц ОЗУ  
  
 **Network**  
 Сетевые события  
  
 **Registry**  
 События доступа к реестру  
  
 Необходимо заметить, что Kernel Provider можно только включить.  До завершения работы монитора невозможно отключить этот поставщик или изменить его флаги.  
  
## Заметки  
  
> [!NOTE]
>  При возникновении событий трассировки событий Windows среды CLR для отчета представления трассировки собираются также дополнительные данные о запуске.  Чтобы исключить события запуска из отчета, используйте следующую команду:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Поскольку события запуска не перечислены в MOF\-файле, то, если их не исключить, они отображаются в отчете в виде идентификаторов GUID.  Дополнительные сведения см. на этой странице веб\-сайта корпорации Майкрософт: [Образец Файла MOF](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)