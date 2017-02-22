---
title: "Метка | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Метка
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметр VSPerfCmd.exe **Mark** вставляет указанные данные в файл данных профилирования.  Метка может быть перечислена в отдельном отчете VSPerfReport или в представлении отчета "Метки" пользовательского интерфейса профилировщика.  **Mark** можно использовать для указания начальных и конечных точек в фильтрах отчетов и представлений.  
  
 Параметр **Mark** должен быть единственным параметром, указанным в командной строке.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]   
```  
  
#### Параметры  
 `MarkID`  
 Определенное пользователем целое число, указанное в качестве идентификатора метки в представлениях и отчетах профилировщика.  `MarkID` не обязательно должен быть уникальным.  
  
 `MarkName`  
 \(Не обязательно\) Определенная пользователем строка, указанная в качестве имени метки в представлениях и отчетах профилировщика.  Если параметр `MarkName` не определен, поле "Имя метки" в списке остается пустым.  Строки, содержащие пробелы или косую черту \("\/"\), заключаются в кавычки.  
  
## Пример  
 В примере вставлена метка с идентификатором 123 и именем "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)