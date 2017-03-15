---
title: "Невозможно получить поток для журнала | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrApplicationLog_ExhaustedPossibleStreamNames"
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно получить поток для журнала
Невозможно получить поток для журнала. Потенциальные имена файлов, основанные на \<имя\>, уже используются.  
  
 Классу <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> не удалось создать файл журнала, так как все возможные имена файлов журнала на основе \<имя\> уже используются.  
  
 Наличие слишком большого количества файлов журнала может быть признаком проблем с архитектурой приложения. Дополнительные сведения содержатся в документации по классу <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>.  
  
### Исправление ошибки  
  
1.  Установите свойство <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> в значение <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> или <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption>, чтобы включить метку даты в имя файла журнала.  
  
2.  Архивируйте существующие журналы и удалите их с компьютера, чтобы разрешить объекту <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> создавать новые журналы.  
  
## См. также  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>   
 [Объект My.Application.Log](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [Объект My.Log](/dotnet/visual-basic/language-reference/objects/my-log-object)