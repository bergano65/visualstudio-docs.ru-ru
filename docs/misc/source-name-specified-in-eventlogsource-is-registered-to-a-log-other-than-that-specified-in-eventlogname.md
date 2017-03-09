---
title: "Имя источника, указанное в EventLogSource, зарегистрировано в журнале, отличном от указанного в EventLogName | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Имя источника, указанное в EventLogSource, зарегистрировано в журнале, отличном от указанного в EventLogName
`EventLog` пытается сослаться на источник, который зарегистрирован в другом журнале. Для добавления записей в журнал событий необходимо задать свойство <xref:System.Diagnostics.EventLog.Source%2A>. Свойство <xref:System.Diagnostics.EventLog.Source%2A> регистрирует компонент в журнале событий в качестве допустимого источника записей. Один источник может быть связан только с одним журналом событий одновременно \(и поэтому может добавлять записи только в него\).  
  
 По умолчанию при попытке добавить запись в журнал без предварительной регистрации компонента в качестве разрешенного источника система автоматически регистрирует его в этом журнале, используя значение свойства <xref:System.Diagnostics.EventLog.Source%2A> в качестве строки источника.  
  
### Исправление ошибки  
  
-   Убедитесь в том, что источник зарегистрирован в соответствующем журнале. Для этого используйте метод <xref:System.Diagnostics.EventLog.CreateEventSource%2A> или одну из его перегрузок, чтобы указать строку, однозначно идентифицирующую компонент в журнале событий.  
  
## См. также  
 [Administering Event Logs](http://msdn.microsoft.com/ru-ru/35f53238-bdd2-417b-acd8-2fd9f7397f18)   
 [Event Log References](http://msdn.microsoft.com/ru-ru/4af0661c-6c96-49f4-961d-b26ed9bc3e87)   
 [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/ru-ru/948ff920-a739-4e66-a191-ee951512d42c)   
 [How to: Remove an Event Source](http://msdn.microsoft.com/ru-ru/bc66c900-4b8a-426a-b8e2-17031a20167e)