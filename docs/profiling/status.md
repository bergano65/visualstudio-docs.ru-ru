---
title: "Состояние | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Состояние
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметр VSPerfCmd.exe **Status** позволяет вывести сведения о состоянии профилировщика и процессов, которые в настоящий момент профилируются.  
  
 Параметр **Status** должен быть единственным параметром, указанным в командной строке.  Для отображения состояния необходимо инициализировать профилировщик параметром VSPerfCmd.exe **Start**.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### Параметры  
 Нет  
  
## Заметки  
 Параметр **Status** позволяет вывести следующие сведения о состоянии профилировщика.  
  
 **Output File Name**  
 Путь и имя текущего файла данных профилировщика.  
  
 **Collection Mode**  
 SAMPLE или TRACE  
  
 **Maximum Processes**  
 Максимальное число процессов, которые можно профилировать одновременно, и количество активных процессов.  
  
 **Maximum Threads**  
 Максимальное число потоков, которые можно профилировать одновременно.  
  
 **Number of Buffers**  
 Количество буферов памяти, выделенных для записи данных профилирования.  
  
 **Size of Buffers**  
 Размер буфера памяти в байтах.  
  
 Параметр **Status** позволяет вывести следующие сведения о состоянии каждого процесса, который в настоящий момент профилируется.  
  
 **Process**  
 Имя профилируемого процесса.  
  
 **Process ID**  
 Системный идентификатор процесса.  
  
 **Num Threads**  
 Количество выполняющихся в настоящее время потоков.  
  
 **Start\/Stop Count**  
 Основной внутренний счетчик профилировщика для управления сбором данных этого процесса.  Для сбора данных счетчик должен быть равен единице.  Управление числом команд начала и остановки может осуществляться с помощью интерфейсов API профилировщика и параметров VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** и **ThreadOff**.  
  
 **Suspend\/Resume Count**  
 Дополнительный внутренний счетчик профилировщика для управления сбором данных этого процесса.  Для сбора данных счетчик должен быть меньше или равен нулю.  Управление счетчиком **Suspend\/Resume** возможно только с помощью интерфейсов API профилировщика.  
  
 **Users with access rights to monitor**  
 Перечисляет имена пользователей, имеющих доступ к профилировщику.  Дополнительным пользователям можно предоставить доступ с помощью параметра VSPerfCmd.exe **Admin**  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)